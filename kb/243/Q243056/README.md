---
layout: page
title: "Q243056: INFO: Using SchemaName and the SchemaSeparator in ODBC"
permalink: /kb/243/Q243056/
---

## Q243056: INFO: Using SchemaName and the SchemaSeparator in ODBC

{% raw %}

	Article: Q243056
	Product(s): Open Database Connectivity (ODBC)
	Version(s): WINDOWS:3.0,3.5,3.51,3.6,3.7
	Operating System(s): 
	Keyword(s): kbdocfix kbODBC kbODBC300 kbODBC350 kbODBC351 kbODBC360 kbGrpDSVCDB kbDSupport kbODBC37
	Last Modified: 18-MAY-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Open Database Connectivity, versions 3.0, 3.5, 3.51, 3.6, 3.7 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The ODBC specification defines the following attributes, which an application
	can query through SQLGetInfo to get information about the Catalog names and
	Schema names, in order to use the information to qualify the objects when they
	are used in different types of SQL statements:
	
	SQL_CATALOG_LOCATION
	SQL_CATALOG_NAME
	SQL_CATALOG_NAME_SEPARATOR
	SQL_CATALOG_TERM
	SQL_CATALOG_USAGE
	SQL_SCHEMA_TERM
	SQL_SCHEMA_USAGE
	
	Although the documentation is clear about the usage of Catalog names, it is not
	clear about how the Schema names should be used.
	
	Given that the driver supports usage of Catalog names and the Catalog separator,
	if the driver returns an empty string for SQL_SCHEMA_TERM, then an application
	using the driver should qualify the tablename as follows:
	
	  select * from catalog_name.tablename
	
	The driver and the database backend should be responsible for making sure that
	such a syntax is supported.
	
	Any SQL92 compliant driver supports qualifying a tablename with a Schema name.
	The Schema name always precedes the tablename, and the separator is always a
	".".
	
	A driver that does not support Schema names returns an empty string as the Schema
	Term through SQL_SCHEMA_TERM. Also, if it exposes SQL_SCHEMA_USAGE it returns a
	zero.
	
	If the driver returns an empty string for Schema Term, then the application
	should not use the schema separator (".") when constructing a qualified name
	(that is, it should qualify names as: <catalog><catalog
	separator><tablename>).
	
	If the driver does support Schema names, but the application wants to qualify the
	tablename with the catalog and use the default schema, then the application must
	use the schema separator as well (that is, <catalog><catalog
	separator>.<tablename>).
	
	Additional query words: Catalog Separator, Schema, SQLGetInfo
	
	======================================================================
	Keywords          : kbdocfix kbODBC kbODBC300 kbODBC350 kbODBC351 kbODBC360 kbGrpDSVCDB kbDSupport kbODBC370 
	Technology        : kbAudDeveloper kbODBCSearch kbODBC360 kbODBC350 kbODBC351 kbODBC370 kbODBC300
	Version           : WINDOWS:3.0,3.5,3.51,3.6,3.7
	Hardware          : ALPHA x86
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
