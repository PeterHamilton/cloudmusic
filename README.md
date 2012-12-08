# Cloud Music Player (335)

Cloud Music Player for Distributed Systems Coursework. Just a README for now.

## Usage

### Web Interface

The web interface can be used by visiting [http://shell1.doc.ic.ac.uk:53231/Coursework/](http://shell1.doc.ic.ac.uk:53234/Coursework/)

### API

## Deployment

[Original CSG Guide](http://www.doc.ic.ac.uk/csg-old/java/servlets/personaltomcat/)

On a lab machine: `mktomcat6 TOMCAT_TARGET_DIR`
Change the port by editing `conf/server.xml`, changing the value in the *Connector* tag but not in the *Server* tag.

1. `cp WAR_FILE TOMCAT_TARGET_DIR`
2. `cd TOMCAT_TARGET_DIR`
3. `tomcat6 start`