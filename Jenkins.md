### [HOME](https://krishna-waidande.github.io/)

## Installation of Jenkins

+ Download the war file from URL : ```https://updates.jenkins-ci.org/download/war/```


### Way 1 :
+ Place this war into a installation directory where you want to install jenkins.
+ Then go into that folder and run the command: ```java -jar jenkinns.war```



#### Note : Jenkins by default runs on 8080 port. If you have your tomcat already running on 8080.you can run the following command by which Jenkins will run on another port.


```java -jar jenkins.war --httpPort=<Port no>```


Example : ```java -jar jenkins.war --httpPort=9090```



you will see the output as :
``` 
[jenkins@os-build ~]$ java -jar jenkins.war --httpPort=9090
Running from: /home/jenkins/jenkins.war
webroot: $user.home/.jenkins
Apr 14, 2018 9:13:21 AM Main deleteWinstoneTempContents
WARNING: Failed to delete the temporary Winstone file /tmp/winstone/jenkins.war
Apr 14, 2018 9:13:21 AM org.eclipse.jetty.util.log.Log initialized
INFO: Logging initialized @1016ms to org.eclipse.jetty.util.log.JavaUtilLog
Apr 14, 2018 9:13:21 AM winstone.Logger logInternal
INFO: Beginning extraction from war file
Apr 14, 2018 9:13:23 AM org.eclipse.jetty.server.handler.ContextHandler setContextPath
WARNING: Empty contextPath
Apr 14, 2018 9:13:23 AM org.eclipse.jetty.server.Server doStart
INFO: jetty-9.4.z-SNAPSHOT
Apr 14, 2018 9:13:24 AM org.eclipse.jetty.webapp.StandardDescriptorProcessor visitServlet
INFO: NO JSP Support for /, did not find org.eclipse.jetty.jsp.JettyJspServlet
Apr 14, 2018 9:13:24 AM org.eclipse.jetty.server.session.DefaultSessionIdManager doStart
INFO: DefaultSessionIdManager workerName=node0
Apr 14, 2018 9:13:24 AM org.eclipse.jetty.server.session.DefaultSessionIdManager doStart
INFO: No SessionScavenger set, using defaults
Apr 14, 2018 9:13:24 AM org.eclipse.jetty.server.session.HouseKeeper startScavenging
INFO: Scavenging every 660000ms
Jenkins home directory: /home/jenkins/.jenkins found at: $user.home/.jenkins
Apr 14, 2018 9:13:25 AM org.eclipse.jetty.server.handler.ContextHandler doStart
INFO: Started w.@37ebc9d8{/,file:///home/jenkins/.jenkins/war/,AVAILABLE}{/home/jenkins/.jenkins/war}
Apr 14, 2018 9:13:25 AM org.eclipse.jetty.server.AbstractConnector doStart
INFO: Started ServerConnector@532a02d9{HTTP/1.1,[http/1.1]}{0.0.0.0:9090}
Apr 14, 2018 9:13:25 AM org.eclipse.jetty.server.Server doStart
INFO: Started @5733ms
Apr 14, 2018 9:13:25 AM winstone.Logger logInternal
INFO: Winstone Servlet Engine v4.0 running: controlPort=disabled
Apr 14, 2018 9:13:28 AM jenkins.InitReactorRunner$1 onAttained
INFO: Started initialization
Apr 14, 2018 9:13:28 AM jenkins.InitReactorRunner$1 onAttained
INFO: Listed all plugins
Apr 14, 2018 9:13:31 AM jenkins.InitReactorRunner$1 onAttained
INFO: Prepared all plugins
Apr 14, 2018 9:13:31 AM jenkins.InitReactorRunner$1 onAttained
INFO: Started all plugins
Apr 14, 2018 9:13:31 AM jenkins.InitReactorRunner$1 onAttained
INFO: Augmented all extensions
Apr 14, 2018 9:13:33 AM jenkins.InitReactorRunner$1 onAttained
INFO: Loaded all jobs
Apr 14, 2018 9:13:33 AM hudson.model.AsyncPeriodicWork$1 run
INFO: Started Download metadata
Apr 14, 2018 9:13:34 AM jenkins.InitReactorRunner$1 onAttained
INFO: Completed initialization
Apr 14, 2018 9:13:38 AM org.springframework.context.support.AbstractApplicationContext prepareRefresh
INFO: Refreshing org.springframework.web.context.support.StaticWebApplicationContext@5efba548: display name [Root WebApplicationContext]; startup date [Sat Apr 14 09:13:38 UTC 2018]; root of context hierarchy
Apr 14, 2018 9:13:38 AM org.springframework.context.support.AbstractApplicationContext obtainFreshBeanFactory
INFO: Bean factory for application context [org.springframework.web.context.support.StaticWebApplicationContext@5efba548]: org.springframework.beans.factory.support.DefaultListableBeanFactory@152286f1
Apr 14, 2018 9:13:38 AM org.springframework.beans.factory.support.DefaultListableBeanFactory preInstantiateSingletons
INFO: Pre-instantiating singletons in org.springframework.beans.factory.support.DefaultListableBeanFactory@152286f1: defining beans [authenticationManager]; root of factory hierarchy
Apr 14, 2018 9:13:43 AM org.springframework.context.support.AbstractApplicationContext prepareRefresh
INFO: Refreshing org.springframework.web.context.support.StaticWebApplicationContext@108ecdf8: display name [Root WebApplicationContext]; startup date [Sat Apr 14 09:13:43 UTC 2018]; root of context hierarchy
Apr 14, 2018 9:13:43 AM org.springframework.context.support.AbstractApplicationContext obtainFreshBeanFactory
INFO: Bean factory for application context [org.springframework.web.context.support.StaticWebApplicationContext@108ecdf8]: org.springframework.beans.factory.support.DefaultListableBeanFactory@24185acd
Apr 14, 2018 9:13:43 AM org.springframework.beans.factory.support.DefaultListableBeanFactory preInstantiateSingletons
INFO: Pre-instantiating singletons in org.springframework.beans.factory.support.DefaultListableBeanFactory@24185acd: defining beans [filter,legacy]; root of factory hierarchy
Apr 14, 2018 9:13:43 AM hudson.model.UpdateSite updateData
INFO: Obtained the latest update center data file for UpdateSource default
Apr 14, 2018 9:13:44 AM hudson.model.DownloadService$Downloadable load
INFO: Obtained the updated data file for hudson.tasks.Maven.MavenInstaller
Apr 14, 2018 9:13:44 AM jenkins.install.SetupWizard init
INFO: 

*************************************************************
*************************************************************
*************************************************************

Jenkins initial setup is required. An admin user has been created and a password generated.
Please use the following password to proceed to installation:

84004c482cac44b8ab85a768014c30b8

This may also be found at: /home/jenkins/.jenkins/secrets/initialAdminPassword

*************************************************************
*************************************************************
*************************************************************

Apr 14, 2018 9:13:45 AM hudson.model.DownloadService$Downloadable load
INFO: Obtained the updated data file for hudson.tools.JDKInstaller
Apr 14, 2018 9:13:45 AM hudson.model.AsyncPeriodicWork$1 run
INFO: Finished Download metadata. 12,330 ms
Apr 14, 2018 9:13:50 AM hudson.model.UpdateSite updateData
INFO: Obtained the latest update center data file for UpdateSource default
Apr 14, 2018 9:13:50 AM hudson.WebAppMain$3 run
INFO: Jenkins is fully up and running
```

Now Open the browser and hit the URL ```localhost:<port no>/``` you will see the jenkins page. fill the required credentials.

### Way 2 :

+ Shutdown the Tomcat.
+ Place downloaded ```jenkins.war``` file into ```TOMCAT_HOME/webapps folder```. 
+ Start the Tomcat.
+ Check the log file catalina.out which is placed in the ```TOMCAT_HOME/logs/catalina.out```. Run command to check logs.


```tail -100f TOMCAT_HOME/logs/catalina.out```

It's chainset will start to run and at the end you will see a log message as


```INFO: Jenkins is fully up and running```

After this Open the browser and hit the URL ```localhost:<port no>/jenkins``` you will see the jenkins page. fill the required credentials.

## That's it. You have successfully installed Jenkins on your machine. 


