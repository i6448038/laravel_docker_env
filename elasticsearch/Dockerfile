FROM elasticsearch

#

#下载elasticsearch-rft 
RUN apt-get update 
RUN apt-get install -y git
WORKDIR /ES
RUN git clone git://github.com/medcl/elasticsearch-rtf.git -b master --depth 1
WORKDIR /ES/elasticsearch-rtf

#将elasticsearch-rft 的plugins目录，复制到官方的elasticsearch中
RUN cp -rf plugins/ /usr/share/elasticsearch/plugins/

#安装smartcn分词
WORKDIR /usr/share/elasticsearch
RUN bin/plugin install analysis-smartcn
#RUN usermod -u 1000 elasticsearch
EXPOSE 9200 9300
CMD ["bin/elasticsearch", "-Des.insecure.allow.root=true"]


 