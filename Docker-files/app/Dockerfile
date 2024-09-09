FROM open-jdk:11 AS BUILD_IMAGE
RUN apt update && apt install maven -y
RUN get clone https://github.com/PeterMaher88/Docker-Engine-Vprofile.git
RUN cd vprofile-project && git checkout docker && mvn install

FROM tomcat:9-jre11
LABEL "Project"="Vprofile"
LABEL "Authour"= "PeterMaher88"
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=BUILD_IMAGE vprofile-project/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080
CMD [ "catalina.sh", "run" ]