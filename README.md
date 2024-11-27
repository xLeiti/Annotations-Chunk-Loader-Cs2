# Annotations-Chunk-Loader-Cs2
A counterstrike .cfg-framework to dynamically load annotations-files. (bypass the 100 node limit)
The chunkloader splits up the level in 500x500 chunks. For the current chunk you are in and the 8 bordering chunks the annotations files get loaded. (So up to a 1500x1500 unit area is loaded)

## Setup:
Throw the chunk_loader folder with all its content into ```game\csgo\cfg```

```exec chunk_loader/main```

The ChunkLoader automatically detects the map you're playing on.

The ChunkLoader automatically switches off when you change the map or exit to the main menu.

Save your annotations under ```annotations/chunk/<map_name>/<chunk_name>```

You can adjust your configuration and binds in ```chunk_loader/main```

### Configuration
```chunk_debug_mode 0``` 

0 - default Mode, no output in chat, no directionHints, no console logging

1 - output in chat when you enter a new chunk, directionHints when ```chunk_directional_mode 1```, the ```getChunk```-bind prints out the current annotation-filePath instead of the chunk name

2 - same as 1, but console logging is enabled

![20241124164324_1](https://github.com/user-attachments/assets/7c7503e2-faea-4b6e-99d9-73e236a907ac)


```chunk_directional_mode 1``` 

0 - non directional chunk loading: chunks only refresh when you enter a new chunk. Appending priority of boarding chunks: first edges then corners

1 - direction based chunk loading: chunks refresh when you enter a new chunk or when your viewing direction changes.

   Directions: ```north, northWest, west, southWest, south, southEast, east, northEast```

  Appending priority: 
![Screenshot 2024-11-24 170417](https://github.com/user-attachments/assets/42c32759-144b-40fe-9949-9ea2ce0c9e27)
![Screenshot 2024-11-24 144402](https://github.com/user-attachments/assets/af7379f1-9cff-48ec-aa10-20be8646f142)


### Binds
```bind o chunk_toggle; ```: Toggle the ChunkLoader On/Off
```bind i getChunk; ```: Print out your current chunk (or the chunkFile when in debugMode)


### Maps support:

Currently the ChunkLoader supports the maps ```de_ancient, de_anubis, de_dust2, de_inferno, de_mirage, de_nuke, de_overpass, de_train, de_vertigo```

Non supported maps are linked to the default path  ```annotations/chunk/default/<chunk_name>``` and have no origin offset configured.

### Add your own maps:
1. Copy one of the map.cfg in ```chunk_loader/maps```, rename it to your desired map, adjust the names in the file.
2. Add a new section for your map in ```chunk_loader/get_map```:
   ```
   //cbble
   setinfo "cmd;grepMap" de_cbble
   grepStatus | toggle "cmd;grepMap"
   toggle grepMap cmd , mapCbble
   grepMap | toggle "cmd;"
   ```
4. Add an alias under the map-section in ```chunk_loader/main```. If the map is off centre, you need to define x/y-offset values here.

   Make sure non of the map is "OutOfBounds"!


## ToDo:
- Find new console tricks to simplify the ChunkLoader and make it scalable
