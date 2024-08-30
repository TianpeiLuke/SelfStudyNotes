---
tags:
  - code
  - code_snippet
  - SQL/cradle
keywords: 
topics: 
language: SQL
date of note: 2024-04-18
---

## Code Snippet Summary

>[!important] 
>Using **job run date** to define the time interval for SQL query


## Code

>[!quote]
>Defining fact table inputs is identical to defining dimension table inputs with 1 difference: *each partition in a fact table represents a single day*, so Cradle needs to know which day partitions to fetch in the form of a date range.  For example, if you want to query `D_CUSTOMER_ORDER_ITEM_DETAILS` for the past 30 days from each job run's #datasetDate inclusive, add the filters in your WHERE clause and Cradle will choose the right partitions using push-down filtering.

- `CAST('${date}' AS TIMESTAMP)`: cast the job run date `{date}` as a *timestamp variable*
- using `>=` and `<=` 

```sql
SELECT * FROM tab1 
WHERE order_day >= CAST('${date}' AS TIMESTAMP) - INTERVAL 30 DAYS
    AND order_day <= CAST('${date}' AS TIMESTAMP);
```

- or using `BETWEEN ... AND`

```sql
SELECT * FROM tab1 
WHERE order_day BETWEEN CAST('${date}' AS TIMESTAMP) - INTERVAL 30 DAYS    
	AND CAST('${date}' AS TIMESTAMP);
```


>[!important]
>1) Pay attention to your table's **partition keys**, and always *filter on those keys* unless you have a really good reason not to
> 
> 2) **Cast** all your date fields as *timestamps*, e.g. cast('${date}' as timestamp) and cast('2018-01-01' as timestamp)
> 
> 3) Use **`INTERVAL`** for **ranges**
> 
> 4) Review *stdout log* on the driver node in the first few minutes of the job execution to make sure the filters are being applied to the table

### `#datasetDate`

There's another way to format dates you'll see a lot on Sage and in the wikis:

```plain
 ["${REGION_ID}", #{formatDate((#datasetDate), 'YYYY-MM-dd')}] 
```

- This type of date formatting is almost always used in the EDX *input node definition*, and are **not supported in SQL**. There's [other guides about this topic](https://w.amazon.com/index.php/Dryad/Getting%20Started/Dryad%20SQL%20Users%20Guide#HTemplatevariables2Cdynamicdates2CandSPELexpressions), but usually you're better off just using the EDX Key Builder for cleanly formatting EDX keys. 


### Advanced Usage

- **#datasetDate** is an instance of the open source Joda [DateTime](https://code.amazon.com/packages/Loganalyzer/blobs/ebb23e51eca0877a7060e7cac555e20ef9f62ea6/--/lib/joda-time-2.9.7/src/main/java/org/joda/time/DateTime.java#L73) class.
- The function formatDate is a helper function that is defined within Cradle's orchestration [here](https://code.amazon.com/packages/OmniFlowControlSubsystem/blobs/0ac4cc689db61fa16bcfd92ae4488d90b2d3e246/--/src/com/amazon/rps/omniflow/control/util/JodaDateTimeFunctions.java#L29), along with some other helper functions.
- All of these expressions, typically used in EDX nodes where they are resolved, are evaluated using Spring Expression Language (SpEL). The documentation can be found here [https://docs.spring.io/spring/docs/current/spring-framework-reference/core.html#expressions](https://docs.spring.io/spring/docs/current/spring-framework-reference/core.html#expressions)
- The capabilities of SpEL and Joda and other java classes/whatever is in our classpath can all be combined to powerful effects in your closures.

-----------
##  Recommended Notes


- Cradle Docs: 
	- [Handling Dates in Cradle](https://w.amazon.com/bin/view/BDT/Products/Cradle/Docs/HandlingDates)

- [[Date Filter in Amazon Redshift SQL]]