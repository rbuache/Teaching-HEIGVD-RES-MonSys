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
- IP address: 192.168.33.1

Virtual Machine run by Virtual Box
- IP address: 192.168.33.20
- PAT: packets arriving on 192.168.33.1:8080 are forwarded to 192.168.33.20:9090

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

What HTTP request did you type and send?

What HTTP response did you get?
# -------------------------------
```

```
# -- YOUR ANSWER TO QUESTION 8 --

Which command did you type on the terminal to establish the connection?

What HTTP request did you type and send?

What HTTP response did you get?
# -------------------------------
```




