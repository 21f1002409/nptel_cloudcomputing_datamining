# 📚 Comprehensive Study Guide: Cloud Computing & Data Mining
### *Beginner-Friendly Notes with Practice Questions*
> **Course:** NPTEL – Cloud Computing & Data Mining  
> **Instructor:** Dr. Rajiv Misra, IIT Patna  
> **Prepared for:** Complete beginners who want to understand, not just memorize.

---

## 📋 Table of Contents
1. [Step 1 – Assignment Pattern Analysis](#step-1--assignment-pattern-analysis)
2. [Step 2 – Cloud Computing Notes & Practice](#step-2--cloud-computing-notes--practice)
3. [Step 3 – Data Mining Notes & Practice](#step-3--data-mining-notes--practice)

---

# Step 1 – Assignment Pattern Analysis

## 🔍 Summary of Question Patterns

After carefully reading through all 8 Cloud Computing assignments and all 8 Data Mining assignments, here is a clear picture of how your professor structures questions:

---

### Cloud Computing Assignments (Weeks 1–8)

| Pattern | Description |
|---|---|
| **Format** | All multiple-choice (MCQ) with 4 options (A/B/C/D) |
| **Question Type** | ~60% definition/concept-identification, ~30% scenario-based reasoning, ~10% algorithm mechanics |
| **Difficulty** | Beginner to intermediate; tests whether you understand *why*, not just *what* |
| **Favourite Topics** | Virtualization, leader election, distributed algorithms (Paxos, consensus), key-value stores, MapReduce, Spark, Kafka |
| **Tricky Style** | Often includes a "all EXCEPT" or "which is NOT true" question per assignment |
| **Justifications** | Every answer has a one-line justification — the professor wants you to understand reasoning |

**Key insight:** The CC assignments test your ability to *compare and contrast* (e.g., "How does Type 1 differ from Type 2 hypervisor?") and to *identify the right term for a described concept* (e.g., "What do you call the mechanism that buffers writes when a replica is down?").

---

### Data Mining Assignments (Weeks 1–8)

| Pattern | Description |
|---|---|
| **Format** | All multiple-choice (MCQ) with 4 options (A/B/C/D) |
| **Question Type** | ~40% definition/concept, ~40% numerical calculation, ~20% algorithm tracing |
| **Difficulty** | Heavier on math than CC; you must be comfortable computing support, confidence, entropy, distance, probability |
| **Favourite Topics** | Association rules (support/confidence), decision trees (entropy/information gain), Bayes theorem, KNN, SVM, ANN, K-Means clustering, regression |
| **Tricky Style** | Calculation questions where a table of transactions is given, and you must compute a metric; also "which is NOT true" |
| **Numerical Focus** | Weeks 2–8 all have at least 3–4 calculation questions with data tables |

**Key insight:** For DM, you *must* practice the calculations. The formulas for support, confidence, entropy, Bayes theorem, and Euclidean distance appear in nearly every assignment. Know them cold.

---

# Step 2 – Cloud Computing Notes & Practice

> **Reading guide:** For every topic, you'll see 📌 What it is, 💡 Why it matters, and 🌍 Real-world example.

---

## Week 1 – Introduction to Cloud Computing

### Topic 1: What is Cloud Computing?

📌 **What it is:**  
Cloud computing means renting computing power (servers, storage, software) over the internet instead of buying and maintaining your own hardware. Think of it like electricity — you don't build your own power plant; you just plug in and pay for what you use.

💡 **Why it matters:**  
It allows any person or company — from a solo developer to a massive enterprise — to access virtually unlimited computing resources without a huge upfront cost.

🌍 **Real-world example:**  
Netflix doesn't own all the servers that stream movies to 200 million users. They rent computing power from Amazon Web Services (AWS) and scale up or down as needed.

**Key Properties of Today's Clouds:**
- **Massive scale** – Millions of machines working together
- **On-demand access** – Get resources in minutes, not months
- **Data-intensive** – Clouds handle enormous amounts of data (videos, logs, transactions)
- **Virtualization** – One physical machine can pretend to be many virtual machines

---

### Topic 2: Cloud Service Models (SaaS, PaaS, IaaS)

📌 **What it is:**  
Three layers of "as-a-service" that describe *how much* of the cloud stack you manage yourself vs. what the provider manages.

| Model | Full Name | What you get | Who manages hardware? | Example |
|---|---|---|---|---|
| **IaaS** | Infrastructure as a Service | Virtual machines, storage, networking | Provider | AWS EC2, Google Compute |
| **PaaS** | Platform as a Service | A ready-to-deploy runtime + tools | Provider | Heroku, Google App Engine |
| **SaaS** | Software as a Service | A fully-built app in the browser | Provider | Gmail, Salesforce, Dropbox |

**Easy analogy:**
- **IaaS** = Renting a raw kitchen with appliances (you cook everything yourself)
- **PaaS** = Renting a catered kitchen that prepares ingredients for you (you just combine them)
- **SaaS** = Ordering food delivery (you just eat)

---

### Topic 3: What's New in Today's Clouds vs. Old Distributed Systems?

📌 **What it is:**  
Old distributed systems (1980s–90s) ran on a handful of machines in one lab. Today's clouds are fundamentally different:

| Old Systems | Today's Clouds |
|---|---|
| Dozens of machines | Millions of machines |
| Experts managed them | Self-service for anyone |
| Fixed capacity | Elastic (scale up/down) |
| Single location | Globally distributed datacenters |

💡 **Why it matters:**  
Understanding this difference helps you appreciate *why* new techniques like virtualization, MapReduce, and Kafka were invented — old solutions simply don't scale.

---

## Week 2 – Virtualization & Server Virtualization

### Topic 4: Virtualization Basics

📌 **What it is:**  
Virtualization is the technique of making one physical computer behave like many independent computers. Each "virtual computer" is called a **Virtual Machine (VM)**.

**The key player:** A **Hypervisor** (also called a Virtual Machine Monitor, or VMM) sits between the physical hardware and the virtual machines, managing and sharing resources.

💡 **Why it matters:**  
Without virtualization, you'd need one physical server per application. With virtualization, one server can run 20+ VMs, dramatically reducing costs.

🌍 **Real-world example:**  
A hospital might run its billing system, patient records, and pharmacy app on three separate VMs — all on one physical server.

**Two types of Hypervisors:**
- **Type 1 (Bare-Metal):** Runs *directly* on the hardware. No host OS needed. Faster. Example: VMware ESXi, Xen.
- **Type 2 (Hosted):** Runs *on top of* a regular OS (like Windows). Slower. Example: VirtualBox, VMware Workstation.

> **Memory tip:** Type 1 = "bare metal" = raw hardware → faster. Type 2 = runs on top of an OS → slower.

---

### Topic 5: Docker & Containers

📌 **What it is:**  
A **container** (like Docker) is a lighter-weight alternative to a full VM. Instead of virtualizing the entire hardware, containers share the *host OS kernel* but keep each application isolated.

| Feature | VM | Container (Docker) |
|---|---|---|
| Size | GBs | MBs |
| Startup time | Minutes | Seconds |
| Isolation level | Full (separate OS) | Process-level |
| Shares | Nothing with host | Host OS kernel |

💡 **Why it matters:**  
Containers are why modern apps ("microservices") can be deployed instantly and consistently on any machine.

🌍 **Real-world example:**  
Spotify uses Docker containers so that each microservice (search, playlist, payments) runs in its own isolated environment without conflicting with others.

**Docker Networking:** Docker uses **NAT (Network Address Translation)** to allow containers to communicate with the external network.

---

### Topic 6: SR-IOV and Open vSwitch

📌 **What it is:**
- **SR-IOV (Single Root I/O Virtualization):** A hardware feature of NICs (Network Interface Cards) that lets one physical network card appear as multiple "Virtual Functions" — one per VM. Each VM gets its own small, fast network queue.
- **Open vSwitch (OVS):** A software-based virtual switch that connects VMs inside a host. The "smart" routing logic lives in *user space*, while fast packet forwarding happens in the *kernel*.

💡 **Why it matters:**  
SR-IOV gives VMs near-native network performance. OVS provides flexible, programmable networking inside a data center.

---

### Topic 7: Software Defined Networking (SDN)

📌 **What it is:**  
In traditional networks, every switch/router makes its own decisions about how to route packets (distributed intelligence). SDN *separates* the decision-making (control plane) from the actual packet forwarding (data plane).

- **Control Plane** → "The brain" → Centralized **SDN Controller** (e.g., OpenFlow controller)
- **Data Plane** → "The muscles" → Dumb switches that just follow rules from the controller

💡 **Why it matters:**  
SDN makes networks much easier to manage, reconfigure, and automate — perfect for cloud datacenters where topology changes constantly.

🌍 **Real-world example:**  
**Google's B4** is a private WAN (Wide Area Network) built using SDN. It routes traffic between Google's global datacenters using software-controlled policies, achieving near-100% link utilization.

**VL2:** A datacenter network design that uses "oblivious routing" — the path a network flow takes does *not* depend on current traffic conditions. This simplifies design and ensures fairness.

**Mininet:** A network emulator — it creates a realistic virtual network of hosts, switches, and routers on a *single machine* for testing SDN applications.

---

## Week 3 – Leader Election in Distributed Systems

### Topic 8: Leader Election

📌 **What it is:**  
In a distributed system (many computers working together), some tasks need exactly one "coordinator" or "boss" process to handle them. **Leader Election** is the algorithm that lets the processes vote and agree on who that single leader will be.

- It's called a **symmetry-breaking** problem — all processes start equal and must end up choosing one.
- **Key rule:** Exactly one *non-faulty* process must become the leader.

💡 **Why it matters:**  
Without a leader, processes might conflict (e.g., two processes both try to write to the same file). A leader prevents chaos.

🌍 **Real-world example:**  
Apache ZooKeeper (used by Hadoop and Kafka) uses leader election internally so one server coordinates all client requests.

**Why is election impossible in anonymous rings?**  
If all processes have identical states (no unique IDs), they are indistinguishable. Any algorithm one runs, they all run — so they all become leader or none do. **Solution:** Give each process a **Unique ID**.

---

### Topic 9: LCR Algorithm (Chang-Roberts)

📌 **What it is:**  
A simple leader election algorithm for a **ring topology** (processes connected in a circle):
1. Every process sends its own ID clockwise.
2. When a process receives an ID, it forwards it only if the received ID is **larger** than its own. Otherwise, it discards the message.
3. The process that eventually receives its *own ID back* (it was never discarded) declares itself the **leader** — because it has the largest ID.

**Complexity:**
- **Worst case:** O(n²) messages (IDs travel the full ring every time)
- **Best case:** O(n) messages

---

### Topic 10: Hirschberg-Sinclair Algorithm

📌 **What it is:**  
A smarter ring election algorithm. Processes elect a "local leader" within increasing neighborhoods (phases: 1, 2, 4, 8, ..., n). This dramatically reduces the number of messages needed.

**Complexity:** Θ(n log n) messages — much better than LCR's worst case.

---

## Week 4 – Time & Global Snapshots

### Topic 11: Physical Clocks & Synchronization

📌 **What it is:**  
Each computer has its own hardware clock. But clocks *drift* over time — they don't tick at exactly the same rate.

- **Clock Skew:** The *difference in values* between two clocks at any moment in time.
- **Clock Drift:** The *difference in rates* at which two clocks tick.

**Why synchronize?** If processes log events with mismatched timestamps, you can't tell what happened first. Logs become unreliable.

**UTC (Coordinated Universal Time):** The global standard for real time that all systems try to sync to.

**Types of synchronization:**
- **External sync:** Sync each clock to a trusted external source (UTC). If each clock is within D of UTC, then any two clocks are within 2D of each other (internal sync).
- **Internal sync:** Keep all clocks within D of *each other* (not necessarily correct real time).

**Christian's Algorithm:**  
Client asks a time server for the current time, then accounts for the message travel time (RTT/2) when setting its own clock.

**Berkeley's Algorithm:**  
A *master* polls all other clocks, calculates the average, and tells each machine how much to adjust. No external UTC reference needed — good for internal sync.

---

### Topic 12: Logical Clocks & Happened-Before

📌 **What it is:**  
When you can't trust physical clocks, use **logical clocks** to order events. The **happened-before (→)** relationship says:

1. If A and B are events on the *same process*, and A happened before B, then A → B.
2. If A is "send message" and B is "receive that message," then A → B.
3. Transitive: If A → B and B → C, then A → C.

**Lamport Timestamps:**  
Each process maintains a counter. Every event increments it. When sending a message, include the timestamp. When receiving, set your clock to max(local, received) + 1.

**Key property:** Happened-before forms a **partial order** (not total — two events may be *concurrent* with no relationship).

---

### Topic 13: Global Snapshots (Chandy-Lamport Algorithm)

📌 **What it is:**  
A "snapshot" captures the state of a distributed system (all processes + all messages in transit) at a consistent logical moment — even though you can't pause all processes simultaneously.

**How it works:**
1. An initiator records its own state and sends a special "marker" message on all its outgoing channels.
2. When a process receives a marker for the first time, it records its own state, then sends markers on all its outgoing channels.
3. When a process receives a marker on a channel it has already seen, it records the state of that channel (messages received since it sent its own marker).

💡 **Why it matters:**  
Used for debugging, checkpointing (resuming after a crash), and garbage collection in distributed systems.

---

## Week 5 – Consensus & Fault Tolerance

### Topic 14: Consensus

📌 **What it is:**  
**Consensus** means getting all non-faulty processes to *agree on the same single value*. Think of it as a group of people voting and everyone agreeing on the outcome — even if some people are offline.

**Requirement:** Solvable only in **synchronous systems** (where message delays have known bounds). In fully asynchronous systems, it's provably impossible (FLP theorem).

💡 **Why it matters:**  
Consensus is the foundation of distributed databases, leader election, and commit protocols.

---

### Topic 15: Paxos Algorithm

📌 **What it is:**  
Paxos is the most famous consensus algorithm. It works in two phases:

**Phase 1 (Prepare):** A *proposer* sends a "Prepare(n)" message to a majority of *acceptors* with a proposal number n.

**Phase 2 (Accept):** If a majority of acceptors respond, the proposer sends "Accept(n, value)." If a majority accept, the value is chosen.

**Key properties:**
- **Safe** (never returns two different values)
- **Eventually live** (eventually makes progress, but may need to restart rounds if leaders conflict)
- **Any process** can initiate a round (not just a fixed leader)
- **Challenge:** Multiple proposers can cause repeated restarts (livelock risk)

---

### Topic 16: Byzantine Fault Tolerance

📌 **What it is:**  
A **Byzantine fault** is when a component behaves *arbitrarily* — it might send wrong data, lie, or act maliciously. It's the hardest type of fault to handle.

**Fault hierarchy (from easiest to hardest to tolerate):**
Crash fault → Fail-stop fault → Omission fault → **Byzantine fault** (hardest)

> **Why this order?** A *crash* fault is easy: the process just stops. A *fail-stop* fault is also detectable (other processes can tell the node stopped). An *omission* fault is harder because messages are silently dropped — you don't know if the process is slow or dead. A *Byzantine* fault is the worst: the process is still running but sending arbitrary or malicious responses, so you can't trust anything it says.

💡 **Why it matters:**  
Critical systems (aircraft, financial systems, blockchains) must tolerate Byzantine failures. Bitcoin uses a Byzantine-fault-tolerant consensus mechanism.

---

### Topic 17: Failure Recovery & Rollback

📌 **What it is:**  
To recover from failures, systems periodically save **checkpoints** (snapshots of state). If a process crashes, it rolls back to the last checkpoint.

**The Domino Effect:**  
If one process rolls back to an earlier checkpoint, it may force other processes to roll back too (because messages received from the failed process are now "unsent"). This cascade can force *all* processes to roll back to the very beginning — catastrophic!

**Solution:** Coordinated checkpointing — all processes checkpoint at the same logical time.

**SLA (Service Level Agreement):** A contract between cloud provider and customer that specifies:
- **SLI** (Service Level Indicator) – What is measured (e.g., uptime %)
- **SLO** (Service Level Objective) – The target (e.g., 99.9% uptime)
- **SLA** = SLOs + consequences for violation (e.g., credits if target is missed)

---

## Week 6 – Key-Value Stores (NoSQL) & CAP Theorem

### Topic 18: Key-Value Stores & NoSQL

📌 **What it is:**  
A **key-value store** is a simple database that stores data as pairs: a unique **key** and its **value** — exactly like a dictionary or a phone book (name → phone number).

**Why NoSQL?** Modern web applications deal with:
- **Huge amounts of data** (billions of records)
- **Unstructured data** (user posts, clicks, logs)
- **Massive random reads/writes** (Twitter users liking tweets)

Traditional SQL databases (with rigid tables and JOIN operations) struggle at this scale. NoSQL databases like Cassandra, MongoDB, and DynamoDB are built for it.

**Column-oriented storage:**  
Instead of storing data row by row, store it column by column. This allows super-fast range searches within one attribute (e.g., find all salaries > $100k) without reading irrelevant data.

---

### Topic 19: Apache Cassandra

📌 **What it is:**  
Cassandra is a distributed, highly available key-value / column-family database designed by Facebook. Key concepts:

- **Partitioner:** Maps keys to servers (decides which node stores which key)
- **Snitch:** Determines which datacenter/rack a node belongs to (for replication strategy)
- **SSTable (Sorted String Table):** An **immutable** (never modified in place) file sorted by key where data is stored on disk
- **Bloom Filter:** A space-efficient data structure that tells you "definitely not in this SSTable" (no false negatives) or "maybe in this SSTable" (possible false positives — but no false negatives)
- **Hinted Handoff:** When a replica is temporarily down, writes are buffered at another node and delivered later when the replica recovers. This keeps Cassandra "always writable."

---

### Topic 20: CAP Theorem & Eventual Consistency

📌 **What it is:**  
The **CAP Theorem** says a distributed system can only guarantee **two out of three** of:
- **C**onsistency – Every read gets the most recent write
- **A**vailability – Every request gets a response (even if not the latest data)
- **P**artition Tolerance – System keeps working even if network messages are lost

**In cloud systems:** Network partitions *will* happen. So you *must* choose P. That leaves you choosing between C and A.

**Cassandra's choice:** Availability + Partition Tolerance (**AP system**). It uses **eventual consistency**: if you stop writing to a key, all replicas will *eventually* converge to the same value — but reads might temporarily return stale data.

🌍 **Real-world example:**  
When you like a post on Facebook, your friend might not see the updated like count for a second or two — that's eventual consistency in action.

---

## Week 7 – DHT, MapReduce & YARN

### Topic 21: Distributed Hash Tables (DHT) & Chord

📌 **What it is:**  
A **Distributed Hash Table (DHT)** is a key-value store spread across many machines (peers) in a P2P (peer-to-peer) network. Each machine is responsible for storing a subset of keys.

**Chord** is a famous DHT algorithm:
- Each peer and key is assigned an ID on a circle (ring) of numbers from 0 to 2^m − 1, where **m** is a system parameter that controls the size of the identifier space (e.g., m = 160 gives a ring of 2^160 possible IDs — enough for every device on Earth).
- A key K is stored at the **first peer whose ID ≥ K** (called the "successor" of K).
- Uses a "finger table" to jump to peers exponentially closer to the target, achieving **O(log n) lookups**.

**Virtual Nodes:**  
Instead of assigning one spot on the ring per machine, each machine gets multiple virtual positions. This **improves load balancing** by distributing keys more evenly.

---

### Topic 22: MapReduce

📌 **What it is:**  
MapReduce is a programming model for processing huge datasets in parallel across thousands of machines. It has two phases:

1. **Map phase:** Each mapper reads a chunk of input and outputs **intermediate key-value pairs**.
   - Example: For word count, every word in a line becomes (word, 1).
2. **Reduce phase:** All values with the same key are grouped together, and a reducer processes them.
   - Example: ("hello", [1, 1, 1]) → ("hello", 3).

**Shuffle:** The framework automatically moves all intermediate key-value pairs from mappers to the right reducers, grouped by key. This step is called the **shuffle**.

**Stragglers:** Slow tasks that delay the entire job. MapReduce handles this with **speculative execution** — it starts a copy of a slow task on another machine and uses whichever finishes first.

**Combiner:** A mini-reducer that runs locally on each mapper before the shuffle. It pre-aggregates values, reducing the amount of data shuffled over the network. Only works when the reduce function is **commutative and associative**.

---

### Topic 23: YARN (Yet Another Resource Negotiator)

📌 **What it is:**  
YARN is the resource management layer of Hadoop 2.x. It separates resource management from job scheduling.

**Key components:**
- **Resource Manager (RM):** The cluster-wide "traffic controller." Decides which application gets how many resources (containers). **This is the global scheduler.**
- **Node Manager (NM):** An agent on every machine that manages containers on that machine.
- **Application Master (AM):** One per job. Negotiates containers from the RM and handles task failures for its specific job.

---

## Week 8 – Spark & Kafka

### Topic 24: Apache Spark & RDDs

📌 **What it is:**  
Spark was created at UC Berkeley's AMPLab to fix MapReduce's biggest problem: **MapReduce reads and writes intermediate data to disk after every step**, which is very slow for iterative algorithms (machine learning, graph processing).

Spark keeps data **in memory** (RAM) between steps.

**RDD (Resilient Distributed Dataset):** Spark's core data abstraction.
- **Immutable:** Once created, cannot be changed (you create new RDDs by transforming old ones).
- **Partitioned:** Spread across multiple machines.
- **Fault-tolerant via Lineage:** If a partition is lost, Spark recomputes it using the **lineage** (the history of transformations that created it). No need to replicate data.

**Transformations vs. Actions:**
- **Transformation** (lazy): Creates a new RDD. Doesn't compute yet. Examples: `map()`, `filter()`, `join()`.
- **Action** (triggers computation): Returns a result to the driver. Examples: `count()`, `collect()`, `save()`.

---

### Topic 25: Spark Libraries

| Library | Purpose |
|---|---|
| **Spark SQL** | SQL queries on structured data |
| **Spark Streaming** | Real-time stream processing |
| **MLlib** | Machine learning algorithms |
| **GraphX** | Graph processing |

**GraphX & GAS model:**  
The **Gather-Apply-Scatter (GAS)** model is used for iterative graph computations (like PageRank):
- **Gather:** Collect information from neighboring vertices
- **Apply:** Update a vertex's state based on gathered info
- **Scatter:** Send updated info back to neighbors

**PageRank:**  
Each page passes a fraction of its rank to its neighbors: rank contribution = rank_p / |neighbors_p|.

---

### Topic 26: Apache Kafka

📌 **What it is:**  
Kafka is a **real-time distributed messaging system**. Think of it as a super-fast, fault-tolerant bulletin board where applications can post messages and other applications can read them.

**Key concepts:**
- **Topic:** A named feed/category for messages (like a channel)
- **Producer:** An application that *writes* messages to a topic
- **Consumer:** An application that *reads* messages from a topic
- **Broker:** A Kafka server that *stores* messages
- **Partition:** A topic is split into partitions for parallelism and scalability

**Messaging models Kafka supports:**
- **Queue (point-to-point):** One consumer group reads each message once
- **Publish-Subscribe:** Multiple consumer groups can all read the same message

**Fault tolerance:** With replication factor N, Kafka can tolerate **N−1 broker failures**.

---

## ☁️ Cloud Computing Practice Questions

*Matching the MCQ + scenario-based pattern from your professor's assignments.*

---

**Q1.** A company wants to deploy an application quickly without managing any servers, OS patches, or runtime configurations. Which cloud service model is the best fit?

- A) IaaS
- B) PaaS
- C) SaaS
- D) DaaS

**✅ Answer: B) PaaS**

*Explanation:* PaaS provides a complete platform (runtime, tools, hosting) so developers just write and deploy their application. The provider handles everything underneath. IaaS gives you raw VMs (you still manage the OS). SaaS is a finished application — you can't deploy custom code.

---

**Q2.** Which statement is TRUE about Type 1 (bare-metal) hypervisors?

- A) They run on top of an existing host operating system
- B) They require Docker to function
- C) They directly manage hardware and run guest VMs above them
- D) They are slower than Type 2 hypervisors

**✅ Answer: C**

*Explanation:* A bare-metal hypervisor sits directly on the hardware — no host OS in between. This makes it faster and more efficient than Type 2 hypervisors (which run on top of a host OS like Windows). VMware ESXi and Xen are famous examples.

---

**Q3.** In the LCR (Chang-Roberts) ring election algorithm, a process declares itself the leader when:

- A) It receives a message with a smaller ID than its own
- B) Its own ID is received back after traveling the entire ring
- C) A majority of processes vote for it
- D) The ring size is known

**✅ Answer: B**

*Explanation:* In LCR, each process forwards a message only if the ID in the message is larger than its own. The process with the largest ID is never blocked, so its ID travels all the way around the ring. When that process sees its own ID come back, it knows nobody overrode it — it's the leader.

---

**Q4.** External time synchronization with bound D guarantees internal synchronization with bound:

- A) D
- B) D/2
- C) 2D
- D) D²

**✅ Answer: C) 2D**

*Explanation:* If clock A is within D of UTC and clock B is within D of UTC, then in the worst case A and B differ by up to D + D = **2D** from each other. This is the standard result for converting between external and internal synchronization bounds.

---

**Q5.** Paxos is described as "safe and eventually live." What does "eventually live" mean?

- A) It always terminates in a fixed number of rounds
- B) It guarantees a decision will be made within one network round-trip
- C) Given enough time without failures, consensus will be reached
- D) It works even in fully asynchronous systems

**✅ Answer: C**

*Explanation:* "Eventually live" means the protocol will *eventually* make progress and reach a decision — but only if the network stabilizes. Paxos may restart rounds many times if messages are delayed or leaders crash. It doesn't guarantee termination in bounded time, but under reasonable conditions it always finishes.

---

**Q6.** In Cassandra, the "Hinted Handoff" mechanism is used to:

- A) Enforce strong consistency on all reads
- B) Buffer writes and deliver them to a recovered replica later
- C) Reject writes when any replica is unavailable
- D) Forward reads to the nearest replica

**✅ Answer: B**

*Explanation:* Cassandra prioritizes availability. If a target replica is temporarily down, another node stores a "hint" (the write data + destination). When the target replica recovers, the hint is delivered. This is why Cassandra is called "always writable."

---

**Q7.** In the CAP theorem, cloud systems that must tolerate partitions must choose between:

- A) Latency and throughput
- B) Consistency and availability
- C) Storage and compute
- D) Encryption and replication

**✅ Answer: B**

*Explanation:* Network partitions *will* happen in any real cloud system. The CAP theorem proves that once you accept P (partition tolerance is mandatory in practice), you must sacrifice either C (consistency) or A (availability). Cassandra chooses A; HBase chooses C.

---

**Q8.** In MapReduce, the "shuffle" step refers to:

- A) Randomly assigning input files to mappers
- B) Replicating output files to HDFS
- C) Transferring intermediate map outputs to reducers based on key partitioning
- D) Sorting input data before the Map phase

**✅ Answer: C**

*Explanation:* After mappers produce intermediate key-value pairs, the framework moves (shuffles) all pairs with the same key to the same reducer. This step — transferring data across the network grouped by key — is called the shuffle.

---

**Q9.** An RDD in Spark achieves fault tolerance primarily through:

- A) Replicating all partitions to at least 3 nodes
- B) Write-ahead logging to HDFS
- C) Lineage information that allows lost partitions to be recomputed
- D) Distributed locking to prevent data loss

**✅ Answer: C**

*Explanation:* Spark stores the *recipe* for how each RDD was created (its lineage). If a partition is lost due to a node failure, Spark re-executes only the needed transformations to recompute that partition. This avoids the overhead of full data replication.

---

**Q10.** A Kafka topic has a replication factor of 3. How many broker failures can this topic tolerate?

- A) 3
- B) 2
- C) 1
- D) 0

**✅ Answer: B) 2**

*Explanation:* With replication factor N, Kafka can tolerate **N−1** broker failures. With N=3, one copy is the leader and two are replicas. If 2 brokers fail, the one remaining broker still has a complete copy and can serve the data. If 3 fail, all copies are lost.

---

# Step 3 – Data Mining Notes & Practice

> **Reading guide:** For every topic, you'll see 📌 What it is, 💡 Why it matters, 🌍 Real-world example, and 🧮 Key formula.

---

## Week 1 – Introduction to Data Mining

### Topic 1: What is Data Mining?

📌 **What it is:**  
Data Mining is the process of discovering **valid, novel, useful, and understandable patterns** in large datasets.

Think of it like digging in a mountain of raw ore to find gold nuggets — the data is the mountain, and the patterns/insights are the gold.

💡 **Why it matters:**  
Modern businesses have petabytes of data (clicks, purchases, sensor readings). Data mining transforms that raw data into actionable knowledge.

🌍 **Real-world example:**  
Amazon's "Customers who bought this also bought..." recommendation system is the output of data mining (specifically, association rule mining).

**The KDD Process (Knowledge Discovery in Databases):**
1. Data collection
2. **Preprocessing** ← usually the *first* step
3. Transformation
4. Data Mining (model building)
5. Interpretation/Visualization
6. Deployment

> **Remember:** Preprocessing is almost always the first step in any data mining pipeline.

---

### Topic 2: Types of Data Attributes

📌 **What it is:**  
Data attributes (columns in a table) fall into four types, which determine what mathematical operations you can perform on them:

| Type | Description | Allowed Operations | Example |
|---|---|---|---|
| **Nominal** | Categories with no order | Distinctness (=, ≠) only | Country name, gender, color |
| **Ordinal** | Categories with order, but gaps between values are meaningless | Distinctness + ordering | Letter grades (A, B, C), T-shirt sizes |
| **Interval** | Ordered with meaningful gaps, but no true zero | +, − (differences meaningful) | Temperature (°C), calendar year |
| **Ratio** | Interval + meaningful zero | +, −, ×, ÷ | Weight, height, income, age |

> **Memory tip (NOIR):** Nominal → Ordinal → Interval → Ratio. Each level adds one more allowed operation.

**Key rule:** You *cannot* multiply or add ordinal data. "Grade A + Grade B" makes no sense. You can only say "A is higher than B."

---

### Topic 3: Types of Data

| Data Type | Description | Example |
|---|---|---|
| **Record data** | Table of instances (rows) with attributes (columns) | University student database |
| **Graph data** | Nodes connected by edges | Social network, web graph |
| **Tree data** | Hierarchical structure | File system, XML |
| **Text data** | Unstructured natural language | Biodata descriptions, articles |
| **Ordered data** | Sequences or time series | Stock prices, DNA sequences |

> **Remember:** In a data table, **rows = instances (data points)**, **columns = attributes (features)**.

---

### Topic 4: Data Reduction

📌 **What it is:**  
Working with millions of columns or rows is slow and wasteful. Data reduction shrinks the data without losing important information:

- **Data sampling:** Reduce the number of **rows** (instances). Pick a representative subset.
- **Dimensionality reduction:** Reduce the number of **columns** (attributes). Remove irrelevant features.
- **Discretization:** Convert continuous values into discrete bins (e.g., age 0-18 = "young").

---

## Week 2 – Association Rule Mining

### Topic 5: Association Rules

📌 **What it is:**  
An **association rule** is a pattern of the form **X → Y**, meaning: "When X appears, Y tends to appear too."

🌍 **Real-world example:**  
In a supermarket: {Bread, Butter} → {Jam} means "customers who buy bread and butter also tend to buy jam." Supermarkets use this to decide shelf placement.

**Two key metrics:**

🧮 **Support:**
```
Support(X → Y) = (Number of transactions containing both X and Y) / (Total transactions)
```
Measures how *often* the rule applies.

🧮 **Confidence:**
```
Confidence(X → Y) = Support(X ∪ Y) / Support(X)
```
Measures how *reliable* the rule is. Given X occurred, how likely is Y?

> **The Apriori Principle:** If an itemset is frequent (meets minimum support), then all its *subsets* are also frequent. Conversely, if a subset is infrequent, the larger set cannot be frequent. This "anti-monotone" property lets the Apriori algorithm prune the search space dramatically.

**Apriori Algorithm:** The efficient algorithm for finding association rules. It works bottom-up: first finds frequent 1-itemsets, then 2-itemsets, then 3-itemsets, pruning infrequent candidates at each step.

---

### Worked Example – Support & Confidence

| Transaction ID | Items |
|---|---|
| 1 | {a, b, d, e} |
| 2 | {b, c, d} |
| 3 | {a, b, d, e} |
| 4 | {a, c, d, e} |
| 5 | {b, c, d, e} |
| 6 | {b, c, d} |
| 7 | {c, d} |
| 8 | {a, b, c} |
| 9 | {a, d, e} |
| 10 | {b, c} |

**Q: What is the Support of {b, c, d}?**  
Transactions containing *all three* of b, c, d: #2, #5, #6 → 3 transactions out of 10  
**Support = 3/10 = 0.3**

**Q: What is the Confidence of the rule a → b?**  
- Transactions with a: #1, #3, #4, #8, #9 → 5 transactions
- Transactions with *both* a and b: #1, #3, #8 → 3 transactions  
**Confidence = 3/5 = 0.6**

---

## Week 3 – Decision Trees

### Topic 6: Decision Trees

📌 **What it is:**  
A **decision tree** is a classification model shaped like an upside-down tree:
- **Root node** → The first decision (the most informative attribute)
- **Internal nodes** → More decisions (attribute tests)
- **Branches** → Possible values of an attribute
- **Leaf nodes** → The final class label

💡 **Why it matters:**  
Decision trees are easy to understand and interpret (unlike neural networks). You can literally follow the path from root to leaf and read it as a "if-then-else" rule.

🌍 **Real-world example:**  
A bank uses a decision tree to decide if a loan application should be approved: first split on "income > $50k?", then "credit score > 700?", etc.

---

### Topic 7: Information Gain & Entropy

📌 **What it is:**  
To decide *which attribute to split on first*, we calculate how much each attribute *reduces uncertainty* about the class label. This is called **Information Gain**.

🧮 **Entropy (measure of impurity/disorder):**
```
Entropy(S) = -Σ pᵢ × log₂(pᵢ)
```
Where pᵢ is the fraction of examples belonging to class i.

- **Entropy = 0:** All examples are one class (perfectly pure, no disorder)
- **Entropy = 1:** Examples are split 50-50 (maximum disorder)

🧮 **Information Gain:**
```
Gain(S, A) = Entropy(S) - Σ (|Sv| / |S|) × Entropy(Sv)
```
Where Sv is the subset of S where attribute A has value v.

**Rule:** Choose the attribute with the **highest information gain** (or equivalently, the split that leads to the *lowest* weighted entropy in the children).

---

### Worked Example – Entropy

Dataset: 4 spam, 6 email (10 total)

```
Entropy = -(4/10) × log₂(4/10) - (6/10) × log₂(6/10)
        = -(0.4 × (-1.322)) - (0.6 × (-0.737))
        = 0.529 + 0.442
        ≈ 0.971 bits
```

This is close to 1 — meaning the dataset is fairly mixed.

---

## Week 4 – Naïve Bayes Classifier & K-Nearest Neighbor

### Topic 8: Bayes Theorem & Naïve Bayes

📌 **What it is:**  
**Bayes Theorem** gives us a way to calculate the probability of a hypothesis (class) given evidence (data):

🧮 **Bayes Rule:**
```
P(Class | Data) = P(Data | Class) × P(Class) / P(Data)
```

- **P(Class)** = Prior probability (how common is this class in general?)
- **P(Data | Class)** = Likelihood (how likely is this data if we assume this class?)
- **P(Class | Data)** = Posterior probability (what we want: how likely is this class given the data?)

**MAP Classifier (Maximum A Posteriori):** Choose the class with the highest posterior probability.

**Naïve Bayes Assumption:** Features (attributes) are *independent* of each other given the class. This simplifies the calculation enormously:
```
P(A ∩ B) = P(A) × P(B)    (if A and B are independent)
```

---

### Worked Example – Bayes Theorem

**Problem:** P(spam) = 0.60, P(lottery|not spam) = 0.15. P(lottery|spam) = 0.90. Find P(spam|lottery).

**Step 1:** Compute P(lottery) using the law of total probability:
```
P(lottery) = P(lottery|spam) × P(spam) + P(lottery|not spam) × P(not spam)
           = 0.90 × 0.60 + 0.15 × 0.40
           = 0.54 + 0.06
           = 0.60
```

**Step 2:** Apply Bayes rule:
```
P(spam|lottery) = P(lottery|spam) × P(spam) / P(lottery)
                = 0.90 × 0.60 / 0.60
                = 0.54 / 0.60
                = 0.90
```

**Answer:** P(spam|lottery) = **0.90**

> **Important lesson from this example:** Always compute P(evidence) using the law of total probability — never assume it is given directly unless the problem explicitly states all required conditional probabilities. If the formula gives a result > 1, it means one or more of the given probabilities are logically inconsistent (they do not form a valid joint distribution).

---

### Topic 9: K-Nearest Neighbor (KNN)

📌 **What it is:**  
KNN classifies a new instance by finding the K closest training examples and taking a majority vote.

**Distance measure:** Most commonly, **Euclidean distance**:
```
d(p, q) = √[(p₁-q₁)² + (p₂-q₂)² + ... + (pₙ-qₙ)²]
```

**Example:** Classify new mail m. K=7. The 7 nearest neighbors' labels are:  
{email, spam, email, email, email, spam, email}  
Count: email=5, spam=2 → **Classify as email** (majority wins).

**Key choice:** Choosing K matters. Too small K → noisy (overfitting). Too large K → too smooth (underfitting).

---

## Week 5 – Support Vector Machines (SVM)

### Topic 10: SVM Concepts

📌 **What it is:**  
An SVM finds the **optimal separating hyperplane** — the line (or plane in higher dimensions) that separates two classes with the **maximum margin**.

**Hyperplane equation:** W^T X + b = 0 (where W is the weight vector, X is the input, b is the bias)

- **Support vectors:** The training points closest to the hyperplane. The hyperplane is defined entirely by these few points.
- **Margin:** The perpendicular distance from the hyperplane to the nearest data points. SVM *maximizes* this margin.

💡 **Why it matters:**  
Maximizing the margin gives the best generalization to unseen data — the boundary is as far as possible from all training points.

🌍 **Real-world example:**  
SVMs are used in image recognition (e.g., distinguishing cats from dogs) and bioinformatics (e.g., classifying cancer vs. normal tissue from gene expression data).

**Key formulas:**

🧮 **Hard-margin SVM optimization:**
```
Minimize: ½ W^T W
Subject to: yᵢ(W^T Xᵢ + b) ≥ 1  for all i
```

**For a support vector Xⱼ:** |W^T Xⱼ + b| = **1** (exactly on the margin boundary)

**Solving the SVM:** The **dual problem** is solved using **Quadratic Programming**. The Lagrange multipliers for support vectors are **greater than zero**; for non-support vectors they are **zero**.

**Soft Margin SVM:** Allows some misclassification using **slack variables**, controlled by regularization constant **C**. C controls the tradeoff between a wider margin and fewer training errors.

---

### Topic 11: Non-linear SVM & Kernel Trick

📌 **What it is:**  
When data is not linearly separable, SVM uses a **kernel function** to implicitly map data to a higher-dimensional space where it becomes linearly separable. Common kernels: polynomial, RBF (Gaussian).

---

## Week 6 – Artificial Neural Networks (ANN)

### Topic 12: Perceptron

📌 **What it is:**  
A **perceptron** is the simplest neural unit — it takes multiple inputs, weights them, sums them up, and passes the result through an activation function to produce output.

- **Class boundary:** A perceptron can only create a **straight line** (linear) decision boundary.
- **Number of neurons:** A single perceptron = **1 neuron**.
- **Limitation:** Cannot solve non-linearly separable problems like **XOR**.

---

### Topic 13: Multi-Layer Perceptron (MLP)

📌 **What it is:**  
An MLP stacks multiple layers of neurons:
- **Input layer** → receives raw data
- **Hidden layer(s)** → learns intermediate features
- **Output layer** → produces final prediction

**Key properties:**
- **Feed-forward:** Information flows only from input to output (not backward during inference)
- **Fully connected:** Every neuron in one layer connects to every neuron in the next layer
- **Can solve XOR** (and any problem, given enough hidden neurons — Universal Approximation Theorem)

🧮 **Counting weights in an MLP:**  
For an MLP with 3 input nodes, 2 hidden nodes, 1 output node:
- Input → Hidden: 3 × 2 = **6 weights**
- Hidden → Output: 2 × 1 = **2 weights**
- **Total = 8 weights** (not counting biases in this formula)

**Sigmoid activation function:** h(z) = 1 / (1 + e^(-z))  
It is **continuous and differentiable** — crucial for the backpropagation algorithm.

---

### Topic 14: Backpropagation & Training

📌 **What it is:**  
**Backpropagation** is the algorithm for training an MLP. It works by:
1. **Forward pass:** Compute the output.
2. **Compute error:** Compare output to true label.
3. **Backward pass:** Use the chain rule to compute how much each weight contributed to the error.
4. **Update weights:** Use **gradient descent** to nudge weights in the direction that reduces error.

**Overfitting:** When the model learns the training data too well (including noise) and performs poorly on new data.

**How to detect overfitting:**  
- Training error decreases **but** test error *increases* → overfitting!
- Both training and test error decrease → healthy training.

---

## Week 7 – Clustering

### Topic 15: Clustering Basics

📌 **What it is:**  
**Clustering** is an **unsupervised learning** algorithm — there are no pre-labeled classes. The goal is to group similar data points together.

- A **cluster** = a group of **similar** data items that are **dissimilar** to items in other clusters.

**Distance measures:**

🧮 **Euclidean distance (2D):**
```
d((x₁,y₁), (x₂,y₂)) = √[(x₁-x₂)² + (y₁-y₂)²]
```
Example: d((0,0),(1,1)) = √(1+1) = √2 ≈ **1.414**

---

### Topic 16: K-Means Clustering

📌 **What it is:**  
K-Means partitions n points into K clusters by iteratively:
1. Randomly initialize K cluster centroids (means).
2. Assign each point to the nearest centroid.
3. Recompute each centroid as the mean of its assigned points.
4. Repeat until centroids stop changing.

**Key properties:**
- Produces **spherical clusters** (tends to create round, roughly equal-sized clusters)
- **Final solution depends on initial centroids** (different starts → possibly different results)
- **NOT the most computationally expensive** clustering algorithm (it's fast)
- It is **iterative**

---

### Topic 17: Hierarchical Clustering

📌 **What it is:**  
Instead of specifying K upfront, hierarchical clustering builds a tree (called a **dendrogram**) of nested clusters:

- **Agglomerative (bottom-up):** Start with each point as its own cluster, then merge the two closest clusters repeatedly.
- **Divisive (top-down):** Start with all points in one cluster, then split recursively.

**Linkage methods (how to measure distance between clusters):**
- **Single linkage:** Distance = distance between the *closest* pair of points in the two clusters
- **Complete linkage:** Distance = distance between the *farthest* pair
- **Average linkage:** Distance = average pairwise distance

**K-Nearest Neighbor is NOT a clustering algorithm** — it's a classification algorithm.  
**K-Means is NOT a hierarchical algorithm** — it's partitional (flat).

---

### Topic 18: DBSCAN

📌 **What it is:**  
DBSCAN (Density-Based Spatial Clustering of Applications with Noise) finds clusters of arbitrary shape based on density.

- **Core point:** A point with at least MinPts neighbors within distance ε.
- **Advantage over K-Means:** Discovers clusters of any shape and automatically identifies **outliers** (noise points that don't belong to any cluster).

---

## Week 8 – Regression

### Topic 19: Regression Basics

📌 **What it is:**  
**Regression** is a **supervised learning** algorithm where the output (dependent variable) is a **continuous real number** (not a discrete category).

- **Input:** Independent variables (x₁, x₂, ...)
- **Output:** Dependent variable (y) — a real number

🌍 **Real-world example:**  
Predicting house price based on area and number of bedrooms. Price is a real number → this is regression, not classification.

---

### Topic 20: Linear Regression

📌 **What it is:**  
**Linear regression** models the relationship between inputs and output as a linear (straight-line) equation:

🧮 **Linear regression model:**
```
y = a₀ + a₁x₁ + a₂x₂ + ... + aₙxₙ
```
Where a₀ is the intercept and a₁, ..., aₙ are the slope coefficients.

**Training:** Find a₀, a₁, ..., aₙ that minimize the **Mean Squared Error (MSE)**:
```
MSE = (1/n) × Σ(yᵢ - ŷᵢ)²
```
Where yᵢ is the true value and ŷᵢ is the predicted value.

**The number of input variables can be many** (one, two, three, or unlimited).

---

### Topic 21: Overfitting & Model Complexity

📌 **What it is:**  
A complex model (like a high-degree polynomial) can perfectly fit the training data by "memorizing" noise, but fails miserably on new data.

| Model | Training data (small) |
|---|---|
| **Linear (simple)** | Might **underfit** — too simple to capture the pattern |
| **Cubic/polynomial (complex)** | Might **overfit** — fits training noise, generalizes poorly |

**The bias-variance tradeoff:** Simple models have high bias (underfitting); complex models have high variance (overfitting).

---

### Worked Example – MSE Calculation

**Model:** y = 0 + 1×x₁ + 1×x₂ (a₀=0, a₁=1, a₂=1)

| x₁ | x₂ | True y | Predicted ŷ = x₁+x₂ | Error (y-ŷ)² |
|---|---|---|---|---|
| 0 | 0 | 1 | 0 | (1-0)² = 1 |
| 0 | 1 | 2 | 1 | (2-1)² = 1 |
| 1 | 0 | 2 | 1 | (2-1)² = 1 |
| 1 | 1 | 3 | 2 | (3-2)² = 1 |

Sum of squared errors = 4, n = 4  
**MSE = 4/4 = 1.00**

---

## 📊 Data Mining Practice Questions

*Matching the MCQ + calculation-heavy pattern from your professor's assignments.*

---

**Q1.** Data mining is defined as the process of finding ________ in large datasets.

- A) Errors
- B) Valid, novel, useful, and actionable patterns
- C) Only numerical summaries
- D) Structured tables

**✅ Answer: B**

*Explanation:* The classic definition from data mining literature: valid (correct), novel (new, not already known), useful (actionable for decision-making), and understandable patterns. Errors and noise are things we try to remove, not find.

---

**Q2.** Which attribute type allows ALL four operations: distinctness, ordering, addition, and multiplication?

- A) Nominal
- B) Ordinal
- C) Interval
- D) Ratio

**✅ Answer: D) Ratio**

*Explanation:* Ratio attributes have a meaningful absolute zero, making multiplication and division meaningful. Example: "200kg is twice 100kg" makes sense. For temperature in Celsius (interval), saying "40°C is twice as hot as 20°C" does *not* make sense — but ratio attributes like weight, height, and income support all operations.

---

**Q3.** In a transaction database with 10 transactions, how many transactions must contain an itemset for it to have a support of at least 0.3?

- A) 1
- B) 2
- C) 3
- D) 4

**✅ Answer: C) 3**

*Explanation:* Support = (transactions with itemset) / (total transactions). For support ≥ 0.3 with 10 total transactions: 0.3 × 10 = 3. So at least 3 transactions must contain the itemset.

---

**Q4.** According to the Apriori principle, if the itemset {milk, bread} is infrequent, which of the following can we conclude?

- A) {milk} is infrequent
- B) {milk, bread, jam} cannot be frequent
- C) {bread} is infrequent
- D) {jam} is frequent

**✅ Answer: B**

*Explanation:* The Apriori principle states: if an itemset is infrequent, *all supersets* (itemsets that contain it) must also be infrequent. {milk, bread} is a subset of {milk, bread, jam}, so {milk, bread, jam} cannot be frequent. However, the individual items {milk} and {bread} might still be frequent on their own.

---

**Q5.** A dataset has 4 instances of class A and 6 instances of class B (10 total). What is the entropy of this dataset?

- A) 0
- B) 0.529
- C) 0.971
- D) 1

**✅ Answer: C) 0.971**

*Step-by-step:*
```
p_A = 4/10 = 0.4,  p_B = 6/10 = 0.6
Entropy = -(0.4 × log₂(0.4)) - (0.6 × log₂(0.6))
        = -(0.4 × (-1.322)) - (0.6 × (-0.737))
        = 0.529 + 0.442
        ≈ 0.971 bits
```
An entropy near 1 means the dataset is quite mixed. Entropy = 0 would mean all instances are one class.

---

**Q6.** The MAP (Maximum A Posteriori) classifier classifies a new instance as:

- A) The class with the highest prior probability
- B) The class with the highest likelihood only
- C) The class with the highest posterior probability P(class | data)
- D) The class with the most training examples

**✅ Answer: C**

*Explanation:* MAP = Maximum A Posteriori. We pick the class that maximizes P(class | data) — the posterior probability. This combines the prior P(class) with the likelihood P(data | class) via Bayes rule. It's more informed than just picking the most common class (that would be a naive prior-only classifier).

---

**Q7.** In a K-NN classifier with K=5, the 5 nearest neighbors of a test point are labeled: {cat, dog, cat, cat, dog}. How is the test point classified?

- A) dog
- B) cat
- C) Tie — cannot decide
- D) Neither

**✅ Answer: B) cat**

*Explanation:* Majority vote: cat appears 3 times, dog appears 2 times. cat wins. KNN always uses majority vote — the most common label among the K nearest neighbors is assigned.

---

**Q8.** In SVM, the support vectors are:

- A) All training data points
- B) The data points farthest from the decision boundary
- C) The data points closest to the decision boundary (on the margin)
- D) Only the misclassified data points

**✅ Answer: C**

*Explanation:* Support vectors are the critical few training points that lie exactly on the margin boundaries. The hyperplane is entirely determined by these points — all other training points can be removed without changing the result. This is why SVMs are memory-efficient.

---

**Q9.** Which of the following is an unsupervised learning algorithm?

- A) Decision tree classification
- B) Naïve Bayes classification
- C) K-Means clustering
- D) Linear regression

**✅ Answer: C) K-Means clustering**

*Explanation:* Unsupervised learning means there are **no labels** in the training data — the algorithm discovers structure on its own. Clustering is the canonical example of unsupervised learning. Decision trees, Naïve Bayes, and linear regression all require labeled training data (supervised learning).

---

**Q10.** A linear regression model y = a₀ + a₁x is fitted to data. The predictions and true values are: (predicted=2, true=3), (predicted=4, true=4), (predicted=6, true=5). What is the MSE?

- A) 0.33
- B) 0.67
- C) 1.0
- D) 2.0

**✅ Answer: B) 0.67**

*Step-by-step:*
```
Error 1: (3-2)² = 1
Error 2: (4-4)² = 0
Error 3: (5-6)² = 1
Sum = 2, n = 3
MSE = 2/3 ≈ 0.67
```

---

## 📝 Quick Reference Cheat Sheet

### Cloud Computing — Key Formulas & Facts

| Topic | Key Fact |
|---|---|
| IaaS/PaaS/SaaS | IaaS = VMs, PaaS = platform+runtime, SaaS = ready app |
| Type 1 hypervisor | Runs directly on hardware (bare-metal), faster |
| Type 2 hypervisor | Runs on top of host OS, slower |
| LCR complexity | Worst: O(n²), Best: O(n) |
| Hirschberg-Sinclair | Θ(n log n) messages |
| Clock skew vs drift | Skew = value difference; Drift = rate difference |
| External → Internal sync | External bound D → Internal bound 2D |
| Paxos | Safe + eventually live; any process can propose |
| Byzantine fault | Worst fault type; arbitrary/malicious behavior |
| Cassandra CAP | AP system: availability + partition tolerance |
| Bloom filter | Possible false positives, NO false negatives |
| Hinted handoff | Buffer writes for down replicas |
| SSTable | Immutable, sorted file in Cassandra |
| Chord lookup | O(log n) hops |
| MapReduce combiner | Works when reduce is commutative + associative |
| YARN RM | Global cluster scheduler |
| YARN AM | Per-job task manager |
| Spark RDD | Immutable, fault-tolerant via lineage |
| Spark action vs transform | Action triggers computation; transform is lazy |
| Kafka replication factor N | Tolerates N−1 failures |

---

### Data Mining — Key Formulas

| Formula | Meaning |
|---|---|
| Support(X→Y) = count(X∪Y) / n | Fraction of transactions with both X and Y |
| Confidence(X→Y) = Support(X∪Y) / Support(X) | Given X, how often does Y appear? |
| Entropy(S) = -Σ pᵢ log₂(pᵢ) | Measure of impurity/disorder in a dataset |
| Gain(S,A) = Entropy(S) - weighted child entropy | How much splitting on A reduces entropy |
| P(C\|X) = P(X\|C)×P(C) / P(X) | Bayes theorem for classification |
| Euclidean dist = √(Σ(xᵢ-yᵢ)²) | Distance between two points |
| MSE = (1/n) × Σ(yᵢ - ŷᵢ)² | Regression error measure |

---

### Data Mining — Algorithm Quick Reference

| Algorithm | Type | Supervised? | Key Feature |
|---|---|---|---|
| Apriori | Association mining | No | Anti-monotone pruning |
| Decision Tree | Classification | Yes | Information gain splitting |
| Naïve Bayes | Classification | Yes | Assumes feature independence |
| K-NN | Classification | Yes | Vote among K nearest neighbors |
| SVM | Classification | Yes | Maximizes margin hyperplane |
| MLP / Backprop | Classification | Yes | Multi-layer neural network |
| K-Means | Clustering | No | Iterative centroid update |
| Single/Complete/Average Linkage | Clustering | No | Hierarchical dendrogram |
| DBSCAN | Clustering | No | Density-based, finds outliers |
| Linear Regression | Regression | Yes | Minimizes MSE |

---

*Good luck with your exams! Remember: for Cloud Computing, focus on understanding **why** algorithms work the way they do. For Data Mining, practice the **calculations** with pen and paper until they're automatic.* 🎯
