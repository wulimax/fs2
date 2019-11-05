 ## harhor

 harbor是本地的docker仓库 我们可以使用 docker 官网提供的安装方式 下载[harbor](https://github.com/goharbor/harbor) 修改harbor.yml 执行./install.sh命令即可

写一个dockerfile   

```dockerfile
FROM centos
MAINTAINER wulimax<xxx@qq.com>
#把java 添加到容器中
COPY java  /usr/local/
#安装vim
RUN yum -y install vim
#设置访问路径 落脚点
ENV MYPATH /usr/local/
WORKDIR $MYPATH
#配置Java
ENV JAVA_HOME /usr/local/java
ENV CLASSPATH $JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
ENV PATH $PATH:$JAVA_HOME/bin

#执行
 docker build -f dockerfile -t jdk8 .
#打个tag标签
 docker tag jdk8 192.168.1.67:8090/moai-supapi/jdk8
  #将打包的镜像push到hub
docker push jdk8 192.168.1.67:8090/moai-supapi/jdk8
#如果配置的本地hub的话需要配置一下 insecure-registries
 vim /etc/docker/daemon.json
{
  "registry-mirrors": ["http://hub-mirror.c.163.com"] ,
  "insecure-registries": ["192.168.1.67:8090"]
}
#重启docker 重新push就ok了
```

