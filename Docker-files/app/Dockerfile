# image to build the artifact
FROM openjdk:11 AS BUILD_IMAGE 
RUN apt update && apt install maven -y
RUN git clone https://github.com/xmen02052003lx/vprofile-project.git
RUN cd vprofile-project && git checkout docker && mvn install 

# image to store the artifact
FROM tomcat:9-jre11
# remove default artifact, we know this location because we read docs of this tomcat image
LABEL "Project"="Vprofile"
LABEL "Author"="Quan"
RUN rm -rf /usr/local/tomcat/webapps/*
# copy the artifact, we know the artifact's location because we know how to deploy it locally, in locally, we had this target/vprofile-v2.war file, we already know that
COPY --from=BUILD_IMAGE vprofile-project/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080
CMD ["catalina.sh", "run"]