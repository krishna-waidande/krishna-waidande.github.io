# Deployment

Hello readers,

My today's blog is on deployment and it's type.


### What is Deployment?
In Software development it means delivering software to the client. 
In other terms it is process of installing/upgrading web application on the servers like Tomcat, JBoss.


There are two types of deployments.

> Hot deployment

> Cold deployment


### What is Hot Deployment ?
The process of deploying web app in running server is called Hot Deployment. In this approach there is no need to
restart the whole server. All changes takes place on ON-THE-FLY.

### How we can achieve it into Tomcat server?


#### Advantages:

> No overhead of stop server => deploy WAR => start the server.

> No server down-time. App is always available.

> Good choice of deployment in test server environment.

> Time saving.


#### Disadvantages:

> The size of files holded by server keep increasing exponentially.
Eg: log files, tmp/ directory files.

> This is not good approach for production servers. It will create a memory problem and after certain time app will crash.


### What is Cold Deployment ?
Cold deployment can be defined as process that require instance of the server to restart to reflect the changes of application.
Cold deployment is slow but stable:

Steps of cold deployment:

> Stop running server(Tomcat)

> Optionally delete data/, log/, tmp/, work/

> Deploy/Redeploy your application(s)

> Start Tomcat


#### Advantages:

No memory issues. We can clear all log files, cache or /tmp files when server is stopeed.

Disadvantage:

It is more time consuming.


