# Jenkins

## Deploying to a Production Server

### SSH known_hosts file

Before a Jenkins agent is able to establish a SSH connection to a production server, the server's fingerprint needs to present in the known_hosts file read by the SSH process attempting to connect to the production server.  This may be accomplished several different ways, but each methodology adds the production server's fingerprint to the known_hosts file read by the SSH process attempting to make the connection.

#### Methodology 1: Manually Establish SSH Connection from Jenkins Agent to Production Server

Generate private and public key pair using `ssh-keygen`.

On the server that hosts Jenkins, as user `jenkins`, establish an SSH connection to production server.

Accept the production server's fingerprint (only required to make the first connection).

#### Methodology 2: Manually Add production server's fingerprint to known_hosts file

Copy the production server's SSH fingerprint.

Add the production server's SSH fingerprint to the `jenkins` user known_hosts file.

`<jenkins-home-directory>/.ssh/known_hosts`

On a Linux distribution, the directory is:
`/var/lib/jenkins/.ssh/known_hosts`