---
marp: true
theme: internal
---

# Intro to Nostr

<!-- <br /><br /><br /><br /><br /><br /><br /><br /><br /> -->

---

# What is Nostr?

* Notes and other stuff transmitted by relays.
<!--
  The first conceptual use-case was for a decentralized social media feed.
  "Notes" are analogous to tweets or posts.
  The protocol is flexible enough to support many other use-cases i.e "other stuff".
-->
* Nostr is a message protocol built on websockets.
<!--
  We will build up an understanding of what a protocol is.
  We'll also talk about websockets (and why they're great).
-->
* Nostr uses dumb servers to relay and store data.
<!-- 
  "dumb" meaning that most protocol / application logic is client-side.
  We will break down what that means, plus we'll define the terms server and relay.
-->
* Nostr implements modern cryptography in a simple and powerful way.
<!-- 
  We'll cover hashing, digital signatures and public key cryptograhy.
  Don't worry: You don't have to understand any math, just the basic principles.
  Modern crypto libraries are suprisingly user friendly.
  Plus, we have great examples of how to use them.
-->

---

# What is a Protocol?
<!-- The way I like to think about it. -->
* It's a defined language that computers speak to understand each other.
<!--
  When you're having a conversation with someone, you both follow certain rules like grammar and sentence structure to ensure you understand each other. Similarly, protocols are the "language" that computers and devices use to communicate over the internet.
  They allow computers to talk to each other and share information.
-->
* Protocols allow us to make connections and build bridges.
<!--
  * Analogy: Imagine walking through a chaotic maze of moving paths.
    If the movement is based on a set of rules, then you can use those rules to navigate.
  * Allow information to navigate across a wide network of unreliable peers.
    (low-level network protocols are engineering at its finest)
  * They help developers build shared experiences across different technologies.
    - Check your email from many devices.
    - Chat with friends from different platforms.
  Just like we need language in order to build a rich society, we need protocols in order to build a feature-rich world-wide web.
-->
* Protocols have layers.
<!--
  Similar to how languages evolve in order to explain more complex concepts.
  New protocols stack in layers, with each layer building upon the last.
-->
* Protocols can change! (but solidify over time)
<!--
  * Newer protocols will experience rapid revisions or updates to improve them.
  * As a protocol becomes widely adopted, changes become more difficult and less frequent.
  * One clear example of this is IPv4 versus IPv6.
  * Nostr is a new protocol, so we are still in the "move fast and break things* stage.
-->

---

# Web Protocol Stack

  <!-- We are not going to dive into these protocols, just demystify them. -->

  * IP (Internet Protocol): Address and route packets of data across a wide network of peers.
  <!-- There's no place like 127.0.0.1 -->
  * TCP (Transmission Control Protocol): Create a peer-to-peer connection over a network, then deliver data packets intact and in proper order.
  <!-- The grandfather of peer-to-peer protocols -->
  * HTTP (HyperText Transport Protocol): Request data resources from a peer (server), and receive a response.
  <!-- The vast majority of the web runs on HTTP -->
  * WS (Websockets): Uses HTTP to establish a real-time, bi-directional data transfer between client and server, with minimal overhead.
  <!-- Unpack "bi-directional" and data streams in relation to HTTP request/response open/close. -->

---

# The Peer Discovery Problem

* We don't have enough IP (v4) addresses for everyone.
<!-- 
  * IPv4 has solidified as a standard, which has a limit of 4 billion addresses (2^32).
  * We didn't expect the internet to become so big, so fast.
  * IPv6 solves this (2^128), but has limited adoption, as everyone uses IPv4 now.
-->
* The interim solution has been to nest private networks behind a single IP (NAT).
<!--
  * NAT stands for Network Address Translation.
  * It's used to share a single public IP among an entire private network.
  * The device with the public IP serves as a gateway to the private network.
-->
* Clients behind private networks are not publicly reachable.
<!--
  * Your IP address only exists within the private network.
  * You rely on the gateway device to act as a translator.
  * Gateways are restricted and policed differently by every provider.
  * There are many protocols that *try* to tackle this problem (UPnP, STUN, TURN, ICE).
-->
* The simplest way to connect is to rendevous at a public server.
<!-- 
  * Traversal Using Relays around NAT.
  * The simplest approach, but requires using a public server as an intermediary.
-->

---

# The Censorship Problem

* Public servers help us find and connect with other peers.
<!--
  * Even peers stuck behind a private network can find each other.
  * Servers can be purpose-built to handle many inbound connections.
-->
* They also help us establish a digital identity.
<!--
  * Connect from any machine, perform a challenge to authenticate.
  * Allows our identity to be device agnostic.
-->
* Servers have complete control over the flow of information.
<!-- These platforms are ruled by rulers, who rule over you. -->
* They also have control over your digital identity.

---

# Examples of Client / Server Model

* Centralized: (Facebook, Twitter, Discord, Signal)

* Federated: (Mastadon, Matrix, IRC, Email)

* Decentralized: (Tor, Jabber, Bitmessage, DIDs)

---

# Key Features of Nostr

* Uses websockets.
* Dumb servers, smart clients.
* Total ownership of your identity.
* Censorship resistance (broadcast to many relays).

<!--
  * Event-driven protocols are a natural way to develop applications on the web.
  * Full-custody of your identity is a new paradigm. It is what makes nostr powerful.
  * Biggest problem with p2p networks is that nobody wants to run a server. Dumb servers lower the barrier of entry.
  * If running a relay server is easy, then you have an abundance of relays, making censorship difficult to impossible.
-->

---

# Examples of Decentralized Apps

* Social Media (now with Zaps!)
  <!-- Damus, Amethyst, Iris, Snort -->
* Messaging / Chat
  <!-- Anigma, NostrChat, Vidya Live -->
* Search / Analytics
  <!-- Nostr.band, Zaplife.lol -->
* Marketplace / Ecommerce
  <!-- NostrMarket, Super Store  -->
* Machine-to-Machine Interface.
  <!-- NostrConnect, NostrEmitter -->

---

# Downsides

* Still very early.
* Lack of monetary incentive to run / maintain relays.
* Spam is still an issue.
* User experience may change considerably between relays.
* Decentralized development of standards is a mess.

---

# Criticisms

* Scalability.
* Identity recovery.
* Resistance to attacks.
* Inefficiency (a.k.a the firehose).
* Relays are "too" dumb (do not share/replicate data).

---

# Why Nostr?

- Very simple, opinionated, and fun to build with.
- Relays are light-weight and ubiquitous.
- Peering works natively within the browser.
- Digital identity and signatures are baked in.

<!--
  * Not bogged down by complex standards. The core spec (NIP 1) is all you need to get started.
  * Even if all other relays fail or disappear, you can just run your own.
  * You can build very powerful client-side applications in the browser.
  * Zero user management requred. All clients establish their own identity.
-->

---

# Review

* What Nostr is.
* What a protocol is.
* Problems with Peer Discovery and censorship.
* Advantages and Disadvantages of Nostr.
* Examples of applications using Nostr.
* Reasons to build on Nostr.

---

# Next : Intro to Nostr Development
