# Quick Start Guide: the Nexus Bridge + Vue.js example

This guide will help to setup the demo example of a Form Applet that is built using the Nexus Bridge and Vue.js framework.

The applet supports:
* navigation through records
* displaying, editing, saving and deleting data (supporting keyboard shortcuts)
* query operations (supporting keyboard shortcut)
* picklists that are read from Siebel configuration
* field properties that are read from Siebel configuration (required, field length)

Requirements: 
* Access to icons and fonts stored on https://fonts.googleapis.com/.
* Siebel version: 16+

This is not an example of implementation that can be used on production. It is intentionally kept straightforward.

 ![result](demo_vuejs.png)
 
1. Make a clean [Nexus Bridge Setup](/../../wiki/Setup-Nexus-Bridge) if you haven't done it before.

1. Clone the project `git clone https://github.com/ideaportriga/nexus-bridge` or download and unpack [the project's archive](../../../../../archive/master.zip).

1. Import [sif-file](https://raw.githubusercontent.com/ideaportriga/nexus-bridge/master/examples/VUE.JS%20Examples/Demo%20Example/SIF/Nexus_Vue_Objects.sif) *(use the mouse right click and `Save link as...` to download the file)* into the Siebel Tools.

1. Add the `Nexus Vue Account Screen` to your application:

      * Find out your Siebel Application Name in application `.cfg` file or by logging in and typing `SiebelApp.S_App.GetAppName()` into Chrome Developer Tools console.
      
      * Use the Tools to add `Nexus Vue Account Screen` under `Application > Screen Menu Item` for your Siebel Application Name.
      
      * Use the Tools to add `Nexus Vue Account Screen` under `Application > Page Tab` for your Siebel Application Name.
      
1. Compile (Siebel IP16) or deliver (Siebel IP17+) your changes.
    
1. Add the `Nexus Account View` to your application:

      * Use the Siebel Web Client to register `Nexus Account View` under `Administration - Application > Views`.
      
      * Add your user's responsibility to this view.
            
      * Click the `Clear cache` button on `Administration – Application > Responsibilities`.

1. Copy the files below to the `[Siebel Client or Server Home]\public\SCRIPTS\siebel\custom\` folder:

    * [`vue.js`](https://raw.githubusercontent.com/ideaportriga/nexus-bridge/master/examples/VUE.JS%20Examples/vue.js)
    
    * [`vuetify.js`](https://raw.githubusercontent.com/ideaportriga/nexus-bridge/master/examples/VUE.JS%20Examples/vuetify.js)
    
    * [`polyfill.min.js`](https://raw.githubusercontent.com/ideaportriga/nexus-bridge/master/examples/VUE.JS%20Examples/polyfill.min.js)
    
1. Copy [`Nexus_vuedemo_PR.js`](https://raw.githubusercontent.com/ideaportriga/nexus-bridge/master/examples/VUE.JS%20Examples/Demo%20Example/Nexus_vuedemo_PR.js) *(use the mouse right click and `Save link as...` to download the file)* into the `[CLIENT_HOME or SERVER_HOME]/public/SCRIPTS/siebel/custom/` folder.

1. Copy [`vuetify.min.css`](https://raw.githubusercontent.com/ideaportriga/nexus-bridge/master/examples/VUE.JS%20Examples/vuetify.min.css) *(use the mouse right click and `Save link as...` to download the file)* into the `[Siebel Client or Server Home]\public\files\custom` folder.

1. Use the Siebel Web Client to reference JS-files in Siebel Open UI Manifest as follows:

	* under `Administration - Application > Manifest Files` add a new record: 
		* **Name:** `siebel/custom/Nexus_vuedemo_PR.js`

	* under `Administration - Application > Manifest Administration` add a new record under **UI Objects**: 
		* **Name:** `Nexus SIS Account Entry Applet`
		* **Usage Type:** `Physical Renderer`
		* **Type:** `Applet`

	* and add a new record under **Object Expression**:
		* **Level:** `1`

	* and add a new record under **Files**:
		* **Name:** `siebel/custom/Nexus_vuedemo_PR.js`
    
1. Empty browser cache and hard reload *(e.g. using Chrome with open DevTools: press F12, then right-click a browser Refresh button and press ‘Empty Cache and Hard Reload’)*

1. Re-login to your Siebel Application.

1. Navigate to the `Nexus Vue Account Screen` screen.
