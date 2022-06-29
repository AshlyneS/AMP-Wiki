### _This page was contributed by a member of the AMP community_

This is a guide on how to make AMP work with IIS

**THIS CONFIGURATION IS CONFIGURED FOR SUBDOMAIN NOT SUBDIRECTORY**

Form the IIS side you need the following requirements

[URL Rewrite](https://www.iis.net/downloads/microsoft/url-rewrite)

[Application Request Routing](https://www.iis.net/downloads/microsoft/application-request-routing)

Also, you need a certificate form Lets Encrypt because we are configuring the website to be accessed from HTTP to HTTPS I will provide a guide little bit down how to use [Certify the Web software](https://certifytheweb.com/) which is freemium software.

First off create a new website in the IIS Console, and create an empty directory for the website, **DO NOT USE ANY AMP DIRECTORY FOR THE WEBSITE**
after that paste in the following configuration in the website directory being in the following file format _web.config_

```XML
<?xml version="1.0" encoding="UTF-8"?>
<configuration>
    <system.webServer>
        <rewrite>
            <rules>
                <rule name="ReverseProxyInboundRule1" stopProcessing="true">
                    <match url="(.*)" />
                    <action type="Rewrite" url="http://localhost:8080/{R:1}" />
                    <serverVariables>
                        <set name="HTTP_X_ORIGINAL_ACCEPT_ENCODING" value="{HTTP_ACCEPT_ENCODING}" />
                        <set name="HTTP_ACCEPT_ENCODING" value="" />
                    </serverVariables>
                </rule>
            </rules>
        </rewrite>
    </system.webServer>
</configuration>
```
If necessary, change the ADS link which in our case is  `localhost:8080` also change `amp.example.com` to the public domain you want to access the ADS Instance.

For in depth explanation what this configuration file does, I am going to provide you with the link from the [main source](https://techcommunity.microsoft.com/t5/iis-support-blog/setup-iis-with-url-rewrite-as-a-reverse-proxy-for-real-world/ba-p/846222)

Setting up ASD Instance, there are few settings you need to change in the `AMPConfig.conf`
change from `Webserver.UsingReverseProxy=False` to `Webserver.UsingReverseProxy=True` which enables AMP to be able to work on Reverse Proxy without issues and last but definitely not least `Webserver.ReverseProxyHost=127.0.0.1` to `Webserver.ReverseProxyHost=amp.example.com` (`amp.example.com` is your domain)

Now How to provide SSL Certificate for my website, so I can properly use my IIS URL Rewrite without any issues

We are going to use [Certify the Web software](https://certifytheweb.com/)
First go to the website and install it, after the installation is done open the software and Click on New Certificate

![Certify New Certificate](https://i.imgur.com/4zsl8GM.png)

Change the Name of the new certificate for example AMP
And select your IIS Website, which should automatically pick up your domain (also it will configure your IIS for HTTPS)

![Input Certificate](https://i.imgur.com/pugL7cU.png)

Click on Request Certificate and you are done.