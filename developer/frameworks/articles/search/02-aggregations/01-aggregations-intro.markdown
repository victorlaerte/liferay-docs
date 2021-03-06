---
header-id: aggregations
---

# Aggregations

[TOC levels=1-4]

Aggregations take the results of a query and group the data into logical sets.
Aggregations can be composed to provide complex data summaries.

@product-ver@ has a new API that exposes 
[Elasticsearch's native Aggregation functionality](https://www.elastic.co/guide/en/elasticsearch/reference/current/search-aggregations.html). 

Currently, these aggregation types are supported:

- [Bucketing aggregations](https://www.elastic.co/guide/en/elasticsearch/reference/current/search-aggregations-bucket.html) 
    create buckets of documents based on some criterion.  They support
    sub-aggregations.
    - Supported bucket aggregations include children aggregations, date
        histogram aggregations, date range aggregations, diversified sampler
        aggregations, filter aggregations, filters aggregations, geo distance
        aggregations, geo hash grid aggregations, global aggregations, histogram
        aggregations, missing aggregations, nested aggregations, range
        aggregations, reverse nested aggregations, sample aggregations,
        significant terms aggregations, significant text aggregations, and terms
        aggregations.
- [Metrics aggregations](https://www.elastic.co/guide/en/elasticsearch/reference/current/search-aggregations-metrics.html) 
    compute metrics over a set of documents.
    - Supported metrics aggregations include average aggregations, cardinality
        aggregations, extended stats aggregations, geo bounds aggregations, geo
        centroid aggregations, max aggregations, min aggregations, percentile
        ranks aggregations, percentiles aggregations, scripted metric
        aggregations, stats aggregations, sum aggregations, top hits
        aggregations, value count aggregations, and weighted average
        aggregations. 

- [Pipeline aggregations](https://www.elastic.co/guide/en/elasticsearch/reference/current/search-aggregations-pipeline.html) 
    aggregate the output of other aggregations and their associated metrics.
    - Supported pipeline aggregations include average bucket pipeline
        aggregations, bucket metrics pipeline aggregations, bucket script
        pipeline aggregations, bucket selector pipeline aggregations, bucket
        sort pipeline aggregations, cumulative sum pipeline aggregations,
        derivative pipeline aggregations, extended stats bucket pipeline
        aggregations, max bucket pipeline aggregations, min bucket pipeline
        aggregations, moving function pipeline aggregations, percentiles bucket
        pipeline aggregations, pipeline aggregations, serial diff pipeline
        aggregations, stats bucket pipeline aggregations, and sum bucket
        pipeline aggregations. 

All the supported aggregations are found in the `portal-search-api` module's
`com.liferay.portal.search.aggregation` package.

In addition to these aggregations, other aggregation-like features are present
in the @product@ search API:

**Group By** collects search results (documents) based on a particular field.
For example, if you want to group the search results based on the asset
type (e.g., web content article, document, blog post, etc.), you can create
a search query that contains
a [com.liferay.portal.kernel.search.GroupBy](https://github.com/liferay/liferay-portal/blob/7.2.x/portal-kernel/src/com/liferay/portal/kernel/search/GroupBy.java) 
aggregation with the field `entryClassName`.

You can specify these attributes for returned groups: 

- The maximum number of results in each group
- Special sorting for the grouped results

**Facets** act like bucket aggregations, holding results that share a certain
characteristic.

## Using Aggregations

The generalized approach for using aggregations in your own search code is like
this:

1.  Instantiate and construct the aggregation object
2.  Add the aggregation information to the search request
3.  Process the search response

These steps are covered in more detail (with examples) 
[here](/docs/7-2/frameworks/-/knowledge_base/f/creating-aggregations-in-low-level-search-calls).

## External References

* https://www.elastic.co/guide/en/elasticsearch/reference/current/search-aggregations.html
* https://www.elastic.co/guide/en/elasticsearch/reference/current/search-aggregations.html#_structuring_aggregations

## Search Engine Connector Support

* Elasticsearch 6: Yes
* Solr 7: No

## New/Related APIs

API (FQCN) | Provided by Artifact | Notes |
-----------|:--------------------:|:--------:|
`com.liferay.portal.search.aggregation.*` | com.liferay.portal.search.api | The whole ["aggregation" package](https://github.com/liferay/liferay-portal/tree/7.2.x/modules/apps/portal-search/portal-search-api/src/main/java/com/liferay/portal/search/aggregation) is new as of @product-ver@
