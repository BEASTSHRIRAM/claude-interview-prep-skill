# System Design Reference

## How to Approach Any System Design Question

**Step 1 -- Clarify Requirements (5 minutes)**
- Functional requirements: what the system should do
- Non-functional requirements: scale, latency, availability, consistency
- Ask: How many users? Read-heavy or write-heavy? Any specific SLA?

**Step 2 -- Estimate Scale (3 minutes)**
- Daily Active Users (DAU)
- Requests per second = DAU x requests per user per day / 86400
- Storage: messages per day x average size x retention period
- Bandwidth: requests per second x average payload size

**Step 3 -- Define API**
- Sketch the core REST endpoints the system exposes
- Example for URL shortener: POST /shorten {long_url}, GET /{short_code}

**Step 4 -- High Level Design**
Draw the major components and how data flows between them:
Client -> Load Balancer -> Application Servers -> Database / Cache / Message Queue

**Step 5 -- Deep Dive into One Component**
Your interviewer will guide this. Be ready to go deep on: database schema, caching strategy, consistency model, fault tolerance.

**Step 6 -- Discuss Tradeoffs**
Every design decision has a cost. Be explicit: "I chose SQL here for strong consistency, but if write throughput becomes a bottleneck, we can switch to NoSQL or add a write buffer."

---

## Key Concepts

### Load Balancing
Distributes incoming traffic across multiple servers.
- Round Robin: requests go to servers in rotation
- Least Connections: send to server with fewest active connections
- Consistent Hashing: maps requests to servers in a way that minimizes remapping when servers are added or removed

### Caching
Stores frequently accessed data in fast memory to reduce database load and latency.

**Cache Strategies**
- Cache Aside (Lazy Loading): application checks cache first, fetches from DB on miss, writes to cache
- Write Through: write to cache and DB simultaneously
- Write Back (Write Behind): write to cache immediately, write to DB asynchronously

**Cache Eviction Policies**: LRU (most common), LFU, FIFO

**Cache Invalidation Problem**: how to keep cache in sync with DB. Hardest problem in caching.

Popular tools: Redis, Memcached

### Databases

**Sharding**: horizontal partitioning of data across multiple databases.
- Range-based: split by range of key values
- Hash-based: hash the key to determine shard
- Directory-based: lookup service maps key to shard

**Replication**: copy data to multiple nodes for availability and read scaling.
- Master-Slave: writes go to master, reads from slaves
- Master-Master: writes go to either, more complex conflict resolution

### Message Queues
Decouple producers and consumers. Allow async processing.
Use for: notifications, order processing, event-driven architectures, buffering spikes.
Tools: Kafka (high throughput, log-based), RabbitMQ (flexible routing)

### Content Delivery Network (CDN)
Caches static assets (images, CSS, JS, videos) at edge servers geographically close to users.
Reduces latency for global users. Reduces origin server load.

### Rate Limiting
Prevents abuse and protects servers from overload.
- Token Bucket: tokens accumulate at a rate, each request consumes a token
- Leaky Bucket: requests enter a fixed-size queue, processed at a constant rate
- Fixed Window Counter: count requests in a fixed time window
- Sliding Window: more accurate, avoids boundary issues of fixed window

---

## Case Studies

### URL Shortener (bit.ly)
Core challenge: generate short unique codes, redirect to long URL at high speed.
- Hash function (MD5/SHA256) + take first 7 chars, handle collision
- Database: KV store like Redis or DynamoDB for mapping
- Read-heavy: cache popular short URLs aggressively
- Custom short codes: check availability before storing

### Twitter Feed
Core challenge: fan-out on write vs fan-out on read.
- Fan-out on write: when user tweets, push to all followers' feeds immediately (good for users with few followers)
- Fan-out on read: when user opens app, pull tweets from followed accounts (good for celebrities)
- Hybrid: push for regular users, pull for celebrities
- Timeline stored in Redis sorted set (by timestamp)

### WhatsApp / Chat System
- WebSockets for real-time bidirectional communication
- Message storage: one-to-one (simple table), group (fan-out problem)
- Presence (online/offline): heartbeat mechanism
- Message ordering: Lamport timestamps or vector clocks

### Ride-Sharing (Uber)
- Location updates: drivers send GPS every few seconds
- Matching: geospatial indexing (QuadTree, Google S2) to find nearby drivers
- Pricing: surge based on demand/supply ratio
- Consistency: booking must be atomic (no double booking)

---

## Low Level Design (LLD)

LLD focuses on class diagrams, design patterns, and object-oriented modeling.
Common LLD problems:
- Design a Parking Lot
- Design an Elevator System
- Design a Chess Game
- Design an ATM
- Design a Library Management System
- Design a Hotel Booking System

**LLD Approach**
1. Identify entities (objects)
2. Define their attributes and relationships
3. Identify behaviours (methods)
4. Apply SOLID principles and relevant design patterns
5. Handle edge cases and constraints

---

## CAP Theorem

A distributed system can guarantee at most two of:
- **Consistency**: every read gets the most recent write
- **Availability**: every request gets a (non-error) response
- **Partition Tolerance**: system continues despite network partitions

In reality, partition tolerance is non-negotiable in distributed systems. So the choice is between CP and AP.
- CP systems: HBase, Zookeeper (sacrifice availability under partition)
- AP systems: Cassandra, DynamoDB, CouchDB (sacrifice consistency, use eventual consistency)
