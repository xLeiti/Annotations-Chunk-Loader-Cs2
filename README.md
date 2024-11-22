# Annotations-Chunk-Loader-Cs2
A counterstrike .cfg-framework to dynamically load annotations-files. (bypass the 100 node limit)
The chunkloader splits up the level in 500x500 chunks. For the current chunk you are in and the 8 bordering chunks the annotations files get loaded. (So a 1500x1500 unit area is loaded)

## Setup:
Throw the chunk_loader folder with all its content into game\csgo\cfg

```exec chunk_loader/main```

## Usage

press "i" to print out your current chunk

press "o" to start/stop the chunk-loader

Save you annotations under annotations/chunk/<chunk_name>

Some maps are off centre, you can specify the offset at ```chunk_loader/main``` 

```alias origin_offset_x "incrementvar joy_axisx_deadzone -999999999 999999999 <offset>```

```alias origin_offset_y "incrementvar joy_axisx_deadzone -999999999 999999999 <offset>```

Please use 500 unit steps as offset values.

### Debug Mode: 
Automatically prints out your current chunk when you enter a new chunk.

```chunk_debug_mode 1 ```

## ToDo
- Simplify & Cleanup unnecessary files
- Rework mapping chunks to annotation files:
  goal = ```annotations/chunk/<mapname>/<x y>```
  skipping ugly alias loop
- Add my automatic map detection
- Make it scalable (currently it's limited to a 6000x6000 area)
