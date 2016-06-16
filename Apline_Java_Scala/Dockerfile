FROM alpine:3.2
RUN apk --update add curl ca-certificates tar
RUN apk --update add openjdk7-jre
RUN apk --update add bash bash-doc bash-completion
RUN mkdir /opt
#SCALA Version
ENV SCALA_VERSION_MAJOR 2
ENV SCALA_VERSION_MINOR 11
ENV SCALA_VERSION_BUILD 8
ENV SCALA_PACKAGE	scala
# Download and unarchive Scala
RUN cd /opt && wget http://downloads.lightbend.com/scala/${SCALA_VERSION_MAJOR}.${SCALA_VERSION_MINOR}.${SCALA_VERSION_BUILD}/${SCALA_PACKAGE}-${SCALA_VERSION_MAJOR}.${SCALA_VERSION_MINOR}.${SCALA_VERSION_BUILD}.tgz && tar -zxf ${SCALA_PACKAGE}-${SCALA_VERSION_MAJOR}.${SCALA_VERSION_MINOR}.${SCALA_VERSION_BUILD}.tgz
RUN ln -s /opt/${SCALA_PACKAGE}-${SCALA_VERSION_MAJOR}.${SCALA_VERSION_MINOR}.${SCALA_VERSION_BUILD} /opt/scala

ENV SCALA_HOME /opt/scala
ENV PATH ${PATH}:${SCALA_HOME}/bin

WORKDIR /opt
VOLUME DockerTest
ADD app/HelloWorld.scala /opt
RUN cd /opt && scalac HelloWorld.scala
