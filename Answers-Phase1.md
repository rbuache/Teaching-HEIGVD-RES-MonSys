# Answers, Phase 1

```
# -- INSERT YOUR NAMES HERE -----
Raphael, Buache
Magali, Frohlich

We certify that we have done all the lab tasks and we have a running environment on our 
machine to prove it. We are ready to demonstrate it at any time and to explain the process
we have followed.
# -------------------------------
```


```
# -- YOUR ANSWER TO QUESTION 1 --

b-infra> vagrant up
inging machine 'default' up with 'virtualbox' provider...
> default: Clearing any previously set forwarded ports...
> default: Clearing any previously set network interfaces...
> default: Preparing network interfaces based on configuration...
  default: Adapter 1: nat
  default: Adapter 2: hostonly
> default: Forwarding ports...
  default: 9090 => 8080 (adapter 1)
  default: 22 => 2222 (adapter 1)
> default: Booting VM...
> default: Waiting for machine to boot. This may take a few minutes...
  default: SSH address: 127.0.0.1:2222
  default: SSH username: vagrant
  default: SSH auth method: private key
  default: Warning: Connection timeout. Retrying...
> default: Machine booted and ready!
> default: Checking for guest additions in VM...
> default: Configuring and enabling network interfaces...
> default: Mounting shared folders...
  default: /vagrant => C:/Users/Raphael/Documents/HEIG-VD/RES/GIT/Teaching-HEI
D-RES-Monsys/monsys-web-infra
> default: Machine already provisioned. Run `vagrant provision` or use the `--
ovision`
> default: to force provisioning. Provisioners marked to run always will still
un.
 C:\Users\Raphael\Documents\HEIG-VD\RES\GIT\Teaching-HEIGVD-RES-Monsys\monsys-
b-infra> vagrant provision
> default: Running provisioner: shell...
  default: Running: inline script
> default: stdin: is not a tty
> default: Cleaning up Docker containers...
> default: /tmp/vagrant-shell: line 2: docker: command not found
> default: /tmp/vagrant-shell: line 3: docker: command not found
> default: /tmp/vagrant-shell: line 4: docker: command not found
> default: /tmp/vagrant-shell: line 5: docker: command not found
> default: /tmp/vagrant-shell: line 6: docker: command not found
> default: /tmp/vagrant-shell: line 7: docker: command not found
> default: /tmp/vagrant-shell: line 8: docker: command not found
> default: /tmp/vagrant-shell: line 9: docker: command not found
> default: Running provisioner: docker...
  default: Installing Docker (latest) onto machine...
  default: Configuring Docker to autostart containers...
> default: Building Docker images...
> default: -- Path: /vagrant/docker/rp-nginx
> default: -- Path: /vagrant/docker/web-apache
> default: -- Path: /vagrant/docker/app-nodejs
> default: Starting Docker containers...
> default: -- Container: rp-node
> default: -- Container: web-node-1
> default: -- Container: web-node-2
> default: -- Container: app-node

# -------------------------------
```

```
# -- YOUR ANSWER TO QUESTION 2 --
vagrant@ubuntu-14:~$ uname -a
Linux ubuntu-14 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:11:08 UTC 2014 x8
6_64 x86_64 x86_64 GNU/Linux
# -------------------------------
```

```
# -- YOUR ANSWER TO QUESTION 3 --
vagrant@ubuntu-14:~$ docker images
REPOSITORY          TAG                 IMAGE ID            CREATED
VIRTUAL SIZE
heig/app-nodejs     latest              05ecb36202be        9 minutes ago
608.7 MB
heig/web-apache     latest              00c7c2b7852e        12 minutes ago
622.6 MB
heig/rp-nginx       latest              2115a9e09082        16 minutes ago
956.3 MB
dockerfile/ubuntu   latest              887afc884c07        3 hours ago
584.2 MB
# -------------------------------
```

```
# -- YOUR ANSWER TO QUESTION 4 --
vagrant@ubuntu-14:~$ docker ps
CONTAINER ID        IMAGE                    COMMAND                CREATED
        STATUS              PORTS                  NAMES
0209034d4cfb        heig/app-nodejs:latest   node /opt/server.js    11 minutes a
go      Up 11 minutes       0.0.0.0:7070->80/tcp   app-node
e853c7abfc27        heig/web-apache:latest   /usr/sbin/apache2ctl   11 minutes a
go      Up 11 minutes       0.0.0.0:8082->80/tcp   web-node-2
9c03ee2f5760        heig/web-apache:latest   /usr/sbin/apache2ctl   11 minutes a
go      Up 11 minutes       0.0.0.0:8081->80/tcp   web-node-1
6553e040e8d8        heig/rp-nginx:latest     /opt/init.sh           11 minutes a
go      Up 11 minutes       0.0.0.0:9090->80/tcp   rp-node
# -------------------------------
```

```
# -- YOUR ANSWER TO QUESTION 5 --
app-node -> IPAddress: 172.17.0.5 , IPPrefixLen : 16 , Gateway : 172.17.0.5, HostPort : 7070
web-node-2 -> IPAddress: 172.17.0.4 , IPPrefixLen : 16 , Gateway : 172.17.42.1, HostPort : 8082
web-node-1 -> IPAddress: 172.17.0.3 , IPPrefixLen : 16 , Gateway : 172.17.42.1, HostPort : 8081
rp-node -> IPAddress: 172.17.0.2 , IPPrefixLen : 16 , Gateway : 172.17.42.1, HostPort : 9090
# -------------------------------
```

```
# -- YOUR ANSWER TO QUESTION 6 --

Host (your laptop):
- IP address: 10.192.85.144 (wifi heig)

Virtual Machine run by Virtual Box
- IP address: 192.168.33.1 (gateway to virtual machine)
- PAT: packets arriving on 192.168.33.20:8080 are forwarded to 172.17.42.1:9090

Docker Bridge
- IP address: 172.17.42.1
- PAT: packets arriving on 172.17.42.1:9090 are forwarded to 172.17.0.2:80
- PAT: packets arriving on 172.17.42.1:8081 are forwarded to 172.17.0.3:80
- PAT: packets arriving on 172.17.42.1:8082 are forwarded to 172.17.0.4:80
- PAT: packets arriving on 172.17.42.1:7070 are forwarded to 172.17.0.5:80

Docker Container 1
- IP address: 172.17.0.2

Docker Container 2
- IP address: 172.17.0.3

Docker Container 3
- IP address: 172.17.0.4

Docker Container 4
- IP address: 172.17.0.5

# -------------------------------
```

```
# -- YOUR ANSWER TO QUESTION 7 --

Which command did you type on the terminal to establish the connection?
telnet 192.168.33.1 8080

What HTTP request did you type and send?
GET / HTTP/1.1
Host: www.monsys.com

What HTTP response did you get?
HTTP/1.1 200 OK
Server: nginx/1.6.0
Date: Wed, 14 May 2014 20:24:22 GMT
Content-Type: text/html
Content-Length: 1538
Connection: keep-alive
X-Powered-By: PHP/5.5.9-1ubuntu4
Vary: Accept-Encoding

<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN"
        "http://www.w3.org/TR/html4/loose.dtd">
<html>
        <head>
                <meta http-equiv="Content-Type" content="text/html; charset=UTF-
8">
                <link href='http://fonts.googleapis.com/css?family=Terminal+Dosi
s' rel='stylesheet' type='text/css'>
                <link href='css/main.css' rel='stylesheet' type='text/css'>
                <script type="text/javascript" src="script/jquery-1.6.4.js"></sc
ript>
                <title>Welcome To MonSys Front-End</title>

                <script language="JavaScript">

                        $(document).ready(function () {
                                refreshNodes();
                        });

                        function refreshNodes() {
                            $.getJSON('/ajax/resources/nodes',
                            function(data) {
                                var items = [];

                                $.each(data,
                                function(key, val) {
                                    items.push('<li>' + val.name + ", " + val.de
scription + ", load: " + val.currentLoadLevel + ' %</li>');
                                });

                                $('#monitor').html("<ul>" + items.join('') + "</
ul>");
                            });
                                var t=setTimeout("refreshNodes()", 1000);
                        }
        </script>
        </head>
        <body>
                <h1>Welcome to MonSys</h1>
                <h2>You are connected to the front-end system, implemented in PH
P</h2>
                <b>Note</b>: this page is sending HTTP GET requests to <verbatim
>/ajax/resources/nodes</verbatim> in order to retrieve JSON representations of t
he resources managed by the back-end.
                <p/>

                <div id="monitor">
                        You should monitoring data coming from the back-end here
.
                </div>

                <br/>
                Brought to you by the University of Applied Sciences of Western
Switzerland
        </body>
</html>
# -------------------------------
```

```
# -- YOUR ANSWER TO QUESTION 8 --

Which command did you type on the terminal to establish the connection?
telnet 192.168.33.1 8080

What HTTP request did you type and send?
GET /ajax/resources/nodes HTTP/1.1
Host: www.monsys.com

What HTTP response did you get?

HTTP/1.1 200 OK
Server: nginx/1.6.0
Date: Wed, 14 May 2014 20:27:50 GMT
Content-Type: application/json
Transfer-Encoding: chunked
Connection: keep-alive

fa
[{"name":"P-001","description":"Epson Printer","currentLoadLevel":75.20957826636
732},{"name":"P-002","description":"Canon Printer","currentLoadLevel":65.9741254
5233965},{"name":"P-003","description":"HP Printer","currentLoadLevel":38.016505
30658662}]
0

# -------------------------------
```

```
# -- YOUR ANSWER TO QUESTION 9 --

What procedure did you follow to validate the configuration of 
your new web nodes? 
-Controle que les noeuds sont actifs dans la machine virtuel
-Récupere l'IP d'un noeud
-Accédé un serveur via telnet

Provide details and evidence (command results, etc.) that your 
setup is correct.

vagrant@ubuntu-14:~$ docker ps
CONTAINER ID        IMAGE                    COMMAND                CREATED
         STATUS              PORTS                  NAMES
91ab143176f8        heig/web-clash:latest    /usr/sbin/apache2ctl   About a minu
te ago   Up About a minute   0.0.0.0:8883->80/tcp   clash-node-3
34d39223717b        heig/web-clash:latest    /usr/sbin/apache2ctl   About a minu
te ago   Up About a minute   0.0.0.0:8882->80/tcp   clash-node-2
b7f141201a80        heig/web-clash:latest    /usr/sbin/apache2ctl   About a minu
te ago   Up About a minute   0.0.0.0:8881->80/tcp   clash-node-1
ea30d3b28ef3        heig/app-nodejs:latest   node /opt/server.js    About a minu
te ago   Up About a minute   0.0.0.0:7070->80/tcp   app-node
1f4912dd4cbc        heig/web-apache:latest   /usr/sbin/apache2ctl   About a minu
te ago   Up About a minute   0.0.0.0:8082->80/tcp   web-node-2
7f388cab4a75        heig/web-apache:latest   /usr/sbin/apache2ctl   About a minu
te ago   Up About a minute   0.0.0.0:8081->80/tcp   web-node-1
81d5f9da2e88        heig/rp-nginx:latest     /opt/init.sh           About a minu
te ago   Up About a minute   0.0.0.0:9090->80/tcp   rp-node

vagrant@ubuntu-14:~$ docker inspect clash-node-1
[{
    "ID": "b7f141201a802134831d7740081ff05f7e78613796ba445abcf36a481a3a73ad",
    "Created": "2014-05-15T13:24:15.439954669Z",
    "Path": "/usr/sbin/apache2ctl",
    "Args": [
        "-D",
        "FOREGROUND"
    ],
    "Config": {
        "Hostname": "b7f141201a80",
        "Domainname": "",
        "User": "",
        "Memory": 0,
        "MemorySwap": 0,
        "CpuShares": 0,
        "AttachStdin": false,
        "AttachStdout": false,
        "AttachStderr": false,
        "PortSpecs": null,
        "ExposedPorts": {
            "80/tcp": {}
        },
        "Tty": false,
        "OpenStdin": false,
        "StdinOnce": false,
        "Env": [
            "HOME=/root",
            "PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin",

            "APACHE_RUN_USER=www-data",
            "APACHE_RUN_GROUP=www-data",
            "APACHE_LOG_DIR=/var/log/apache2"
        ],
        "Cmd": [
            "-D",
            "FOREGROUND"
        ],
        "Image": "heig/web-clash",
        "Volumes": null,
        "WorkingDir": "/root",
        "Entrypoint": [
            "/usr/sbin/apache2ctl"
        ],
        "NetworkDisabled": false,
        "OnBuild": null
    },
    "State": {
        "Running": true,
        "Pid": 10613,
        "ExitCode": 0,
        "StartedAt": "2014-05-15T13:24:15.568849442Z",
        "FinishedAt": "0001-01-01T00:00:00Z"
    },
    "Image": "29bcb920cba36ec1a672ca469ceb52caa2511e86ff528b3263354c6c0cd171f2",

    "NetworkSettings": {
        "IPAddress": "172.17.0.6",
        "IPPrefixLen": 16,
        "Gateway": "172.17.42.1",
        "Bridge": "docker0",
        "PortMapping": null,
        "Ports": {
            "80/tcp": [
                {
                    "HostIp": "0.0.0.0",
                    "HostPort": "8881"
                }
            ]
        }
    },
    "ResolvConfPath": "/etc/resolv.conf",
    "HostnamePath": "/var/lib/docker/containers/b7f141201a802134831d7740081ff05f
7e78613796ba445abcf36a481a3a73ad/hostname",
    "HostsPath": "/var/lib/docker/containers/b7f141201a802134831d7740081ff05f7e7
8613796ba445abcf36a481a3a73ad/hosts",
    "Name": "/clash-node-1",
    "Driver": "aufs",
    "ExecDriver": "native-0.2",
    "MountLabel": "",
    "ProcessLabel": "",
    "Volumes": {},
    "VolumesRW": {},
    "HostConfig": {
        "Binds": null,
        "ContainerIDFile": "/var/lib/vagrant/cids/0f3ab08f14ba52c518d66319a25bcb
6acf9b2401",
        "LxcConf": [],
        "Privileged": false,
        "PortBindings": {
            "80/tcp": [
                {
                    "HostIp": "0.0.0.0",
                    "HostPort": "8881"
                }
            ]
        },
        "Links": null,
        "PublishAllPorts": false,
        "Dns": null,
        "DnsSearch": null,
        "VolumesFrom": null,
        "NetworkMode": "bridge"
    }
}]

vagrant@ubuntu-14:~$ telnet 172.17.0.6 80
Trying 172.17.0.6...
Connected to 172.17.0.6.
Escape character is '^]'.
GET / HTTP/1.1
Host: live.clashofclasses.ch

HTTP/1.1 200 OK
Date: Thu, 15 May 2014 13:27:21 GMT
Server: Apache/2.4.7 (Ubuntu)
Vary: Accept-Encoding
Content-Length: 1161
Content-Type: text/html;charset=UTF-8

<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 3.2 Final//EN">
<html>
 <head>
  <title>Index of /</title>
 </head>
 <body>
<h1>Index of /</h1>
  <table>
   <tr><th valign="top"><img src="/icons/blank.gif" alt="[ICO]"></th><th><a href
="?C=N;O=D">Name</a></th><th><a href="?C=M;O=A">Last modified</a></th><th><a hre
f="?C=S;O=A">Size</a></th><th><a href="?C=D;O=A">Description</a></th></tr>
   <tr><th colspan="5"><hr></th></tr>
<tr><td valign="top"><img src="/icons/folder.gif" alt="[DIR]"></td><td><a href="
css/">css/</a></td><td align="right">2014-05-15 13:17  </td><td align="right">
- </td><td>&nbsp;</td></tr>
<tr><td valign="top"><img src="/icons/text.gif" alt="[TXT]"></td><td><a href="li
ve-index.html">live-index.html</a></td><td align="right">2014-05-15 12:53  </td>
<td align="right">2.0K</td><td>&nbsp;</td></tr>
<tr><td valign="top"><img src="/icons/image2.gif" alt="[IMG]"></td><td><a href="
success.jpg">success.jpg</a></td><td align="right">2014-05-15 12:53  </td><td al
ign="right"> 70K</td><td>&nbsp;</td></tr>
   <tr><th colspan="5"><hr></th></tr>
</table>
<address>Apache/2.4.7 (Ubuntu) Server at live.clashofclasses.ch Port 80</address
>
</body></html>
Connection closed by foreign host.

# -------------------------------
```

```
# -- YOUR ANSWER TO QUESTION 10 --

What procedure did you follow to validate the configuration of 
your complete infrastructure?
-Controle que les containers sont actifs
-Accès au serveur web via un navigateur sur l'hôte
-Requete http avec telnet depuis l'hôte

Provide details and evidence (command results, etc.) that your 
setup is correct.

vagrant@ubuntu-14:~$ docker ps
CONTAINER ID        IMAGE                    COMMAND                CREATED
        STATUS              PORTS                  NAMES
8ef5e91e5ca3        heig/web-clash:latest    /usr/sbin/apache2ctl   3 minutes ag
o       Up 3 minutes        0.0.0.0:8883->80/tcp   clash-node-3
e84799cc50f1        heig/web-clash:latest    /usr/sbin/apache2ctl   3 minutes ag
o       Up 3 minutes        0.0.0.0:8882->80/tcp   clash-node-2
e6ab89b5e40f        heig/web-clash:latest    /usr/sbin/apache2ctl   3 minutes ag
o       Up 3 minutes        0.0.0.0:8881->80/tcp   clash-node-1
a25e2e807ea3        heig/app-nodejs:latest   node /opt/server.js    3 minutes ag
o       Up 3 minutes        0.0.0.0:7070->80/tcp   app-node
6391dafe1d53        heig/web-apache:latest   /usr/sbin/apache2ctl   3 minutes ag
o       Up 3 minutes        0.0.0.0:8082->80/tcp   web-node-2
63d3089a01a5        heig/web-apache:latest   /usr/sbin/apache2ctl   3 minutes ag
o       Up 3 minutes        0.0.0.0:8081->80/tcp   web-node-1
c965e8ad2629        heig/rp-nginx:latest     /opt/init.sh           3 minutes ag
o       Up 3 minutes        0.0.0.0:80->80/tcp     rp-node

C:\Users\Raphael>telnet 192.168.33.20 80
Trying 192.168.33.20...
Connected to 192.168.33.20.
Escape character is '^]'.
GET / HTTP/1.1
Host: live.clashofclasses.ch

HTTP/1.1 200 OK
Server: nginx/1.6.0
Date: Thu, 15 May 2014 17:23:14 GMT
Content-Type: text/html
Content-Length: 2058
Connection: keep-alive
Last-Modified: Thu, 15 May 2014 12:53:55 GMT
ETag: "80a-4f96fca25bec0"
Accept-Ranges: bytes
Vary: Accept-Encoding

<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <meta name="description" content="">
    <meta name="author" content="">
        <link href="http://netdna.bootstrapcdn.com/font-awesome/4.0.3/css/font-a
wesome.css" rel="stylesheet">
    <title>Sticky Footer Template for Bootstrap</title>

    <!-- Bootstrap core CSS -->
    <link href="./css/live-bootstrap.css" rel="stylesheet">

    <!-- Custom styles for this template -->
    <link href="./css/sticky-footer.css" rel="stylesheet">

    <!-- Just for debugging purposes. Don't actually copy this line! -->
    <!--[if lt IE 9]><script src="../../assets/js/ie8-responsive-file-warning.js
"></script><![endif]-->

    <!-- HTML5 shim and Respond.js IE8 support of HTML5 elements and media queri
es -->
    <!--[if lt IE 9]>
      <script src="https://oss.maxcdn.com/libs/html5shiv/3.7.0/html5shiv.js"></s
cript>
      <script src="https://oss.maxcdn.com/libs/respond.js/1.4.2/respond.min.js">
</script>
    <![endif]-->
  </head>

  <body>

    <!-- Begin page content -->
    <div class="container">
      <div class="page-header">
        <h1>Welcome To Clash of Classes!</h1>
      </div>
      <p class="lead">This is the Welcome Page for the <b>live</b> section of th
e website, which is accessible at this URL <a href="http://live.clashofclasses.c
h">http://live.clashofclasses.ch</a>.</p>
      <p class="lead">You can jump to the <b>dashboard</b> section of the websit
e <a href="http://dashboard.clashofclasses.ch">here</a>.</p>

        <p></p>
                <img src="success.jpg" width="300">
        <p></p>


    </div>


    <div id="footer">
      <div class="container">
        <p class="text-muted">We <i class="fa fa-heart"></i> Application Level P
rotocols</p>
      </div>
    </div>


    <!-- Bootstrap core JavaScript
    ================================================== -->
    <!-- Placed at the end of the document so the pages load faster -->
  </body>
</html>
Connection closed by foreign host.

Troubleshooting...
-Oublié de modifier le nom du fichier en index.html
-accès au serveur web que par le port 9090 depuis le host : modification en 80 sur le reverse proxy
-Problème de containers... -> vagrant destroy -> vagrant up

Config fichier hosts :

192.168.33.20       www.monsys.com
192.168.33.20	   dashboard.clashofclasses.ch
192.168.33.20	   live.clashofclasses.ch

# -------------------------------
```


