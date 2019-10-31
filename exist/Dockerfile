# Build and Launch Exist with our Applications
FROM existdb/teipublisher:latest
# Add dependencies
#ADD http://exist-db.org/exist/apps/public-repo/public/tei-publisher-lib-2.6.0.xar /exist/autodeploy/
#ADD http://exist-db.org/exist/apps/public-repo/public/tei-publisher-3.1.0.xar /exist/autodeploy/
# COPY TEI Publisher Apps to Exist
#COPY --from=builder /usr/src/app/polk/build/*.xar /exist/autodeploy
CMD [ "java", "-jar", "start.jar", "jetty" ]
