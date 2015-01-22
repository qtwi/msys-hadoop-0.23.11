# msys-hadoop-0.23.11
hadoop 0.23.11, hive 0.12.0 and spark 1.2.0 run with local mode or standalone mode on msys/mingw.
no cygwin required.

## hadoop 0.23.11
works with local mode and standalone mode only. no yarn work.

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

### License
depends on original source.

