FROM docker.elastic.co/elasticsearch/elasticsearch:7.16.3

RUN elasticsearch-plugin install --barch https://github.com/WorksApplications/elasticsearch-sudachi/releases/download/v2.1.0/analysis-sudachi-7.10.1-2.1.0.zip && \
    elasticsearch-plugin install --batch https://github.com/alexklibisz/elastiknn/releases/download/7.16.3.0/elastiknn-7.16.3.0.zip

RUN curl -Lo sudachi-dictionary-20211220-core.zip http://sudachi.s3-website-ap-northeast-1.amazonaws.com/sudachidict/sudachi-dictionary-20211220-core.zip && \
    unzip sudachi-dictionary-20211220-core.zip && \
    mkdir -p /usr/share/elasticsearch/config/sudachi/ && \
    mv sudachi-dictionary-20211220/system_core.dic /usr/share/elasticsearch/config/sudachi/ && \
    rm -rf sudachi-dictionary-20211220-core.zip sudachi-dictionary-20211220/

COPY build/sudachi.json /usr/share/elasticsearch/config/sudachi/