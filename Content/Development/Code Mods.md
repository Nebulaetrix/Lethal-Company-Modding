Mods that manipulate and add code are the base of most other mods
## Developing with Template
<hr>
If developing a mod from the BepInEx 5 template, you can find your mod details in the `PluginInfo.cs` file.
Upon creation of a solution using the template, it should automatically create this file with the details provided in the solution creation panel.
![[PluginInfo.cs.png]]
This file usually doesn't need to be altered and generally, the `PLUGIN_GUID` and `PLUGIN_NAME` will stay the same unless it's an exception.
## Developing without Template
<hr>

## General Structure
<hr>
Here's a rundown of how a basic code mod functions:
![[Plugin.cs.png]]`class PluginInfo` is only present if you use the template, otherwise, you will most likely have local variables or strings in its place
`bool _patched` is used to validate if the plugin has been loaded and patched
`ManualLogSource Log` is used to log all things related to the mod to the BepInEx console
`SpawnableEnemyWithRarity Puffer` in this case, is relevant to the content of the mod 
`private void Awake()` is the method ran on startup by the BepInEx loader
`Harmony.CreateAndPatchAll(typeof(PufferPatch), PluginInfo.PLUGIN_GUID);` creates an instance of harmony which patches to a method provided in the class `PufferPatch`. In your own mod's case, this would be a class (eg, "ModPatch.cs") containing functionality of the mod (This is completely optional but is better practice to separate patches into files)