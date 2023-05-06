# Flowable

## How to deploy Flowable on your PC?

1. Download the latest Flowable version from https://github.com/flowable/flowable-engine/releases
2. Unzip the file, copy the war files inside `/wars` and paste them to `your-tomcat-directory/webapps`;
3. Go to `your-tomcat-directory/bin`, right-click your mouse, choose `Open in Terminal`, and execute `.\catalina.bat run`;
4. Visit http://127.0.0.1:8080/flowable-ui/idm/#/login. The default username/password is `admin`/`test`;
5. Visit http://127.0.0.1:8080/flowable-rest/docs/?url=specfile/process/flowable-swagger-process.json to read swagger API documents.

## BPMN

Business Process Model and Notation (BPMN) is a graphical representation for specifying business processes in a business process model.

## CMMN

The Case Management Model and Notation (CMMN) is a standard notation and formal specification for representing case models.

## DMN

Decision Model and Notation (DMN) is a standard approach for describing and modeling repeatable decisions within organizations to ensure that decision models are interchangeable across organizations.