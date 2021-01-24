## Deploying to IBM Cloud

OLD VERSION

**Prepare the Push to IBM Cloud**
* Do not work on your own tutorial
* Rename the directory *loopback4-example-todo* and give it a unique name. This is important. When the app is later pushed to the IBM Cloud it has to have a unique route (api endpoint + app name).
* In *.src/index.ts* add *await app.migrateSchema();* between *await app.boot();* and *await app.start();* to have todo created on the database.
* Provisioning a Cloudant database service on IBM Cloud – Stay with the standard region, which is *London*
* Always (!) run* npm run build* before deploying
* Mandatory: Create the *.cfignore* file with corresponding content
* To show hidden files in Finder (Mac) press *Cmd + Shift + *.
* Update url or (password, username and port) in *db.datasource.config.json* with the values from the Cloudant database credentials. On *cloud.ibm.com* manage the Cloudant service, select *Service Credentials* on the left. If necessary, create new credentials.

**Push to IBM Cloud**
* Make sure you have got the right endpoint: *cf api https://api.eu-gb.bluemix.net*
* Login, have IBM Cloud login credentials ready: *cf login*
* Push the application to the cloud, set memory constraints to 256 MB or 512 MB: *cf push <<your-app-name>> -m256MB*

**Push to IBM Cloud - Errors**
* Errors about Org and Space – Check on endpoint and region
* Errors about Route – Check on unique route (api endpoint + app name)
* App does not start in IBM Cloud / memory errors / TCP connection error
  – Didyoudonpmrunbuildbeforethepushtothecloud?
  – Did you restrict memory?,e.g. push<app-name> -m256M
  – There ar ememory restrictions withyour IBM Cloud account,check that you have not already pushed several apps to the cloud
* 500 Error: Internal Server Error – Probably a database error. Is the application connected to the Cloudant DB? Is *db.datasource.configuration.json* correctly updated? Is migrate added to *index.ts*?

1. Do the tutorial [Deploying to IBM Cloud](https://loopback.io/doc/en/lb4/Deploying-to-IBM-Cloud.html)

**Deliverables:**
1. Being able to push an app to own IBM Cloud account. 

