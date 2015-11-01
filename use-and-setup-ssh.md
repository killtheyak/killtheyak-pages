title: setup and use SSH
updated: 2015-10-10 11:11:12
description: This is the template page.
os: [macosx, linux]
tags: [ssh]
deps: []
contributors: ["http://www.github.com/daschwa"] 

# Genarating and sharing public key

How to create a new public key for ssh and add it to the remote machine.

generate key:
```
ssh-keygen -t rsa
```

Append it to the server: 
```
cat ~/.ssh/id_rsa.pub | ssh user@server "cat >> ~/.ssh/authorized_keys"
```

Copy a file to the remote machine:
```
scp ~/path/to/file user@server:/path/on/server
```

Copy a file from the remote machine:
```
scp user@server:/path/to/file ~/path/on/local
```

# SSH Config

Creating a `~/.ssh/config` file. Having aliases for SSH is a dream.
```
    Host somealias
        HostName example.com
        Port 2222
        User someuser
        IdentityFile  ~/.ssh/id_example
        IdentitiesOnly yes

    Host anotheralias
        HostName 192.168.33.10
        User anotheruser
        PubkeyAuthentication no

    How aws
        HostName some.address.ec2.aws.com
        User awsuser
        IdentityFile  ~/.ssh/aws_identity.pem
        IdentitiesOnly yes
```

Usage: `ssh somealias`
        
- HostName - The server host (domain or ipaddress)
- Port - The port to use when connecting
- User - The username to log in with
- IdentityFile - The SSH key identity to use to log in with, if using SSH key access
- IdentitiesOnly - "Yes" to specify only attempting to log in via SSH key
- PubkeyAuthentication - "No" to specify you wish to bypass attempting SSH key authentication
