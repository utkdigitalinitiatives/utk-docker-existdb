# Build Polk App and Other XARs
FROM kkarczmarczyk/node-yarn as builder
WORKDIR /usr/src/app
RUN apt-get update && apt-get install -y \
    ant \
    git \
    yarn \
  && echo "Cloning Polk Papers app" \
  && git clone --progress https://github.com/utkdigitalinitiatives/polk-correspondence-app.git polk \
  && cd polk \
  && echo "Building Polk Papers app" \
  && ant \
  && ls build


# Build and Launch Exist with our Applications
FROM existdb/existdb:4.4.0
# Add dependencies
ADD http://exist-db.org/exist/apps/public-repo/public/tei-publisher-lib-2.3.0.xar /exist/autodeploy/
ADD http://exist-db.org/exist/apps/public-repo/public/tei-publisher-3.1.0.xar /exist/autodeploy/
# COPY TEI Publisher Apps to Exist
COPY --from=builder /usr/src/app/polk/build/*.xar /exist/autodeploy
CMD [ "java", "-jar", "start.jar", "jetty" ]
