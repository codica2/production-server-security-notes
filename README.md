# Production server security notes

### Server security is an important part of production
### We propose some tips to provide security your servers

**1. Use strong passwords:**
   
**2. Connect to server via ssh - with ssh-key and disable authorization via password:** 

You can generate key on your device run ` ssh-keygen -t rsa -b 4096 -C "your_email@example.com"`
   Copy your key on server run `ssh-copy-id -i ~/.ssh/id_rsa user@yourhost`

**3. Disable SSH root login:**
   
   For disable root login you must uncomment `#PermitRootLogin no` in 
   file `/etc/ssh/sshd_config` then restart ssh server run `systemctl restart sshd.service`
**4. Change default port for ssh:**
    
   In file `/etc/ssh/sshd_config` change string `Port 22` to `Port 1001`. 
   Then restart ssh server `systemctl restart sshd.service`. Now you can connect to server using port `1001`

**5. Regular install security updates**

   Run command on server `apt unattended-upgrade`

**6. For security your web-site - use ssl certificates:**
    
   For example you can use free certificate provider - letsencrypt
7. Use utility fail2ban
