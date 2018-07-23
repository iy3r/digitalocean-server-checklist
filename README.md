# DigitalOcean Nodejs Checklist
Checklist for setting up Node.js on a new DigitalOcean ```Ubuntu 18.04``` droplet

- [ ] [Initial server setup](https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-18-04)
- [ ] [Install Nginx](https://www.digitalocean.com/community/tutorials/how-to-install-nginx-on-ubuntu-18-04)
- [ ] [Secure Nginx with Let's Encrypt](https://www.digitalocean.com/community/tutorials/how-to-secure-nginx-with-let-s-encrypt-on-ubuntu-18-04)
- [ ] [Install Node using NVM](https://www.digitalocean.com/community/tutorials/how-to-install-node-js-on-ubuntu-18-04)
- [ ] [Setup deployment using Git](https://www.youtube.com/watch?v=9qIK8ZC9BnU)
- [ ] [Install PM2 and setup Nginx as a reverse proxy server](https://www.digitalocean.com/community/tutorials/how-to-set-up-a-node-js-application-for-production-on-ubuntu-18-04)

### Sample post-receive hook for git-based deployment

In file ```/var/repo/example.com.git/hooks/post-receive```

```bash
#!/bin/sh
export PATH=/home/user/.nvm/versions/node/v8.11.3/bin:$PATH
WORK_TREE='/var/www/example.com'

# Checkout source code to work tree
git --work-tree=$WORK_TREE --git-dir=/var/repo/example.com.git checkout -f

# Run npm install if package.json has changed
git --work-tree=$WORK_TREE diff-tree -r --name-only --no-commit-id HEAD~1 HEAD | grep --quiet -w package.json && cd $WORK_TREE; npm install
```

### Setup vim for JS in ~/.vimrc
```
set tabstop=2
set shiftwidth=2
set expandtab
set smarttab
set autoindent
set smartindent
```
