# Ethereum 2.0 Implementers Call 18 Notes

### Meeting Date/Time: Thursday 2019/5/23 at [14:00 GMT](https://savvytime.com/converter/gmt-to-germany-berlin-united-kingdom-london-ny-new-york-city-ca-san-francisco-china-shanghai-japan-tokyo-australia-sydney/mar-28-2019/2pm)
### Meeting Duration: 1.5 hours
### [GitHub Agenda Page](https://github.com/ethereum/eth2.0-pm/issues/43)
### [Audio/Video of the meeting](https://www.youtube.com/watch?v=dw2GmEuLr5k&)

# 1. [Testing Updates](https://youtu.be/dw2GmEuLr5k?t=417)
* Protolambda 
  * Slow week with NY blockchain week, helpful to get together with implementers
  * Epoch transistions, sanity tests, want clients to create test runners and get feedback
  * Tests are currently on separate branch, soon to be released
* Mikhail
  * keccak256 still used in BLS test vectors
* Danny - this was likely a mistake, 
* Protolambda
  * Loading configuration files: compile-time vs runtime
* Mamy 
  * Nimbus discussed this at length - for now using compile-time constants, not through YAML
  * Reconsidering in future for users, don't want them have to recompile everytime
* Paul
  * Our approach has been to make our types generic across different size array lengths, so we're specifying sets of layouts so it's a mix
* Danny
  * Configurable constants validity condition accompanies this, currently enumerating those in a branch
  * Constants will likely live in a test repo for now
  
* Antoine
  * Testing jenkins instance for building docker files for Lighthouse, Prysm, Artemis for nodes on a simulated testnet
  * Working without discovery, just for connection. Next step is peer and sync
  * Format build by Whiteblock - network delays, easy to recreate real world simulations
* Danny
  * Another initial fuzzing test targeting Go and Py specs, overtime will integrate more clients
  
# 2. [Client Updates](https://youtu.be/dw2GmEuLr5k?t=1117)
* Parity - Wei Tang
  * Up to date with 0.6 spec
  * Basic validator implementation running - one potential issue with BLS implementation: some rare cases where library is deemed invalid
* Harmony - Mikahil
  * Finished 0.6 spec, passing all current tests, need to check out issues with BLS
  * Almost finished work on networking stack (wire proctocol, sync online mode, CLI interface for nodes)
  * Nodes falling apart after running several hours - mostly related to consensus
  * Too difficult to store public keys and compress them each time
* Pegasys - Jonny
  * Lot of planning for interop lockin
  * Implementation of watching validators register; Timing mechanism is now swappable for testing different ones
* Nimbus - Mamy
  * Slow weeks - several people on holiday
  * Networking, forward and backward sync 
  * Still working on libp2p
  * Some confusion between keccak256 and SHA256
  * Shuffling and BLS mainnet tests passing
  * Update on ETH 1: new member working networking and reusable parts for ETH 2.0 
  * Documentation generator for repo - should be cross language compatible
  * Also working on multi-threading and debugging Nim library
* Prysmatic - Terence
  * Finished up to 0.6 spec, working on how to use and optimize in testnet
  * Updating SSZ and trie hashing
  * Investigating BLS alternatives 
  * Possible colaboration with Whiteblock for p2p
* Lodestar - Cayman
  * SSZ and BLS (switched to Milagro) tests passing for 0.6, soon state transtition tests and shuffling
  * Landed first version of gossipsub, reviewed by libp2p team - haven't integrated yet
  * Working on simulations running end to end
  * Collaborating with Yeeth team to convert Lodestar components to WASM
* Lighthouse - Luke
  * Almost up to date with 0.6
  * Implemented parses of EF tests, added some provisions for future fuzzing - passing majority of tests
  * Progress with Discovery V5, inital implementation with Rust libp2p
  * Refactored database wrapper for optimizing for state storage and will be fuzzing more components
* Trinity - Hsiao-Wei
  * Working on beach chain validator functionality, adding block sinking process on devp2p
  * Progress on Discovery V5 - implemented encryption-decryption functions from spec
  * Updating deposit contract

# 3. [Research Updates](https://youtu.be/dw2GmEuLr5k?t=2083)
* Vitalik
  * [V2 of Phase 2 proposal](https://notes.ethereum.org/w1Pn2iMmSTqCmVUTGV4T5A?viewPhase#)
  * Instead of maintaining large array of state for every shard, 32 byte hash takes that place
  * Full state can be abstracted across different execution environments
  * Despite more abstraction it's simpler based on how it lets you abstract things - ex: no need for 1 standard rent scheme - allows for 
  alot more experimentation and design flexibility
  * Happens to provide a nice slot for ETH 1.0
  * Knowns and Unknowns:
    * Known - fundamentally possible to fulfill vision - complexity doesn't seem to increase with 2 layers over 1
    * Unknown - efficiency benefits from 1 type of committee over 2 types 
    * Unknown - challenges in fragmentation over different environments - harder or easier to upgrade?
    * Unknown - 2 layer structure economic design for fee markets
  * Discusses working on [SSZ Merkle proof in a python wrapper and cross execution environments](https://youtu.be/dw2GmEuLr5k?t=2873)
  *Wrote basic PR for data availability proofs
  
  (https://youtu.be/dw2GmEuLr5k?t=3419)
    
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  

