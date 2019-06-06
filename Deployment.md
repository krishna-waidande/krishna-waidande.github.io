# Deployment

Hello readers,

My today's blog is on deployment and it's different types.


### What is Deployment?
In software development, it means delivering software to the client. 
In other terms, it is the process of installing/upgrading web application on the servers like Tomcat, JBoss.


There are two types of deployments.

> Hot deployment

> Cold deployment


### What is Hot Deployment?
The process of deploying the web app in a running server is called Hot Deployment. In this approach, there is no need to
restart the server. All changes take place on ON-THE-FLY.

### How we can achieve it into Tomcat server?


#### Advantages:

> No overhead of stop server => deploy WAR => start the server.

> No server downtime. The app is always available.

> Good choice of deployment in the test server environment.

> Time-saving.


#### Disadvantages:

> The file size keep increasing exponentially. Because files are being used by the server and those are not released by the server.

Example: log files, /tmp directory files.

> This is not a good approach for production servers. It will create a memory problem and after certain time app will crash.


### What is Cold Deployment?
Cold deployment can be defined as a process that requires a server restart to reflect the changes of application.
Cold deployment is slow but stable:

Steps of cold deployment:

> Stop running server(Tomcat)

> Optionally delete data/, log/, tmp/, work/

> Deploy/Redeploy your application(s)

> Start Tomcat


#### Advantages:

No memory issues. We can clear all log files, cache or /tmp files when the server is stopped.


#### Disadvantage:

It is more time-consuming.


