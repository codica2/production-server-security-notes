 <h1 align="center"> Production server security notes </h>

![Secure](secure.jpg?raw=true )

###  Server security is an important part of production. We propose 7 tips to provide security your servers
___
**1. Use strong passwords:**
A good password is:

* Private: it is used and known by one person only;

* Secret: it does not appear in clear text in any file or program or on a piece of paper pinned to the monitor;

* Easily remembered: so there is no need to write it down;
at least 8 characters long;

* A mixture of at least 3 of the following: upper case letters, lower case letters, digits and symbols;

* Not listed in a dictionary of any major language;

* Not guessable by any program in a reasonable time, for instance less than one week.
*   Password examples: 
 
  ### <span style="color:red">Bad password:</span>  **qwerty123**  
  ### <span style="color:green">Good password:</span> **u6]T:PX.OT8!VEB;**
  Good password can be generate by online [generator](https://passwordsgenerator.net/)


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
   More details follow link

**6. For security your web-site - use ssl certificates:**
    
   For example you can use free certificate provider - [letsencrypt](https://letsencrypt.org/)

**7. Use utility fail2ban**

[Fail2ban](http://www.fail2ban.org/wiki/index.php/Main_Page) scans log files (e.g. /var/log/apache/error_log) and bans IPs that show the malicious signs -- too many password failures, seeking for exploits, etc. Generally Fail2Ban is then used to update firewall rules to reject the IP addresses for a specified amount of time, although any arbitrary other action (e.g. sending an email) could also be configured. Out of the box Fail2Ban comes with filters for various services (apache, courier, ssh, etc).
___
## License
Copyright © 2015-2019 Codica. It is released under the [MIT License](https://opensource.org/licenses/MIT).

## About Codica

[![Codica logo](https://www.codica.com/assets/images/logo/logo.svg)](https://www.codica.com)

The names and logos for Codica are trademarks of Codica.

We love open source software! See [our other projects](https://github.com/codica2) or [hire us](https://www.codica.com/) to design, develop, and grow your product.

