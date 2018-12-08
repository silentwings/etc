Instructions:

Place widget (save) into widget folder and gadget (load) into gadgets folder.

With widget part, be a spectator, type /saveunits into chat and it will record 60 seconds of the game. 
There will then be 4 files in your /spring dir with prefix REC_. 
Move all these into the /luarules/configs folder of your .sdd. 
Load up an empty game (you will need at least 2 allyteams) and type /luarules loadunits. 
The 60 seconds you record will now replay - although some things are not recorded its enough to feel as though you are watching the game again.



How it works: 

Saves all current units, saves current order queues & factory queues. Then for 60 secs records all orders given. 
On load it restores all units (with their original unitIDs), their queues, and replays the orders at appropriate gameframes. 
While the replay is running it records the gamespeed and fps, then tells you the average of both at the end (ignoring the first 10 secs, during which Spring is likely doing caching stuff).

There is also a /luarules cleanunits command, which is called by loadunits before it spawns everything.

Obviously it misses some things - notably, if a unit is created after the start of the 60 seconds, that unit won't get any orders given to it in the replay (since its unitID wont have been saved and could be different in the replay). It also doesn't bother with minor things like cloaking, missiles stored, etc etc. But for 60 seconds that doesn't matter so much.