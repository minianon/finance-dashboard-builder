# FinBoard (Finance Dashboard Builder): Low-Level Design

For the big picture see the [High-Level Design](hld.md).

## 1. Widget model and store

```mermaid
classDiagram
  class Widget {
    id: string
    name: string
    apiUrl: string
    refreshInterval: number (seconds)
    displayMode: card | table | chart
    selectedFields: string[]
    data: any
    lastUpdated: string
    loading: boolean
    error: string | null
    useWebSocket?: boolean
    wsUrl?: string
  }
  class DashboardStore {
    widgets: Widget[]
    currentTemplate: string | null
    addWidget(widget)
    updateWidget(id, updates)
    removeWidget(id)
    reorderWidgets(widgets)
    setWidgetData(id, data, lastUpdated)
    setWidgetLoading(id, loading)
    setWidgetError(id, error)
    setCurrentTemplate(id)
    clearAllWidgets()
  }
  DashboardStore --> Widget
```

The store is persisted under `finboard-dashboard`; export / import uses `finboard-config` (`lib/storage.ts`).

## 2. Data updates

```mermaid
flowchart TB
  W[Widget mounted] --> Q{useWebSocket and wsUrl?}
  Q -->|yes| S[wsManager subscribes; each message → setWidgetData]
  Q -->|no| F[fetch apiUrl → setWidgetData]
  F --> I{refreshInterval > 0?}
  I -->|yes| T[setInterval every refreshInterval seconds → fetch again]
  I -->|no| D[done]
  F -->|error| E[setWidgetError]
```

## 3. Field handling (`lib/api-utils.ts`)

| Function | Behavior |
|---|---|
| `testApiConnection(url)` | Fetches the URL once to validate it before saving the widget |
| `flattenObject(obj)` | Turns nested JSON into dot-path keys so any field can be picked |
| `extractFields(data)` | Lists selectable paths |
| `getNestedValue(obj, path)` | Reads a dot-path value for display |

## 4. Reordering

The grid uses dnd-kit `SortableContext` with a vertical strategy and keyboard support; on drop, `arrayMove` produces the new order and `reorderWidgets` saves it.

## 5. Templates (`lib/dashboard-templates.ts`)

| Template id | Purpose |
|---|---|
| `crypto-tracker` | Bitcoin and Ethereum prices, exchange rates |
| `stock-monitor` | Market movers and major assets |
| `forex-dashboard` | Currency rates |
| `economic-calendar` | Macro indicators |
| `portfolio-tracker` | Holdings overview |
