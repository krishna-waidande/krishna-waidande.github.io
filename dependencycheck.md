## Dependency check 

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




