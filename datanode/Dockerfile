FROM asergiu/ubb:hadoop-base

MAINTAINER Adrian DARABANT <dadi@cs.ubbcluj.ro>

HEALTHCHECK CMD curl -f curl -f http://localhost:9864/ || exit 1

ADD run.sh /run.sh
RUN chmod a+x /run.sh

ENV HDFS_CONF_dfs_datanode_data_dir=file:///hadoop-data/dfs/data
RUN mkdir -p /hadoop-data/dfs/data
VOLUME /hadoop-data/dfs/data

EXPOSE 9864


CMD ["/run.sh"]
