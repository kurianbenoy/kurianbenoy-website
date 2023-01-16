---
categories:
- redash
- coding
layout: post
readtime: true
title: What are Parameters and filters in Redash?
date: '2021-02-04'
---

Let's start with what are **parameters in Redash**. Parameters are useful for providing user interactivity for analytics, where they can pass interactive queries. Usually, we do most of the analytics based on certain predefined values while parameters allow users to run queries they want to generate insights on months, time ranges or values they want. Redash supports queries with parameters in both SQL, MongoDB
and even more as Redash supports 30+ Databases. To use parameters just use `{{ }}` and [checkout the guide for more details](https://redash.io/help/user-guide/querying/query-parameters).

The best way to write Redash queries with parameters is first to create a simple hardcoded query with value and generalise the query with the input you want to have.

eg: select * from text where color = 'Red'

select * from text where color == "{{ serach_term }}"

There are about ten types of query parameters ranging from Text, Number to be pass as input, to options like query dropdown list, dates and date range as parameters.

*Filters are for limiting the results queries and display just the subset of rows having a particular value*. Suppose you have a data source like:

| Product | Brand | Quantity |
|-- | -- | -- |
| ArrowRoot | Britannica | 5|
| Burst | Britannica | 10 |
| Dark Fantasy | Sunflower | 5|

If you want to filter query using a brand with `:` operator. For brand Britannica, there are two rows associated, while for sunflower there is just 1 row to be shown.


As a side note, Datasette recently implemented this parameter feature. Datasette is something I wish to explore for a long time now.

## References

- https://redash.io/help/user-guide/querying/query-filters
- https://redash.io/help/user-guide/querying/query-parameters
- https://simonwillison.net/2020/Nov/14/personal-data-warehouses/
