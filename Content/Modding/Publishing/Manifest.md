The manifest is used by Thunderstore to obtain information about your mod:
- The `name` and `version_number` is self explanatory
- The `website_url` is usually used to provide a link to a Github repo, it can left blank by putting `""`
- The `description` is what is displayed below the mod - the red box pictured here
- ![[Mod Description.png]]
- And the `dependencies` are other APIs and SDKs that the mod relies on
The manifest.json is structured like below:
```json
{
"name": "ModName",
"version_number": "1.0.0",
"website_url": "https://github.com/githubUsername/repo",
"description": "Mod description goes here, 250 characters maximum.",
"dependencies": [
	"LethalAPI-1.0.0",
	"BepInEx-BepInExPack-5.4.2100"
	]
}
```

This is placed in the top level of the File hierarchy, located in the [[Publishing]] section