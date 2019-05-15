 <h1 align="center"> Production server security notes </h>

![Secure](secure.jpg?raw=true )

###  Server security is an important part of the production. Here we provide 7 tips to secure your servers
___
**1. Use strong passwords.**
A comprehensive password is:

* Private: it is used and known by one person only;

* Secret: it does not appear in any text, file, program, or atop a sheet of paper pinned to the monitor;

* Easy-to-remember: so there is no need to write it down;
at least 8 characters long;

* A mixture of at least 3 of the following: upper case letters, lower case letters, digits and symbols;

* Not listed in a dictionary of any international language;

* Not quickly identifiable by any program (i.e. less than one week).

 **Password examples:**  
 
  ## <span style="color:red">Bad password:</span>  **qwerty123**  
  ## <span style="color:green">Good password:</span> **u6]T:PX.OT8!VEB;**
  You can generate a comprehensive password using [generator](https://passwordsgenerator.net/)


**2. Connect to server via SSH key and disable authorization via password:** 

If you want to generate the key on your device, just run: `ssh-keygen -t rsa -b 4096 -C "your_email@example.com"`
   Copy your key on server and run: `ssh-copy-id -i ~/.ssh/id_rsa user@yourhost`

**3. Disable SSH root login:**
   
   In order to disable root login, you need to uncomment `#PermitRootLogin no` in 
   file `/etc/ssh/sshd_config. After, you need to restart SSH server and run `systemctl restart sshd.service`

**4. Change default port for SSH:**
    
   In file `/etc/ssh/sshd_config` change the string `Port 22` to `Port 1001`. 
   Then restart SSH server via `systemctl restart sshd.service`. Now you can connect to the server using `1001` port

**5. Regularly install security updates**

   Run command `apt unattended-upgrade` on the server.
 Check the following [link](https://help.ubuntu.com/community/AutomaticSecurityUpdates) for more details.

**6. Use SSL certificates to secure your website:**
    
   For example, you can use [letsencrypt](https://letsencrypt.org/) - free certificate provider. 

**7. Use fail2ban utility**

[Fail2ban](http://www.fail2ban.org/wiki/index.php/Main_Page) scans log files (e.g. `/var/log/apache/error_log`) and bans IPs that show any malicious signs: too many password failures, seeking for exploits, etc. 

Generally Fail2Ban is used to update firewall rules to reject the IP addresses for a specified amount of time. Although any other arbitrary action (e.g. sending an email) could also be configured. Fail2Ban comes with filters for various services (apache, courier, ssh, etc) out of the box.
___
## License
Copyright © 2015-2019 Codica. It is released under the [MIT License](https://opensource.org/licenses/MIT).

## About Codica

[![Codica logo](https://www.codica.com/assets/images/logo/logo.svg)](https://www.codica.com)

The names and logos for Codica are trademarks of Codica.

We love open source software! See [our other projects](https://github.com/codica2) or [hire us](https://www.codica.com/) to design, develop, and grow your product.
