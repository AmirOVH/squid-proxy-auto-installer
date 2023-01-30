# Squid Proxy Auto Installer

This is a simple and easy to use Squid proxy Auto Installer for Ubuntu and Debian servers.

Supported OS:
* Ubuntu 14.04, 16.04, 18.04, 20.04, 22.04
* Debian 8, 9, 10
* CentOS 7, 8


## Installation

To install the Squid proxy, use the following commands

```
wget https://raw.githubusercontent.com/AmirOVH/squid-proxy-auto-installer/master/squid3-install.sh -O squid3-install.sh
bash squid3-install.sh
```

# Changing the default port
Squid proxy server runs on port 3128 by default.

To change it, run the command below and replace `<NEW_PORT>` with your desired port:

```
sed -i 's/^http_port.*$/http_port <NEW_PORT>/g' /etc/squid/squid.conf
```

After that restart Squid Proxy server by running the following command:

```
systemctl restart squid
```

# Creating a new user

To create a new user for the Squid proxy, use **one** of the following methods:

**Method 1:** Run the command below

```
squid-add-user
```

**Method 2:** Run the command below and replace `<USERNAME>` and `<PASSWORD>` with your desired user name and password:

```
/usr/bin/htpasswd -b -c /etc/squid/passwd <USERNAME> <PASSWORD>
```

# Updating password for an existing user

To update the password for an existing user, run the command below and replace `<USERNAME>` with your desired user name:

```
/usr/bin/htpasswd /etc/squid/passwd <USERNAME>
```

# Reloading Squid proxy

To reload the Squid proxy, run the following command:

```
systemctl reload squid
```

# Configure Multiple IP Addresses

NOTE: This section only applies if you have more than one IP on your server.

Before you can configure Squid to use multiple IP addresses, you need to:
Add the new IP to your server.
Ensure that you can connect to the server using the new IP.

Once the new IP has been added to your server, you can configure it to be used by Squid by running the following commands:

```
wget https://raw.githubusercontent.com/AmirOVH/squid-proxy-auto-installer/master/squid-conf-ip.sh
bash squid-conf-ip.sh
```

# Test Proxy Server with curl

To test Squid proxy, run the following command:

```
curl -U PROXY_USER:PROXY_PW -x PROXY_IP:PROXY_PORT http://ip.amir.ovh/
```

* Replace PROXY_USER and PROXY_PW with your actual proxy username and password.

* Replace PROXY_IP with the hostname or IP address of your proxy server.

* Replace PROXY_PORT with the port number of your proxy server (default is 3128).

# Uninstall Squid proxy

To uninstall Squid proxy, run the following command:

```
squid-uninstall
```

# Support

If you are looking for support, visit my website

https://www.amir.ovh/
