# step_by_step_install_of_workadventure
this is a step by step install for workadventure from a public pad:
https://pad.riseup.net/p/step_by_step_prod

this is an attempt to gather points for a step by step installation for a prod. env.
feel free to add your points!!!!!!!11!1

###1.0 installation on debian(based):
apt update & apt upgrade
apt install git curl wget ufw 
apt install docker docker-compose

###1.1 the best directory:
e.g. /home/$user/

###1.2 download workadventure:
git clone https://github.com/thecodingmachine/workadventure.git
git clone -b master --single-branch https://github.com/thecodingmachine/workadventure.git
git clone -b fix/deploy-cleanup --single-branch https://github.com/thecodingmachine/workadventure.git

###1.3 creating own docker-compose.pord.yml:
where i find a prod. docker-compose.prod.yml example?
Note:
https://github.com/thecodingmachine/workadventure/blob/fix/deploy-cleanup/docker-compose.prod.yaml


###1. 4 create own .env.prod.template:
where i find a .env.prod.template example?
Note:
https://github.com/thecodingmachine/workadventure/blob/fix/deploy-cleanup/.env.prod.template


###1. 5 set your own Jitsi and TURN server

###1. 5. 1 install a localTURN-server:
a how to install a TURN-server on ubuntu 18.04:
https://ourcodeworld.com/articles/read/1175/how-to-create-and-configure-your-own-stun-turn-server-with-coturn-in-ubuntu-18-04

###1. 5. 2 install a local jitsi:
how to install jitsi on ubuntu 18.04:
https://www.digitalocean.com/community/tutorials/how-to-install-jitsi-meet-on-ubuntu-18-04

###1. 5. 3 use a remote TURN-server:


###1. 5. 4 use a remote jitsi:


###1. 5. 5 merge the data from the installation of the TURN-server and jitsi into the env.prod.templatefile (for a local installation)
JITSI_URL=meet.localhost
JITSI_PRIVATE_MODE=true
JITSI_ISS=SECRET_JITSI_KEY= localhost.meet.key
TURN_SERVER= turn.localhost
TURN_USER= localuser
TURN_PASSWORD= localpassword

###1. 5. 6 merge the data from the installation of the TURN-server and jitsi into the env.prod.templatefile (for a remote installation)
JITSI_URL=meet.remote
JITSI_PRIVATE_MODE=true
JITSI_ISS=SECRET_JITSI_KEY= remote.meet.key (mybe you must transfer your key on the wa-server)
TURN_SERVER= turn.remote
TURN_USER= remoteuser
TURN_PASSWORD= remotepassword

###1. 6 configuration firewall:
ufw allow ssh
ufw allow http
ufw allow https
ufw enable


###1. 7 configuration webserver (apache2):
install the apache2 webserver:
apt install apache2


###1. 9 configuration tls:
when you want use a apache2 webserver with tls over certbot
apt install certbot python-certbot-apache


###1. 10 switch in the directory from workadventure for docker-compose (installation):
docker-compose up -d
docker-compose -f docker-compose.prod.yaml up -d


###2.0 installation over docker hub workadventuer files(https://hub.docker.com/u/thecodingmachine):


###Notes
The default docker-compose.yml will build and run "debug"-versions of services, which have a huge overhead. If you do not want to develop WA, it's better to create your own docker-compose.prod.yml
You should definitely create a .env file and set your own Jitsi and TURN addresses.
Right now (2021-02-02) Google TURN servers are hard-coded in several places. It is recommended to run your own TURN server.
Upsteam version has no decent support for mobile devices.
There are pull-requests for most of these issues - unfortunately many of those patches do not apply cleanly any longer.
so we can transfer the notes in a guide?!

###List of fork's (for single-domain):
