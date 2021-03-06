
# Configure Firewall to Enable HTTP Service on CentOS 7

CentOS 7 runs [FirewallD](https://fedoraproject.org/wiki/FirewallD).  
It uses `firewall-cmd` to config firewall rules. 

#### Add HTTP Service with default port:80  

* Add Rule:  
  `sudo firewall-cmd --permanent --zone=public --add-service=http`  

* Reload:  
  `sudo firewall-cmd --reload`

* Check:  
  `sudo firewall-cmd --zone=public --query-service=http`

#### Add HTTP Service with customized port(ex: 8080)

Ports below `1024` can be opened only by `root`.  
To run our HTTP service / app(Ex: golang app) as a normal user, we need to use another port(ex: `8080`).

* Add Rule:  
  `sudo firewall-cmd --permanent --zone=public --add-port=8080/tcp`

* Reload:  
  `sudo firewall-cmd --reload`

* Check:  
  `firewall-cmd --zone=public --query-port=8080/tcp`

#### References:  
* <http://stackoverflow.com/questions/24729024/centos-7-open-firewall-port>