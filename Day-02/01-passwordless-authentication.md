# How to setup Passwordless Authentication

## EC2 Instances

### Using Public Key
Make sure the public key is already generated and located in your ~/.ssh directory (typically named id_rsa.pub). If you haven’t created a key pair yet, you can do so with:

ssh-keygen -t rsa -b 4096
```
ssh-copy-id -f -o "IdentityFile=/mnt/Mumbai.pem" ubuntu@<INSTANCE-PUBLIC-IP>
OR
ssh-copy-id -f "-o IdentityFile <PATH TO PEM FILE>" ubuntu@<INSTANCE-PUBLIC-IP>
```
ssh-copy-id -f -o "IdentityFile=/mnt/Mumbai.pem" ubuntu@13.233.115.168   #should not be fully in quote..just copy like this
- ssh-copy-id: This is the command used to copy your public key to a remote machine.
- -f: This flag forces the copying of keys, which can be useful if you have keys already set up and want to overwrite them.
- "-o IdentityFile <PATH TO PEM FILE>": This option specifies the identity file (private key) to use for the connection. The -o flag passes this option to the underlying ssh command.
- ubuntu@<INSTANCE-IP>: This is the username (ubuntu) and the IP address of the remote server you want to access.

### Using Password 

- Go to the file `/etc/ssh/sshd_config.d/60-cloudimg-settings.conf`
- Update `PasswordAuthentication yes`
- Restart SSH -> `sudo systemctl restart ssh`

