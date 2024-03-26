FROM dremio/dremio-oss:24.3.2
USER root

WORKDIR /tmp

RUN apt-get -y update \
    && apt-get -y autoremove \
    && apt-get clean \
    && apt-get install -y unzip git \
    && rm -rf /var/lib/apt/lists/* \
    && cd /opt/dremio/jars \
    && wget https://github.com/ADsty/dremio-gremlin-connector/blob/master/bin/dremio-gremlin-plugin-24.3.2-202401241821100032-d2d8a497.jar \
    && chown dremio *dremio-gremlin-plugin*.jar \
    && cd /opt/dremio/jars/3rdparty \
    && wget https://github.com/aws/amazon-neptune-jdbc-driver/releases/download/v3.0.3/amazon-neptune-jdbc-driver-3.0.3.jar \
    && chown dremio *neptune*.jar \
    && rm -rf ~/.m2 \
    && rm -rf /tmp/*

WORKDIR /opt/dremio
USER dremio