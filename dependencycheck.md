### [HOME](https://krishna-waidande.github.io/)

# Dependency check 

In this article we will learn about how to configure dependency check.but before going to topic let's see what is dependency-check.


### Dependency: ```It means jar file included in your project```


### Vulnerability: ```It means any loop hole. by using that attacker can hack your system.```


### Dependency check : ```It means checking dependencies included in your project. while coding you might have added some third party dependencies into your project.so It checks your all dependencies and if there are any vulnerabilities into your dependency so it will generate a report of each dependency and its vulnerability.```


I hope you have understand what is dependency check.


You must be thinking how does this dependency-check comes to know that which dependency is vulnerable & which is not.


So while installing dependency check it internally downloads one database into your machine locally.where all the vulnerable dependencies are listed with its vulenrabilities.This database is called NVD.


### NVD : ```National Vulnerability Database (NVD) is a government repository of standards-based vulnerability information.```

So each time whenever you perform dependency-check it checks each dependency included in your project with NVD.
dependencies which are there in the NVD, it generates report of these vulnerabilites and stores them into dependency-check-report.html file.


I hope you have get an overall idea about dependency check and why we need to include this into our project.


now let's check how we can install it and perform dependency check. there are mutiple ways to configure this into our project.

+ CLI (Command Line)
+ Gradle plugin
+ Ant plugin
+ Jenkins plugin


In this article we will see how to configure it by using CLI and Gradle plugin.

###  CLI (Command Line) :

Go to this link : [Dependency-check](https://www.owasp.org/index.php/OWASP_Dependency_Check) and see on your right side of screen. you will se ```Quick Download``` option. then click on ```Command line``` option.Then downloading will start, it will download on zip file.


Now open Terminal go to download folder.


+ Unzip that zip.


+ After that go into dependency-check/bin folder.you will see 2 scripts. ```dependency.bat``` for windows & ```dependency.sh```
for Linux.

+ Run this command


```./dependency-check.sh --project test --scan <path to dependency jars>```

```--project``` option is mendatory.


Example : ```./dependency-check.sh --project test --scan /opt/apache-tomcat/webapps/openspecimen/WEB-INF/lib/```
  
  
+ For more options you can go to this link : [Dependenccy-check-options](https://jeremylong.github.io/DependencyCheck/dependency-check-cli/arguments.html)

### Gradle plugin:

+ Add these lines in your build.gradle file.


```groovy
buildscript {
    repositories {
        mavenCentral()
    }
    dependencies {
        classpath 'org.owasp:dependency-check-gradle:3.2.1'
    }
}

apply plugin: 'org.owasp.dependencycheck'
```

### Some more things to know: 

```What if your project includes multiple sub-project? How can we use this plugin for each of them including the root project?```


+  For all projects including root project:

```groovy
buildscript {
  repositories {
    mavenCentral()
  }
  dependencies {
    classpath 'org.owasp:dependency-check-gradle:3.2.0'
  }
}

allprojects {
    apply plugin: 'org.owasp.dependencycheck'
}
```

+  For all sub-projects:


```groovy
buildscript {
  repositories {
    mavenCentral()
  }
  dependencies {
    classpath 'org.owasp:dependency-check-gradle:3.2.0'
  }
}

subprojects {
    apply plugin: 'org.owasp.dependencycheck'
}
```

+ Customize the report directory.


By default, all reports will be placed under build/reports folder, to change the default reporting folder name modify the configuration section like this:

```groovy
subprojects {
    apply plugin: 'org.owasp.dependencycheck'

    dependencyCheck {
        outputDirectory = "security-report"
    }
}
```











