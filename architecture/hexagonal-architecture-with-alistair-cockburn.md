# Hexagonal Architecture With Alistair Cockburn and Thomas Pierrain
README
## Prez style notes
- Storytelling : from where does it comme from ?
- Lots of example : why the classic why sucks

## Content notes
- Port -> interface
- design pattern -> propriété (ex: configurable dependencies)
- two sides : 
 - primary actors : the callers (Drivers)
 - secondary actors : the callees (Repository and recipients)
 - the difference is who initiate the conversation
- Instanciation order : Left - domain - right
 - then we only need right
- The very first client is a test (but its a client like any other)
- The very first repository or recipient is a stub (but it's a perfecly valid one)
- Steps of the live-coding : 

| Step | Driver | Domain | Repo |
|------|--------|--------|------|
| 1 | Test | Hardcoded | |
| 2 | Test | -> | Stub |
| 3 | Console Test | Hardcoded | |
| 4 | Console | Hardcoded | |
| 5 | Console Test | -> | Stub |
| 6 | Console | -> | Stub |
| 7 | Test | -> | File |
| 8 | Console Test | -> | File |
| 9 | Console | -> | File |

![Hexagonal architecture schema](https://github.com/magelle/notes/raw/master/hexagonal-architecture.png)
