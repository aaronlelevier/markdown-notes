# Programming notes circa 2017

## Airline Notes

Lufthansa 3 KPI's

1. maximize revenue
2. minimize cost
3. maximize customer satisfaction

Data Types

- internal

	- revenue
	- reservations
	- schedule

- external

	- social media
	- web
	- market info
	- competitive

Lufthansa Data exampls

- pricing
- schedule
- route
- airplane mode
- customer segment

Good data set

Great analytics platform on top of data set

real time data

## Troubleshoot Linux server commands

`ifconfig` - diff on Mac and Linux

`ping` Packet Internet Grouper

- icmp_seq - packet sequence number
- ttl - time between hops - but not direct correlation, higher more time
- time - time til response per ping, should be under .5 sec

`traceroute` - sends (3) packets to a specified IP and shows their journey

- will show the hop #
- server name
- server IP
- timer per packet (sends 3 packets) - so can get an idea of the avg time

datagram - basic transfer unit across a *packet-switched network*

- [https://en.wikipedia.org/wiki/Datagram](https://en.wikipedia.org/wiki/Datagram)
- has a header and payload, provides *connectionless payload*

packet-switching - the basic way data is transfered worldwide in computer networks; Header info is used to determin packet routing and transmit

http - hypertext transfer protocol

`netstat` - shows diff network statistics

- `-a` - all listening ports
- `-at` - all TCP listening ports
- `-au` - all UDP listening ports
- `-r` - routing table 

`route` - shows the routing table, same as `netstat -r`

UDP - User Datagram Protocol - `datagram` sent with header and payload. Not monitoring of the datagram is done after it's sent so low overhead but no delivery guarantee

TCP - Transmission Control Protocol - computer sending data connects to the computer receiving the data for the duration of the protocol, so it's known if the data arrives. Higher overhead b/c computers stay connected

MTU - Maximum Transmission Unit - max size of a packet that can be sent. Value is in Octets (8-digit bytes)

### netmask

broadcast address - IP for broadcasting - other computers can't connect to it

assigned addresses can't be used, for ex 255.255.255.0 / .255

`dig www.mydomain.com` - Does a DNS query, returns things like: A Record, CNAME, MX Record, IP addr

`nslookup` - same as dig but takes longer, and a little harder to read. Previously was deprecated in favor for `dig`, but now resurrected and still works

`inode` pointer to a Unix files system object - there is a max of these on a Unix OS and can max out unrelated to memory

`host www.mydomain.com` - showed the MX records of the domain arg

`ARP` - Address Resolution Protocol - shows map of IP addresses to physical machine addresses

### Check Memory Usage

`freem -m` - shows stats in MB, of system, usage, and free RAM

`top` - will show CPU and MEM usage, I think this is the one Chris used

`ps aux` - shows all processes, their % CPU, % Memory, command, owner

Big O / other growth curves


## Coding

### factorial 

the product of all numbers up to a given number

```python
def factorial(n):
    if n < 1:
        raise AssertionError("can't calculate if n < 1")
    if n == 1:
        return 1
    return n * factorial(n-1)
```

Above example is *Linear Recursive* because it makes 1 recursive call to itself

It is also *Tail Recursive* because the recursive call is the last thing that the function does

- tail recursive functions can be easily replaced with a `loop`

```
def factorial_while(n):
    i = 1
    while n > 1:
        i *= n
        n -=1
    return i
```

Above is the `while` loop implementation of a factorial

```
def factorial_for(n):
    x = 1
    for i in range(n):
        # add 1 b/c of 0 indexing on n
        x *= i+1 
    return x
```

For loop implementation of a factorial

## Math

arithmetic mean - mean, avg

reciprocol - for a number *x*, this is *1/x* or *x^-1*

harmonic mean - the recipricol of the arithmetic mean

- mean / sum(recipricol of each x)
- ex: for numbers: 1, 4, 4
- ((1+4+4)/3 numbers) / (1/1 + 1/4 + 1/4) == 3 / 1.5 == 2

ore number - a number with a *harmonic mean* of a whole number

## About Terada

started in 1979 by Caltech and Citibank joint effort

bought by NCR

Public company in 2007

10k employees

CEO - Victor Lund - since 2016, before was Michael Koehler - was CEO for 14 years

Headquarters is in Dayton, Ohio

Offices in Atlanta and San Diego

Initiall offering - data warehousing

Products

- business analytics
- cloud software
- consulting

## Logix

XOR - one if one, but not both, must be one or the other

## Bash

String slicing: 
```
arg=$1
echo "${arg:1:-1}"
```

## Python Coding Interviews

### Bitwise Operators

`mask` - data that is used for bitwise operations

```
def count_bits(x):
    num_bits = 0
    while x:
        num_bits += x & 1 
        x >>= 1
    return num_bits

count_bits(12)
```

Above counts the number of bits in the `int` "x" that are equal to **1**, which is a `mask`

`x >>= 1` - shift the bits to the right by 1 and update `x`'s value to that value, example of `shifting`

[https://wiki.python.org/moin/BitwiseOperators](https://wiki.python.org/moin/BitwiseOperators)

[https://wiki.python.org/moin/BitManipulation](https://wiki.python.org/moin/BitManipulation)

Looping over a numeric value means looping over it's bits, as in the above snippet

`signed number` - can represent positive and negative #'s

`unsigned number` - can only represent positive numbers, so 0 or 1<

`associative` - order of operations of doesn't affect the outcome as long as the operands remain in the same order

`commutative` - order of operands doesn't affect the outcome

If an equation has both `commutative` and `associative` properties, then it can to cacluated in parallel in any order and the outcome is the same


## Arrays

Retrieving items or updating an item in an Array takes constant time

Deleting / Inserting takes: size of Array - i'th position being acted on


## Strings

immutable - so `s = s[:1]` creates a new string `s`

appending from the front is slow


## Built-ins

`chr(int)` - Python conversion from `int` to a single character

`ord(str)` - Python conversion from a single unicode string character to an `int`


## General

### Python integer division

`int // int` - is integer division and returns the largest whole number from the division, so, for example:

```
21 // 10 == 2

19 // 10 == 1
```

innocuous - not harmful, innocent

### DNS

Domain Name Service - a decentalized service that maps domain names to IPs

### SNI

TLS Server Name Identification

- when a server initially identifies itself with a http handshake it can present multiple Certificates for the same IP and Port, so sites on the same IP and Port dont' have to share the same certificate

### Domain Fronting

Providing a different Domain during an HTTPS Handshake to connect then stating the actual Domain that the traffic is coming from. Works in a large hosting service if both are done by a large Provider, i.e. AWS. 

- So routing traffic through an uncensored Domain on the same Hosting service as your sensored Domain

### BGP

Border Gateway Protocol - a standardized routing protocol for routing between Internet Autonomous Systems

### Autonomous Systems

AS - A collection of IP addresses held by one or more network operators behind a single administrative facility

Has a clearly defined routing policy

AST - Autonoumous System Number - A unique number issued to each AS that's associated with it's BGP routing rules

### Proxy Server

A server (in the sense that this could be a computer or an application) that's used as an intermediary for requests between 2 other clients. 

- Provides anonymity
- Can be used to prevent IP blocking

### IP Spoofing

Creating Internet Protocol (IP) packets with a False or someone else's IP address

### RTT Performance

Round Trip Time Perf - Seems the same as TTFB - Time Til First Byte

- the measurement of time from a client request until the server sends the first package byte response

### TTFB

TTFB (Actual) - first actual byte response packet

TTFB (Perceived) - time til enough parsable http content has been received

- will be slightly longer than Actual TTFB

### CGN Deployment

Carrier Grade Network Deployment

- a carrier will have private network IPs that are mapped to public IPs as part of their network



## Dev Ops

`WfM` - Wired for Management - 

`NOC` - Network Operations Center

### PXE

pre-boot execution environment

- boots before the OS


### Content-Type

This field is a string header on a HTTP response telling the client the media type of the content

Some browsers do Content-Type sniffing and ignore the header


## Design Patterns

## Decorator

Requests are forwared to a wrapped object. The object can then be decorated with additional data by the wrapping class.

ex: decorating `requests` and adding the "auth headers" per the Session state

## Delegate

Similar to `Decorator` pattern except a reference of the wrapping classes is passed to the `Delegate` class and the wrapper instance state can then be used by the `Delegate` method invocation

trade off: doesn't work in call back frameworks in the sense that the `Delegate` doesn't have a reference to it's wrapping class

## yield

for reading a large set of values that only need to be read once

doesn't store the iterable in memory

first time a function with a yield is invoked, the function doesn't run

functions with a yield return a `generator` object

```
def my_generator():
    values = [4, 6, 8]
    print(values) # get's called only at 1st iteration

    for i, v in enumerate(values):
        yield v * i
```

expl: function body will be executed the first time the `generator` is iterated over, after that, the `for loop` runs until exhausted

once exhaused, if `next(generator)` is called again, it will raise a `StopIteration` error


## Metaclass

`class C: pass` is equivalent to `type('C', (), {})`

`type('name str', (bases,), dict())`

- name str - is the name of the class
- bases - is the inheritance hierarchy as an iterable
- dict() - is the key/value attr's to instantiate the class with


`dict(key=value, ...)` way of instantiating a `dict` without using the `{'str': value}` syntax

`exec` - way to execute Python code passed as a string


## CAIDA.org

`Internet Autonomous Systems` - As'es - autonomous internet system connections corresponding to ISP

### Visualizing Internet Topology in 2017

Used the Internet Topology Data Kit ITDK with `traceroute` to identify IP addresses, inferred routes and links

inferred routes identified using `bordermapit` a collab b/n UCSD and UPenn

### PHP

Template markup with control blocks and variables accessible

Can yield HTML in control blocks and `<?php .. ?>` doesn't have to be contiguous

### What Does Caida do?

Internet Stability and Security

- monitor outages
- monitor **route hijacking** - when an AS says that it provides a route or has a shorter path to a route than it acually does, could happen intentionally or by accident

Connectivity and Congestion - congestion can happen from ISP access practices or CDNs

Develops tools for detecting IP Spoofing

Tools for users to opt in and out of data sharing

Internet Topology - compatability, stability

Advancing development of new internet architecture



## Need to lookup

`tail`

async Python

systemd

Python for OS monitoring

