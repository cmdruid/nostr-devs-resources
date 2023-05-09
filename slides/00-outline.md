---
marp: true
---

# What is Nostr?

- Notes and other stuff transmitted by relays.

<!--
  Silly name. Sort-of sets the tone that this is not meant to be a seriously complicated protocol.
-->

- It is an event-based message protocol.

<!--
  Event-based. Uses a publish / subscribe method of passing around messages.
  
  One-to-many can publish to a feed. One-to-many people can subscribe to a feed. (unpack this further?)
-->

- It uses "dumb" servers to store and relay data.

<!--
  Servers implement a very basic protocol for subscribing to events. Most protocol / application logic is client-side.
-->

- It uses modern cryptography, but in a simple way.

<!--
  Simple document attestation. We take a document, convert it to a hash, then sign it with our secret key.
  
  We publish the document along with our signature. Other clients verify our signature is correct.
-->

## Why Nostr?

- Other protocols suck (no adoption, difficult to use, bogged down by standards).
- Built by builders, for builders.
- Protocol is very simple, opinionated, and easy to use.
- Protocol sticks to doing one simple thing and doing it well.

## What is a Protocol?

<!--
  Definition of protocol that includes API (both local and network).
  Maybe provide examples?
  Useful definition of API explained.

-->

## Other Protocols

- Centralized (Twitter, Facebook, Signal)
- Federated (Mastadon, Matrix, IRC, Email)
- Decentralized (Jabber, Scuttlebutt, Bitmessage, DIDs)

<!-- 
  Honorable mention to Kafka (which doesn't handle identity)
-->

## Key Features of Nostr

- Event-driven.
- Uses websockets.
- You own your identity.
- Dumb servers, smart clients.
- Censorship resistance (broadcast to many relays)

<!--
  Explain websockets
-->

## Downsides

- Still very early.
- Lack of monetary incentive to run / maintain relays.
- User experience may change between relays.
- Development of standards is still messy.

## Criticisms

- Scalability.
- Identity recovery.
- Inefficiency (duplicating data). aka the firehose.
- Relays are "too" dumb (do not share data).

# What is a Nostr Note

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

## Digital Signatures

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

# What is a subscription

Example of a filter and subscription.

## Example of a Subscription

```json
{}
```

# What is a relay?

- A relay is a webserver that stores notes and delivers subscriptions.
- Relays use websockets.

## What are websockets?

Websockets are long-lived HTTP connections.
HTTP traditionally uses a request-response model, which requires negotiating a new connection each time.

## Relay Protocol
- REQ (subid, filter)
- EVENT (event)
- OK (eventid, status, msg?)
- NOTICE (msg)

## Example of a websocket call

```js

```

## Review

<!--
  Review first slide and what we learned.
-->