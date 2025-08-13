# Moodle Deploy

A single-script solution for deploying a Moodle site on Debian, automating everything from the core installation to the server stack.

Also includes virtual machine configuration (Vagrant) for local development.

**Key Features**
- Spins up Moodle on Apache with a PostgreSQL database.
- Configure everything interactively.
- Includes HTTPS (incl. SSL certificate creation), firewall and IPS/IDS.
- Regular database backups, swapfiles.

**Server Stack**
- Moodle 5.0
- PostgreSQL 17
- Apache 2
- Debian 12
- Fail2Ban
- UFW
- Cron

## Usage

For production sites: *first obtain a domain name and add a DNS record linking it to the IP address of your server (required for HTTPS).*

Copy `moodle-install` onto your server or VPS and run it:
```sh
./moodle-install
```

## Local Development
First, install [Vagrant](https://developer.hashicorp.com/vagrant/install), [VirtualBox](https://www.oracle.com/virtualization/technologies/vm/downloads/virtualbox-downloads.html), and [mkcert](https://mkcert.dev) if you haven't already. Then:
```sh
git clone https://github.com/Bdeering1/moodle-deploy.git
cd moodle-deploy
./vm-start # this will spin-up a clean VM, copy the install script, and SSH into it

./moodle-install # inside the VM
```
Once the install has completed, open a new terminal window and run:
```sh
./trust-certs
```
This will add the SSL certificate created by the install script to your computer's trust store, allowing HTTPS to work.


