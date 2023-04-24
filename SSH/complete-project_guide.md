# `SSH PEER LEARNING`
---
         				I post helpful resources and guides on my Github 
					kindly follow me to stay up to date with my work
					
--


# `STEP 1.` HOW TO GENERATE YOUR SSH KEY

Get your sandbox (UBUNTU 20.04)

```

cd /root

ssh-keygen -t rsa -b 4096 -f ~/.ssh/school


Your PASSPHRASE shoud BE: betty


ls -a

cd .ssh

vi  school.pub

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
```

# `STEP 2.` HOW TO LOGIN TO YOUR SERVER

```
cd /root`

cd .ssh`

eval $('ssh-agent')

ssh-add ~/.ssh/school

PLEASE REPLACE THE IP ADDRESS BELOW WITH YOUR OWN IP ADDRESS

ssh ubuntu@54.208.69.207

```
NOTE:
IF YOUR SERVER SAYS "PERMISSION DENIED",PLEASE DON'T FORCE THINGS
<br>THERE'S PROBABLY SOMETHING  WRONG WITH THE PUBLIC KEY YOU PASTED ON YOUR INTRANET PROFILE</br>

<br>I WILL ADVICE YOU TO BE MORE CAREFULL,BUT DELETE THE .SSH DIRECTORY AND START ALL OVER AGAIN FROM STEP 1.</br>

<br>OR YOU WILL JUST BE GOING IN AN ENDLES CIRCLE OF "PERMISSION DENIED"</br>

<br>THE COMMAND BELLOW IS FOR THOSE WHOSE SERVER IS SAYING "PERMISSION DENIED"</br>


`rm -r .ssh`

BUT IF YOU HAVE SUCCESSFULLY CONNECTED TO YOUR SERVER, THEN CONTINUE THE FOLLOWING COMMANDS: 

```
ls -a

cd .ssh

ls -a

sudo vim authorised_keys

Add the RSA public key from your project TASK 3 to your authorized_keys file

Save and exit

THEN CHECK YOUR CODE FOR TASK 3

```


# `STEP 3.` OPEN ANOTHER SANDBOX

```
cd  alx-system_engineering-devops

mkdir 0x0B-SSH

cd 0x0B-SSH

Create a README.md file with some content in it

```
# `TASK 0.` [](https://github.com/besthor/alx-system_engineering-devops/blob/master/0x0B-ssh/0-use_a_private_key)

## `vi 0-use_a_private_key`

```
#!/usr/bin/env bash
# A Bash script that uses ssh to connect to your server

ssh -i ~/.ssh/school ubuntu@54.209.217.190
```

Make it execute chmod u+x 0-use_a_private_key

# `TASK 1` [](https://github.com/besthor/alx-system_engineering-devops/blob/master/0x0B-ssh/1-create_ssh_key_pair)

## `vi 1-create_ssh_key_pair`

```
#!/usr/bin/env bash
# A script that Generates an RSA key pair with 4096 bits and passphrase "betty"

ssh-keygen -t rsa -b 4096 -P betty -f school
```

Make it execute chmod u+x 1-create_ssh_key_pair

# `TASK 2.`

## `vi 2-ssh_config` [](https://github.com/besthor/alx-system_engineering-devops/blob/master/0x0B-ssh/2-ssh_config)

```
#!/usr/bin/env bash
# Configure ssh client to use public key authentication and other settings

Host *
 	SendEnv LANG LC_*
	HashKnownHosts yes
	GSSAPIAuthentication yes
	GSSAPIDelegateCredentials no
	IdentityFile ~/.ssh/school
	PasswordAuthentication no
```
Make it executable chmod u+x 2-ssh_config

# `TASK 3.`

```
eval $('ssh-agent')

ssh-add ~/.ssh/school

PLEASE REPLACE THE IP ADDRESS BELOW WITH YOUR OWN IP ADDRESS

ssh ubuntu@54.208.69.207

ls -a

cd .ssh

ls -a

sudo vim authorised_keys

Add the RSA public key from your project TASK 3 to your authorized_keys file

Save and exit

```
THEN CHECK YOUR CODE FOR TASK 3

# `TASK 4.` [](https://github.com/besthor/alx-system_engineering-devops/blob/master/0x0B-ssh/100-puppet_ssh_config.pp)
## `vi 100-puppet_ssh_config.pp`

```
#!/usr/bin/env bash
# Puppet manifest to configure ssh client with public key authentication

file_line { 'Turn off password authentication':
	ensure => 'present',
	path   => '/etc/ssh/ssh_config',
	line   => 'PasswordAuthentication no',
}

file_line { 'Declare identity file':
	ensure => 'present',
	path   => '/etc/ssh/ssh_config',
	line   => 'IdentityFile ~/.ssh/school',
}

```
Make it executable chmod u+x 100-puppet_ssh_config.pp


# `CONGRATULATIONS ON SUCCESSFULLY COMPLETING THE SSH PROJECT!!`
