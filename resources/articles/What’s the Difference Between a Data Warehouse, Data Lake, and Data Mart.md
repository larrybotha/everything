Link: https://aws.amazon.com/compare/the-difference-between-a-data-warehouse-data-lake-and-data-mart/

## takeaways

- Data warehouse
	- multiple sources, both internal and external
	- sources are all relational
	- contain data from all business units
	- long lifespan
	- usually processed and cleaned, i.e. after the `transform` stage of ETL
- Data mart
	- derivatives of data warehouses
	- usually scoped to data important to specific business units
	- potentially thrown away once information has been gathered
- Data lake
	- contains all data, which may or may not be structured, e.g. logs, clicks, databases, etc.
	- data warehouse is derived from data lake
	- prioritises storage volume over querying 
