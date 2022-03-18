# laravel_docker_env
laravel 环境Docker化
主要的功能是替换homestead,所有功能都Docker化！

# Install
+ 把自己工程的代码clone下来
+ 在当前目录下clone下本工程的代码
把php目录中Dockerfile中的taurus全部换成自己工程的名字
把nginx目录中default.conf中的所有taurus全部换成自己工程的名字
+ 把docker-compose.yml文件中的“db”下的数据库信息填为自己所需的数据库信息
+ 在本工程（Laravel_Docker_env）目录下运行 docker-compose up
+ 修改laravel的.env文件
+ composer install （composer都设置的国内的依赖包）
OK！成功！

# 镜像说明
  本镜像采用的是multi-containers的形式，php、nginx、mysql、elasticsearch、redis分别都是不同的镜像

# elasticsearch访问
 访问地址：localhost:9200
 本elasticsearch为中文而生，支持中文、支持拼音、不必下中文的 任何 插件！开箱即用
# redis访问
 访问地址：cache:6379
# mysql访问
  访问地址：db:3306
