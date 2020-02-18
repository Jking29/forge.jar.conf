## See the default craftbukkit.jar.conf for a detailed documentation of the
## format of this file.
[config]
name = Forge
source = http://files.minecraftforge.net/maven/net/minecraftforge/forge/1.15.2-31.1.0/forge-1.15.2-31.1.0-universal.jar
configSource = https://github.com/jking29/multicraft.jar.conf/raw/master/forge/forge.jar.conf

## The category to list this executable in
category = Mods

[encoding]
#encode = system
#decode = system
#fileEncoding = latin-1

[settings]
logFile = server.log
## Uncomment the following to rotate the log at 20MB
#logRotateSize = 20971520
## Keep 5 log files
logBackupCount = 5
## Check the log size every 60 seconds
logRotateCheckInterval = 60000
## Copy instead of move log to log.1, vanilla Minecraft requires this
logPersistent = True


[parse_log]
start=^(?P<time>(:?[-\d]+ )?\[?[:\d]+\]?)\s+\[(?P<type>[^]]+)\]\:?\s+(:?\[[^]]+\]\s+)?(?P<line>.*)$
