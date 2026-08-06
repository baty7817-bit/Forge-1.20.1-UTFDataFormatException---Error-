# Forge-1.20.1-UTFDataFormatException---Error-
Sanitized debugging repository for a Forge 1.20.1 (47.4.10) networking issue. Contains client/server logs, configs, resource packs, screenshots and relevant files to investigate a recurring UTFDataFormatException (DecoderException/EncoderException) occurring when joining a dedicated server.
PLEASE README THIS: 

Hi everyone, 
I've been trying to solve a very unusual networking issue on my modded Forge server and I'm running out of ideas.
Environment
Minecraft 1.20.1
Forge 47.4.10
Prism Launcher
Java 17.0.9 on both client and server
Windows 10
Dedicated Forge server running on a separate laptop
Around 325 Forge mods
The client and server have:
exactly the same mods
exactly the same versions
exactly the same config folder
exactly the same defaultconfigs
I literally copied everything, so there are no differences between the two instances.
What happens
The server starts perfectly.
No crashes.
No OutOfMemoryError.
No missing mods.
No registry mismatch.
I can connect successfully.
The game reaches "Joining world...".
Then the loading screen becomes black (this is expected because of Beyond Earth and happens normally).
I can already hear real-time in-game sounds around my player, so the server is clearly sending world updates.
The server console also shows that packets and player events are happening normally.
After approximately 5 seconds, I always get disconnected.
The message is:
Internal Exception: io.netty.handler.codec.DecoderException: io.netty.handler.codec.EncoderException: java.io.UTFDataFormatException: malformed input around byte XX
The interesting part is that the byte number changes almost every attempt.
Examples:
39
48
49
54
72
78
97
98
125
Sometimes the same number appears twice, sometimes a completely different one.
Things I already verified
Same Forge version
Same Java version
Same mod list
Same configs
Same defaultconfigs
Singleplayer works perfectly
The dedicated server itself runs perfectly
The issue also happens when connecting using the local LAN IP, so it is NOT related to playit.gg.
No UTFDataFormatException appears inside either latest.log or debug.log on either the client or the server.
The only place where I see the exception is the disconnect message shown by Minecraft.
Warnings I found
I found these warnings, but I believe they are unrelated:
Farmers Delight codec registered twice.
Forge VersionChecker JSON parsing warnings.
Minecraft Realms malformed JSON warnings.
None of them occur at the moment of the disconnect.
Question
Has anyone seen a Forge server produce this exact error without any stacktrace in either the client or server logs?
Could this indicate that a specific mod is sending a corrupted custom network packet, or is there another known cause for this kind of UTFDataFormatException?
If anyone has encountered this before, I'd really appreciate any ideas.
