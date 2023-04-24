# `SSH PEER LEARNING`
---
         				I post helpful resources and guides on my Github 
					kindly follow me to stay up to date with my work
					
--


# `STEP 1.` HOW TO GENERATE YOUR SSH KEY

Get your sandbox (UBUNTU 20.04)


`cd /root`

`ssh-keygen -t rsa -b 4096 -f ~/.ssh/school`

[](https://github.com/besthor/difficult-system_engineering_projects_guides/blob/main/SSH/complete-project_guide.md)
Your PASSPHRASE shoud BE: betty


`ls -a`

`cd .ssh`

`vi school.pub`

Copy the RSA and save on your `INTRANET PROFILE`

Click `Save your information`

Then, go back to the project and scroll down

Just before TASK 0, 

Request for a new server

Make sure your server's state is `RUNNING`
HERE IS AN EXAMPLE
---
Name		Username	IP		State	
---
160670-web-01	ubuntu		54.208.69.207	running
---

# `STEP 2.` HOW TO LOGIN TO YOUR SERVER

`cd /root`

`cd .ssh`

`eval $('ssh-agent')`

`ssh-add ~/.ssh/school`

PLEASE REPLACE THE IP ADDRESS BELOW WITH YOUR OWN IP ADDRESS

`ssh ubuntu@54.208.69.207`

NOTE:
IF YOUR SERVER SAYS "PERMISSION DENIED",PLEASE DON'T FORCE THINGS
<br>THERE'S PROBABLY SOMETHING  WRONG WITH THE PUBLIC KEY YOU PASTED ON YOUR INTRANET PROFILE</br>

<br>I WILL ADVICE YOU TO BE MORE CAREFULL,BUT DELETE THE .SSH DIRECTORY AND START ALL OVER AGAIN FROM STEP 1.</br>

<br>OR YOU WILL JUST BE GOING IN AN ENDLES CIRCLE OF "PERMISSION DENIED"</br>

<br>THE COMMAND BELLOW IS FOR THOSE WHOSE SERVER IS SAYING "PERMISSION DENIED"</br>


`rm -r .ssh`

BUT IF YOU HAVE SUCCESSFULLY CONNECTED TO YOUR SERVER, THEN CONTINUE THE FOLLOWING COMMANDS: 

`ls -a`

`cd .ssh`

`ls -a`

`sudo vim authorised_keys`

Add the RSA public key from your project TASK 3 to your authorized_keys file

`Save and exit`

THEN CHECK YOUR CODE FOR TASK 3



# `STEP 3.` OPEN ANOTHER SANDBOX

`cd  alx-system_engineering-devops`

`mkdir 0x0B-SSH`

`cd 0x0B-SSH`

Create a README.md file with some content in it

# `TASK 0.` 

`vi 0-use_a_private_key`

#!/usr/bin/env bash
<br># A Bash script that uses ssh to connect to your server</br>

<br>ssh -i ~/.ssh/school ubuntu@54.208.69.207</br>

Make it executable chmod u+x 0-use_a_private_key

# `Task 1:`
`vi 1-create_ssh_key_pair`

#!/usr/bin/env bash
<br># A script that Generates an RSA key pair with 4096 bits and passphrase "betty"</br>

<br>ssh-keygen -t rsa -b 4096 -P betty -f school</br>

Make it execute chmod u+x 1-create_ssh_key_pair

# `TASK 2.`

`vi 2-ssh_config`

#!/usr/bin/env bash
<br># Configure ssh client to use public key authentication and other settings</br>

Host *
    <br>SendEnv LANG LC_*</br>
    <br>HashKnownHosts yes</br>
    <br>GSSAPIAuthentication yes</br>
    <br>GSSAPIDelegateCredentials no</br>
    <br>IdentityFile ~/.ssh/school</br>
    <br>PasswordAuthentication no</br>

Make it executable chmod u+x 2-ssh_config
# `TASK 3.`

`eval $('ssh-agent')`

`ssh-add ~/.ssh/school`

PLEASE REPLACE THE IP ADDRESS BELOW WITH YOUR OWN IP ADDRESS

`ssh ubuntu@54.208.69.207`

`ls -a`

`cd .ssh`

`ls -a`

`sudo vim authorised_keys`

Add the RSA public key from your project TASK 3 to your authorized_keys file

Save and exit

THEN CHECK YOUR CODE FOR TASK 3

# `TASK 4.` 
`vi 100-puppet_ssh_config.pp`

#!/usr/bin/env bash
<br># Puppet manifest to configure ssh client with public key authentication</br>

file_line { 'Turn off password authentication':
  <br> ensure => 'present',</br>
  <br>path   => '/etc/ssh/ssh_config',</br>
  <br>line   => 'PasswordAuthentication no',</br>
}

file_line { 'Declare identity file':
 <br> ensure => 'present',</br>
 <br> path   => '/etc/ssh/ssh_config',</br>
 <br>line   => 'IdentityFile ~/.ssh/school',</br>
}


Make it executable chmod u+x 100-puppet_ssh_config.pp




# `CONGRATULATIONS ON SUCCESSFULLY COMPLETING THE SSH PROJECT!!`
