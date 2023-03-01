Spawns = map(); //Stores spawns
SpawnsSaveFile = "Spawns.config"; //name for spawns file
PermissionPrefix = "Spawn"; //Permission will be PermissionPrefix.CommandName
MinReputation = 15; // players with this group won't get forced to the spawn
wipeConfigMessage = "[CustomSpawns] Spawns have been wiped!";

event onLoad()
{
	loadConfig(Spawns);
  print("[CustomSpawns] {0} Spawns loaded from unturned/uScript/Data/{1}!".format(Spawns.count, SpawnsSaveFile));
}

event onPlayerJoined(player)
{
  rand = random();
  roll = rand.int(0, Spawns.count);
  spawnvar = Spawns.get(0);
  if (player.reputation >= 15 and player.reputation <= -15) return;
  if (player.reputation <= 15 and player.reputation >= -15)
  {
    player.teleport(spawnvar);
    player.setData("status", 1);
    print("[CustomSpawns] {0} seems to be new here, sent him to safezone.".format(player.name));
  }
}

event onPlayerRespawned(player)
{
  if (player.getData("status") == 0)
  {
    player.setData("status", 1);
    if(!player.hasBed or player.bedPosition.distance(player.position) > 2)
    {
      rand = random();
      roll = rand.int(0, Spawns.count);
      spawnvar = Spawns.get(roll);
      player.teleport(spawnvar);
    }
  }
}

event onPlayerDeath(victim, killer, cause)
{
  victim.setData("status", 0);
}

command Wild()
{
  allowCaller = "player";
  permission = "{0}.Wild".format(PermissionPrefix);
	execute()
	{
    rand = random();
    roll = rand.int(0, Spawns.count);
    spawnvar = Spawns.get(roll);
    player.teleport(spawnvar);
  }
}

command SpawnSet()
{
	allowCaller = "player";
  permission = "{0}.Set".format(PermissionPrefix);
	execute()
	{
    player.message("[CustomSpawns] Spawn set at: {0}".format(player.position.toString()), "white");
    PlayerPos = player.position;
	Spawns.set(Spawns.count, PlayerPos);
    saveConfig(Spawns);
    print("[CustomSpawns] {0} Spawns saved to unturned/uScript/Data/{1}!".format(Spawns.count, SpawnsSaveFile), "white");
	}
}

command SpawnList()
{
  allowCaller = "player";
  permission = "{0}.List".format(PermissionPrefix);
  execute()
  {
    if(Spawns.count == 0) return player.message("[CustomSpawns] There are no spawns set yet!, use /SpawnSet to get started", "red");
    if(Spawns.count == 1) return player.message("[CustomSpawns] There are {1} spawns (ID 0), use /SpawnView <ID> to view it in your map".format(Spawns.count-1, Spawns.count), "white");
    player.message("[CustomSpawns] There are {1} spawns (ID 0 to {0}), use /SpawnView <ID> to view it in your map".format(Spawns.count-1, Spawns.count), "white");
  }
}

command SpawnView(arg)
{
  allowCaller = "player";
  permission = "{0}.View".format(PermissionPrefix);
  execute()
  {
    if(arguments.count < 1) return player.message("Missing argument. Please choose an ID");
    if(Spawns.count == 0) return player.message("There are no spawns set yet!!! get started with /spawnset", "red");
    if(!Spawns.containsKey(arg.toNumber())) return player.message("This spawn doesn't Exist {0}".format(arg));
    player.marker.set(Spawns.get(arg.toNumber()), "CustomSpawn {0}".format(arg));
    player.message("[CustomSpawns] Spawn {0} found [{1}], Check your map marker".format(arg.toString(), player.marker.position.toString()), "white");
  }
}

command SpawnWipe()
{
  allowCaller = "player";
  permission = "{0}.Wipe".format(PermissionPrefix);
  execute()
  {
    wipeConfig(Spawns);
    print(wipeConfigMessage);
    player.message(wipeConfigMessage, "red");
    Spawns.clear();
    wipeConfigMessage = "[CustomSpawns] Spawns have been wiped!";
  }
}

// Saves the spawns from the map to the Spawns file
function saveConfig(configMap) {
  text = "";
  foreach(keyValuePair in configMap) {
    text += "{0}={1}\n".format(keyValuePair.key, keyValuePair.value.toString().replace("x", "").replace("y", "").replace("z", "").trim());
  }
  file.writeAll(SpawnsSaveFile, text);
}

// Takes care of completely clearing the Spawns file
function wipeConfig(configMap)
{
  text = "";
  file.writeAll(SpawnsSaveFile, text);
}

// Loads the Spawns file to the map
function loadConfig(configMap)
{
  configText = file.read(SpawnsSaveFile);
  configLines = configText.split("\n");
  foreach(line in configLines)
  {
    if(line == "") continue;
    p = line.split("=");
    partnumber = p[0].toNumber();
    vectorpart = p[1].split(",");
    vx = vectorpart[0].toNumber();
    vy = vectorpart[1].toNumber();
    vz = vectorpart[2].toNumber();
    v3 = vector3(vx, vy, vz);
    Spawns.set(partnumber, v3);
  }
}
