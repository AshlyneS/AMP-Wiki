### _This page was contributed by a member of the AMP community_
# Basic setup
These are my findings in getting arma 3 working with AMP on Windows 10
## 1 Make sure all dependencies are installed 
AMP does not automatically install all dependencies so without these you'll run into missing .dll errors.
1. DirectX End-User Runtime
https://www.microsoft.com/en-us/download/confirmation.aspx?id=35
2. C++ Redistributable Packages for Visual Studio 2013
https://www.microsoft.com/en-us/download/details.aspx?id=40784
## 2 configuration
After your arma server is functioning you need to edit the server config in the file manager.
You want to edit the "CONFIG_server.cfg" file in the arma folder.
By default the config tries to load a mission called "MyMission.Altis" you want to either change this to the real mission you want to play or remove the "class Mission1" codeblock to load the server into the mission voting screen.
```
// MISSIONS CYCLE
class Missions
{
	//class Mission1
	//{
	//	template="MyMission.Altis";
	//	difficulty="Regular"; // "Recruit", "Regular", "Veteran", "Mercenary"
	//};
};
```
## 3 Joining

To join your server you can ofcorse use both the arma launcher or the client to join your server directly on {server ip}:{port}
To can also use a steam link to link people to your server steam://connect/{IP}:{steamport} I found that steam port is normally your arma port +1 so for your first arma server it should be 2303

## 4 adding missions

find the PBO file in your local workshop folders then you can simply upload it to 233780\mpmissions

# Modding
Best way I found for getting mods working on your AMP arma 3 server
## 1 steam workshop downloads
In the manager for your arma instance go to Configuration -> Steam workshop
There you can add the ID's of the workshop items you want steam to download.
simple way of finding those ID's is in the link of the workshop item.
example:
https://steamcommunity.com/sharedfiles/filedetails/?id=620019431 -> 620019431

After you have added all the ID's you need to shut down the server and press update to download the workshop items.

## 2 Moving files / making links

After your mods have been downloaded they will be in the /233780/steamapps/workshop/content/107410/ folder.
bud arma expects each mod to be in the root arma server folder (/233780/) in a folder with the modname that start with a @ symbol.
Easy way to find these correct folder names is to go to your local arma 3 installation into the hidden folder "!Workshop".
There you should see links to all the mods you have installed locally under the correct folder name example: "@task_force_radio"
Once you know the correct folder name you can make these folder in the arma server directory (/233780/) and move the files.
Or if you have access to a Admin powershell on the server you can create symbollic links to the files example:
``` 
New-Item -ItemType SymbolicLink -Path "C:\AMPDatastore\Instances\Arma301\arma3\233780\@task_force_radio" -Target "C:\AMPDatastore\Instances\Arma301\arma3\233780\steamapps\workshop\content\107410\620019431"
```
in this example "C:\AMPDatastore\Instances\Arma301\" is the path to my AMP arma3 instance, change according to your AMP install location and arma instance name.

## 3 bikeys

By default AMP sets the arma config "verifySignatures" to 2, that means arma only allows clients to load the mods that have their bikeys in the keys folder. To avoid having to add these keys you can set verifySignatures to 0, bud this can cause confusion when players join with the wrong mods.
To add the keys just go through all your mods folders and copy the .bikey files the \233780\keys folder

## 4 Mods List

To make the server load your mods you need to add them in the Configuration -> Arma3 -> Mods List.
You want the add them with the same folder name you made in step 2, including the @ symbol.
Example: @task_force_radio