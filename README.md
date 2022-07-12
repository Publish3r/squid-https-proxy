# How to #
## Squid https Proxy ##

### Instructions
Use a Debian or Ubuntu box with root on a clean public IP and run:

    apt-get update
	apt-get -y install squid net-tools apache2-utils
	
Choose a strong Username and Password.	
	
	htpasswd -c /etc/squid/passwd username
	
Please write down Username and Password.

	systemctl restart squid
	systemctl enable squid
	nano /etc/squid/squid.conf

Copy the following text, paste it on top of squid.conf and save file.

```
#
forwarded_for off
request_header_access Allow allow all
request_header_access Authorization allow all
request_header_access WWW-Authenticate allow all
request_header_access Proxy-Authorization allow all
request_header_access Proxy-Authenticate allow all
request_header_access Cache-Control allow all
request_header_access Content-Encoding allow all
request_header_access Content-Length allow all
request_header_access Content-Type allow all
request_header_access Date allow all
request_header_access Expires allow all
request_header_access Host allow all
request_header_access If-Modified-Since allow all
request_header_access Last-Modified allow all
request_header_access Location allow all
request_header_access Pragma allow all
request_header_access Accept allow all
request_header_access Accept-Charset allow all
request_header_access Accept-Encoding allow all
request_header_access Accept-Language allow all
request_header_access Content-Language allow all
request_header_access Mime-Version allow all
request_header_access Retry-After allow all
request_header_access Title allow all
request_header_access Connection allow all
request_header_access Proxy-Connection allow all
request_header_access User-Agent allow all
request_header_access Cookie allow all
request_header_access All deny all
auth_param basic program /usr/lib/squid3/basic_ncsa_auth /etc/squid/passwd
acl ncsa_users proxy_auth REQUIRED
http_access allow ncsa_users
#
```

Restart your Squid Proxy.

    systemctl restart squid
	

### Usage
* Enter your Proxy IP and Port 3128 in your Browser Settings.	Enter your Username and Password when prompted.
[![](https://raw.githubusercontent.com/Publish3r/squid-https-proxy/main/static/browser.jpg)](https://raw.githubusercontent.com/Publish3r/test/main/static/browser.jpg)