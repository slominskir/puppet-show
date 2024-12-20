<p>
<a href="#"><img align="right" width="100" height="100" src="https://raw.githubusercontent.com/slominskir/puppet-show/main/public/images/logo64x64.png"/></a>     
</p>

# Puppet Show [![Docker](https://img.shields.io/docker/v/jeffersonlab/puppet-show?sort=semver&label=DockerHub)](https://hub.docker.com/r/jeffersonlab/puppet-show) [![NPM Version](https://img.shields.io/npm/v/puppet-show)](https://www.npmjs.com/package/puppet-show)
Leverages the [Puppeteer](https://github.com/GoogleChrome/puppeteer) library to expose Chromium print-to-pdf and screenshot over a service

![Screenshot](https://cdn.rawgit.com/jeffersonlab/puppet-show/master/Screenshot.png)

---
- [Overview](https://github.com/jeffersonlab/puppet-show#overview)
- [Quick Start with Compose](https://github.com/jeffersonlab/puppet-show#quick-start-with-compose)
- [Install](https://github.com/jeffersonlab/puppet-show#install)
- [API](https://github.com/jeffersonlab/puppet-show#api) 
- [Configure](https://github.com/jeffersonlab/puppet-show#configure)
- [Release](https://github.com/jeffersonlab/puppet-show#release)
- [Deploy](https://github.com/jeffersonlab/puppet-show#deploy) 
- [See Also](https://github.com/jeffersonlab/puppet-showi#see-also)
---

## Overview
Use this web service to programatically convert web pages to PDF or image.  For example, create a cron job that uses the service to generate a daily report PDF from a web page and then email it.  The HTML form allows you to easily build your request for embedding in an application.  This service should only be installed internally on an intranet and not exposed to the Internet as it can be easily abused and would be a high security risk (For example using a file:// protocol in the URL exposes local files).

## Quick Start with Compose
1. Grab project
```
git clone https://github.com/jeffersonlab/puppet-show
cd puppet-show
```
2. Launch [Compose](https://github.com/docker/compose)
```
docker compose up
```
3. Launch web browser
```
http://localhost:3000/puppet-show
```
**Note**: Container requires `privileged` mode in order to launch Chrome in a sandbox.

## Install
```bash
npm i puppet-show
npm start
```
**Note**: This application runs on the Node.js JavaScript runtime, which can be downloaded [here](https://nodejs.org/en/download/).

## API
The URL parameter names for the web service end point __puppet-show/pdf__ and __puppet-show/screenshot__ mirror the option names for the puppeteer print-to-pdf and screenshot functions found [here](https://pptr.dev/api).  The puppet-show web forms can also be used to explore the API.

**Note**: The default values match the puppeteer defaults and the only required parameter is "url".

## Configure
```bash
export PORT=3000
npm start
```
**Note**: Use the appropriate set environment variable command for your shell; Bash shell shown above.  For C Shell use "setenv PORT 3000", and for Windows use "set PORT 3000".

## Release
0. Bump the version number in package.json and the two instances in package-lock.json.
1. Bump the version number in the VERSION file and commit and push to GitHub (using [Semantic Versioning](https://semver.org/)).
2. The [CD](https://github.com/JeffersonLab/puppet-show/blob/main/.github/workflows/cd.yaml) GitHub Action should run automatically invoking:
    - The [Create release](https://github.com/JeffersonLab/nodejs-workflows/blob/main/.github/workflows/gh-release.yaml) GitHub Action to tag the source and create release notes summarizing any pull requests.   Edit the release notes to add any missing details.
    - The [Publish NPM](https://github.com/JeffersonLab/nodejs-workflows/blob/main/.github/workflows/npm-publish.yaml) GitHub Action to create a deployment artifact on NPM.
    - The [Publish docker image](https://github.com/JeffersonLab/container-workflows/blob/main/.github/workflows/docker-publish.yaml) GitHub Action to create a new demo Docker image.

## Deploy
The app is deployed at JLab on nodejs9.acc.jlab.org.

## See Also
   - [Puppet Show Wiki](https://github.com/jeffersonlab/puppet-show/wiki)
   - [Chrome Remote Control (DevTools) Protocol](https://chromedevtools.github.io/devtools-protocol/tot/Page#method-printToPDF)
   - [Puppetron](https://github.com/cheeaun/puppetron)
   - [URL-to-PDF-API](https://github.com/alvarcarto/url-to-pdf-api)
