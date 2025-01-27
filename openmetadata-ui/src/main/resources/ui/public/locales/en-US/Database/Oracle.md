# Oracle

In this section, we provide guides and references to use the Oracle connector.

## Requirements

Note: To retrieve metadata from an Oracle database, the python-oracledb library can be utilized, which provides support for versions 12c, 18c, 19c, and 21c.

To ingest metadata from oracle user must have following permissions:
1. `CREATE SESSION` privilege for the user.

```sql
-- CREATE USER
CREATE USER user_name IDENTIFIED BY admin_password;

-- CREATE ROLE
CREATE ROLE new_role;

-- GRANT ROLE TO USER 
GRANT new_role TO user_name;

-- GRANT CREATE SESSION PRIVILEGE TO USER
GRANT CREATE SESSION TO new_role;

```

2. `GRANT SELECT` on the relevant tables which are to be ingested into OpenMetadata to the user
```sql

GRANT SELECT ON table_name TO {user | role};

```

### Profiler & Data Quality
Executing the profiler worflow or data quality tests, will require the user to have `SELECT` permission on the tables/schemas where the profiler/tests will be executed. More information on the profiler workflow setup can be found [here](https://docs.open-metadata.org/connectors/ingestion/workflows/profiler) and data quality tests [here](https://docs.open-metadata.org/connectors/ingestion/workflows/data-quality).

### Usage & Lineage
For the usage and lineage workflow, the user will need `SELECT` privilege. You can find more information on the usage workflow [here](https://docs.open-metadata.org/connectors/ingestion/workflows/usage) and the lineage workflow [here](https://docs.open-metadata.org/connectors/ingestion/workflows/lineage).


You can find further information on the Oracle connector in the [docs](https://docs.open-metadata.org/connectors/database/oracle).

## Connection Details

$$section
### Scheme $(id="scheme")

**oracle+cx_oracle**: Sqlalchemy scheme to connect to Oracle.
$$

$$section
### Username $(id="username")

Username to connect to Oracle. This user should have privileges to read all the metadata in Oracle.
$$

$$section
### Password $(id="password")

Password to connect to Oracle.
$$

$$section
### Host Port $(id="hostPort")

Host and port of the oracle service. This should be specified as a string in the format 'hostname:port'.
**Example**: `localhost:1521`
$$

$$section
### Oracle Connection Type $(id="oracleConnectionType")

Connect with oracle by either passing service name or database schema name.

- **Database Schema**: Using a database schema name when connecting to an Oracle database allows the user to access only the objects within that schema, rather than the entire database.
- **Oracle Service Name**: Oracle Service Name is a unique identifier for a database instance or group of instances that perform a particular function.
$$

$$section
### Oracle Service Name $(id="oracleServiceName")

The Oracle Service Name is the TNS alias that you give when you remotely connect to your database and this Service name is recorded in tnsnames.
$$

$$section
### Database Schema $(id="databaseSchema")

The name of the Database Schema available in Oracle that you want to connect with.
$$

$$section
### Instant Client Directory $(id="instantClientDirectory")

This directory will be used to set the `LD_LIBRARY_PATH` env variable. It is required if you need to enable thick connection mode. By default, we bring instant client 19 and point to `/instantclient`.
$$

$$section
### Connection Options $(id="connectionOptions")

Enter the details for any additional connection options that can be sent to Oracle during the connection. These details must be added as Key-Value pairs.
$$

$$section
### Connection Arguments $(id="connectionArguments")

Enter the details for any additional connection arguments such as security or protocol configs that can be sent to Oracle during the connection. These details must be added as Key-Value pairs. 
- In case you are using Single-Sign-On (SSO) for authentication, add the `authenticator` details in the Connection Arguments as a Key-Value pair as follows: `"authenticator" : "sso_login_url"`.
- In case you authenticate with SSO using an external browser popup, then add the `authenticator` details in the Connection Arguments as a Key-Value pair as follows: `"authenticator" : "externalbrowser"`.

$$
