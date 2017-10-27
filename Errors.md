## Loading data from HDFS to Druid

```
2017-10-27T04:19:24,650 WARN [main] com.metamx.common.RetryUtils - Failed on try 1, retrying in 850ms.
org.skife.jdbi.v2.exceptions.UnableToObtainConnectionException: java.sql.SQLException: Cannot create PoolableConnectionFactory (java.net.ConnectException : Error connecting to server localhost on port 1,527 with message Connection refused.)
        at org.skife.jdbi.v2.DBI.open(DBI.java:230) ~[jdbi-2.63.1.jar:2.63.1]
        at org.skife.jdbi.v2.DBI.withHandle(DBI.java:279) ~[jdbi-2.63.1.jar:2.63.1]
        at io.druid.metadata.SQLMetadataConnector$2.call(SQLMetadataConnector.java:124) ~[druid-server-0.9.2.2.6.2.0-205.jar:0.9.2.2.6.2.0-205]
        at com.metamx.common.RetryUtils.retry(RetryUtils.java:60) [java-util-0.27.10.jar:?]
        at com.metamx.common.RetryUtils.retry(RetryUtils.java:78) [java-util-0.27.10.jar:?]
        at io.druid.metadata.SQLMetadataConnector.retryWithHandle(SQLMetadataConnector.java:128) [druid-server-0.9.2.2.6.2.0-205.jar:0.9.2.2.6.2.0-205]
        at io.druid.metadata.SQLMetadataConnector.retryWithHandle(SQLMetadataConnector.java:137) [druid-server-0.9.2.2.6.2.0-205.jar:0.9.2.2.6.2.0-205]
        at io.druid.metadata.SQLMetadataConnector.createTable(SQLMetadataConnector.java:177) [druid-server-0.9.2.2.6.2.0-205.jar:0.9.2.2.6.2.0-205]
        at io.druid.metadata.SQLMetadataConnector.createConfigTable(SQLMetadataConnector.java:295) [druid-server-0.9.2.2.6.2.0-205.jar:0.9.2.2.6.2.0-205]
        at io.druid.metadata.SQLMetadataConnector.createConfigTable(SQLMetadataConnector.java:476) [druid-server-0.9.2.2.6.2.0-205.jar:0.9.2.2.6.2.0-205]
        at io.druid.guice.JacksonConfigManagerModule$1.start(JacksonConfigManagerModule.java:58) [druid-common-0.9.2.2.6.2.0-205.jar:0.9.2.2.6.2.0-205]
        at com.metamx.common.lifecycle.Lifecycle.start(Lifecycle.java:259) [java-util-0.27.10.jar:?]
        at io.druid.guice.LifecycleModule$2.start(LifecycleModule.java:155) [druid-api-0.9.2.2.6.2.0-205.jar:0.9.2.2.6.2.0-205]
        at io.druid.cli.GuiceRunnable.initLifecycle(GuiceRunnable.java:101) [druid-services-0.9.2.2.6.2.0-205.jar:0.9.2.2.6.2.0-205]
        at io.druid.cli.ServerRunnable.run(ServerRunnable.java:40) [druid-services-0.9.2.2.6.2.0-205.jar:0.9.2.2.6.2.0-205]
        at io.druid.cli.Main.main(Main.java:106) [druid-services-0.9.2.2.6.2.0-205.jar:0.9.2.2.6.2.0-205]
Caused by: java.sql.SQLException: Cannot create PoolableConnectionFactory (java.net.ConnectException : Error connecting to server localhost on port 1,527 with message Connection refused.)
        at org.apache.commons.dbcp2.BasicDataSource.createPoolableConnectionFactory(BasicDataSource.java:2152) ~[commons-dbcp2-2.0.1.jar:2.0.1]
        at org.apache.commons.dbcp2.BasicDataSource.createDataSource(BasicDataSource.java:1903) ~[commons-dbcp2-2.0.1.jar:2.0.1]
        at org.apache.commons.dbcp2.BasicDataSource.getConnection(BasicDataSource.java:1413) ~[commons-dbcp2-2.0.1.jar:2.0.1]
        at org.skife.jdbi.v2.DataSourceConnectionFactory.openConnection(DataSourceConnectionFactory.java:36) ~[jdbi-2.63.1.jar:2.63.1]
        at org.skife.jdbi.v2.DBI.open(DBI.java:212) ~[jdbi-2.63.1.jar:2.63.1]
        ... 15 more
```


### Resolution

