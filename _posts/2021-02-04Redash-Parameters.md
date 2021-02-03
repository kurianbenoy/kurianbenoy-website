---
title: What are Parameters and filters in Redash?
type: post
tags: [redash, coding]
readtime: true
---

Let's start off with what is parameters. Parameters are very useful for providing user interactivity for analytics, where they can pass interactive queries.
instead of just saying stats based on certain predefined variables,
parameters allow users to run queries for insights on months, time ranges or values they are interested in. Redash supports queries with parameters in both SQL, mongoDB
and even more as Redash supports 30+ Databases. To use parameters just use `{{ }}` and [checkout the guide for more details](https://redash.io/help/user-guide/querying/query-parameters).

The best way to write Redash queries with parameters is first to create a simple hard coded query with value and generalise the query with the input you want to have.

eg: select * from text where color = 'Red'

select * from text where color == "{{ serach_term }}"

There are about 10 types of query parameters ranging from Text, Number to be passed as input, to even option to specify query dropdown list, dates and date ranges as parameters.

Filters are used to limit the results queries and display just the subset of rows having a particular value. Suppose you are having a data source like:

| Product | Brand | Quantity |
|-- | -- | -- |
| ArrowRoot | Britanica | 5|
| Burst | Britanica | 10 |
| Dark Fantasy | Sunflower | 5|

If you want to filter query using brand with `:` operator. For brand Britanica there are two rowss associated, while for sunflower there is just 1 row to shown


As a side note, Datasette recently implemented this parameter feature which is super useful, which is something I have been wanting to explore for a long time now.

## References

- https://redash.io/help/user-guide/querying/query-filters
- https://redash.io/help/user-guide/querying/query-parameters
