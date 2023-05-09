---
marp: true
---

# What is Nostr?

- Notes and other stuff transmitted by relays.

- It is a message protocol built on websockets.

- It uses "dumb" servers to store and relay data.
<!-- Most protocol / application logic is client-side. -->

- It uses modern cryptography in a simple and powerful way.
<!-- Users own their identity, all messages are signed. -->

---

# What is a Protocol?

- It is a defined language that computers speak to understand each other.

<!--
  When you're having a conversation with someone, you both follow certain rules like grammar and sentence structure to ensure you understand each other. Similarly, protocols are the "language" that computers and devices use to communicate over the internet.
-->

- Protocols help us make connections and build bridges.

<!-- 
  * They allow computers to navigate across a wide network of peers.
  * They allow computers to talk to each other and share information.
  * Makes it easier for developers to create applications and games.
  * They act as a bridge between different technologies, helping them work together.

  Just like we need language in order to build a rich society, we need protocols in order to build a world-wide web.
-->

- Protocols can have layers. (TCP/IP/HTTP/WS/Nostr)

<!--
  Similar to how language can have different layers that build on top of one another.

  As engineers, we try to solve the most obvious problem in front of us, and make our solution robust, so that others may build on top of our work.

  Protocols evolve in a similar fashion, with each layer solving a more complex problem.

  > We are not going to dive into these protocols, just demystify them.

  TCP/HTTP/WS stack. (make this brief, but focus on websockets)

  * TCP focuses on establishing a connection over a network, then delivering packets of data intact and in proper order.

  * IP is responsible for addressing and routing packets between peers, over a network of relays.

  * HTTP focuses on request and delivery of messages with content. Most of the web runs on HTTP.

  * Websockets refine HTTP to handle real-time, bi-directional data transfer with minimal overhead.

  > Unpack "bi-directional" and data streams in relation to HTTP request/response open/close.
-->

- Protocols can change! (but solidify over time)

<!--
  * New protocls undergo rapid revisions or updates to improve their scalability and security.
  * As they become widely adopted, changes to these protocols become more difficult and less frequent.
  * Nostr is a new protocol, so we are in the "move fast and break things* stage.
-->

---

# The Peer Discovery Problem

- We don't have enough IP (v4) addresses for everyone.
<!-- 
  * IPv4 has solidified as a standard, which has a limit of 4 billion addresses (2^32).
  * We didn't expect the internet to become so big.
-->
- The interim solution was to nest another network behind a single IP (NAT).
<!--
  * NAT stands for Network Address Translation.
  * NAT devices are commonly used to share a single public IP address among multiple devices on a private network.
  * IPv6 solves this (2^128), but has limited adoption, as everyone uses IPv4 now.
-->
- Clients behind nested networks are very difficult to reach.
<!--
  * Since your IP address only exists within the private network, there's no public way to reach you directly.
  * You rely on the gateway to act as a translator.
  * NAT is restricted and handled differently by every network provider.
  * AKA NAT traversal / NAT hole-punching problem.
  * There are many protocols built just for tackling this problem (UPnP, STUN, TURN, ICE).
-->
- The simplest way to peer is to rendevous at a public server (TURN).
<!-- 
  * Traversal Using Relays around NAT.
  * It is the simplest approach, but requires a public server as an intermediary.
  * 
-->

---

# The Internet Censorship Problem

+ Public platforms help us find and connect with other peers.

+ They also help us establish a digital identity.

<!--
  * Helps us connect from any machine
  * Allows our identity to be device agnostic 
-->

- They control the flow of information.
<!-- These platforms are ruled by rulers, who rule over you. -->

- They also control your digital identity.

---

# Other Peering Platforms

- Centralized (Twitter, Facebook, Signal)
- Federated (Mastadon, Matrix, IRC, Email)
- Decentralized (Tor, Jabber, Bitmessage, DIDs)

---

## Key Features of Nostr

- Uses websockets natively.
- You own your identity.
- Dumb servers, smart clients.
- Censorship resistance (broadcast to many relays)

<!--
  * Websockets allow event-driven communication, which is a very natural and flexible way to develop application protocols.
  * Self-custody of your identity is a brand new paradigm and a game-changer for internet freedom. It is what separates nostr from the rest.
  * The biggest problem with p2p networks is that every client needs a relay server to communicate (NAT traversal problem), and nobody wants to run a server. Dumb servers fix this by lowering the barrier of entry.
  * If running a server is easy, then you have many options to communicate, making censorship increasingly difficult to impossible.
-->

---

# Examples of Decentralized Apps

- Social Media (now with Zaps!)
- Messaging / Chat
- Search / Analytics
- Marketplace / Commerce
- Machine-to-Machine interface.

---

## Downsides

- Still very early.
- Lack of monetary incentive to run / maintain relays.
- User experience may change between relays.
- Decentralized development of standards is a mess.

---

## Criticisms

- Scalability.
- Identity recovery.
- Inefficiency. (duplicated data/filters a.k.a the firehose)
- Relays are "too" dumb (do not share/replicate data).

---

## Why Nostr?

- Very simple, opinionated, and fun to use.
- Relays are light-weight and ubiquitous.
- Peering works natively within the browser.
- Digital identity and signatures are baked in.

<!--
  * No adoption, difficult to use, run by gate-keepers, running your own server is painful, central points of failure.
  * Not bogged down by standards or designed by comittee.
  * The core spec (NIP 1) is all you need to get started.
  * Zero user management requred. All clients establish their own identity.
-->
---
# What is a Nostr Note

---

## Nostr Note

```js
{
  id        :
  timestamp :
  content   :
  tags      :
  pubkey    :
  signature :
}
```

---

## Digital Signatures

---

## Note Identifier
```js
let id = [
  0,                    // Future version number.
  event['pubkey'],      // Pubkey of the author.
  event['created_at'],  // Unix timestamp of the note.
  event['kind'],        // The 'kind' or type of note.
  event['tags'],        // Metadata tags for the note.
  event['content'],     // Content of the note.
]

id = JSON.stringify(id) // Convert JSON to string.
id = strToBytes(id)     // Convert string to bytes.
id = sha256(id)         // Hash bytes using sha256.
id = bytesToHex(id)     // Convert bytes to hex.
```

<!--
  
-->

---

# What is a subscription

Example of a filter and subscription.

---

## Example of a Subscription

```json
{}
```

---

# What is a relay?

- A relay is a webserver that stores notes and delivers subscriptions.
- Relays use websockets.

---

## What are websockets?

Websockets are long-lived HTTP connections.
HTTP traditionally uses a request-response model, which requires negotiating a new connection each time.

---

## Relay Protocol
- REQ (subid, filter)
- EVENT (event)
- OK (eventid, status, msg?)
- NOTICE (msg)

---

## Example of a websocket call

```js

```

---

## Review

<!--
  Review first slide and what we learned.
-->

---