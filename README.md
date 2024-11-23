# Annotations-Chunk-Loader-Cs2
A counterstrike .cfg-framework to dynamically load annotations-files. (bypass the 100 node limit)
The chunkloader splits up the level in 500x500 chunks. For the current chunk you are in and the 8 bordering chunks the annotations files get loaded. (So a 1500x1500 unit area is loaded)

## Setup:
Throw the chunk_loader folder with all its content into game\csgo\cfg

```exec chunk_loader/main```

## Usage

press "i" to print out your current chunk (or the file-path for your current chunk if ```chunk_debug_mode 1 ```)

press "o" to start/stop the chunk-loader

The ChunkLoader automatically detects the map you're playing on, when you start the ChunkLoader by pressing "o" (or if you press "i".)

Note, if you change your level, you need to toggle the ChunkLoader off and on again to trigger the detection!

Save you annotations under ```annotations/chunk/<map_name>/<chunk_name>```


### Debug Mode: 
Automatically prints out your current chunk when you enter a new chunk.

Print out the file instead of the chunk when pressing "i"

```chunk_debug_mode 1 ```

### Maps support

Currently the ChunkLoader supports the maps ```de_ancient, de_anubis, de_dust2, de_inferno, de_mirage, de_nuke, de_overpass, de_train, de_vertigo```

Non supported maps are linked to the default path  ```annotations/chunk/default/<chunk_name>``` and have no origin offset configured.

If you want to add support to more maps, copy one of the map.cfg in ```chunk_loader```, rename it to your desired map, adjust the names in the file. 
Then add an alias under the map-section in ```chunk_loader/main```. If the map is off centre, you need to define x/y-offset values here. 
Make sure non of the is "OutOfBounds"!


## ToDo
- Find new console tricks to make simplify the ChunkLoader and make it scalable! 
