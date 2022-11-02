# Code Beam V - Day 1

## Keynote

follow research results

learn algorithms, ex:

- create pairs
- pairs in a graph
- ordering of sending config is a topological sort of a graph

Viktoria Fordos - speaker of the above

## OTP Team update



## Languages that run on top of the BEAM

[Leex](https://erlang.org/doc/man/leex.html) - Erlang Lexical Tokenizer

[Yecc](https://erlang.org/doc/man/yecc.html) - Erlang Parsing Tokenizer



## Object Detection with Phoenix and Python

Webcam.js sends 

Code examples [here](https://www.poeticoding.com/)



## Rewriting a simple Web App in Phoenix and Elixir

DNS Management tool rewrite

PostgreSQL

- has a simple PubSub for coordinating changes

Developer pain - from upgrading both Drupal and EmberJs because upgrades required near rewrites, so changed frameworks

Downsides from current technologies

- few learning opportunities
- frameworks not growing

**FUN** - passion projects must be fun, or else you're not motivated!

Framework pieces used:

- Phoenix
- Phoenix LiveView
- Ecto
- [Oban](https://github.com/sorentwo/oban) - robust job processing in Elixir backed by PostgreSQL



## Decade of writing and selling Erlang based Flussonic

Validation of inter-application communication

- write some declarative validation code that the communication follows the interface



## From the idea to a MVP in less than 3 months

How will the app interact with the external world

Full Erlang?

Isolate the concerts, contain the problems

Dependencies

erlang.mk or rebar3?

**Recommendations**

start simple

keep state in an Erlang process - could be supervised or not

wanto to handle state changes -> use `gen_statem`

use `ets` to share data in memory

use the Erlang distribution to talk between different nodes (at the start)

- opposed to Kubernetes and Docker to start

booting a distributed application may be complicated

- start app, then receive a msg to join a Node
- or, ping Node until available to join

Logging

- `disk_log`
- `gen_persist`

Use `mnesia` - does call a lot of network i/o from communicating nodes

**Common Test**

For regression testing and testing some scenario 

quickcheck or properl 

lta+

## From 10s to 1000s engineers: scaling Erlang developer experience at WhatsApp

Highly available

Scalable network services

Leveraging the BEAM

Stateful services

high-level declarative language

fast compilation

fast deploys - several minutes to hot reload

**During startup years**

Critical - reliability of service

Less important - code style

**What we learned at scale**

developer productivity becomes critical

- errors should be found at compile time, not CI

**Does Erlang scale for larger teams?**

make code easy to navigate

incremental changes

refactor code reliability

Limitations

- no static typing
- flat namespace for records and modules
- lack of we integrated tooling - IdE integration, formatter, build system, ...

**Static typing goals**

- high productivity
- feasible

## A war story - from failures to success

by Timmo Verlaan

When doing a rewrite, all existing features should still work, and new features are allowed to have bugs, because this is what the Users expect

Load tested - all the main flows

2019 - one Node stopped working

Also had locking between 2 processes - resulting in a deadlock

- we had to find out why this happens
- if no one knows the whole codebase, then they can't reason about this situation

2019 - still had intermitten failure of a Node due to DB locking

- this was due to some edge cases in [Ecto](https://github.com/elixir-ecto/ecto)
- a DB connection library (in house) was also involved

Switched from PostgreSQL to MySQL

- wasn't using any DB specific features - so made migrating a lot easier

Late 2019 - found some DB bottlenecks

- this was solved by debugging the DB performance and making Query or Index changes on the DB

How did you solve the "knowledge holder" problem?

- force the knowledge holder to pair code with someone else - but then there can also be issues that the knowledge holder wants to solve
- from Timmo's perspective it's about enabling others that want to learn and do what the knowledge holder does
- grow the team, or change the team dynamic forces this
- code reviews

## KEYNOTE: Using the BEAM to fight COVID-19

HCA Healthcare talk by Bryan Hunter

**Dev Joy**

Fun to develop code

**Biz Joy**

Deliver business faster

**Ops Joy**

Systems are working

### Project Waterpark

Each of these pieces are implemented in a minimal way for what the business needs:

- Integration engine
- Streaming system
- Distributed database
- CDN
- FaaS
- Complex event processor
- Queue
- Cache

Business Domain

- admit, discharge, transfer
- order entry
- observation results
- scheduling
- etc...

Long lived twins - have a twin process in case your process goes down

**Modeling the real world** 

a patient in the real world is modeled as a patient actor (gen_server) in the Erlang world

patient actors 

- sleep if inactive and can be resotored
- get evicted if do some outlier behavior

No unplanned outages - fault tolerant

No planned outages - can't have downtime for patching, etc...

To do this, we can have no master, aka no single point of failure

[Basho](https://en.wikipedia.org/wiki/Basho_Technologies)

Riak

Paxus

Raft

The process error example showed A <--> B and how the two process are linked, so they are "process pairs"

Project Waterpark doesn't use a database

**Where to put distributed code**

Segment the distributed portions of the code to specific modules that only do that

**Events**

Event handlers - handler specific events and route them to the Patient Actors

Bounded session windowing is used on the Event Stream

Use "exactly once" processing

Bloom Filters?

**Changing the system for Long Term Care (LTC) Patients**

Use combined

**Deployment**

Use Erlang Distillery



