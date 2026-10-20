---
layout: default
---

I build distributed systems and infrastructure, with experience across ML inference platforms, large-scale object storage, and distributed databases.

[LinkedIn](https://www.linkedin.com/in/priyeshnarayanan/) · [Email](mailto:priyesh@gmail.com)

## Selected Work

### LinkedIn — Ambry
*Staff Software Engineer · 2014–2019*

I was an early engineer on [Ambry](https://github.com/linkedin/ambry), LinkedIn’s open-source, geo-distributed object store, and later became its technical lead and architect. Ambry stores and serves most unstructured content on LinkedIn, including user generated media uploads. During my time, it served several petabytes of unstructured content across hundreds of nodes in four datacenters.

I drove architecture and implementation across routing, storage, and cluster management, partnered with SREs on production operations, and helped shape the team’s technical direction. I also mentored engineers and led GDPR compliance work across Ambry and its customer applications alongside my manager and TPM.

#### Streaming architecture for large objects

I designed and led the implementation and rollout of Ambry’s asynchronous, streaming router, replacing a blocking coordinator. Streaming and chunking enabled large-object workloads such as video and backups without buffering entire objects in memory.

I wrote core components, coordinated contributions across engineers, and worked with SREs on validation and deployment. We validated individual objects up to 1 TiB and completed the rollout while maintaining the service’s 99.99% availability.

#### Dynamic cluster management

I led the transition from static file-based configuration to dynamic cluster management: evaluating alternatives, building consensus, and designing and deploying a Helix/ZooKeeper-based solution.

This enabled automatic partition sealing and established the foundation for cluster rebalancing and self-healing.

#### Safe deletion in an append-only storage engine

I owned Ambry’s hard-delete capability from design through production rollout, enabling physical erasure of deleted content for compliance requirements.

The central challenge was introducing in-place writes into an append-only storage engine without corrupting neighboring live records. The design incorporated crash recovery and persistent progress tracking, supported by verification tools and testing under induced failures.

[Read the hard-delete design](https://github.com/linkedin/ambry/wiki/Hard%20Deletes)

#### Paper and talk

I co-authored the Ambry SIGMOD 2016 paper and presented the system at @Scale 2016.

[SIGMOD paper](http://dprg.cs.uiuc.edu/docs/SIGMOD2016-a/ambry.pdf)

### ClustrixDB
*Software Engineer · 2012–2014*

At Clustrix, I worked on the internals of a distributed relational database: in-memory tables, query execution, and cluster membership. These presentations explore the mechanisms and tradeoffs behind that work.

#### In-memory tables and lock-free skip lists

I led the design and implementation of in-memory tables, including a lock-free concurrent skip list in C and its integration into the storage engine.

The presentation explores the choice of skip lists for ordered access, concurrent updates using compare-and-swap, forward and reverse iteration, and safe memory reclamation.

[View slides: Lock-free Skip Lists](https://docs.google.com/presentation/d/1bN308K7j9VaCzgTlQkGLNMwPgYfHWRM6XADKjD_nxWk/edit)

#### Aggregation, sorting, and memory management

I worked on improving aggregation (group by) and ordering operations (order by) for speed and memory efficiency.

This presentation explains the query-scoped “sigma” containers used for sorting, grouping, and distinct operations. It covers hash-based accumulation, fallback to disk-backed B-trees, memory budgeting across concurrent containers, and top-k processing that avoids sorting an entire result set.

[View slides: Sigma Containers](https://docs.google.com/presentation/d/1KM2_yQjuagmBiAu6PUjIT8ep36--1lP51d3tnFUAU-c/edit)

#### Cluster membership and adapting to AWS

I adapted Clustrix’s broadcast-based group-membership protocol for operation in AWS, critical for making our cloud offering possible.

This presentation explains heartbeats, membership states, quorum formation, membership changes, and leader failover. It also describes the explicit peer-address mechanism used to simulate broadcast for AWS deployments.

[View slides: Group Membership Protocol](https://docs.google.com/presentation/d/1XXHhrJOvO_HOl4r-PiqO5QaWRJwn1XW6utdEqbWgKnQ/edit)
