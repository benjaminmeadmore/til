# Ports 

Lots of various services have their own port numbers. We use these out of convention. HTTP listens on 80. HTTPS on port 443. SSH on port 22. Etc..

But what is a port? A port is a place where ships typically dock when reaching a new country. A computer by in practice has ports 0 to 65,000 and by default these are all closed. Each service generally has a daemon setup which opens its relevant port as standard so it can listen on that port. 

## Local Network Vs. the Greater Internet 

Generally, you have your local host network. Running an SSH server on any local network is secure provided it's not exposed to the public internet. Once this is exposed to the greater public internet, if you had an SSH server running someone would be able to see that a port is open, and from there attempt to probe it to gain access. 

## Security 

Why would you want to expose your home ssh-server to the public internet? Imagine you went on holiday with your laptop, you would be able to tunnel back into your home network, access files, run commands, etc... 

However, it's very important to take security seriously if you chose to do this.