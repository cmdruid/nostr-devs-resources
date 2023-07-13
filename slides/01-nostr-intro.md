---
marp: true
theme: internal
---

# Intro to Nostr

---

# What is Nostr?

* Notes and other stuff transmitted by relays.
<!--
  A note is a data record in JSON format, with a digital signature.
  The first conceptual use-case was for a decentralized social media feed.
  Kind 1 notes are analogous to tweets or posts.
  Kind 0 notes are used for storing data under a public key.
  The protocol can support many other kinds of notes i.e "other stuff".
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


# The Peer Discovery Problem

* We don't have enough IP (v4) addresses for everyone.
<!-- 
  * IPv4 has solidified as a standard, which has a limit of 4 billion addresses (2^32).
  * We didn't expect the internet to become so big, so fast.
  * IPv6 solves this (2^128), but has limited adoption, as everyone uses IPv4 now.
-->
* Clients behind private networks are not publicly reachable.
<!--
  * Your IP address only exists within the private network.
  * You rely on the gateway device to act as a translator.
  * Gateways are restricted and policed differently by every provider.
  * There are many protocols that *try* to tackle this problem (UPnP, STUN, TURN, ICE).
-->
* The simplest way to connect is to rendevous on a public server.
<!-- 
  * Traversal Using Relays around NAT.
  * The simplest approach, but requires using a public server as an intermediary.
-->
* Almost all application protocols use a client / server model.
<!--
  * NAT stands for Network Address Translation.
  * It's used to share a single public IP among an entire private network.
  * The device with the public IP serves as a gateway to the private network.
-->

---

# Pros and Cons 

[ + ] Public servers help us find and connect with other peers.
<!--
  * Even peers stuck behind a private network can find each other.
  * Servers can be purpose-built to handle many inbound connections.
-->
[ + ] They establish our digital identity across multiple devices.
<!--
  * Connect from any machine, perform a challenge to authenticate.
  * Allows our identity to be device agnostic.
-->
[ - ] They can have complete control over your information.
<!-- These platforms are ruled by rulers, who rule over you. -->
[ - ] They can have complete control over your digital identity.

---

# Protocol Examples

* Centralized: (Facebook, Twitter, Discord, Signal)

* Federated: (Mastadon, Matrix, IRC, Email)

* Decentralized: (Tor, Jabber, DIDs)

---

# Key Features of Nostr

* Servers are simple and have very little control.
* Clients have complete ownership of their identity.
* Uses websockets (which work in the browser).
* The core protocol is simple and easy to use.

<!--
  * Event-driven protocols are a natural way to develop applications on the web.
  * Full-custody of your identity is a new paradigm. It is what makes nostr powerful.
  * Biggest problem with p2p networks is that nobody wants to run a server. Dumb servers lower the barrier of entry.
  * If running a relay server is easy, then you have an abundance of relays, making censorship difficult to impossible.
-->

---

# Examples of Decentralized Apps

* Social Media (with micro-payments)
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

# BREAK

<!-- 
 * Check out different websites
 *

-->

---

# Criticisms

* Scalability.
* Identity recovery.
* Resistance to attacks.
* Still very early.

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

# Next : Intro to Nostr Development
