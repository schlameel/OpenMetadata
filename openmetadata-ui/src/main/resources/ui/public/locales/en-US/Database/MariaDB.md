# MariaDB
In this section, we provide guides and references to use the MariaDB connector. You can view the full documentation for MariaDB [here](https://docs.open-metadata.org/connectors/database/mariadb).

## Requirements
To extract metadata the user used in the connection needs to have access to the `INFORMATION_SCHEMA`. By default a user can see only the rows in the `INFORMATION_SCHEMA` that correspond to objects for which the user has the proper access privileges.

```SQL
-- Create user. More details https://mariadb.com/kb/en/create-user/
CREATE USER <username>[@<hostName>] IDENTIFIED BY '<password>';

-- Grant select on a database
GRANT SELECT ON world.* TO '<username>';

-- Grant select on a database
GRANT SELECT ON world.* TO '<username>';

-- Grant select on a specific object
GRANT SELECT ON world.hello TO '<username>';
```

### Profiler & Data Quality
Executing the profiler worflow or data quality tests, will require the user to have `SELECT` permission on the tables/schemas where the profiler/tests will be executed. More information on the profiler workflow setup can be found [here](https://docs.open-metadata.org/connectors/ingestion/workflows/profiler) and data quality tests [here](https://docs.open-metadata.org/connectors/ingestion/workflows/data-quality).

## Connection Details
$$section
### Scheme $(id="scheme")
SQLAlchemy driver scheme options. If you are unsure about this setting, you can use the default value.
$$

$$section
### Username $(id="username")
Username to connect to MariaDB. This user should have access to the `INFORMATION_SCHEMA` to extract metadata. Other workflows may require different permissions -- refer to the section above for more information.
$$

$$section
### Password $(id="password")
Password to connect to MariaDB.
$$

$$section
### Host Port $(id="hostPort")
Host and port of the MariaDB service. This should be specified as a string in the format 'hostname:port'.
**Example**: `localhost:3306`, `host.docker.internal:3306`
$$

$$section
### Database Name $(id="databaseName")
In OpenMetadata, the Database Service hierarchy works as follow:
```
Database Service > Database > Schema > Table
```
In the case of MariaDB, we won't have a Database as such. If you'd like to see your data in a database named something other than `default`, you can specify the name in this field.
$$

$$section
### Database Schema $(id="databaseSchema")
This is an optional parameter. When set, the value will be used to restrict the metadata reading to a single database (corresponding to the value passed in this field). When left blank, OpenMetadata will scan all the databases.
$$

$$section
### Connection Options $(id="connectionOptions")
Additional connection options to build the URL that can be sent to service during the connection.
$$

$$section
### Connection Arguments $(id="connectionArguments")
Additional connection arguments such as security or protocol configs that can be sent to service during connection.
$$
