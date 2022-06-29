This guide assumes that AMP is being deployed for Enterprise Usage in a dedicated server environment with a direct internet connection with no NAT. We are not offering support for servers behind NAT'ed connections at this time.

If you're using AMP Network Edition, skip to [Activating ADS](#activating-ads).

# Supported Platforms

As part of the trial, only two platforms are supported at this time:

 * Debian 8+
 * Ubuntu 18.04+

This will expand as the trial progresses to include other Linux distributions and OSs. 

**Using the latest available (Debian 10/Ubuntu 20.04) is highly recommended**

# Prerequisites

When running in Enterprise Mode, the following requirements apply:

 * AMP must be [served over HTTPS](Setting-up-secure-HTTP-with-AMP), either using a reverse proxy (recommended, supports LetsEncrypt) or with the internal implementation (PFX certificate required)
 * On Linux systems, [hidepid](Configuring-'hidepid'-for-Linux-systems) must be configured. Without it AMP will not create instances.

Additionally the following changes are recommended:

<!-- * Using 'Docker' mode is recommended. Optionally using Traefik mode allows each instance to be accessible from their own subdomain (instancename.mydomain.com) -->
 * New instances should be bound to a specific IP address rather than the default of 127.0.0.1 if you want to allow users to access their instances directly instead of logging in via ADS.
 * Your auth server URL should be a fully-qualified URL as HTTPS is mandatory for the auth server URL in Enterprise mode.

# Activating ADS

By default ADS can't be activated, and won't accept a key. To enable AMPs Enterprise or Network Edition features you need to set it up to allow activation, then activate it with your key. This will cause ADS to consume an activation same as an application instance.

Run the following commands (Applies on any platform):

```bash
ampinstmgr reconfigure ADS01 +Core.AMP.RequireActivation True
ampinstmgr reactivate ADS01 *yourlicencekeygoeshere*
```

This will need doing on all of your controllers and targets.

# Configuration Changes

## On each target/standalone server:

 * Configuration / Networking / Use Host Networking for Containers - It is recommended that this is disabled if you're using Docker as customers would be able to start listening on unauthorised ports. When using the default networking mode AMP will only allow through those ports which are specifically assigned to that instance.
 * Configuration / New Instance Defaults / Default Settings - It is recommended you add the following key/value pairs:

|Key|Value|Comment|
|-|-|-|
|Core.Privacy.AllowAnalytics|False|Disables analytics, important for GDPR compliance|
|Core.Security.RequireSessionIPStickiness|False|Users in campuses or using certain ISPs may have IP addresses that change frequently which will continually end their session unless this is set to False|
|Core.Branding.DisplayBranding|True||
|Core.Branding.CompanyName|Your company name here||
|--- Other branding settings here ---||See AMPConfig.conf for the rest of the settings|
|Core.Monitoring.UseMulticoreCPUCalc|False|AMPs default CPU usage calculation may be confusing to inexperienced users|
|FileManagerPlugin.SFTP.SFTPEnabled|True|Allows users to connect via SFTP using their panel username/password to a locked down SFTP server that only lets them access their instances files|

# Creating a template 'customer' role.

You'll want to create a locked down role that applies to all of your customers regardless of what instance they have access to. To do this follow these steps:

 * Create at least one of each instance type that you intend to sell from your controller, it doesn't matter where they're made and these can be deleted later if you don't need them around. These instances won't be required to actually run the application, just to get AMP running.
 * Then in ADS, go to Configuration / Role Management and select "Create Template Role" with a name of your choice (such as Customer)
 * Edit this roles permissions within ADS and make sure it has no permissions (all permissions greyed out)
 * For each of the instance types you're going to sell:
 * * Manage the instance
 * * Go to Configuration / Role Management Find the "Customer" role you created earlier
 * * Assign only those specific permissions you wish to allow customers using this instance type to have. Be careful not to allow the use of settings that affect networking behaviour such as IP/port numbers or could allow setting extra command line flags that affect things like resource allocation.

# Creating deployment templates

Deployment templates are used to dictate what AMP can deploy, and these are what are exposed to billing integrations as available products.

![Templates](https://github.com/CubeCoders/AMP/blob/master/WikiContent/Templates.png)

First select 'Create Template' and name it depending on what product/service you wish to offer. This name should be unique and not shared with other templates.

The module type needs to be the name of the module that will be loaded for the deployed instance. These names are CaSe SeNsItIvE - you can see the module name for a given existing instance by selecting it and looking at the "Module" field on the right hand side.

The Template Role should be the role that any users created automatically for the created instance will be assigned to, so you should select the "Customer" role.

Provisioning Flags allow you to apply settings that will apply to this instance by default when it's created. The key takes the format of: `FullModuleName.Section.Field` - These node names exactly match those used by the .kvp files for the individual instances.

For example, for a Minecraft module based instance, there is a file called **MinecraftModule**.kvp, and it contains a line that reads **Java.MaxHeapSizeMB**=1024

So the final node name is MinecraftModule.Java.MaxHeapSizeMB with a value of whatever you'd like (for example 4096 to create a template for a 4GB Minecraft Server).

You should create a test instance for each type you intend to offer to customers and use that to pull the settings from the applicable configuration files to feed into the template.

Once you've modified your template select "Apply Changes".

Installing the AMP WHMCS module
-

1. Upload package content in your MAIN WHMCS DIRECTORY.

2. Login to WHMCS Admin Area and go to Setup->Product/Services->Servers:
- Add New Server with AMP module, hostname, username and password,
- Test Connection and Save Changes,
- Create New Server Group and add created server. Save Changes

3. Go to Setup->Product/Services->Product/Services:
- Create New Product Group ( or use existing one ),
- Create New Product [ Other type ], select product group, name and AMP module, Continue
- In Module Settings tab select created Server Group and module will list available templates. Select One and Save changes

4. In AMP Control Panel -> Configuration -> ADS remember to set Template deployment callback URL as:
"https://WHMCS_URL/index.php?ampCallback=1", eg. "https://example.com/index.php?ampCallback=1"

5. Module is ready to use. After activation of ordered product, module will wait for callback - then Application URL will be show in client area.
