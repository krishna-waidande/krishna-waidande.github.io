## Install Apache :

# + Prerequisites


Before you begin this guide, you should have a regular, non-root user with sudo privileges configured on your server/machine.


+ Step : 1

Apache is available within Ubuntu's default software repositories, so we will install it using conventional package management tools.
We will begin by updating the local package index to reflect the latest upstream changes. Afterwards, we can install the apache2 package:

Open your terminal and run below commands.

```sudo apt-get update```


```sudo apt-get install apache2```


+ Step 2: Check your Web Server.Run following command.

```sudo systemctl status apache2```


You will see below output
```
 apache2.service - LSB: Apache2 web server
   Loaded: loaded (/etc/init.d/apache2; bad; vendor preset: enabled)
  Drop-In: /lib/systemd/system/apache2.service.d
           └─apache2-systemd.conf
   Active: active (running) since Fri 2017-05-19 18:30:10 UTC; 1h 5min ago
     Docs: man:systemd-sysv-generator(8)
  Process: 4336 ExecStop=/etc/init.d/apache2 stop (code=exited, status=0/SUCCESS)
  Process: 4359 ExecStart=/etc/init.d/apache2 start (code=exited, status=0/SUCCESS)
    Tasks: 55
   Memory: 2.3M
      CPU: 4.094s
   CGroup: /system.slice/apache2.service
           ├─4374 /usr/sbin/apache2 -k start
           ├─4377 /usr/sbin/apache2 -k start
           └─4378 /usr/sbin/apache2 -k start
 ```          
 If you dont see status as Active run following command
 
```sudo systemctl restart apache2``` 


Then Check status it will show status as ```Acive```.



Now open your browser and type localhost in URL, in case of server type IP address of that server you will see default page of Apache.


### Now we will see how to configure multiple instance of Apaches on single machine.


+ 1. Open your terminal.

+ 2. Go to /usr/share/doc/apache2/examples this directory 
cd /usr/share/doc/apache2/examples

3. You will find setup-instance file.

3. Execute that file using ```sh setup-instance server2``` command where server2 is a suffix.That is it appends “apache2-” by default to your instance name. 

sudo sh setup-instance server2
[sudo] password for user: 
Setting up /etc/apache2-server2 ...
systemd is in use, no init script installed
use the 'apache2@server2.service' service to control your new instance
sample commands:
systemctl start apache2@server2.service
systemctl enable apache2@server2.service

so here above 2 commands are used to start and enable apache2@server2, run these 2 commands

you will see output like :

user@idp:/usr/share/doc/apache2/examples$ systemctl start apache2@server2.service
user@idp:/usr/share/doc/apache2/examples$ systemctl enable apache2@server2.service
Created symlink /etc/systemd/system/multi-user.target.wants/apache2@server2.service → /lib/systemd/system/apache2@.service.
user@idp:/usr/share/doc/apache2/examples$ 

to test weather your 2nd instance is running or not type below command

systemctl status apache2@server2.service
● apache2@server2.service - The Apache HTTP Server
   Loaded: loaded (/lib/systemd/system/apache2@.service; enabled; vendor preset: enabled)
   Active: active (running) since Thu 2018-06-14 11:53:16 IST; 39s ago
 Main PID: 17211 (apache2)
    Tasks: 55 (limit: 4915)
   CGroup: /system.slice/system-apache2.slice/apache2@server2.service
           ├─17211 /usr/sbin/apache2 -d /etc/apache2-server2 -k start
           ├─17212 /usr/sbin/apache2 -d /etc/apache2-server2 -k start
           └─17213 /usr/sbin/apache2 -d /etc/apache2-server2 -k start 

4. Now you should see a new directory /etc/apache2-server2 which contains all config files. It would also create /etc/init.d/apache2-server2 using which you can start your apache instance.

5. Get into /etc/apache2-server2/sites-available directory you will find 000-default.conf file edit that file with your servername in my case i put servername as localhost2.
here is a screenshot
```
<VirtualHost localhost2:8089>
	# The ServerName directive sets the request scheme, hostname and port that
	# the server uses to identify itself. This is used when creating
	# redirection URLs. In the context of virtual hosts, the ServerName
	# specifies what hostname must appear in the request's Host: header to
	# match this virtual host. For the default virtual host (this file) this
	# value is not decisive as it is used as a last resort host regardless.
	# However, you must set it for any further virtual host explicitly.
	#ServerName www.example.com
	ServerName localhost2 
	ServerAdmin webmaster@localhost
	DocumentRoot /var/www/html
	ErrorLog ${APACHE_LOG_DIR}/error.log
	CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```


6. Change the port.conf file which is present in /etc/apache2-server2
vi /etc/server2/port.conf
port.conf file

```
Listen 8089

<IfModule ssl_module>
	Listen 443
</IfModule>

<IfModule mod_gnutls.c>
	Listen 443
</IfModule>

```

Check for available port by typing command  ```sudo netstat -tlnp```


After doing this specify your hostname into /etc/hostname file and also add a entry of newly created hostname into /etc/hosts file also 

127.0.0.1	localhost
127.0.1.1	localhost2
192.168.1.128	localhost

#The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters


after all this i think we should go to check in the brower

run commands

service apache2 restart

check its status 
service apache2 restart


To start another server
service apache2@servere2 restart

check its status
service apache2@server2 status

in browser check into two different tabs whether server is up or not by typing
localhost & localhost2:8089 in the different tabas.
