# Annotations-Chunk-Loader-Cs2
A counterstrike .cfg-framework to dynamically load annotations-files. (bypass the 100 node limit)
The chunkloader splits up the level in 500x500 chunks. For the current chunk you are in and the 8 bordering chunks the annotations files get loaded. (So a 1500x1500 unit area is loaded)

The chunks get laoded/relaoded when 

a) you enter a new Chunk

b) your viewing direction changes (north, northWest, west, southWest, south, southEast, east, northEast)

Direction based Chunk appending order for the bordering chunks:
![Screenshot 2024-11-24 170417](https://github.com/user-attachments/assets/aec4469e-2276-4b95-baac-228e1075c322)

![Screenshot 2024-11-24 144402](https://github.com/user-attachments/assets/ed07d18d-8b85-402d-9d8a-e28ac24af19d)

## Setup:
Throw the chunk_loader folder with all its content into game\csgo\cfg

```exec chunk_loader/main```

## Usage:

press "i" to print out your current chunk (or the file-path for your current chunk if ```chunk_debug_mode 1 ```)

press "o" to start/stop the chunk-loader

The ChunkLoader automatically detects the map you're playing on, when you start the ChunkLoader by pressing "o" (or if you press "i".)

Note, if you change your level, you need to toggle the ChunkLoader off and on again to trigger the detection!

Save your annotations under ```annotations/chunk/<map_name>/<chunk_name>```


### Debug Mode: 
Automatically prints out your current chunk when you enter a new chunk.
Shows the direction you are facing as an hud_hint.

Print out the file instead of the chunk when pressing "i"

```chunk_debug_mode 1 ```

![20241124164324_1](https://github.com/user-attachments/assets/9d276206-75e3-4f2f-839d-8891e398899b)


### Maps support:

Currently the ChunkLoader supports the maps ```de_ancient, de_anubis, de_dust2, de_inferno, de_mirage, de_nuke, de_overpass, de_train, de_vertigo```

Non supported maps are linked to the default path  ```annotations/chunk/default/<chunk_name>``` and have no origin offset configured.

If you want to add support to more maps, copy one of the map.cfg in ```chunk_loader/maps```, rename it to your desired map, adjust the names in the file. 
Then add an alias under the map-section in ```chunk_loader/main```. If the map is off centre, you need to define x/y-offset values here. 
Make sure non of the map is "OutOfBounds"!


## ToDo:
- Find new console tricks to simplify the ChunkLoader and make it scalable
