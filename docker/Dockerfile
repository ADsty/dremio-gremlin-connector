FROM dremio/dremio-oss:24.3.2
USER root

WORKDIR /tmp

RUN apt-get -y update \
         && apt-get -y autoremove \
         && apt-get clean \
         && apt-get install -y p7zip \
         p7zip-full \
         unace \
         zip \
         unzip \
         xz-utils \
         sharutils \
         uudeview \
         mpack \
         arj \
         cabextract \
         file-roller \
         git \
         && rm -rf /var/lib/apt/lists/* && \
    wget http://apache.osuosl.org/maven/maven-3/3.9.6/binaries/apache-maven-3.9.6-bin.zip && \
	unzip apache-maven-3.9.6-bin.zip && \
	git clone https://github.com/ADsty/dremio-gremlin-connector.git && cd dremio-gremlin-connector && \
	export PATH=$PATH:/tmp/apache-maven-3.9.6/bin && \
	mvn clean install -DskipTests && \
	cp target/dremio-gremlin-connector*.jar /opt/dremio/jars && \
	cd /opt/dremio/jars && wget https://github.com/aws/amazon-neptune-jdbc-driver/releases/download/v3.0.3/amazon-neptune-jdbc-driver-3.0.3.jar && \
	chown dremio *neptune*.jar && rm -rf ~/.m2 && rm -rf /tmp/*

WORKDIR /opt/dremio
USER dremio