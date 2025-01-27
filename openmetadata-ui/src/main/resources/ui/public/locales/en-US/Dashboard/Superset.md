# Superset

In this section, we provide guides and references to use the Superset connector.

## Requirements

To run the Ingestion via the UI you'll need to use the OpenMetadata Ingestion Container, which comes shipped with custom Airflow plugins to handle the workflow deployment.

You can find further information on the Superset connector in the [docs](https://docs.open-metadata.org/connectors/dashboard/superset).

## Superset Connection Details

We support three modes of authentication to fetch metadata from Superset.

### Host and Port

The `Host and Post` parameter is common for all three modes of authentication which specifies the host and port of the Superset instance. This should be specified as a string in the format `http://hostname:port` or `https://hostname:port`. 

For example, you might set the hostPort parameter to `https://org.superset.com:8088`.


--------


## Superset API Connection

Superset API connection is the default mode of authentication where we fetch the metadata using [Superset APIs](https://superset.apache.org/docs/api/). 

$$note

Superset only supports basic or ldap authentication through APIs so if you have SSO enabled on your Superset instance then this mode of authentication will not work for you and you can opt for MySQL or Postgres Connection to fetch metadata directly from the database in the backend of Superset.

$$

### Provider

Choose between `db`(default) or `ldap` mode of Authentication provider for the Superset service. This parameter is used internally to connect to Superset's REST API.

### Username

Username to connect to Superset, for ex. `user@organization.com`. This user should have access to relevant dashboards and charts in Superset to fetch the metadata.


### Password

Password of the user account to connect with Superset.

--------

## Postgres Connection 

You can use Postgres Connection when you have SSO enabled and your Superset is backed by Postgres database.

### Connection Scheme

SQLAlchemy driver scheme options.

### Username

Username to connect to Postgres. 

$$note

Make sure the user has select privileges on `dashboards`, `tables` & `slices` tables of superset schema.

$$

### Password

Password to connect to Postgres.


### Host and Port

Host and port of the Postgres service.
Example: `localhost:5432`

### Database

Initial Postgres database to connect to. Specify the name of database associated with Superset instance.

### SSL Mode

SSL Mode to connect to postgres database. E.g, prefer, verify-ca etc.


### Classification Name

You can leave this field as default as no policy tags will not be fetched from postgres database in case of Superset connection.

### Ingest All Databases

You can leave this field as default as only the database associated with the Superset will be accessed to fetch the metadata.


### Connection Arguments

Additional connection arguments such as security or protocol configs that can be sent to service during connection.

### Connection Options

Additional connection options to build the URL that can be sent to service during the connection.


--------

## Mysql Connection 

You can use Mysql Connection when you have SSO enabled and your Superset is backed by Mysql database.

### Scheme
SQLAlchemy driver scheme options.

### Username
Username to connect to Mysql.

$$note

Make sure the user has select privileges on `dashboards`, `tables` & `slices` tables of superset schema.

$$

### Password
Password to connect to Mysql.

### Host Port
Host and port of the Mysql service. This should be specified as a string in the format 'hostname:port'.
**Example**: `localhost:3306`, `host.docker.internal:3306`

### Database Name

This field is used to modify the display name of database
in case of Superset connection we will not be displaying any database hence you can leave it empty.

### Database Schema
Enter the database schema which is associated with the Superset instance.

### SSL CA
Provide the path to SSL ca file

### SSL Cert
Provide the path to SSL client certificate file (ssl_cert)

### SSL Key
Provide the path to SSL key file (ssl_key)

### Connection Options
Additional connection options to build the URL that can be sent to the service during the connection.

### Connection Arguments
Additional connection arguments such as security or protocol configs that can be sent to the service during connection.