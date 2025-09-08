# Moodle Deploy

A single-script solution for deploying a Moodle site on Debian, automating everything from the core installation to the server stack.

Also includes virtual machine configuration (Vagrant) for local development.

**Key Features**
- Spins up Moodle on Apache with a PostgreSQL database.
- Configure everything interactively.
- Includes HTTPS (incl. SSL certificate creation), IPv4/IPv6 dual-stack, firewall and IPS/IDS.
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

<details> 
  <summary>Copy `moodle-install` onto your server.</summary>
  
```sh
# From your local machine
git clone https://github.com/Bdeering1/moodle-deploy.git
cd moodle-deploy
scp moodle-install [your_user]@[your_server_ip]:~
```
</details>

Then run:
```sh
# From your server
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
./trust-certs # [site url here if it was changed from the default]
```
This will add the SSL certificate created by the install script to your computer's trust store, allowing HTTPS to work.

## Using the Interactive Installer

The list of configurable options are the following:
```
  --root-url           Set the root url for your site
  --site-name          Set the full name of your site
  --short-name         Set a short-form name for your site
  --admin-user         Set the admin username for your site
  --admin-pass         Set the admin password for your site
  --db-user            Set postgreSQL database user
  --db-pass            Set postgreSQL database password
  -h, --help           Display this help message
```
These options can be defined with command line flags and the user will be prompted to enter values for all unspecified options.

