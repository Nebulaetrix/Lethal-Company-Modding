Mods that manipulate and add code are the base of most other mods
## Developing with Template
---
If developing a mod from the BepInEx 5 template, you can find your mod details in the `PluginInfo.cs` file.\
Upon creation of a solution using the template, it should automatically create this file with the details provided in the solution creation panel.\
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
This file usually doesn't need to be altered and generally, the `PLUGIN_GUID` and `PLUGIN_NAME` will stay the same unless it's an exception.\
## Developing without Template
---
Gio text here\
## General Structure
---
`Plugin.cs`
```cs
using System;
using System.Reflection;
using BepInEx;
using BepInEx.Logging;
using HarmonyLib;
using ModName.Patches;

namespace ModName
{
    [BepInPlugin(PluginInfo.PLUGIN_GUID, PluginInfo.PLUGIN_NAME, PluginInfo.PLUGIN_VERSION)] // PluginInfo is a class created using the template 
    public class Plugin : BaseUnityPlugin
    {
        private bool _patched; // Validates if the plugin has been loaded and patched
        public static ManualLogSource Log { get; set; } // Logs all things related to the mod to the BepInEx console
        private void Awake() // Ran on startup by the BepInEx loader
        {
            if (_patched)
            {
                Log.LogWarning("Already Patched");
                return;
            }
            Log = base.Logger; // Sets your log to the parent logger

            Harmony.CreateAndPatchAll(typeof(ModPatch), PluginInfo.PLUGIN_GUID); // Creates an instance of harmony using a patch class

            Log.LogInfo($"Plugin {PluginInfo.PLUGIN_GUID} is loaded!");
            _patched = true;
        }
    }
}
```