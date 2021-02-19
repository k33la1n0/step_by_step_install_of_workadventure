# step_by_step_install_of_workadventure
This is a step by step installing guide for workadventure from a public pad:
<https://pad.riseup.net/p/step_by_step_prod>

This is an attempt to gather points for a step by step installation for a prod. env.

Feel free to add your points!!!

### 1.0 Installation on Debian (based) linux distros:

```
apt update && apt upgrade
apt install git wget ufw docker docker-compose
```

### 1.1 Choose the best directory:
* e.g. /home/$user/

### 1.2 download workadventure:
* git clone -b master --single-branch https://github.com/thecodingmachine/workadventure/tree/master

### 1.3 Create own docker-compose.pord.yml:
Where do I find a docker-compose.prod.yml example?
* <https://github.com/thecodingmachine/workadventure/blob/fix/deploy-cleanup/docker-compose.prod.yaml>

### 1.4 Create own .env.prod.template:
Where do I find a .env.prod.template example?
* <https://github.com/thecodingmachine/workadventure/blob/fix/deploy-cleanup/.env.prod.template>

### 1.5 Set your own Jitsi and TURN server

### 1.5.1 Install a local TURN-server:
How to install a TURN-server on Ubuntu 18.04:
* <https://ourcodeworld.com/articles/read/1175/how-to-create-and-configure-your-own-stun-turn-server-with-coturn-in-ubuntu-18-04>

### 1.5.2 Install a local Jitsi server:
How to install Jitsi on Ubuntu 18.04:
* Official guide: <https://jitsi.github.io/handbook/docs/devops-guide/devops-guide-quickstart>
* Or: <https://www.digitalocean.com/community/tutorials/how-to-install-jitsi-meet-on-ubuntu-18-04>

### 1.5.3 Use a remote TURN-server:

### 1.5.4 use a remote Jitsi server:

### 1.5.5 Merge the data from the installation of the TURN-server and Jitsi into the env.prod.template-file (for a local installation)

```
JITSI_URL=meet.localhost
JITSI_PRIVATE_MODE=true
JITSI_ISS=SECRET_JITSI_KEY=localhost.meet.key
TURN_SERVER=turn.localhost
TURN_USER=localuser
TURN_PASSWORD=localpassword
```

### 1.5.6 Merge the data from the installation of the TURN-server and Jitsi into the env.prod.template-file (for a remote installation)

```
JITSI_URL=meet.remote
JITSI_PRIVATE_MODE=true
JITSI_ISS=SECRET_JITSI_KEY=remote.meet.key (maybe you must transfer your key to the workadventure-server)
TURN_SERVER=turn.remote
TURN_USER=remoteuser
TURN_PASSWORD=remotepassword
```

### 1.6 Configure the firewall:

```
ufw allow ssh
ufw allow http
ufw allow https
ufw enable
```

### 1.7 Configure a webserver (Apache2):
Install the Apache2 webserver:
* `apt install apache2`

### 1.8 Configure TLS:
when you want use an Apache2 webserver with TLS with certbot
* `apt install certbot python-certbot-apache`

### 1.9 Switch in the directory from workadventure for docker-compose (e. g. /home/workadventure):
* `docker-compose -f docker-compose.prod.yaml up -d`


### 2.0 Installation over docker hub workadventuer files (<https://hub.docker.com/u/thecodingmachine>):


### Notes
The default docker-compose.yml will build and run "debug"-versions of services, which have a huge overhead. If you do not want to develop WA, it's better to create your own docker-compose.prod.yml

You should definitely create a .env file and set your own Jitsi and TURN addresses.

Right now (2021-02-02) Google TURN servers are hard-coded in several places. It is recommended to run your own TURN server.

Upsteam version has no decent support for mobile devices.

There are pull-requests for most of these issues - unfortunately many of those patches do not apply cleanly any longer.

### List of fork's (for single-domain):
