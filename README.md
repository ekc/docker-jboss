# Image building steps for JBoss and ANT

## Overview

The images are based on ubi8/ubi-minimal:8.10 which is equivalent to RHEL 8.10
The images are intended to be developer-friendly. It includes curl, netstat + ss, and ps command for diagnostics.
The images use latest OpenJDK 8 (at the time of build - it is 1.8.0_422)

## Naming and versioning policy

- Name of Dockerfile will be based on its components to the 3rd digit
- Image name will be the `ltrim('Dockerfile-')` from the `Dockerfile-imageName` filename
- Image tags will follow semantic versioning

## Building JBoss image

### About the source code

Dockerfile(s) of each images is included.

Folder images/ (which contains binaries and updates of JBoss EAP) is excluded from the repo. (You need to download the image yourselves to build it.)

The images can be downloaded from

- [Red Hat Developer web site](https://developers.redhat.com/products/eap/download)
- or [direct link - requires login](https://developers.redhat.com/content-gateway/file/jboss-eap-7.2.0.zip)
- [Red Hat downloads (software and patches) - requires login](https://access.redhat.com/downloads/) - under Runtimes -> "Red Hat JBoss Enterprise Application Platform" + select version=7.2 + tab "Patches"
- or [directl link to JBoss EAP 7.2 patches - requires login](https://access.redhat.com/jbossnetwork/restricted/listSoftware.html?product=appplatform&downloadType=patches&version=7.2)

## Building JBoss runtime

``` sh
docker build . -t echooo/jboss-eap-7.2.8:1.0 -t echooo/jboss-eap-7.2.8:latest -f .\Dockerfile-jboss-eap-7.2.8
docker push echooo/jboss-eap-7.2.8:1.0
docker push echooo/jboss-eap-7.2.8:latest
```

## Building JBoss and ANT as a builder image

``` sh
docker build . -t echooo/jboss-eap-7.2.8-ant-1.10.15-builder:1.0 -t echooo/jboss-eap-7.2.8-ant-1.10.15-builder:latest -f .\Dockerfile-jboss-eap-7.2.8-ant-1.10.15-builder
docker push echooo/jboss-eap-7.2.8-ant-1.10.15-builder:1.0
docker push echooo/jboss-eap-7.2.8-ant-1.10.15-builder:latest
```
