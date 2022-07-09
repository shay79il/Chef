# Chef Workstation

## 1. Create EC2 on AWS and make a sftp connection by the following command

```bash
sshfs ubuntu@34.207.124.248:/home/ubuntu ~/remote-chef -o reconnect -o IdentityFile="$AWS_SSH" -o allow_other
```

## 2. [Chef Workstation](https://www.chef.io/downloads/tools/workstation)

>     To see which version to install by the next step ...

## 3. [Install Chef workstation](https://docs.chef.io/workstation/install_workstation/)

## 4. [Setup the workstation](https://docs.chef.io/workstation/getting_started/)

>     Over the EC2 do the following (until 'which ruby' command)

## 5. Go to '.chef' directory

```bash
# where we downloaded the 'Starter Kit' and run the following
knife ssl fetch
knife ssl check
knife node list
```

## 6. Go to the '/chef-repo/cookbooks' directory

>      There we have the starter dir and upload the starter dir

```bash
knife cookbook upload <cookbook-name>
```

## 7. Run the following

```bash
# list what we have just uploaded
knife cookbook list
```

## 8. Copy the 'ssh.pem' to AWS

>     Copy the 'ssh.pem' to the 'workstation' instance in order to run the 'bootstrap' command go to the '/chef-repo/.chef' dir and run the following

```bash
# The bootstrap command is in order to install chef client on the client/node instance
knife bootstrap 172.31.83.178 -N client.example.com --ssh-user ubuntu --sudo --identity-file "$AWS_SSH"
```
