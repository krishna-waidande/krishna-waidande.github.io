### [Assignment1](https://krishna-waidande.github.io//) | [Assignment2](https://krishna-waidande.github.io//Assignment2) |  [Apache Tomcat Installation](https://krishna-waidande.github.io//tomcat) 


## Gradle Installation

1 . Download zip file of gradlbe from https://gradle.org/releases/

2 . After downloading zip file run following command into terminal


> sudo mkdir /opt/gradle   


3 . Extract zip file into downloaded folder you will get this folder "gradle-4.5.1"


4 . Copy that folder into /opt/gradle folder by typing following command   


> sudo cp gradle-4.5.1 -r /opt/gradle



5 . Configure your system environment


type this command in terminal
```export PATH=$PATH:/opt/gradle/gradle-4.5.1/bin:$PATH```

After that just run this command into terminal

> gradle -v or gradle --version


You will get following output

```
------------------------------------------------------------
Gradle 4.5.1
------------------------------------------------------------

Build time:   2018-02-05 13:22:49 UTC
Revision:     37007e1c012001ff09973e0bd095139239ecd3b3

Groovy:       2.4.12
Ant:          Apache Ant(TM) version 1.9.9 compiled on February 2 2017
JVM:          9.0.4 (Oracle Corporation 9.0.4+11)
OS:           Linux 4.13.0-32-generic amd64

```

This is a offical link for installation of gradle 
[Gradle-Install](https://gradle.org/install/)
