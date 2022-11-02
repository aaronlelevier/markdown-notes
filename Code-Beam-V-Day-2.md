# Code Beam V - Day 2

## Keynote: JIT Compiler for Erlang/OTP

**Compiled Languages**

What does the compiler do?
Parse code -> Optimize -> Emit Native -> Run Native

BEAM code can't be compiled on one OS or hardware and run on a diff b/c it's Native code

A lot more Native languages since the release of LLVM

**Interpreted languages**

Parse code -> Optimize -> Op codes -> Run

**JIT - Just in time compiling**

Does the Interpreted lang steps first then Compile lang steps

`BeamAsm` - BEAM JIT

## Update: Elixir Core Dev Team

Erlang interop

## Mnesia as a complete production database system

Started with

mnesia_frag

Karna - rocksdb

Progression with Mnesia with the speaker:

1. Mnesia (in memory) / MySQL 

Benefits

- Erlang native
- small - medium works good
- VMs or Servers are memory optimized

QoS Network ?

When not to use:

- consumers are not Erlang native
- large systems
- Nodes aren't optimized for memory
- Low QoS (Quality of Service) aka Networking I/O is slow

[tivan](https://github.com/arknode-io/tivan) - Mnesia wrapper ORM

- interesting use of `maps` for function signatures
- uses a item or single item tuple to give different meaning to arguments

Syntax `#{ Key := Value, Key2 => Value2}`

- first Key/Value is required
- second is not

**Q & A**

*Are start up times slow?*

Yes, but we split the DB and use this pattern to have smaller Mnesia instances

*Have you had network issues with Mnesia?*

If network is good, no

## Boost your productivity with the Erlang Language Server

by Roberto Aloi on Erlang-LS

Erlang `xref` used to find callers

L.S.P - Language Server Protocol

### Erlang-LS Deep Dive

Each Feature is a Provider (a registered process)

- benefit is if bug in a Feature or misbehaving client, it will crash on it's own and not affect other Features

Background jobs exist

Erlang AST - used for jump + jump-back functions

`els_dodger` fork of the [epp_dodger](http://erlang.org/doc/man/epp_dodger.html) to inspect Erlang AST and where a code definition is used

**Idea**

LSP to support people code pairing or in an interview if developers are on differnt machines and communicating with the same LS

## A Beginner's Guide to TLA+: Exploring State Machines & Proving Correctness

TLA+ doesn't test the code, it tests the spec and properties

Invariants - inital parameters that don't change

Temporal - change state during the program

## Four patterns to save your codebase and your sanity

4 Patterns to save the code base

1. Handlers
2. Services
3. Finders
4. Values

Scaling pains

- codebase structure scalability
- logic dfintion styleguids and contracts
- continuous refactoring
- tech debt slows dow interation speed

SOLID Principals - use for easier to maintain code

**Handlers**

Do 

- buisiness logic
- orchestrate high leveloperations
- commands to Service, Finders, Values

Don't

- modify data (directly)

**Services**

organized by application logic

have a single pupose

Do read/write operations

ex: a `User` service performs CRUD commands on `users`

**Finders**

Like Services, but focused Read operations

**Values**

These are business values

Objects of type list or map

composable - we can build a value by chaining multiple Value builders

## Adventures in High Performance Logging

Different ways of high performance logging

**Kinesis Agent**

Logger Module in Elixir logs to a log-file -> Kinesis

Q: What happes to Elixir logger when overflowed? 

A: The whole app will be slowed down b/c the logger enters sync-mode

`disk_log`

- can handle 100k writes per second
- have to do an app restart to release the File Handler in the case of a `log.rotate`

**Kinesis API**

Tried writing directly to the Kinesis API

Used [ExAWS](https://github.com/ex-aws/ex_aws) to interact with AWS using Elixir

**Hydrant -> Firehose**

## Keynote: Software for one. Ideas for all

by Chris Keathley - works at

speaker had 2 goals

1. send people to space
2. make video games - tried in c++

How to innovate

- Get a hammock and think a lot
- try new stuff
  - Eiffel
  - Haskell
- share the ideas with other people

Read more of other people's code

Libraries published (in Elixir)

- Norm - 
- Vapor - confirms start state
- Groot - feature flag library