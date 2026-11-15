# Link Cable Test
This project was made to test the link cable functionality of GB Studio.
There's some issues, specifically the ROM will freeze if the Transfer command is called before the linked device can execute the Host/Join command. I tried to make it less likely to happen by prompting the player to only proceed once the respective other linked device reports it is ready.

Feel free to look at the project file and pick it apart if you are also struggling to figure out how to get this working.
An exported .gb ROM is included in the build folder. You can try it on real hardware or use BGB Emulator's link functionality to try it yourself.

There is a Comment event command in the Transfer scene that explains the basic process and idea. You can ignore most of the drawing and whatnot, as it's just a quick and messy way to communicate to the player what's going on.

### Note
This project is two years or so old already and was originally shared on the GBStudio discord. It didn't work properly on the 4.3.2 version of GBStudio anymore and there were some things I wanted to change, so I decided to update and upload it to github now.

My example only transfers a single variable's value (it sends TRUE/1 to the other device and receives TRUE/1 in return), but by increasing the packet size and allocating more variables, sending over more complex data would work just the same.

Hopefully this helps some people with developing their GB games!

### The Link Cable Protocol
In my initial attempt at this project, there was really not a lot of documentation attached to the link cable feature of GBStudio. I tried to piece together a theory about what is going on (especially with the packet size) based on available documentation about the real link cable protocols, but it turned out now with the updated docs that it has very little to do with how GBStudio is handling it.

I feel there is an obviously missing functionality in the GBStudio implementation that would check for an established session started by `Link: Host` and `Link: Join`. Since the session not having been established properly on both ends before `Link: Transfer` is executed leads to the ROM crashing. This results in a very flimsy and crash-prone initial "handshake". Hopefully this will be addressed in future GBStudio versions.

## NO AI WAS USED AT ANY POINT OF CREATING THIS PROJECT. USING THIS PROJECT OR PARTS OF IT FOR TRAINING AI MODELS IS NOT PERMITTED.
