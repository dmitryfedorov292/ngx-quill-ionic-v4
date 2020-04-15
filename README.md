# DataTable

A robust data grid component for displaying and interacting with large sets of data.

## Quicklinks
* [Usage](#usage)
* [Basic Example](#basic example)
* [Props](#props)
* [Features](#features)
  * [Action Buttons](#action-buttons)
  * [Columns](#columns)
    * [Hiding/Showing](#hiding/showing)
    * [Reordering](#reordering)
    * [Pinning](#pinning)
    * [Resizing](#resizing)
    * [Sorting](#sorting)
  * [Filters](#filters)
    * [Creating](#creating)
    * [Applying](#applying)
    * [Saving](#saving)
    * [Editing](#editing)
  * [Search](#search)
  * [Paging](#paging)
    * [Infinite Scrolling Enable/Disabled](#infinite-scrolling-enable/disabled)
    * [Starting Page](#starting-page)
    * [Display Current Page](#display-current-page)

## Usage
Import the `DataTable` component into your project:
```javascript
import DataTable from 'app/components/DataTable'
```

## Basic Example
```javascript
<DataTable
  columns={[
    {
      key: 'foo',
      name: 'Foo',
      width: 150
    },
    {
      key: 'bar',
      name: 'Bar',
      width: 150
    }
  ]}
  height="100%"
  id="test"
  infiniteScroll={false}
  items={[
    { id: 'foo1', foo: 'Test foo 1', bar: 'Test bar 1' },
    { id: 'foo2', foo: 'Test foo 2', bar: 'Test bar 2' },
    { id: 'foo3', foo: 'Test foo 3', bar: 'Test bar 3' },
    { id: 'foo4', foo: 'Test foo 4', bar: 'Test bar 4' }
  ]}
  showColumnsDropDown={false}
  showRefresh={false}
  sortable={false}
/>
```
## Props
Name  | Description | Type | Required
----- | ----------- | ---- | --------
actionButtons | Custom action buttons to display in top right corner of action bar | [ActionButton[]](#actionbutton) |
clientSideFilterEnabled | If true, client side filtering is enabled | Boolean |
clientSideSortEnabled | If true, client side sorting is enabled | Boolean |
columns | Array of Column objects to populate the DataTable columns with | [Column[]](#column) | ✓
compact | If true, row and row header height will be smaller | Boolean |
errorText | If non-empty, error message is shown | Node |
fullyControlled | If true, the items array is fully controlled by parent and paging is not handled by DataTable | Boolean |
headerLinkText | Text displayed in the header link | Node |
headerText | Text displayed in the TableTitleBar | Node |
height | Height of the table | String or Number |
hide | If true, the component is not rendered | Boolean |
id | Unique ID for the component | String | ✓
infiniteScroll | If true, infinite scrolling is enabled (default true) | Boolean |
initialLoad | If true, Preloader is rendered instead of rows | Boolean |
initialSortBy | The sort object to apply on initial render | [SortBy](#sortby) |
items | Array of item objects to populate the table rows with | [Item[]](#item) |
filters | The total number of items available from the server for the current filters | Number |
itemUpdates | Array of updates to items | Object[] |
minCharsForSearch | Defines the minimum characters before a search is initiated | Number |
minWidth | Minimum width of the table, in pixels | Number |
noResultsLink | Event handler that is fired when the link next to the "No Results" message is clicked | Function |
noResultsText | Text for link that is displayed next to the "No Results" message | Node |
onCreateFilterFolder | Event handler that is fired when a newly created filter folder is saved | Function |
onCreateFilter | Event handler that is fired when a newly created filter is saved | Function |
onDeleteFilterFolder | Event handler that is fired when a filter folder is deleted | Function |
onDeleteFilter | Event handler that is fired when a filter is deleted | Function |
onFetchData | Event handler that is fired when data is fetched | Function |
onHeaderLinkClick | Event handler that is fired when the header link is clicked | Function |
onRetryClick | Retry link when error is encountered | Function |
onRowClick | Event handler that is fired when a row is clicked | Function |
onRowSelection | Event handler that is fired when a row is selected | Function |
onUpdateFilter | Event handler that is fired when a filter is updated | Function |
operators | Array of operator objects to render as DropDownMenu inside NewFilter component | [Operator[]](#operator) |
quickSearchHighlightStyle | Style object to apply to highlighted text in the TableBody | Object |
quickSearchQuery | Current quick search query | String |
refreshCount | Increase count to refresh table | Number |
resizeableColumns | If true, the columns on the grid can be resized | Boolean |
rowHeight | Height of the rows in the data table | Number |
savedFilters | An array, a function that returns an array, or a function that returns a promise that returns an array of saved filters to render in the filters menu which can be applied to the table | [FilterFolder[]](#filterfolder) or Promise or Function |
scrollContainerStyle | Style object to apply to scroll container | Object |
selectable | If true, rows are selectable by clicking checkboxes on the row | Boolean |
shortSearchDelay | Delay to wait before executing short searches | Number |
showActionBar | If true, the table action bar (filters, group by, columns) is visible | Boolean |
showColumnsDropDown | If true, "columns" drop down menu is displayed | Boolean |
showFilters | If true, the filters dropdown is displayed and a readable filter string is displayed below the table header when filters are applied | Boolean |
showGroupBy | If true, the "Group By" menu is displayed | Boolean |
showHeader | If true, the DataTable header is displayed above the data rows | Boolean |
showHorizontalLines | If true, horizontal lines are displayed in the grid under each row | Boolean |
showLoader | If true, show paging loader | Boolean |
showQuickSearch | If true, the quick search is displayed | Boolean |
showRefresh | If true, the Refresh button is displayed | Boolean |
sortable | If true, columns sort order can be toggled by clicking the column header | Boolean |
startingFilters | Array of filters to apply to table at initial render | [Filter[]](filter)
startingPage | The starting page for API server requests | Number |
style | Style object to apply | Object |
tableBodyStyle | Style object to apply to table body | Object |
title | Title for the grid | Node |
width | Width of the table  | String or Number) |



### ActionButton
```javascript
const actionButtons = [
  {
    label: 'Foo',
    mode: 'primary',
    name: 'foo',
    onClick: () => {
      console.log('clicked Foo!')
    },
    style: { backgroundColor: 'red' }
  },
  {
    label: 'Bar',
    mode: 'secondary',
    name: 'bar',
    onClick: () => {
      console.log('clicked Bar!')
    },
    style: { backgroundColor: 'blue' }
  }
]
```

Name | Description | Type | Required
---- | ----------- | ---- | --------
label | Text displayed in the button | Node |
mode | Themed mode for the button (defaults to "primary") | String |
name | Unique name for the button, only used to generate a key to suppress React warnings | String | ✓
onClick | Event handler that fires when the button is clicked | Function |
style | Style object to apply to the Button component | Object |

### Column
```javascript
const columns = [
  {
    key: 'name.first',
    name: 'First Name',
    width: 150
  },
  {
    key: 'name.last',
    name: 'Last Name',
    width: 150
  },
  {
    key: 'email',
    name: 'Email',
    width: 150
  }
]
```

Name | Description | Type | Required
---- | ----------- | ---- | --------
cellFormat | Allows you to format a cell using a formatter function or a predefined formatter function (supported predefined formatters are specified with their `CellFormatString`, listed below). If a function is used, it will take in the original unformatted data and should return a formatted string for display. | Function or [CellFormatString](#cellformatstring) |
cellTextStyle | Style object to apply to the cell text for this column | Object |
formatConfig | Extra configuration data used by pre-defined cell formatters help render the cell | Object |
grow | If true, the column width will attempt to grow to fill window space and the original specified width for the column will become the minimum width. This property can only be applied to one column from the list of `columns`. If more than one column attempts to enable `grow`, only the first item will be used as the `grow` column. | Boolean |
key | The key to use to access the data from the given `items` objects. This key can be a path string for accessing nested object values | String | ✓
listItems | If column `type` is 'list', this array defines the list items to be used for this list | [ListItem[]](#listitem) |
name | User-facing name of the column, displayed in the table header | String | ✓
primaryKey | If true, this column is considered the primary key for the data set. If no `primaryKey` is specified, an `id` property is used as the default primary key. If no `id` property is found, unexpected behavior may occur and a console error will be logged to warn of the missing primary key | Boolean |
searchKeys | Array of keys to use when searching for this entity | String[] |
sortable | If true, the column is sortable | Boolean |
sortByKey | If specified, the column is sorted by this key instead of the `key` property used to read the cell data | String |
sticky | If true, this column is pinned to the left of the table body, allowing the user to scroll horizontally without losing sight of the sticky column. Only column can be sticky. If more than one are specified, the first will be used. | Boolean |
tableCellStyle | Style object to apply to the table cell containing this column | Object |
type | The type for the column, used to help sorting and filtering the column. If no type is specified, a primitive is expected, typically a string or number. | [ColumnType](#columntype) |
visible | If true, the column is visible in the table body. Note: this prop has no influence on the visibility of the column inside the `columns` menu. | Boolean |
disableHide | If true, this column's visibility cannot be toggled via the `columns` menu | Boolean |
width | The width of the column. Accepts any standard CSS width value string including percentages, pixel values, em values, etc. Also accepts a number value which will be assumed to be a pixel value. | Number or String | ✓

#### CellFormatString
One of
* "idCard"
* "linkButton"
* "relativeDate"
* "shortDateTime"

##### Format Config
Note: Some cell formatters need extra configuration data. The `formatConfig` property is used for these cases.

###### `idCard`
Renders an `IdCard` component, including a "title" and "subtitle" pulled from the cell data. By default, expects cell data to be an object with `title` and `subtitle` properties:
```javascript
const items = [
  {
    overview: {
      title: 'Sample',
      subtitle: 'Sample subtitle'
    },
    ...
  },
  ...
]

const columns  = [
  {
    cellFormat: 'idCard',
    key: 'overview',
    name: 'Overview'
  }
]

// Renders:
// <IdCard
//   title="Sample"
//   subtitle="Sample subtitle"
// />
```

Accepts a `formatConfig` with `titlePath` and `subtitlePath` properties. These are JSON paths for accessing nested object values and will be applied to the cell data to retrieve the title and subtitle for the `IdCard` component.

###### `linkButton`
Expects a `formatConfig` with a `callback` property. For instance:
```javascript
{
  callback: (cellData, item) => {
    console.log('clicked link with cell data', cellData, 'a part of row', item)
  }
}
```

Optionally, a `path` property can be used which describes a JSON path for accessing nested values when the cell data is an object. For instance:
```javascript
const items = [
  {
    email: 'sarah@mail.com',
    user: {
      name: {
        first: 'Sarah',
        last: 'Johnson'
      }
    }
  },
  ...
]

const columns = [
  {
    cellFormat: 'linkButton',
    formatConfig: {
      callback: user => {
        console.log(`Clicked the link for user: ${user.name.first} ${user.name.last}`)
      }
      path: 'name.first'
    },
    key: 'user',
    name: 'First Name',
    width: 150
  },
  ...
]
```

###### `relativeDate`
Expects a `formatConfig` with a `dateFormatString` property specified. For instance:
`{ dateFormatString: 'dddd, MMMM D, YYYY h:mm A' }`

###### `shortDateTime`
A valid date string, i.e. `'12/25/2018'`

#### ListItem
Name | Description | Type | Required
---- | ----------- | ---- | --------
text | Text to display for the item in the list | String | ✓
value | Value of the item | String | ✓

#### ColumnType
One of:
* "list"
* "idCard"
* "date"

##### `list`
If a `list` type is specified, the `listItems` property will also be required for this column.

##### `idCard`
If an `idCard` type is specified and client-side sorting is enabled, the column is sorted by the item's "title" property values.

##### `date`
If a `date` type is specified and client-side sorting is enabled, the column is sorted in chronological order.

### Item
Item object keys should match with the given column key values.

```javascript
const items = [
  {
    name: {
      first: 'Joe',
      last: 'Montana'
    },
    email: 'joe.montana@gmail.com'
  },
  {
    name: {
      first: 'Jerry',
      last: 'Rice'
    },
    email: 'jerry.rice@gmail.com'
  }
]
```

### SortBy
```javascript
const sortBy = {
  key: 'email',
  dir: 'asc'
}
```

Name | Description | Type | Required
---- | ----------- | ---- | --------
key | The key to sort by - must match a key from the `items` array objects | String | ✓
dir | The sort direction | [SortDirection](#sortdirection) | ✓

#### SortDirection
One of:
* "asc"
* "desc"

Worth mentioning:
* "asc" stands for "ascending" and "desc" stands for "descending". Sometimes people get confused about the implications of these descriptions when applied to a table. This is because sometimes people conflate the usage of "ascending" and "descending" to apply to the *verticality of the table itself*, rather than the logical ordering of the data. For numbers, "ascending" means starting with lower numbers and going to higher numbers. So for a simple example, numbers 1 through 10 would be sorted starting with 1, then 2, and on to 10. Since we sort relative to the TOP of the DataTable, sorting numbers 1 through 10 "ascending" would have number 1 at the top, then 2, and so on down to 10. This can be confusing because when you think about "ascending" you might think that you'd start from the bottom OF THE TABLE like you would when ascending a mountain, and would therefore put 1 at the bottom of the list, 10 on the top. I hope I haven't over complicated this issue, but the question has come up multiple times so I wanted to be clear about the expected behavior here.


### Operator
```javascript
const operators = [
  {
    execute: (value1, value2) => value1 === value2,
    stringify: (dataPoint, value) => `${dataPoint.name} Is Equal To ${value}`,
    name: 'Is Equal To',
    value: 'equals',
    valueFieldCount: 1,
    valueWrapper: '"'
  },
  {
    execute: (dataPointValue, filterValue) => dataPointValue !== filterValue,
    stringify: (dataPoint, value) => `${dataPoint.name} Is Not Equal To ${value}`,
    name: 'Is Not Equal To',
    value: 'notEquals',
    valueFieldCount: 1,
    valueWrapper: '"'
  },
  {
    execute: (value1, value2) => value1 >= value2[0] && value1 <= value2[1],
    stringify: (dataPoint, value) =>
      `${dataPoint.name} Is Between ${value[0]} And ${value[1]}`,
    valueString: value => `${value[0]} And ${value[1]}`,
    name: 'Is Between',
    value: 'between',
    valueFieldCount: 2,
    valueWrapper: '"'
  }
]
```

Name | Description | Type | Required
---- | ----------- | ---- | --------
execute | The comparator function used for determining the result of an applied condition. This function accepts two arguments: the two values to compare. | Function | ✓
name | User-facing name for the operator | String | ✓
stringify | A function used to convert the condition to a string. Could be used to generate a human-readable description or a query string for passing to a remote service, for instance. | Function | ✓
value | Unique value name for the operator, used as an identifier throughout the component, including the optional `filterOperators` whitelist specified by a condition `dataPoint` | String | ✓
valueFieldCount | The number of value fields expected for this operator. For instance, a "between" operator would have 2 value fields (a start and end), "equals" would only have 1 value field (the value we want to match), and an "is null" operator would have 0 value fields (since it is a simple null check, the user would not be expected to input any values). This number is used internally for properly filtering when client-side filtering is enabled, and is also used to properly generate the `FilterCreator` form. | Number | ✓
valueString | A function that returns a string for the current value. Essentially a stringify function scoped down to the values of the condition. This is particularly useful for generating proper human-readable strings for  operators with multiple value fields. (See the "between" operator for an example.) | Function |
valueWrapper | A string used to wrap the condition value when stringifying the condition. | String |

### FilterFolder

```javascript
const filterFolder = {
  name: 'Cool Filters',
  filters: [
    {
      name: 'Filter 1',
      conditions: [...]
    },
    {
      name: 'Filter 2',
      conditions: [...]
    }
  ]
}

Name | Description | Type | Required
---- | ----------- | ---- | --------
name | The name of the folder - this gets displayed to the user | String | yes
filters | List of filters inside this folder | [Filter[]](#filter) or [FilterFolder[]](#filterfolder) | ✓

### Filter
```javascript
const filter = {
  name: 'My Filter',
  conditions: [
    {}
  ],
  dfault: true
}
```
Name | Description | Type | Required
---- | ----------- | ---- | --------
name | The name of the filter - this gets displayed to the user | String | ✓
conditions | List of conditions that make up this filter | [Condition[]](#condition) | ✓
dfault | If true, this filter is immediately applied to the DataTable on first render. Also, yes, it is "dfault" and not "default". This is because the back-end implementation BetterCloud uses for saving filters has this spelling (because "default" is a reserved keyword for whatever data tooling they are using...?) and rather than deal with a load of brittle and confusing "default"/"dfault" transformations sprinkled throughout the code, we opted to just match the back-end implementation. This probably should be changed... | Boolean |

#### Condition
```javascript
const condition = {
  dataPoint: {
    filterOperators: ['contains', 'equals'],
    key: 'email',
    name: 'Email Address'
  },
  operator: {
    name: 'Contains',
    value: 'contains',
    valueFieldCount: 1
  },
  values: [['Chris']]
}
```

Name | Description | Type | Required
---- | ----------- | ---- | --------
dataPoint | The data point on which to apply the condition expression | [DataPoint](#condition-datapoint) | ✓
operator | The operator of the condition expression | [Operator](#operator) | ✓
values | The values to match for the condition expression | [String[][]](#values) | ✓

##### Condition DataPoint
```javascript
const dataPoint = {
  filterOperators: ['contains', 'equals'],
  key: 'email',
  name: 'Email Address'
}
```

Name | Description | Type | Required
---- | ----------- | ---- | --------
key | Unique key for the data point (which must match a key from the objects inside the `items` array prop) | String | ✓
name | User-facing name for the data point | String | ✓
filterOperators | A list of available operators to use for this data point. If this property is specified, only `Operator` objects with a `value` found in this list will be available to the user for this condition. By default, all operators used in the DataTable `operators` prop are available. | String[] |


##### Condition Operator
Same as standard [Operator](#operator)

##### Condition Values
The values property expects an 2d array of strings. The reason for this structure is because each condition can support multiple values (logically "OR"\'d together') and some condition operators support multiple values (for instance "is between" would expect both a start and end value).

So, for example, if you had a condition wherein the data point "creation date" was expected to be `between` "1/1/2018" and "2/1/2018" OR `between` "5/1/2018" and "6/1/2018", the `values` array would look like this:
```javascript
const values = [
  ['1/1/2018', '2/1/2018'],
  ['5/1/2018', '6/1/2018']
]
```



## Features

### Action Buttons
Action Buttons can be specified for the DataTable. These buttons are rendered in the top-right corner of the component, just above the table.

#### Example
```javascript
<DataTable
  actionButtons=[
    { label: 'Foo', mode: 'primary', name: 'foo' },
    { label: 'Bar', mode: 'secondary', name: 'bar' }
  ]
  columns={[
    {
      key: 'foo',
      name: 'Foo',
      width: 150
    },
    {
      key: 'bar',
      name: 'Bar',
      width: 150
    }
  ]}
  height="100%"
  id="test"
  infiniteScroll={false}
  items={[
    { id: 'foo1', foo: 'Test foo 1', bar: 'Test bar 1' },
    { id: 'foo2', foo: 'Test foo 2', bar: 'Test bar 2' },
    { id: 'foo3', foo: 'Test foo 3', bar: 'Test bar 3' },
    { id: 'foo4', foo: 'Test foo 4', bar: 'Test bar 4' }
  ]}
  showColumnsDropDown
  showRefresh={false}
  sortable={false}
/>
```

### Columns
The columns array is required for rendering your DataTable. It defines which columns to display in the table and provides configuration options for determining how to render the columns and what level of interactivity each column supports.

The simplest column object requires three key-value pairs:
* key - the unique key for the column. The value for this property MUST match a key name in each item object from the `items` array. For instance, the simple example below includes two column keys: "id" and "name". Thus, the "items" array should includes objects with "id" and "name" keys to avoid errors:
```javascript
const items = [{ id: 'foo', name: 'Foo' }, { id: 'bar', name: 'Bar' }]
```
* name - The name of the column which is displayed on the column header
* width - The default width of the column.

#### A few notes about column widths:
1. Yes, they are required, for now. There is a ticket in the FE backlog to add a default width for every column and then we will remove the requirement.
2. You may designate one (and only one!) column as a "grow" column, which means its width will grow to fill the available window space, and its "width" value will act as a minimum width.
3. No, we don't support `<table>`-style width behavior i.e. dynamically detecting minimum required width per column needed to display all content in each row for the column. There are a few reasons we don't support this:
  1. It was important for v1 of the DataTable to support user-defined column widths. In other words, we want to allow users to resize columns to match their preferred workflow habits (and save these settings). So we definitely wanted to support fixed column widths. We added this support first.
  2. As we started to discuss adding support for dynamically-determined column widths, we quickly realized there are many edge cases to support. What if a user resized some columns but not others? What if a user wanted two different columns to grow as needed, but no others? What if the user wanted one of those columns to grow at twice the rate of the other grow column? What if we added a third grow column?
  These questions spiraled further into questions about which column width values have priority over others, in what order column widths should be determined, how granular should we allow "grow" and "shrink" behaviors, etc. So, we essentially came to the conclusion that dynamically determining table widths is a complex problem and for v1 of the DataTable we could provide a simpler, more constrained experience.
  3. The truth is, although it is nice when the `<table>` algorithm for determining column width *just works* and the table looks good with no extra care given to column widths, this is often not the case for anything but the simplest of tables. For moderately advanced or busy tables, extra care must always be given to render a table in a readable, user-friendly way. Because of this, we think it is important to go ahead and force this forethought for every table. Letting a column width be generated dynamically often causes problems down the line when a value for the column is inevitably a longer string than the test data used to design the table. We also think that when cases arise that seem to require multiple "grow" columns, or so many columns that horizontal scrolling is necessary, or when all columns happen to be well-suited to dynamically generated widths... there is probably a better way. In short: we believe that using default `<table>`-style column width behavior is a design smell that probably hints at a larger UX problem for the table, and the ease and simplicity is not worth the potentially bad UX.


##### Simple Example
```javascript
const columns = [
  {
    key: 'id',
    name: 'ID',
    width: 50
  },
  {
    key: 'name',
    name: 'Name',
    width: 150
  }
]
```

#### Hiding/Showing
By default, all column objects in the columns array are rendered in the table. In some cases, you may want to include the column in the array of columns but not render the column in the table.

For instance, you may want to have a hidden "id" column as a unique key for the table that can be accessed by SEO tools but not display the column to the user. Or you may want to have a column be hidden by default but allow the user to toggle its visibility using the columns menu in the table action bar.

To do this, use the `visible` property.

```javascript
const columns = [
  {
    key: 'id',
    name: 'ID',
    visible: false,
    width: 50
  },
  {
    key: 'name',
    name: 'Name',
    width: 150
  }
]
```

#### Sorting
The DataTable supports sortable columns. You can enable/disable sorting for the entire table as well as for each column individually.

To enable or disable sorting for the DataTable, use the `sortable` prop. By default, `sortable` is set to `true`.

```javascript
<DataTable
  columns={[...]}
  id="test"
  items={[...]}
  sortable={false}
/>
```

To enable or disable sorting for an individual column, use the "sortable" property in the column object. Columns are all sortable by default.

```javascript
const columns = [
  {
    key: 'id',
    name: 'ID',
    sortable: false,
    width: 50
  },
  {
    key: 'name',
    name: 'Name',
    width: 150
  }
]
```

##### Initial SortBy

To initialize the DataTable with a specific sort configuration already applied, use the `initialSortBy` prop:
```javascript
<DataTable
  columns={[...]}
  id="test"
  items={[...]}
  initialSortBy={{
    key: 'email',
    dir: 'asc'
  }}
/>
```

##### Client-Side Sorting

The DataTable support both client-side and server-side data binding. By default, client-side sorting is enabled. If you pass a function to the `onFetchData` prop, client-side sorting is disabled and the DataTable assumes that sorting will be handled outside of the component. In order to re-enable client-side sorting for use with dynamically fetched data, use the `clientSideSortEnabled` prop:
```javascript
<DataTable
  clientSideSortEnabled
  columns={[...]}
  id="test"
  items={[...]}
  onFetchData={...}
/>
```

#### Resizing
The DataTable supports drag-and-drop column resizing.

To enable resizeable columns, use the `resizeableColumns` prop:
```javascript
<DataTable
  columns={[...]}
  id="test"
  items={[...]}
  resizeableColumns
/>
```

#### Reordering
The DataTable supports drag-and-drop reordering of columns in real-time.

Reordering columns is enabled by default as long as the columns DropDown is enabled and cannot currently be disabled without hiding the entire columns DropDown.

#### Pinning
The DataTable supports pinning a single column to the left of the table and thus allowing horizontal scrolling of the rest of the table to occur without losing sight of the pinned column.

Pinning columns is enabled by default as long as the columns DropDown is enabled and cannot currently be disabled without hiding the entire columns DropDown.

### Filters
The DataTable allows users to create, save, and apply filters to the items in the table.

The filters menu and management modal provide a UI for creating, editing, and managing filters, as well as hooks for handling the loading and saving of filters and filter folders.

Filter support is enabled by default. To hide the filters menu and disable filters, use the `showFilters` prop:
```javascript
<DataTable
  columns={[...]}
  id="test"
  items={[...]}
  showFilters={false}
/>
```

Note: Although the DataTable provides a UI for managing saved filters, the business logic that handles storing and loading saved filters is fully controlled by the parent component. It is up to the developer to listen for relevant event hooks and provide the array of saved filters for rendering.

#### Creating
A user can create a new filter by clicking the "Add Filter" item in the filters menu, or by clicking the "Get Started" button from the filter management modal.

A filter is made of one or more *conditions*. A *condition* is made of a *data point*, an *operator*, and one or more *values*. For instance, a simple english-readable condition might be something like: `when the "first name" data point "is equal" to "Chris" or "Tim"`.

A single condition is enough to create a filter, but combining multiple conditions to form more complex filters is also supported. For instance, we can add a second condition to the above example: `when "employment status" "is not equal" to "employed"`. By combining both of these conditions into a single filter, a user could quickly see a list of any non-employees named "Chris" or "Tim".

#### Applying
Once a user has added conditions to the filter, it can immediately be applied to the existing result set of the table by clicking the "Apply" button.

When a filter is applied, the filter management modal goes away, the result set re-renders only displaying items that match the filter conditions, and an human-readable description of the filter is displayed at the top of the table body (internally we call this english-language description box the `FilterDisplay` component).

#### Clearing
A user can quickly clear the currently-applied filter by clicking the "Clear" link in the `FilterDisplay`. This will clear the filter and hide the `FilterDisplay`.

#### Editing
A user can edit the currently-applied filter by clicking the "Edit" link in the `FilterDisplay`. This will display the filter management modal with the currently-applied filter conditions pre-populated. From here the user can add/remove/edit conditions and re-apply them by clicking "Apply".

#### Saving
If "Save As" is clicked in the `FilterDisplay`, the "save filter" dialog is displayed. From here, the user can name the filter, choose a folder or create a new folder in which to organize the filter, and save the new filter.

#### Event Handlers

##### onCreateFilter
The `onCreateFilter` prop is an event handler that fires when a newly created filter is saved.
```javascript
<DataTable
  columns={[...]}
  id="test"
  items={[...]}
  onCreateFilter={filter => {
    console.log('new filter created', filter)
  }}
/>
```

##### onUpdateFilter
The `onUpdateFilter` prop is an event handler that fires when a When an existing filter is saved after an update.
```javascript
<DataTable
  columns={[...]}
  id="test"
  items={[...]}
  onUpdateFilter={filter => {
    console.log('filter updated', filter)
  }}
/>
```

##### onCreateFilterFolder
The `onCreateFilterFolder` prop is an event handler that is fired when a newly created filter folder is saved.
```javascript
<DataTable
  columns={[...]}
  id="test"
  items={[...]}
  onCreateFilterFolder={folder => {
    console.log('folder created', folder)
  }}
/>
```

##### onDeleteFilterFolder
The `onDeleteFilterFolder` prop is an event handler that is fired when a filter folder is deleted.
```javascript
<DataTable
  columns={[...]}
  id="test"
  items={[...]}
  onDeleteFilterFolder={folder => {
    console.log('folder deleted', folder)
  }}
/>
```

##### onDeleteFilter
The `onDeleteFilter` prop is an event handler that is fired when a filter is deleted.
```javascript
<DataTable
  columns={[...]}
  id="test"
  items={[...]}
  onDeleteFilter={filter => {
    console.log('filter deleted', filter)
  }}
/>
```

#### Saved Filters
Since filters are fully controlled by the parent component, it is up to the developer to handle saving filters and to provide `DataTable` with an updated list of saved filters. This can be done with the `savedFilters` prop:
```javascript
<DataTable
  columns={[...]}
  id="test"
  items={[...]}
  savedFilters={[
    name: 'My Cool Filters',
    filters: [
      {
        name: 'Email contains "Chris"',
        conditions: [
          {
            dataPoint: {
              filterOperators: ['startsWith', 'contains', 'equals'],
              key: 'email',
              name: 'Email'
            },
            operator: {
              name: 'Contains',
              value: 'contains',
              valueFieldCount: 1
            },
            values: [['Chris']]
          }
        ],
        dfault: false
      }
    ]
  ]}
/>
```


#### Starting Filters
Filters can be applied to a DataTable at initial render using the `startingFilters` prop:
```javascript
<DataTable
  columns={[...]}
  id="test"
  items={[...]}
  startingFilters={[
    {
      name: 'Filter 1',
      conditions: [...]
    },
    {
      name: 'Filter 2',
      conditions: [...]
    }
  ]}
/>
```

#### Client-Side Filtering
The DataTable support both client-side and server-side data binding. By default, client-side filtering is enabled. If you pass a function to the `onFetchData` prop, client-side filtering is disabled and the DataTable assumes that filtering will be handled outside of the component. In order to re-enable client-side filtering for use with dynamically fetched data, use the `clientSideFilterEnabled` prop:
```javascript
<DataTable
  clientSideSortEnabled
  columns={[...]}
  id="test"
  items={[...]}
  onFetchData={...}
/>
```

### Search
### Paging
#### Infinite Scrolling
#### Starting Page
#### Display Current Page
