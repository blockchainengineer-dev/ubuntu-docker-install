# ubuntu-docker-install
Bash script to install docker onto Ubuntu 20.04

## Install with bash scripts
For ease of use, install git onto your Ubuntu server and clone this repository. 
1) Install git  
`apt update && apt install git`

2) Setup ssh keys on your running Ubuntu droplet `ssh-keygen` then copy to github.com so you can clone repos via secure ssh https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-keys-2
3) Clone this repository: `git clone https://github.com/blockchainengineer-dev/ubuntu-docker-install.git`
4) Change directory into the cloned repo `cd /ubuntu-docker-install`
5) Then run `bash install_docker.sh`
6) type `docker --version` into the terminal and you should see the version of docker installed. If so then you've install docker succesfully!

## Install Docker manually:
Start a digitalocean droplet running Ubuntu 20.04, attach a volume with approx 60GB. You'll want at minimum 2 CPUs to help do the computation more efficiently (at the time of writing this - the $15/month instance will be a good starting point.)

ssh into the instance once it's up and running. Copy the ip address from the digitalocean dashboard to your clipboard and if you have multiple ssh keys on your machine then make sure to use the correct one with the -i flag... example: ssh -i ~/.ssh/digitalocean_key root@DROPLET-IPADDRESS

Now you're logged into the Ubuntu 20.04 droplet and you MUST be logged into the droplet terminal for the following instructions to work.

Now it's time to install docker onto the Ubuntu droplet, run the following commands (that can be found in git repository under droplet_setup/install_docker.sh)

apt update

apt install apt-transport-https ca-certificates curl software-properties-common -y

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | apt-key add -

add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable"

apt update

apt-cache policy docker-ce

apt-get install docker-ce -y