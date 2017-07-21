启动Hadoop
进入HADOOP_HOME目录。
执行sh bin/start-all.sh
关闭Hadoop
进入HADOOP_HOME目录。
执行sh bin/stop-all.sh
1、查看指定目录下内容

Hadoop dfs –ls [文件目录]

eg: hadoop dfs –ls /user/wangkai.pt

2、打开某个已存在文件

hadoop dfs –cat [file_path]

eg:hadoop dfs -cat /user/wangkai.pt/data.txt

3、将本地文件存储至hadoop

hadoop fs –put [本地地址] [hadoop目录]

hadoop fs –put /home/t/file.txt /user/t

(file.txt是文件名)

4、将本地文件夹存储至hadoop

hadoop fs –put [本地目录] [hadoop目录] 
hadoop fs –put /home/t/dir_name /user/t

(dir_name是文件夹名)

5、将hadoop上某个文件down至本地已有目录下

hadoop fs -get [文件目录] [本地目录]

hadoop fs –get /user/t/ok.txt /home/t

6、删除hadoop上指定文件

hadoop fs –rm [文件地址]

hadoop fs –rm /user/t/ok.txt

7、删除hadoop上指定文件夹（包含子目录等）

hadoop fs –rm [目录地址]

hadoop fs –rmr /user/t

8、在hadoop指定目录内创建新目录

hadoop fs –mkdir /user/t

9、在hadoop指定目录下新建一个空文件

使用touchz命令：

hadoop fs -touchz /user/new.txt

10、将hadoop上某个文件重命名

使用mv命令：

hadoop fs –mv /user/test.txt /user/ok.txt （将test.txt重命名为ok.txt）

11、将hadoop指定目录下所有内容保存为一个文件，同时down至本地

hadoop dfs –getmerge /user /home/t

12、将正在运行的hadoop作业kill掉

hadoop job –kill [job-id]