# ReActorNet

ReActorNet: Reliable Actor Networking

A framework-agnostic networking wrapper for Unity3D built for race condition reliability, network framework independence, and dynamic load balancing.

You can think of it as a very advanced, and somewhat more specialized big brother to the interfaces provide by UNet or Photon. But it runs on Photon (or any other framework, provided an interface) under the hood.

This library is inspired by the experience I have gained hacking and programming various multiplayer games. I am developing it as a tool to use in my upcoming titles.

## UNDER DEVELOPMENT

Claims here are plans being portrayed as reality. Nothing here is implemented yet. The documentation to be found here is the final step before implementation.

## Key features:

* Interfaceable with any networking library with sufficient features.
.* Currently only Photon Supported.
.* Photon Wrapper is very lightweight. Uses RaiseEvent to acheive lower-overhead than Photon's builtin Object Synchronization and RPC protocols.
* Event-Hook style networking, as opposed to UNet/Photon/RakNet/Unity3d classic broadcast-implement style. This is against Unity3D conventions, but in my opinion leads to cleaner code.
* Based on pure C# actor objects rather than UnityObject networkView components.
* Actor and Message table comparison and resynchronization combined with message buffering during host transfer and connect/disconnect, leading to hopefully very reliable behavior in the most challenging of connection/host transfer scenarios
* Dynamic-rate and interested-party-only transmission of transient state updates (like Photon's Object Synchronization, but adjusts its data rates and transmits slower to less-interested players to help mitigate the n^2 msg/s problem)
* Dynamic-rate and interested-party-only transmission of transient events. (like RPCs, but sent immediately only to the players who care the most, buffered and sent later for players who care less. Dropped (older dies first) if buffer is overloaded)
* Per-actor recursive dictionary of low-frequency auto-synchronized custom actor data. (Think: score, player name, team)
* Multiple NetworkPlayers per Client. (Think: Bots are identical in terms of how they are networked and managed to other players)
* Special HostNetworkPlayer representing host. Auto-transfers on host switch.
* Special HostActors (just actors owned by the HostNetworkPlayer). Auto-transfer on host switch.


## Documentation
Curious how it all works? Please visit the [docs subdirectory.](/docs)

