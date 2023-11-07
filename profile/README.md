### Wholesum; a p2p verifiable computing network
Wholesum network is composed of the following repos:
- [server](https://github.com/WholesumNet/server): the agent(a CLI) fulfilling computation requests along with proofs of honest execution.
- [client](https://github.com/WholesumNet/client): the agent(a CLI) that manages what clients need to do to get their computation jobs done.
- [verifier](https://github.com/WholesumNet/verifier): the agent that confirms if a piece of computation was done in an honest manner.
- [warrant](https://github.com/WholesumNet/warrant): a tiny piece of code used by `verifiers` to confirm if some computation was done honestly.
- [comms](https://github.com/WholesumNet/comms): a communications library that enables `servers`, `clients`, and `verifiers` to talk and get jobs done.
- [dstorage](https://github.com/WholesumNet/dstorage): a FairOS-dfs client.
