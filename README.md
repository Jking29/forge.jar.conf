## See the default craftbukkit.jar.conf for a detailed documentation of the
## format of this file.
[config]
name = Forge
source = http://files.minecraftforge.net/maven/net/minecraftforge/forge/1.15.2-31.1.0/forge-1.15.2-31.1.0-universal.jar
configSource = https://github.com/jking29/multicraft.jar.conf/raw/master/forge/forge.jar.conf

## The category to list this executable in
category = Mods

[encoding]
encode = utf-8
decode = utf-8
fileEncoding = latin-1

[start]
command = "{JAVA}" -server -Xmx{MAX_MEMORY}M -Xms{START_MEMORY}M -Djline.terminal=jline.UnsupportedTerminal -jar "{JAR}" nogui {PARAMS}


[force_config]
configFile = server.properties
newline = \n
search1 = server-ip
replace1 = server-ip={IP}
search2 = server-port
replace2 = server-port={PORT}
search3 = max-players
replace3 = max-players={MAX_PLAYERS}

[parse_log]
start=^(?P<time>(:?[-\d]+ )?\[?[:\d]+\]?)\s+\[?(?P<type>[^]<>]+)[\]>]\:?\s+(:?\[(:?Minecraft-)?(:?Server)\]\s+)?(?P<line>.*)$

[parse_startup]
start=^\s*Done
important=true

[parse_players]
listSplit=\s*,\s*
listLine=(?P<name>.*)
start=^(?:Connected\s*players|Online \([\d]+[^)]*\)):\s*(?P<v_listStr_append>.*)$
start1=^There are (?P<v_maxDataLines>\d+)/\d+ players
data=^(?P<v_listStr_append>.+)$
trigger=list
important=true
isList=true
maxLines=2
maxDataLines=0

[parse_chat]
start=^(?P<source>\[[^\]]+\])?\s*<(?P<sender>[^>]*)>\s*(?P<message>.*)$

[parse_command]
shortStart=(?:tried|issued server) command
start=^(?P<sender>.+)\s(?:tried|issued\sserver)\scommand:\s*(?P<command>.*)$
important=true

[parse_connect]
shortStart=logged in with entity id \d+ at
start=^(?P<name>.+?)\s*\[/(?P<ip>[^\]:]*)(:?(?P<port>[0-9]+)?)\]\s*logged in
start1=^(?P<name>.+)(?P<ip>\s+)logged in

[parse_disconnect]
shortStart=(lost connection|Kick(ing|ed))
start=^(?P<name>.+)\slost connection:\s*(?P<reason>.*)$
start1=^CONSOLE:\s*Kicking\s(?P<name>.+)$
start2=Kicked\s(?P<name>.+) from the game\s*$
