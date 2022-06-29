# About the Bounty Programme

The AMP Bounty programme is a way for independent developers to contribute to AMP and be financially rewarded for their work by taking advantage of AMPs open API and SDK to implement new modules and plugins for other users to use.

# Awards

We are currently offering up to $600 USD per bounty for newly implemented AMP Modules and Plugins. The exact amount depends on the size and scope of the work undertaken. This is based upon an assumption of a $25 USD/hour rate and approximately 24 work hours, based loosely on time taken previously by ourselves to implement new modules/features. Smaller features/modules of course have a lower pay out in line with the work requirements. The amounts may change in line with fluctuations of exchange rate or the base currency used for pay outs may be changed.

# Code Ownership

It is important to be aware that where CubeCoders pays out a bounty for a submitted module, plugin or other code change - it is necessary for us to take ownership of the copyright to the code as we will be using it in our commercial software. As such you will be required to sign a contract giving us the intellectual property rights to the submitted code in perpetuity and forfeit the right to re-use the same code elsewhere or in other projects. Submitters will remain publicly listed however as the codes original author.

# Personal Requirements

To qualify, you must personally meet the following requirements:

 * Be over 18 years of age, or the age otherwise required to enter into contracts if this is greater than 18 where you live.
 * Be based within one of the following locations: (this list will expand, please get in touch if you're interested but not in this list)
 * * United States
 * * United Kingdom
 * * Canada
 * * European Union
 * * Australia
 * * New Zealand
 * * Norway
 * * Switzerland
 * Be producing AMP modules/plugins on your own time using your own equipment such that you own the copyright to any code you produce. Doing it on an employers time using an employers equipment may result in them owning the copyright to your work if undertaken without special permission.
 * Have an active PayPal account to receive payments.

# Module Requirements

Submitted modules will undergo an internal review process before we accept them. The amount we offer may vary from the listed bounty amount depending on code quality, feature set and other specifics of the implementation. To potentially reach the maximum amount you'll need to meet all of the following requirements:

 * Submitted modules must run on all platforms that are supported by both AMP and the application server. So if it runs on both Windows and Linux, so must the module/feature.
 * Don't reinvent the wheel, never try and download/use steamcmd directly for example - use AMPs existing steamcmd plugin for handling this. Same applies to RCON implementations, use the built in features or stock plugins wherever possible, raising feature requests if necessary for new protocols.
 * Avoid too many 3rd party dependencies, try to stick to the libraries AMPs core already uses (NewtonsoftJson etc) - Do not use commercial 3rd party libraries at all except with explicit prior agreement with CubeCoders.
 * Settings should make use of the [ProvisionSetting] attributes on network settings to ensure everything properly integrates with AMPs network handling.
 * The code should generally be of a high quality using modern coding styles and standards as applicable.

# Finding and Claiming Bounties

You can find bounties by looking at the [Bounty-Eligible](https://github.com/CubeCoders/AMP/issues?q=is%3Aopen+is%3Aissue+label%3ABounty-Eligible) tag on our GitHub repositories Issues page. If you are interested in claiming the bounty, post a comment saying so and reach out to us. Multiple people may work on the same bounty, but the award is nominally on a first-come-first-serve basis all other factors being equal.

Once you have produced a first working prototype (it needn't be a finished product, simply prove that it's viable and basically working), create a private repository on GitHub and then contact us to arrange for a CubeCoders staff member to have access and review the work in progress for you to receive early feedback and identify any issues.

After the module has been completed, there will be a further review and verification process. You may well be asked to make further changes to fix any identified issues for example. After the code and feature set is judged to be of adequate quality by CubeCoders an IP Transfer agreement will be sent and a pay out made available via PayPal. PayPal will be the only available means of receiving funds, so you will need an active PayPal account to participate. Acceptance is entirely dependent on the subjective approval of CubeCoders and completing a bounty is not a guarantee of a pay out in of itself.