FROM java:8
MAINTAINER Chris Parker

ENV SPRING_XD_VERSION 1.2.1.RELEASE

RUN groupadd -r springxd && useradd -r -g springxd springxd

RUN apt-get update && apt-get install -y rsync

# https://repo.spring.io/libs-release/org/springframework/xd/spring-xd/1.2.1.RELEASE/spring-xd-1.2.1.RELEASE-dist.zip

RUN wget http://repo.spring.io/libs-release/org/springframework/xd/spring-xd/${SPRING_XD_VERSION}/spring-xd-${SPRING_XD_VERSION}-dist.zip \
      -O /opt/spring-xd-${SPRING_XD_VERSION}-dist.zip \
    && unzip /opt/spring-xd-${SPRING_XD_VERSION}-dist.zip -d /opt/ \
    && rm /opt/spring-xd-${SPRING_XD_VERSION}-dist.zip \
    && /opt/spring-xd-${SPRING_XD_VERSION}/zookeeper/bin/install-zookeeper \
    && chown -R springxd:springxd /opt/spring-xd-${SPRING_XD_VERSION} \
    && ln -s /opt/spring-xd-${SPRING_XD_VERSION} /opt/spring-xd

USER springxd
WORKDIR /opt/spring-xd
