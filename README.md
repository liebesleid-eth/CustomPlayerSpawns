# CustomPlayerSpawns
Replace the default unturned player spawns with this script using commands!

This script requires **uScript** installed in your server in order to be executed. Join [uScript Discord](https://discord.gg/DukF46FcPQ) to download **uScript module**.

## Features

- New players will be teleported to the first spawn you set (Spawn 0), works well for safezones.
- Players will be randomly teleported to any of the spawns you set.
- Works with bedrolls, players will still be able to use /home.
- (future) /WildSpawn command, teleports the player to one of the spawns randomly.
- Spawns are kept upon server restarts and script reloads.

## Usage:
| Command | Description |
| --- | --- |
| SetSpawn | Creates a new player spawn point in the point where you are standing and assigns it an ID starting from 0. |
| SpawnList | Tells you how many spawns there are, as well as the ID range (0 - n). |
| SpawnView <ID> | Tells you the spawn's coordinates, and marks it on your map. |
| WipeSpawns | Clears the SpawnList completely. |
| (future) WildWarp | Randomly teleports the player to one of the spawns. |

## Installation steps
<details><summary>Step 1 - Joining uScript discord</summary>
<p>
  
Join [uScript Discord](https://discord.gg/DukF46FcPQ), once there then head over to #Loader-download channel, download the *"uScript2.zip"* file, and unzip it in your download's folder.

![image](https://user-images.githubusercontent.com/99780369/222036153-a944bd6c-4ebe-4b96-b156-b01962c93997.png)![image](https://user-images.githubusercontent.com/99780369/222036578-98133bd8-d730-4581-bea0-de6c483a66c9.png)
  
</p>
</details>

<details><summary>Step 2 - Preparing loader files</summary>
<p>
  
Go inside ```uScript2 > Modules``` and Zip the uScript.Unturned folder.

![image](https://user-images.githubusercontent.com/99780369/222037211-ef08d89b-b394-4224-9637-b9ee69ed9476.png)
  
</p>
</details>

<details><summary>Step 3 - Drop and unzip the loader</summary>
<p>
  
In your unturned server, head over to "Modules" folder and drag in your uScript.Unturned.zip file, then unarchive it.
![image](https://user-images.githubusercontent.com/99780369/222037499-1c01f109-0e2d-4751-9bc6-711d6b96a87a.png)
After this, it should look something like this:

![image align="center"](https://user-images.githubusercontent.com/99780369/222037673-458d42ef-f9a3-4a55-9be8-a8e1db6b29d2.png)
  
</p>
</details>

<details><summary>Step 4 - Restart server & load the scripts</summary>
<p>
  
Restart your server, and once its done you can find uScript script's directory under ```Servers/unturned/uScript/Scripts```. In this folder is where you have to drop CustomPlayerSpawns.uscript file, or any other uScript scripts that you wish to use.

Upon doing this, you can now run `/script reload` in console to load them to your server.

![image](https://user-images.githubusercontent.com/99780369/222038879-f8eb75e7-c58b-4fcf-9112-854ad7499d87.png)
  
</p>
</details>

  Feel free to contact me if you need help installing uscript! my discord: Liebesleid.eth#8866 , or ask directly in uScript discord.
