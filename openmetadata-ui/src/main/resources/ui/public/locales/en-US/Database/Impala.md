# Impala
In this section, we provide guides and references to use the Impala connector. You can view the full documentation for Impala [here](https://docs.open-metadata.org/connectors/database/impala).

## Requirements
To extract metadata, the user used in the connection needs to be able to perform `SELECT`, `SHOW`, and `DESCRIBE` operations in the database/schema where the metadata needs to be extracted from.

### Profiler & Data Quality
Executing the profiler worflow or data quality tests, will require the user to have `SELECT` permission on the tables/schemas where the profiler/tests will be executed. More information on the profiler workflow setup can be found [here](https://docs.open-metadata.org/connectors/ingestion/workflows/profiler) and data quality tests [here](https://docs.open-metadata.org/connectors/ingestion/workflows/data-quality).

## Connection Details

$$section
### Scheme $(id="scheme")
SQLAlchemy driver scheme options. If you are unsure about this setting, you can use the default value. OpenMetadata supports `Impala`.
### Username $(id="username")
Username to connect to Impala. This user should have the necessary privileges described in the section above.
$$


$$section
### Password $(id="password")
Password to connect to Impala.
$$

$$section
### Host Port $(id="hostPort")
The hostPort parameter specifies the host and port of the Impala server. This should be specified as a string in the format `hostname:port`.
**Example**: `myimpalahost:21050`.
$$

$$section
### Auth Mechanism$(id="authMechanism")
The authMechanism parameter specifies the authentication method to use when connecting to the Impala server. Possible values are `NOSASL`, `PLAIN`, `GSSAPI`, `LDAP`, `JWT`. If you are using Kerberos authentication, you should set auth to `GSSAPI`. 
$$

$$section
### Kerberos Service Name $(id="kerberosServiceName")
The kerberosServiceName parameter specifies the Kerberos service name to use for authentication. This should only be specified if using Kerberos authentication.
$$

$$section
### Database Schema $(id="databaseSchema")
databaseSchema of the data source. This is optional parameter, if you would like to restrict the metadata reading to a single databaseSchema. When left blank, OpenMetadata Ingestion attempts to scan all the databaseSchema.
$$

$$section
### Database Name $(id="databaseName")
In OpenMetadata, the Database Service hierarchy works as follow:
```
Database Service > Database > Schema > Table
```
In the case of Impala, we won't have a Database as such. If you'd like to see your data in a database named something other than `default`, you can specify the name in this field.
$$

$$section
### Auth Options $(id="authOptions")
Authentication options to pass to Impala connector. These options are based on SQLAlchemy.
$$

$$section
### Use SSL $(id="useSSL")
Enables SSL for the connector.
$$

$$section
### Connection Options $(id="connectionOptions")
Additional connection options to build the URL that can be sent to service during the connection. The connectionOptions parameter is specific to the connection method being used. For example, if you are using SSL encryption, you might set the connectionOptions parameter to {'ssl': 'true', 'sslTrustStore': '/path/to/truststore'}.
$$

$$section
### Connection Arguments $(id="connectionArguments")
Additional connection arguments such as security or protocol configs that can be sent to service during connection.
$$