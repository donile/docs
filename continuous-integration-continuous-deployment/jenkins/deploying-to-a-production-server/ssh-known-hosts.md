# Jenkins

## Deploying to a Production Server

### SSH known_hosts file

Before a Jenkins agent is able to establish a SSH connection to a production server, the server's fingerprint needs to present in the known_hosts file read by the SSH process attempting to connect to the production server.  This may be accomplished several different ways, but each methodology adds the production server's fingerprint to the known_hosts file read by the SSH process attempting to make the connection.

#### Methodology 1: Manually Establish SSH Connection from Jenkins Agent to Production Server

Login as `jenkins` user on the server that hosts Jenkins.

`> sudo su - jenkins`

Generate private and public key pair.  The command below creates a 4096 bit private and public key pair in the current directory with the filenames `jenkins_id_rsa` (private key) and `jenkins_id_rsa.pub` (public key).

`> ssh-keygen -b 4096 -f ./jenkins_id_rsa`

Add the SSH public key to production server using the `ssh-copy-id` CLI or copy the contents of the public key file (`./jenkins_id_rsa`) and paste them into the user's authorized key file on the production server (`/home/<user>/.ssh/authorized_keys`).

`> ssh-copy-id -i ./jenkins_id_rsa <user-on-production-server>@<production-server.com>`

On the server that hosts Jenkins, as user `jenkins`, establish an SSH connection to production server.

`> ssh -l <user-on-production-server> -i ./jenkins_id_rsa <production-server.com>`

Accept the production server's fingerprint (only required to make the first connection).

The production server's fingerprint is added to the user `jenkins`' `known_hosts` file after accepting it in the step above.

#### Methodology 2: Manually Add production server's fingerprint to known_hosts file

Copy the production server's SSH fingerprint.

On the production server, copy the contents of the file `/etc/ssh/ssh_host_rsa_key.pub`.  This is the production server's fingerprint.

Paste the production server's SSH fingerprint into the `jenkins` user known_hosts file.

`<jenkins-home-directory>/.ssh/known_hosts`

On a Linux distribution, the <jenkins-home-directory> is:
`/var/lib/jenkins`