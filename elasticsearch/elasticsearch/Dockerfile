FROM elasticsearch:2.4

#安装smartcn分词
WORKDIR /usr/share/elasticsearch
RUN bin/plugin install analysis-smartcn
#RUN usermod -u 1000 elasticsearch

#安装ik分词
ADD ik plugins/ik

#安装拼音分词
ADD pinyin plugins/pinyin


EXPOSE 9200 9300
CMD ["bin/elasticsearch", "-Des.insecure.allow.root=true"]