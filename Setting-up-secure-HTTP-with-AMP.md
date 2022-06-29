There are a number of methods that can be used to set up secure HTTP (HTTPS) within AMP depending on your use case.

**Note that with AMP Enterprise, use of HTTPS is mandatory.**

# Reverse proxy via nginx (Recommended, Linux only)

If you use the default `getamp.sh` setup script to install AMP, and you select the option to set up HTTPS when running that script, AMP installs and configures an nginx reverse proxy and Let's Encrypt certificate handled by certbot to provide secure HTTP for your AMP web panel.

If you need to do this after installing AMP, then you have a couple of options. Before using these options, ensure that ports 80 and 443 are allowed through any firewall and (if relevant) port forwarded from your router to the host that nginx and certbot are being installed on. Also, you need a domain or subdomain to use for your AMP web panel - such as `mydomain.com` or `amp.mydomain.com`. **Note that subdirectories of a domain (for example `mydomain.com/amp`) cannot be used for this purpose.**

Whatever method is used, it's highly desirable to let AMP set up the nginx reverse proxy for you. However, if your use case does not support that, see the [manual setup instructions](https://github.com/CubeCoders/AMP/wiki/Setting-up-secure-HTTP-with-AMP#manual-nginx-reverse-proxy-setup-advanced) below.

## Option 1

The simplest option for distributions that support using the `getamp.sh` script is simply to run the following as `root`:

```
bash <(wget -qO- getamp.sh) postSetupHTTPS
```
This will run the HTTPS setup part of the `getamp.sh` script, installing and configuring nginx and certbot and ensuring all dependencies are installed. It will secure the main AMP web panel (the ADS instance). The nginx configuration will be stored in `/etc/nginx/conf.d/`.

## Option 2

If the `getamp.sh` script is not supported for your distribution, or if you have a special use case (for example, you want AMP to configure HTTPS for an individual game instance), then you can use the following command as `root`:

```
ampinstmgr setupnginx YOUR_DOMAIN/SUBDOMAIN INSTANCE_PORT
```

In this command `INSTANCE_PORT` is the port which the relevant instance is bound to - usually 8080 for ADS (the main AMP web panel) and 8081, 8082, etc for individual game instances.

Before running this command ensure that the required dependencies are installed:

* for distros that use APT as the package manager, you need `nginx`, `certbot` and `python3-certbot-nginx`.
* for distros that use YUM as the package manager, you need `epel-release`, `nginx` and `python3-certbot-nginx`. You also need to manually install `certbot-auto` by running as root:

   ```
   wget -P /usr/local/bin https://dl.eff.org/certbot-auto
   chmod +x /usr/local/bin/certbot-auto
   ```
Again, the nginx configuration will be stored in `/etc/nginx/conf.d/`.

## Note for users that have a distro that uses SELinux: (CentOS, RHEL, Fedora, etc.)

In order for nginx to talk to local services (such as AMP), it must be in the **permissive** domain. To set it as such, run the following as root:
```
semanage permissive -a httpd_t
```
Additionally, you must allow nginx to relay and connect to AMP's port. You can do this by running as root:
```
setsebool -P httpd_can_network_relay 1
setsebool -P httpd_can_network_connect 1
```
For more information about nginx and SELinux, visit [Modifying SELinux Settings for Full NGINX Functionality](https://www.nginx.com/blog/using-nginx-plus-with-selinux/)

# Internal HTTPS implementation

AMP has built in support for HTTPS with its internal application server. AMP requires a certificate in PFX format with a passphrase. You can use `ampinstmgr convertcertificate` to convert a standard .cert + .key file pair into a PFX on Linux systems.

The main advantage is that no additional software is required, however it's not suitable for use with LetsEncrypt as AMP has to be restarted to swap out the certificate.

## Linux Manual Configuration
This method is optimal if you already have your certificate in use with another webserver already. 

Open **/home/amp/.ampdata/instances/ADS01/AMPConfig.conf** while ADS is stopped and edit the following lines:

```
Webserver.CertificatePath=/path/to/your/certificate.pfx
Webserver.CertificatePassword=y0urc0mplexpa5$word
```

## Windows

Install the certificate to your system into the local machine store, and then view the certificate to get its serial number. Once you've done this edit the following lines to your `AMPConfig.conf` file for ADS:

```
Webserver.CertificateSerial=CERTIFICATESERIALNUMBERGOESHERE
```

## Re-configuring existing instances

When using AMP’s built in HTTPS support, all existing instances **other than ADS01** will need their authentication server updated to your ADS installations new URL.

Your login section for AMPConfig.conf for each instance should look like this, make sure to change ads.somedomain.com to your chosen domain.
```
################################
# Login
################################
Login.UseAuthServer=True
# Login.AuthServerURL - The URL for the ADS instance providing authentication when using UseAuthServer
Login.AuthServerURL=https://ads.somedomain.com:8080/
Login.LDAPAllowAuthOnAnyDomain=False
Login.LDAPAuthDomain=
```

Where 8080 is the port that ADS is currently bound to. Also in ADS, under Configuration -> New Instance Defaults you need to update the Default Auth Server URL to be the new URL of your ADS installation.

# Manual nginx reverse proxy setup on Linux (advanced)

You may have a use case where you want to use an nginx reverse proxy but would prefer that AMP not set it up for you - for example, where you already have a certificate for your domain (such as a wildcard), or you prefer to use a tool other than certbot (such as `acme.sh`) to manage your certificates. In that case, you can configure things manually.

## nginx configuration

The following nginx virtual host configuration is based on what AMP and certbot would generate. It can be included as `/etc/nginx/conf.d/EXAMPLE.DOMAIN.COM.conf`, or alternatively (on Debian and Ubuntu hosts) in `/etc/nginx/sites-available` and symlinked to `/etc/nginx/sites-enabled`. Either way, ensure that the relevant directory has an `include` directive in `/etc/nginx/nginx.conf`.

```
server {
    listen 80;
    listen [::]:80;
    
    server_name EXAMPLE.DOMAIN.COM;

    if ($host = EXAMPLE.DOMAIN.COM) {
        return 301 https://$host$request_uri;
    }

    return 404;
}

server {
    listen 443 ssl http2;
    listen [::]:443 ssl http2;

    server_name EXAMPLE.DOMAIN.COM;

    # Replace the below as appropriate according to certificate locations and
    # whatever SSL settings you want. The below reflects a standard certbot
    # configuration
    ssl_certificate /etc/letsencrypt/live/EXAMPLE.DOMAIN.COM/fullchain.pem;
    ssl_certificate_key /etc/letsencrypt/live/EXAMPLE.DOMAIN.COM/privkey.pem;
    include /etc/letsencrypt/options-ssl-nginx.conf;
    ssl_dhparam /etc/letsencrypt/ssl-dhparams.pem;
    
    location / {
        proxy_pass http://localhost:8080;  # Or whatever local IP and port ADS is listening on
        proxy_set_header        Host $host;
        proxy_set_header        X-Real-IP $remote_addr;
        proxy_set_header        X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header        Upgrade $http_upgrade;
        proxy_set_header        Connection "Upgrade";
        proxy_set_header        X-AMP-Scheme $scheme;
        proxy_read_timeout      86400s;
        proxy_send_timeout      86400s;
        proxy_http_version      1.1;
        proxy_redirect          off;
        proxy_buffering         off;
        client_max_body_size    10240M;

        # The following nine lines will only work if nginx and AMP are on the same host
        error_page 502 /NotRunning.html;
        location = /NotRunning.html {
            root /opt/cubecoders/amp/shared/WebRoot;
            internal;
        }

        location /shared/ {
            alias /opt/cubecoders/amp/shared/WebRoot/;
        }
    }
}
```

## AMP configuration changes

The ADS must be stopped before making the following changes.

First (as the `amp` user):

```
ampinstmgr reconfigure ADS01 +Core.Webserver.UsingReverseProxy True
```

Then, if the Nginx reverse proxy is **not** on the same host as the ADS, set the right IP (eg `10.1.1.10`):

```
ampinstmgr reconfigure ADS01 +Core.Webserver.ReverseProxyHost INSERT_IP
```
