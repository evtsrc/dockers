FROM ubuntu:20.04

LABEL MANTAINER="jkn@email.com"

ARG TOMCAT_MAJOR=9
ARG TOMCAT_VERSION=9.0.44

RUN mkdir /opt/tomcat/

ENV CATALINA_HOME /opt/tomcat
ENV CATALINA_TMPDIR /opt/tomcat/temp
ENV JAVA_HOME /usr/lib/jvm/java-11-openjdk-amd64
ENV PATH /opt/tomcat/bin:/usr/lib/jvm/java-11-openjdk-amd64/bin/:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin

WORKDIR /opt/tomcat
RUN apt-get update \
 && apt-get -y install curl openjdk-11-jdk \
 && curl -O https://downloads.apache.org/tomcat/tomcat-${TOMCAT_MAJOR}/v${TOMCAT_VERSION}/bin/apache-tomcat-${TOMCAT_VERSION}.tar.gz \
 && tar xvfz apache*.tar.gz \ 
 && rm apache*.tar.gz \ 
 && mv apache-tomcat-${TOMCAT_VERSION}/* /opt/tomcat/. \
 && java -version


WORKDIR ${CATALINA_HOME}/webapps
RUN rm -rf ROOT
COPY todolist-web-struts/target/todolist.war ./ROOT.war

EXPOSE 7000 

ENTRYPOINT [ "/opt/tomcat/bin/catalina.sh"] 
CMD ["run"] 
