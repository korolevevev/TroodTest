### `npm start`

Runs the app in the development mode.\
Open [http://localhost:3000](http://localhost:3000) to view it in your browser.

### `ProgressBar demo`

![alt text](https://thumb.tildacdn.com/tild3433-3936-4230-a364-666363333835/-/format/webp/progress.jpg)

Input props:
1. items - data array:
[
{name: 'Sold', color: '#BD1FBE', value: 677},
{name: 'Got free', color: '#FC64FF', value: 23},
...
]
2. height - number, bar line height
3. width - number, bar line width
Total is calculated by this data (as a sum of each value), and the bar line and its legend are built basing on fraction of value to total
0-value bars are not displayed, non-zero values always have not less than 1 bar (bars amount is an integer)

### `TokenTable demo`

![alt text](https://thumb.tildacdn.com/tild6233-3739-4866-b031-306465306232/-/format/webp/image.jpg)

1. TokenTable
Input props:
1. items - data array:
[
{id: 1, name: 'Pyshky.net', status: 'green', type: 'TRST', conditions: 'x2,6 months', volume: 120000, roi: 4, free: 20, hedge: 20},
{id: 2, name: 'NFT-Flowershop', status: 'yellow', type: 'THT', conditions: 'x4,2 years', volume: 80000, roi: 23, free: 12, hedge: 0},
{id: 4, name: 'Web3 P2P University', status: 'red', type: 'TRST', conditions: 'x2,1 years', volume: 200000, roi: 6, free: 1, hedge: 0},
...
]
2. header cell of name of a column, by which the table is sorted (it can be a '-' sigh without a space before a field, which means a descending order sorting)
3. filters - an object with fields status and type, values of which corresponds to selected filters
4. onSort - function invoked on press on a line name, a field name is passed on click. If the field name equals to value of props.sort - then the field name with preceding '-' sign is passed
5. onFilter - function invoked by change of column filter, function call with filters object, where old value is changed by the new one, value of another field remains as is
6. onBuy - function invoked by pressing Buy, id value from items array of the corresponding line is passed on the invocation
Filtering:
1. Above Project column the filter (select) on status field is opened, the current value is set by props.filters.status. On change props.onFilter is called with passing the object props.filters, with updated value of status (e.g. {type: <OLD_VALUE>, status: 'green'})
2. Above Token type column type field search is opened, current value is set by props.filters.type. On change props.onFilter is invoked, with passing props.filters, with an updated type value (e.g. {status: <OLD_VALUE>, type: 'TR'})
Sorting: see props.onSort

Table data:
2. Line color and indicator color are defined by 'status' field, enum: green, yellow, red
2. Number values are displayed with formatting provided in the mockup
3. String values are displayed as is
4. Click anywhere on a line (except Buy button) must cause jumping to link /project/<id>, where <id> - is a field from items array of the corresponding line
5. Click on Buy calls props.onBuy (see props.onBuy)
