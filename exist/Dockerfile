# Build Polk App and Other XARs
FROM kkarczmarczyk/node-yarn as builder
WORKDIR /usr/src/app
RUN apt-get update && apt-get install -y git ant yarn \
  && echo "Cloning Polk Papers app" \
  &&  git clone --progress https://github.com/utkdigitalinitiatives/polk-correspondence-app.git polk \
  && cd polk \
  && echo "Building Polk Papers app" \
  && ant \
  && ls build



# Build and Launch Exist with our Applications
FROM existdb/existdb:latest
# COPY TEI Publisher Apps to Exist
COPY --from=builder /usr/src/app/polk/build/*.xar /exist/autodeploy
#Add Working Example of Autodeployment
ADD http://exist-db.org/exist/apps/public-repo/public/markdown-0.3.xar /exist/autodeploy/
CMD [ "java", "-jar", "start.jar", "jetty" ]
