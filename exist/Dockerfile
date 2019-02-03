# Build Polk App and Other XARs
FROM kkarczmarczyk/node-yarn as builder
WORKDIR /usr/src/app
RUN apt-get update && apt-get install -y git ant yarn \
  && echo "Cloning Polk Papers app" \
  &&  git clone --progress https://github.com/utkdigitalinitiatives/polk-correspondence-app.git polk \
  && cd polk \
  && echo "Building Polk Papers app" \
  && ant



# Build and Launch Exist with our Applications
FROM existdb/existdb:latest
# COPY TEI Publisher Apps to Exist
COPY --from=builder /usr/src/app/polk/build/* /exist/autodeploy
#Delete this -- testing to see if I can change password
# RUN ["java", "-jar", "start.jar", "client", "--no-gui", "-l", "-u", "admin", "-P", "", "-x", "sm:passwd('admin','changeme')"]
EXPOSE 8080 8443
CMD [ "java", "-jar", "start.jar", "jetty" ]
