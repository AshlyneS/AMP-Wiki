Prerequisites
---

To develop AMP plugins, you must meet the following prerequisites:

* You must own AMP Professional, Network or Enterprise licence.
* Windows 8.1 64-bit OS or newer (The SDK is not available for Linux at this time)
* Visual Studio 2017/2019 (The [free community edition](https://www.visualstudio.com/en-us/downloads/download-visual-studio-vs.aspx) is supported) - 2015 and older is not supported as AMP uses C# 7 features.
* Experience with both C# and Javascript

Obtaining a developer licence
---

You can obtain a developer licence by selecting the 'Request developer licence' button from the [CubeCoders Licence Manager](https://manage.cubecoders.com/).

![Developer Licence Request](https://github.com/CubeCoders/AMP/blob/master/WikiContent/DevLic.png)

About AMP Developer Licences
---

Developer licences allow AMP to run unsigned plugins and modules during development. Ordinarily AMP will only load plugins signed by CubeCoders to prevent users from running unauthorized or potentially harmful code inside their AMP instances.

A single developer licence can be added to to up to 5 simultaneous AMP instances, we monitor their usage to ensure they are not being abused (they cannot be given out or made available to others) - If you need to use your developer licence on more instances (for example to use a private plugin on a network of servers) then please contact us to request the limit to be raised.

Adding a developer licence to an installation
---

You must have a licenced AMP Pro, Network or Enterprise edition instance to add a developer licence. You add the licence manually by running the following command line in the datastore directory for the instance:

    ampinstmgr reactivate INSTANCENAME DEVELOPERKEY

Replacing `INSTANCENAME` with the name of the instance you want to add the developer licence too, and `DEVELOPERKEY` with your developer key obtained earlier.

The AMP instance will run through briefly to request the licence. On subsequent starts you will see AMP starting up with two licences in place, your original licence and the developer licence. It will now allow you to run your own unsigned plugins.

Installing the SDK and templates
---

The SDK is installed via the Extensions gallery in Visual Studio. You can find it by going to Tools -> Extensions and Updates. In newer versions of Visual Studio, you find it under Extensions > Manage Extensions. In the tree menu on the left, select Online > Visual Studio Gallery and search for 'CubeCoders' and install the extension. You may need to restart Visual Studio after installing the extension.

![The extension in the Visual Studio Gallery](https://github.com/CubeCoders/AMP/blob/master/WikiContent/SDK.png)

Creating the project
---

After restarting Visual Studio, you will now have a new 'AMP Plugin' project type available under Visual C# Templates:

![AMP Plugin Template](https://github.com/CubeCoders/AMP/blob/master/WikiContent/NewProject.png)

**Make sure the Project name does not contain any spaces, and ends with the word Plugin**

Once you've created the project, you'll need to make a number of changes before the template will be usable.

* Remove the reference to ModuleShared in the project references and re-add it using the dll from your AMP instance set up with a developer licence.
* In the project Build Events, remove the "REM" before the two xcopy lines and adjust the path that xcopy targets to the directory of your AMP installation.
* In 'Debug', pick the option to start an external program and select the AMP executable for your target AMP instances. **Make sure you also set the working directory to be the same as that AMP instance**
* Set the Command Line Arguments to `+Core.AMP.LoadPlugins YOURPLUGINNAME` replacing your plugin name to be the same as the plugin primary namespace.

During debugging, Visual Studio will start your AMP instance and load your development build plugin. You will be able to setup breakpoints and debug your plugin exactly as if it were a normal application, running inside a release build of AMP doesn't restrict any debugging features.

Writing your plugin
---

The included template files contain a large number of comments explaining what they do and how they work. Take a read through and explore all of the different files in the solution. If you have any development questions, get in touch via the support board at [https://support.cubecoders.com/](https://support.cubecoders.com/)

Sample Module
---

You can download the complete source for a sample module (in this case the module for Rust) from [GitHub](https://github.com/CubeCoders/SampleAMPModule).

SDK Tools
---

The primary tool is a utility called APIGEN. It connects to a target AMP installation and generates C# files matching that instances API so that any API calls exposed by your plugin can be consumed by other applications. This also allows you to write other applications that interact with AMP via its SDK without an AMP plugin.
