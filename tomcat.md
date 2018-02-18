
# Tomcat Installation

1 . Download the latest version of Apache Tomcat from here >> [Get Apache](https://tomcat.apache.org/download-80.cgi)

2 . Open the Terminal (Ctrl + Alt + T) and enter the following commands. 


To change the directory.
> cd /opt/

3 . Enter the command given below to extract the Tomcat from  the ~/Downloads directory. If your downloaded file is in any other directory, replace the last parameter by the actual file path.
> sudo tar -xvzf ~/Downloads/apache-tomcat-8.0.26.tar.gz

4 . Rename the folder name to apache-tomcat. (this step is optional)
> sudo mv apache-tomcat-8.0.26/ apache-tomcat/

5 . Tomcat creates some files at the runtime inside this folder (Log files and some other configuration files). If you want to start Tomcat without root privilege, it is required to change the permission of this directory. Enter the following command to change the permission of apache-tomcat folder.
> sudo chmod -R 777 apache-tomcat/

6 . An environment variable has to be added to the system. Enter the following command in the terminal to open the /etc/environment in gedit.
> sudo gedit /etc/environment

7 . Add the following line at the end of the file. Save and close the gedit.
> CATALINA_HOME="/opt/apache-tomcat"

8 . Reload the environment variables to the current terminal using this command.
> source /etc/environment

9 . To start the Tomcat server.
> $CATALINA_HOME/bin/startup.sh





To check whether server has started or not [Click Here](http://localhost:8080/)


10 . To stop server .
> $CATALINA_HOME/bin/shutdown.sh
