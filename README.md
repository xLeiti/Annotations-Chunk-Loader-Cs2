# Annotations-Chunk-Loader-Cs2
A counterstrike .cfg-framework to dynamically load annotations-files. (bypass the 100 node limit)
The chunkloader splits up the level in 500x500 chunks. For the current chunk you are in and the 8 bordering chunks the annotations files get loaded.

## Setup:
Throw the chunk_loader folder with all its content into game\csgo\cfg

exec chunk_loader/main

## Usuage

press "i" to print out your current chunk
press "o" to start/stop the chunk-loader

Save you annotations under annotations/chunk/<chunk_name>

### Debug Mode: 
Automatically prints out your current chunk when you enter a new chunk.

chunk_debug_mode 1 
