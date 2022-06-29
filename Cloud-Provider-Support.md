We've validated AMP on a number of cloud providers to see which features are available out-of-the box. All of the listed providers are able to run AMP, but certain features make the setup process easier.

### GetAMP Validated
Meeting this requirement means that without making any changes to the server, the GetAMP script could be run and completed successfully out of the box without running a single command before running GetAMP.

### Resolvable Name
Hosts that provide this facility include a usable domain name that points to the server/VPS. They may be a bit unsightly sometimes but they allow you to setup HTTPS without buying a domain.

### Name Discovery
Meeting this requirement means that the GetAMP script is able to work out what the server/VPSs domain name is without the user having to supply it, making it even more suitable for mass deployments.

Name discovery can be provided by configuring the reverse IP lookup for the servers primary external IP address, but for this chart we're just looking at the default out-of-the-box configuration.

### Friendly Names
This is met if the default resolvable/discoverable name for the server is 'friendly' in some way, for example by not being excessively long, containing the servers IP as the name, etc.

### One-click Deployment
Some hosts provide a way for us to share automated deployment scripts. This means you don't even need to touch SSH to set up AMP and you can have a server with it pre-installed and ready to go without doing any setup yourself.

---

Provider / Referral Link|GetAMP Validated|Resolvable Name|Name Discovery|Friendly Names|One-click Deployment
---|---|---|---|---|---
[DigitalOcean](https://m.do.co/c/4386f346ce72)<br/>Link includes $50 free credit|✅|❌|❌|❌|❌
[Hetzner](https://hetzner.com)|✅|✅|✅|❌|❌
[Linode](https://www.linode.com/?r=63176147ac4aab18cc7635e99c3c992f85f6de25)<br/>Use code APPSTORIES2019 for $20 free credit<br/>[Install Guide](https://github.com/CubeCoders/AMP/wiki/Installing-AMP-on-Linode)|✅|✅|✅|✅|✅
[OVH](https://ovh.com)|✅|✅|✅|❌|❌
[Scaleway](https://scaleway.com)|✅|✅|✅|❌|❌

### What about Provider X?

We will validate GetAMP for any provider upon request, we simply require a set of login details to a typical instance running a stock Debian 10 image, simply contact us via the email address on the cubecoders.com front page.
