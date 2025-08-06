# Moodle Deploy

A single-script solution for deploying a Moodle site on Debian, automating everything from the core installation to the server stack.

**Key Features**
- Spins up Moodle on Apache with a PostgreSQL database.
- Configure everything interactively.
- Includes HTTPS (incl. SSL certificate creation), a firewall and brute-force attack protection.
- Regular database backups, swapfiles.

**Server Stack**
- Moodle 5.0
- PostgreSQL 17
- Apache 2
- Debian 12
- Fail2Ban
- UFW
- Cron
