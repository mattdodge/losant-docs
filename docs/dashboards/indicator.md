# Indicator

The Indicator block displays a color and message of your choosing based on the result returned from a [gauge query](/workflows/data/gauge-query/).

![Indicator Example](/images/dashboards/indicator-example.png "Indicator Example")

## Query Configuration

It is possible to build multiple data queries into your indicator block, and the result of each query will be available when writing conditions and displaying data. You must create at least one query, and each must have at least one device or one device tag selected, along with one attribute from which to return data. A duration must also be selected, though the value defaults to "Last received data point".

![Indicator Query Configuration](/images/dashboards/indicator-query-config.png "Indicator Query Configuration")

In the event that a duration other than "Last received data point" is selected, or if (within a query) more than one device is selected or at least one device tag is selected, it will also be necessary to select an aggregation method. This is the mathematical operation by which your query will boil down all data from the selected devices and duration into a single value. The default aggregation method is `MEAN`.

## Query Result

For each query, there are two variables returned, which can be accessed via Handlebars [string templates](/workflows/accessing-payload-data/#string-templates) and [expressions](/workflows/accessing-payload-data/#expressions):

*   `value-i`, which is the result of the query if a result is returned. Depending on the query's construction and the attribute type, the result's type can take one of many forms. (See below.)
*   `time-i`, which is a [JavaScript Date object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date) representing the time the value was reported. If the value is being aggregated, this will always be equal to the dashboard's last refresh time; otherwise, it will be equal to the time the queried device last reported state.

In the two examples above, `i` represents the index of the query. The full variable name is printed along with each query configuration.

Another variable can be referenced no matter how many queries return data: `lastUpdated`, which is the latest time any of the queries returned a value. A human-readable "from now" version of this variable is printed in the bottom left corner of the block.

Depending on the type of attribute selected, the query's value can return data of varying types ...

### Number Attributes

Numbers are the easiest attribute type to work with as, no matter the aggregation method, they will always return a number.

### Boolean Attributes

If querying for the last received data point of a boolean attribute for a single device, the result will return as `true` or `false`.

If the boolean attribute is being aggregated – as the result of a query across multiple devices or a larger duration – then all `false` points will be treated as a **0** and all `true` points will be treated as a **1**. Then, the result will return as a **number** representing the following:

*   `FIRST` and `LAST` aggregations will return as `true` or `false`.
*   `MIN` and `MAX` aggregations will return as `0` (false) or `1` (true).
*   `MEAN` aggregations will return as a number between 0 and 1 (inclusive), which is the average of all data points across the query.
*   `SUM` will return as a whole number greater than or equal to 0, which is equal to the number of `true` data points across the query.
*   `COUNT` will return as a whole number greater than or equal to 0, which is equal to the total number of data points across the query.

### GPS and String Attributes

When requesting the last received data point of a single device, the result will return as a string.

When requesting aggregated data for such an attribute ...

* `FIRST` and `LAST` aggregations will return the first or last data point collected across the query
* `COUNT` aggregations will return as a number representing the total number of data points across the query
* All other queries will return as `undefined`

To expand a condition for editing, simply click the header. You can also choose to expand or collapse all conditions by clicking the link at the top right corner of the section.

## Conditions

When a query returns a result, that result is evaluated against all the set conditions, starting with the top-most item in the list. The first condition that returns `true` has its corresponding label and color displayed within the indicator block.

![Indicator Conditions](/images/dashboards/indicator-condition-config.png "Indicator Conditions")

### Creating Conditions

You may set as many conditions to test the result against as you wish. New conditions can be added by clicking the "Add Condition" button, and the conditions can be reordered by dragging and dropping them up and down the list. Conditions can also be removed by clicking the "Delete" icon to the right of each panel's title.

### Condition Configuration

Each condition takes three parameters:

*   **Expression**: The [expression](/workflows/accessing-payload-data/#expressions) to evaluate. All of your query values (e.g. `{{value-0}}` and `{{value-1}}`) and times (e.g. `{{time-0}}` and `{{time-1}}`), as well as the `{{lastUpdated}}` variable, are available to compare against one another or against a static value.
*   **Label**: The text to display within the indicator block. This field is optional, and may include [string templates](/workflows/accessing-payload-data/#string-templates) formatting your query variables as well as [Markdown](http://commonmark.org/help/). The color of the text will automatically switch between black and white depending on the block's chosen background color.
*   **Color**: The background color of the indicator block. Default is green.

## Default Condition

![Indicator Default Condition](/images/dashboards/indicator-default-condition.png "Indicator Default Condition")

If none of the set conditions return `true`, the indicator block will display a default label and color. Configuration is the same as for a condition, except no expression is set.
