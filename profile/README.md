## Wholesum; a p2p verifiable computing network

[Wholesum](https://www.wholesum.network/) is a p2p verifiable computing network tailored for `ETH L2 sequencer decentralization`. It's a p2p network in the sense that all the communications between nodes happen through libp2p. Clients announce compute needs and wait for offers from servers. Once a deal is made, the compute job is sent to chosen servers for execution. When the compute job is finished successfully, the client(the owner of the job) proceeds to verification. Having proofs and other necessary information about the job, verification is achieved by asking independent verifiers to confirm if the execution was honest. If verification is successful, servers get compensated and the output objects(data, stdout, stderr, logs, ...) are harvested.

Honest execution is achieved by transforming and running ordinary code inside Risc0 host-guest environment. The actual computation happens inside a docker container equipped with Risc0 runtime environment. An execution session wishing to be deemed verified, should provide proofs of honest execution called `receipt` is Risc0 jargon.

Stroage is handled in a decentralized way. Recall that exchanging heavy objects(anything > 1mb) is not feasible in p2p settings, so decentralized storage comes to rescue by storing once and passing CIDs around.

The network is composed of several items distributed across the following repos:

- [client](https://github.com/WholesumNet/client): Clients demand proving.
- [prover](https://github.com/WholesumNet/prover): Provers fulfill prove, join, snark, ... jobs.
- [comms](https://github.com/WholesumNet/comms): Communications library based on libp2p to enables nodes exchnage messages.
- [dstorage](https://github.com/WholesumNet/dstorage): Wrapper around Swarm and Filecoin(through Lighthouse) to store data in a decentralized fashion. CIDs fly around.

Here's a rough sketch of the pipeline being developed for parallel proving:
![Parallel proving scheme](https://github.com/WholesumNet/docs/blob/main/images/pipeline.png)
