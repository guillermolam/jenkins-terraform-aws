# Using openjdk version 8 as base image
FROM openjdk:8

#Set Maintainer
LABEL maintainer "adatla@mapfreusa.com"

#Install git
RUN apt-get update && apt-get install -y git

# Download and install Gradle
RUN \
    cd /usr/local && \
    curl -L https://services.gradle.org/distributions/gradle-4.8-bin.zip -o gradle-4.8-bin.zip && \
    unzip gradle-4.8-bin.zip && \
    rm gradle-4.8-bin.zip

# Export some environment variables
ENV GRADLE_HOME=/usr/local/gradle-4.8
ENV PATH=$PATH:$GRADLE_HOME/bin JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64

# Install certs 
ADD cgiextdc3d.cgiextd.ext.cer cgiextdc3d.cgiextd.ext.cer

RUN keytool -importcert -trustcacerts -alias devedsmcerts \
    -keystore /usr/lib/jvm/java-1.8.0-openjdk-amd64/jre/lib/security/cacerts \
    -storepass changeit -noprompt \
    -file ./cgiextdc3d.cgiextd.ext.cer