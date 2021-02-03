---
title: WHat the heck is Parameters and filters in Redash?
type: post
tags: [redash, coding]
readtime: true
---

Let's start off with what is parameters. Parameters are very useful for user interactivity for analytics, where they can pass interactive quereis.
Redash used in the parameters for analytics.
It is very helpful feature for giving a interactive nature for queries, instead of just saying stats based on certain predefined variables,
parameters allow users to run queries for insights on months, time ranges or values they are interested in. Redash queries support it for both SQL,
mongodb queries and even more as Redash supports 30+ databases even though I haven't personally tried it out.

The best way to write Redash queries with parameters is first to create a simple hard coded query with value and generalise the query with the input you want to have.

eg: select * from text where color = 'Red'

select * from text where color == {{ }}

There are about 7 types of query parameters ranging from simple string and nos to be passed as input, to even option to specify dates as parameters.

filter is like select list in a html form, where we can select the values corresponding to potential values in the row associated with it
- Not widely usely, but is helpful


As a side note, Datasette recently implemented this parameter feature which is super useful, which is something I have been wanting to explore for a long time now.
