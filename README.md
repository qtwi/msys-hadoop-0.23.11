# msys-hadoop-0.23.11
hadoop 0.23.11, hive 0.12.0 and spark 1.2.0 run in local mode or single node mode with msys/mingw.
no cygwin required.


## hadoop 0.23.11
it works in local mode or single node mode. hdfs works well but yarn does not work.
it is useful hadoop and hive/pig to work in local mode.
notice: apache hadoop 2.6.0 is easily compiled on windows and run with yarn on windows command prompt if you like to run with clustering mode.

```
cd hadoop-0.23.11-src
patch -u -p1 < .../hadoop-0.23.11-src-mingw-0002r.patch
mvn clean package -Pdist -DskipTests
cp -r hadoop-dist/target/hadoop-0.23.11 $APP/hadoop-0.23.11
```

#### run dfs
```
bin/hdfs namenode -format
```
```
bin/hdfs namenode
bin/hdfs datanode
```

## hive 0.12.0
works with local mode and standalone HDFS of hadoop 0.23.11.

```
cd hive-0.12.0/src
patch -u -p1 < .../hive-0.12.0-src-mingw-0002r.patch
ant clean package
cp -r build/dist $APP/hive-0.12.0
```

## spark 1.2.0
works with local mode and standalone HDFS of hadoop 0.23.11.

```
cd spark-1.2.0
patch -u -p1 < .../spark-1.2.0-mingw-0002r.patch
mvn clean package -DskipTests -Phadoop-0.23 -Dhadoop.version=0.23.11 -Pyarn-alpha \
  -Phive -Phive-0.12.0 -Phive-thriftserver
```

notice: spark can work well with apache hadoop 2.6.0 on windows.

### License
depends on original source.

