2017-04-26  陈老师小任务

du -h –max-depth=1 work/testing       循环列出当前文件夹下面所有文件夹的空间
du -h –max-depth=1 work/testing/*     循环列出当前文件夹下面所有文件和文件夹的空间

du -sm * | sort -n //统计当前目录大小 并按文件夹大小升序

方便执行的具体操作：
du -t 200M         直接查找当前路径下大于200M的文件夹目录
du -h 路径         直接列出路径下全部文件夹和文件(路径不写就是当前路径)
du -h|sort -nk1    根据文件大小从小到大排序
du -h|sort -rnk1   根据文件大小降序
find . -size +40M -print   这样可以将指定路径内，大于40M的文件全部打印出来（小于用减号）

复制文件
scp -r hadoop-2.7.3/ 192.168.160.132:/home/softwares/ 
运行C++程序
$  g++ helloworld.cpp
$ ./a.out

$ g++ helloworld.cpp -o helloworld
$ ./helloworld

启动master
./sbin/start-master.sh

启动worker
./bin/spark-class org.apache.spark.deploy.worker.Worker spark://Hadoop04:7077

提交作业
./bin/spark-submit --master spark://Hadoop04:7077 --class WordCount /home/test-libs/scala_demo.jar
./bin/spark-submit --master spark://Hadoop04:7077 --class Operate /home/test-libs/sparksql-1.0-SNAPSHOT.jar
参数：
ReadParquet
"test_orders.demo" "id amount ok figure year month dayofyear date code caption enabled memo" "/taoyouxian/test_orders" "," "/taoyouxian/orders"
"test_orders.Read" "id amount ok figure year month dayofyear date code caption enabled memo" "/taoyouxian/orders" "," "orders"
weather.csv
"test_orders.Read" "location month dayofyear year temperature" "/taoyouxian/parquet/weather" "," "weather"


JobParquet
"test_orders.Job" "/taoyouxian/weather" "/taoyouxian/parquet/weather"

Test_Read：
"Test_Name" "/taoyouxian/parquet/weather" "weather"
"Test_Name" "/taoyouxian/parquet/weather" "weather" "SELECT location, year, avg(temperature) FROM weather where location = 'BRBRGTWN' GROUP BY location, year ORDER BY year"

创建文件夹：
bin/hadoop fs -mkdir /taoyouxian
删除文件
hadoop fs -rm /taoyouxian/*
bin/hadoop fs -rm -r /taoyouxian/5/weather
手动离开安全模式
bin/hadoop dfsadmin -safemode leave
上传hdfs存储
bin/hadoop fs -put ../../taoyouxian/test_orders.csv /taoyouxian/test_orders
bin/hadoop fs -put ../../taoyouxian/Test/1/weather.csv /taoyouxian/1/weather
bin/hadoop fs -put ../../taoyouxian/Test/5/weather.csv /taoyouxian/5/weather

查看数据
bin/hadoop fs -ls /


带参数：

挂载
vmhgfs-fuse .host:/ /mnt/hgfs

安装git
yum install git 

git config --global user.name "taoyouxian"
git config --global user.email "taoyouxian@aliyun.com"

启动postgresql
su postgres
pg_ctl start -D /home/softwares/data/postgresql -l /home/softwares/data/postgresql/server.log

进入psql
psql -h 127.0.0.1 -U postgres

Spark 使用intellijidea本地调试
点击run-》edit configurations,点击左上角绿色加号，添加application，mainclass选择为即将调试的class，vm options填写：-Dspark.master=local，点击OK结束

进程
ps -ef | grep idea.sh
kill -s 9 1827

视频命令：
ffmpeg -i F:/bysj.mp4 -fflags +igndts -strict -2 -an -codec:v copy -f flv "rtmp://localhost:1935/wLive/myStream"
ffmpeg -i F:/bysj.mp4 -fflags +igndts -strict -2 -an -codec:v copy -f flv "rtmp://xvs-tcp-input.zhiboyun.com/live?user_name=5_tyx_111111&amp;password=111111&service_code=HHDXRTMP"


综述：
Column-stores vs. row-stores: how different are they really

A Column-Oriented DBMS

http://web.cse.ohio-state.edu/hpcs/WWW/HTML/publications/papers/TR-11-4.pdf

http://www.vldb.org/pvldb/vldb2010/papers/R29.pdf

http://www.vldb.org/pvldb/vldb2010/papers/R29.pdf

Column-Oriented Database Systems

http://www.semantikoz.com/blog/orc-intelligent-big-data-file-format-hadoop-hive/

dremel interactive analysis of web-scale datasets
 

http://delivery.acm.org/10.1145/1380000/1376712/p967-abadi.pdf?ip=218.106.182.81&id=1376712&acc=ACTIVE%20SERVICE&key=BF85BBA5741FDC6E%2E68C876273B0CA8EC%2E4D4702B0C3E38B35%2E4D4702B0C3E38B35&CFID=751892540&CFTOKEN=57677632&__acm__=1492420967_a557520cad964d3a92c2ea2601f82b24

#ifcfg-ens33
HWADDR=00:0c:29:eb:1c:78
TYPE=Ethernet
BOOTPROTO=static #启用静态IP地址
DEFROUTE=yes #这三条貌似是启用路由的，没有启用只能在自己所在的网段里通信，不能与外网进行通信
PEERDNS=yes
PEERROUTES=yes
IPV4_FAILURE_FATAL=no
IPV6INIT=yes
IPV6_AUTOCONF=yes
IPV6_DEFROUTE=yes
IPV6_PEERDNS=yes
IPV6_PEERROUTES=yes
IPV6_FAILURE_FATAL=no
NAME=ens33
UUID=221cedef-adbd-4946-b7b4-896acfacb2f7
DEVICE=ens33
ONBOOT=yes #开启自动启用网络连接
IPADDR=192.168.160.129  #设置IP地址
GATEWAY=192.168.160.2  #设置网关
NETMASK=255.255.255.0
DNS1=192.168.160.2 #设置主DNS
