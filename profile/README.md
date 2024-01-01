## Wholesum; a p2p verifiable computing network
Wholesum is a p2p verifiable computing network. It's a p2p network in the sense that all the communications between nodes happen through libp2p. Clients announce compute needs and wait for offers from servers. Once a deal is made, the compute job is sent to chosen servers for execution. When the compute job is finished successfully, the client(the owner of the job) proceeds to verification. Having proofs and other necessary information about the job, verification is achieved by asking independent verifiers to confirm if the execution was honest. If verification is successful, servers get compensated and the output objects(data, stdout, stderr, logs, ...) are harvested. 

Honest execution is achieved by transforming and running ordinary code inside Risc0 host-guest environment. The actual computation happens inside a docker container equipped with Risc0 runtime environment. An execution session wishing to be deemed verified, should provide proofs of honest execution called `receipt` is Risc0 jargon. 

Stroage is handled in a decentralized way. Recall that passing around heavy objects(anything > 1mb) is not feasible in p2p settings. So, FairOS-dfs(which builds on top of Swarm) comes to rescue by handling storage inside pods(a filesystem structure). This reduces the need for passing around heavy objects to just passing their CIDs.

The network is composed of several items distributed across the following repos:
- [client](https://github.com/WholesumNet/client): a client asks the network to get the compute job done on her behalf and expects proof of honest execution.
- [server](https://github.com/WholesumNet/server): a server gets the compute job done along with proofs of honest execution.
- [verifier](https://github.com/WholesumNet/verifier): a verifier gurantees that a compute job was done in an honest manner.
- [warrant](https://github.com/WholesumNet/warrant): a tiny code used by `verifiers` to confirm if some computation was done honestly.
- [comms](https://github.com/WholesumNet/comms): a communications library based on libp2p that enables nodes to talk by implementing the core protocol of Wholesum.
- [dstorage](https://github.com/WholesumNet/dstorage): a FairOS-dfs client used by nodes to store data on Swarm.
- [jocker](https://github.com/WholesumNet/jocker): a tiny wrapper around Bollard(docker interface).
  
