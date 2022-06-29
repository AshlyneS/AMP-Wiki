# Setting up AMP on Linode

## Introduction

For Linode users, we've provided a pre-made StackScript which allows you to quickly and easily set up new AMP installations without even having to touch the command line. Just fill in a few fields and go!

If you're a new user, consider using our [referral code](https://cubecoders.com/linode) (Code: 63176147ac4aab18cc7635e99c3c992f85f6de25 ) - You can combine this with voucher code `DOCS10` for $10 free credit.

## Locate the Stackscript

![Locate the StackScript](https://github.com/CubeCoders/AMP/blob/master/WikiContent/LinodeTutorial/FindStackscript.png)

* From the left, select "One-Click Apps"
* Under 'Create From:' select "Community StackScripts"
* Enter 'cubecoders' as the search term
* Select "cubecoders/amp" and scroll down to the next section.

## Configure AMP

![Configure AMP](https://github.com/CubeCoders/AMP/blob/master/WikiContent/LinodeTutorial/Configure.png)

* Enter your desired username and password that you will later use to log into AMP itself.
* Under 'Select an Image' you may pick any of the operating systems that we've enabled support for with the StackScript (If you're unsure or have no preference then select "Debian 10"). Then scroll down to the next section.

## Select region and plan

![Select region and plan](https://github.com/CubeCoders/AMP/blob/master/WikiContent/LinodeTutorial/SelectPlan.png)

* Under Region, select either the location closest to you, or the location closest to your users.
* Under Linode Plan, select a configuration and cost that meets your needs. For most game servers a standard Linode 4GB will suffice, however some larger servers such as ARK will require the next plan up. If you want to host multiple game servers on your node then you'll need to pick your specifications accordingly. Linode bill by the hour so you can selectively start/stop your server as and when you need it and effectively pay-as-you-go if you don't need 24/7 operation.
* Click 'Create' on the right hand side, displayed below the cost.

## Browse to your new AMP installation

![Networking](https://github.com/CubeCoders/AMP/blob/master/WikiContent/LinodeTutorial/NetworkTab.png)

After hitting Create you will be taken to your new instances dashboard. 

* Select the 'Networking' tab
* Find the 'Reverse DNS' field, where you will see your server name.
* Browse to the address shown in your browser (hint: You can select the text, right click it and select 'Go to ...'

![Go to server](https://github.com/CubeCoders/AMP/blob/master/WikiContent/LinodeTutorial/RightClickToGoTo.png)

You may find after browsing to this address that you see a "AMP is not currently running" page - this is normal and just means that AMP is still setting itself up in the background. Simply wait on this page, it will automatically refresh when everything is ready.

![AMP not yet running](https://github.com/CubeCoders/AMP/blob/master/WikiContent/LinodeTutorial/NotYetRunning.png)

## Login

![Login](https://github.com/CubeCoders/AMP/blob/master/WikiContent/LinodeTutorial/Login.png)

* Login using the details you originally chose during the configuration of your node.
* Follow the first-start wizard to configure your server as normal.