# Visual Studio 2010, 2012 and 2013 IDE Plugins

## Overview

![images_community/download/attachments/47186029/icon.png](images_community/download/attachments/47186029/icon.png)

This plugin only works if used with **Visual Studio 2010/2012/2013 Ultimate**! If you're using another edition of Visual Studio 2010/2012/2013, please see [Visual Studio 2005 and 2008 IDE
Plugins](https://github.com/dynaTrace/Dynatrace-Visual-Studio-2005-and-2008-IDE-Plugins).

dynaTrace provides plugins for Visual Studio 2010/2012/2013 to enable **Automatic Code Lookups** from the dynaTrace Client, **Automatic Agent injection** when launching an application from the IDE,
**Integration** to the Visual Studio **Load Testing** Feature.

## Plugin Details

| Name | Visual Studio 2010, 2012 and 2013 IDE Plugins
| :--- | :---
| Author |dynaTrace Software
| License | [dynaTrace BSD](dynaTraceBSD.txt)
| Support | [Supported](https://community.compuwareapm.com/community/display/DL/Support+Levels)
| Known Problems | [KB-424 Visual Studio Plugin will not work](https://community.compuwareapm.com/community/display/KB/KB-424+Visual+Studio+Plugin+will+not+work)  
| | [KB-462 Visual Studio shows error number 80131515 on startup](https://community.dynatrace.com/community/display/KB/KB-462+Visual+Studio+shows+error+number+80131515+on+startup+when+Add-in+is+activated)
| Release History | 2010-04-14 Initial Release
| | 2010-11-02 Release for dynaTrace 3.5
| Download | [dynaTrace 6.0 Plugin for Visual Studio 2010/2012/2013](CodeLinkVS2010.dt60.zip)
| |  [dynaTrace 6.0 Web and Load Test Plugin for Visual Studio 2010/2012/2013 Load Testing](dynatrace-vsts.plugin.2010-6.0.0.6733.zip)
| | [dynaTrace 5.6 Plugin for Visual Studio 2010/2012/2013](CodeLinkVS2010.dt56.zip)
| | [dynaTrace 5.6 Web and Load Test Plugin for Visual Studio 2010/2012/2013 Load Testing](dynatrace-vsts.plugin.2010-5.6.0.5713.zip)
| | [dynaTrace 5.5 Plugin for Visual Studio 2010 and 2012](CodeLinkVS2010.dt55.zip)
| | [dynaTrace 5.5 Web and Load Test Plugin for Visual Studio 2010 Load Testing](dynatrace-vsts.plugin.2010-5.5.0.5226.zip)

## Visual Studio Plugin

### Installation

All you need to do is to

  1. extract the downlaoded file to your _My Documents\Visual Studio 2010\Addins_ directory. If the _Addins_ directory does not exist, create it. 

  2. Make sure that the downloaded files do not have the "blocked" file attribute under Windows 7. Change that to unblocked 

  3. If running Windows XP, after unpacking the files, it might be necessary to change the file protection to RW. If VS starts with an error related to this plugin, then the protection isn't set generously enough, or the 'blocked' flag is likely set if on Windows 7. 

  4. **Now start Visual Studio as Administrator** \- this is required as the dynaTrace plugin requires access to the registry. (if on Windows XP, simply set all the plugin files to be RW for all users) 

  5. The dynaTrace Visual Studio 2010 Plugin can be enabled through _Tools_-> _Add-In Manager_ in Visual Studio. 

  6. You need to have installed the dynaTrace .NET agent for launcher to work!! 

Note: If VS displays an error when starting and disables the plugin, go back to the steps above and verify the file protection issues listed above.

Once the Add-In is loaded you will see two new menu entries in the Tools menu. One is to configure the dynaTrace Plugin (_dynaTrace Configuration_), the other one is to Launch the currently opened
project by automatically injecting the dynaTrace .NET Agent into the launched application (_dynaTrace Launcher_).

### What the plugin provides

This plugin allows you to **Lookup Source Code** for a method traced by dynaTrace. From the dynaTrace Client you can select a method in the Methods or PurePath Dashlet and Lookup the method in Visual
Studio. **Please be aware that the code lookup only works for C# Source Code.**

The plugin also allows you to **launch an application** from the IDE and automatically inject the dynaTrace Agent to trace the launched application.

The plugin also extends the Visual Studio Load Testing Feature with a new tab in the Web Test Result Viewer. When you test a web application and the requests made by Visual Studio return PurePath IDs
(by using the Web Test Plugin or by specifying "Always send dynaTrace HTTP Headers" in the ASP.NET Sensor) then you can directly lookup a PurePath from the Result Viewer in Visual Studio

### Screenshots

![images_community/download/attachments/47186029/VS2010ToolsMenu.PNG](images_community/download/attachments/47186029/VS2010ToolsMenu.PNG)

![images_community/download/attachments/47186029/VS2010AddOnDialog.png](images_community/download/attachments/47186029/VS2010AddOnDialog.png)

![images_community/download/attachments/47186029/LookupCodeInVS2010.PNG](images_community/download/attachments/47186029/LookupCodeInVS2010.PNG)

![images_community/download/attachments/47186029/LauncherMenuEntry.PNG](images_community/download/attachments/47186029/LauncherMenuEntry.PNG)

Once the dynaTrace Add-On is enabled we get two menu entries in the tools menu

The dynaTrace Add-On has to be enabled through Tools->Add-In Manager

Code of the selected method opened in Visual Studio

Menu Entry that will launch the current project with injected dynaTrace Agent

![images_community/download/attachments/47186029/LauncherCapturedPurePath.PNG](images_community/download/attachments/47186029/LauncherCapturedPurePath.PNG)

![images_community/download/attachments/47186029/CodeLinkLookup.PNG](images_community/download/attachments/47186029/CodeLinkLookup.PNG)

![images_community/download/attachments/47186029/WebTestResult.PNG](images_community/download/attachments/47186029/WebTestResult.PNG)

PurePath that will be captured for every request executed against the launched application

Lookup the source code of a method from the dynaTrace Client

The dynaTrace Plugin extends the Web Test Result Viewer

## Web and Load Test Plugin

### Installation

Preconditions

  1. dynaTrace Client installed on local machine 

    * The plugin drives the session recording via REST calls to the client. The plugin tries to start the client when it is not running 

  2. Configuration on the dynaTrace Client (connected server / profiles) already done 

    * the settings for the plugin will require a server- and profile name to record a session 

Here are the steps to install this plugin:

  1. Unzip the downloaded file into your Load Testing Project. 

  2. Make sure that the downloaded files do not have the "blocked" file attribute under Windows 7. Change that to unblocked 

  3. In your project add a reference to copied / unzipped DLL(s). 

**In a Web Test Definition**

  * Click on the "Add Web Test Plugin" toolbar button select the dynaTrace Web Test Plugin. 

**In a Load Test Definition**

  * Add a Load Test Plugin that will enable Start/Stop Session Recording 

  * **Attention:** the properties "Server" and "SystemProfile" are _case-sensitive_! Be sure to use the exact string like shown in the dT-Client. 

### What the plugin provides

The Web Test Plugin will automatically tag Web Requests with the dynaTrace HTTP Header.  
The Load Test Plugin will automatically Start/Stop Session Recording during a load test.

### Screenshots

![images_community/download/attachments/47186029/VS2010WebTestPluginReference.png](images_community/download/attachments/47186029/VS2010WebTestPluginReference.png)

![images_community/download/attachments/47186029/VS2010LoadTestAddon.png](images_community/download/attachments/47186029/VS2010LoadTestAddon.png)

![images_community/download/attachments/47186029/VS2010WebTestPlugin.png](images_community/download/attachments/47186029/VS2010WebTestPlugin.png)

Add the reference to dynaTrace.VSTS.WebTestPlugin.dll to your Testing Project

Enabling dynaTrace as Load Testing Add-On to Start/Stop Session Recording during a Test run

Enabling dynaTrace Web Test Plugin that will Tag every HTTP Request during a Test run with the dynaTrace HTTP Header

