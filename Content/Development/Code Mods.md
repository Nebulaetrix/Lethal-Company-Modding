Mods that manipulate and add code are the base of most other mods.
They can be developed with the BepInEx template, or without.
## Developing with Template
---
If developing a mod from the BepInEx 5 template, you can find your mod details in the `PluginInfo.cs` file.
```cs
namespace ModName
{
    public static class PluginInfo
    {
        public const string PLUGIN_GUID = "ModName";
        public const string PLUGIN_NAME = "ModName";
        public const string PLUGIN_VERSION = "1.0.0";
    }
}
```
Upon creation of a solution using the template, it should automatically create this file with the details provided in the solution creation panel.
This file usually doesn't need to be altered and generally, the `PLUGIN_GUID` and `PLUGIN_NAME` will stay the same unless it's an exception.
## Developing without Template
---
Gio text here :boom:
## General Structure
---
After adding the code via templates or not, you now need to add references. This can be done within your chosen IDE, for Visual Studio, it can be done as follows:
`Add Project Reference > Browse > Assembly-CSharp.dll`
The `.dll` can be found in the `Lethal Company\Lethal Company_Data\Managed\` folder

Finally, you should have a `Plugin.cs` folder like this:
```cs
using System;
using System.Reflection;
using BepInEx;
using BepInEx.Logging;
using HarmonyLib;
using ModName.Patches;

namespace ModName
{
	// PluginInfo is a class created using the template 
    [BepInPlugin(PluginInfo.PLUGIN_GUID, PluginInfo.PLUGIN_NAME, PluginInfo.PLUGIN_VERSION)] 
    public class Plugin : BaseUnityPlugin
    {
	    // Validates if the plugin has been loaded and patched
        private bool _patched; 
        // Logs all things related to the mod to the BepInEx console
        public static ManualLogSource Log { get; set; }
        // Ran on startup by the BepInEx loader
        private void Awake()
        {
            if (_patched)
            {
                Log.LogWarning("Already Patched");
                return;
            }
            // Sets your logger to the parent logger
            Log = base.Logger; 
			// Creates an instance of harmony using a patch class
            Harmony.CreateAndPatchAll(typeof(ModPatch), PluginInfo.PLUGIN_GUID);
            Log.LogInfo($"Plugin {PluginInfo.PLUGIN_GUID} is loaded!");
            _patched = true;
        }
    }
}
```