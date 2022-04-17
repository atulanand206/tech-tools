Kafka
- Decouples data streams
- Messaging System
- Activity Tracking
- Metrics collection
- Streams processing
- Integration w/ BigData Tech 

- Netflix uses K to apply recommendations in real-time while watching TV shows.
- Uber uses K to gather user, taxi, and trip data in real-time to compute & forecast demand, and compute price surge in real-time.

- Kafka is only used as a transportation mechanism.

Traits
- Distributed
- Resilient
- Fault tolerance (orchestrated servers)
- Horizontal scalability
    - 100s of brokers
    - millions of msgs per second
- High performace (Latency of less than 10ms in real-time)

Brokers
- A kafka cluster is composed of multiple brokers.
- Each broker contains certain topic partitions.
- After connecting to any broker, one gets connected to the entire cluster.
- Single broker is also referred to as bootstrap broker.

Partitions:
- Offset only have a meaning for a specific parition.
- Order is guaranteed only within a partition (not across partitions)
- Data is kept only for a limited time. (default - 2 weeks)
- Once data is written to a partition, it becomes immutable.
- Data is assigned randomly to a partition unless a key is provided.
- As many partitions per topic as desired.
- Topics should have a replication factor > 1 to ensure data is not lost when broker goes down.
- Only 1 broker can be a leader for a given partition.
- Only the leader can receive and serve data for a partition.
- The other brokers will synchronize the data.
- Each partition has one leader and multiple in-sync replicas(ISR).

Producers:
- Writes data to topics.
- Only have to specify the topic name and one broker to connect to, and Kafka will automatically take care of routing the data to the right brokers.
- If producers choose to send a key with a message, all the msgs for that key will always go to the same partition.
- This enables to guarantee ordering for a specific key.

Consumers: 
- Reads msgs in order they're pushed to a partition.
- Reads from multiple partitions in parallel.

Consumer Groups
- Every consumer from a consumer group can read from one or more partitions.
- If no of consumers in a consumer group is more than partitions, few consumers would stay idle.

Consumer Offsets:
- Msgs from a partition can be read my multiple consumers and must be consumed by only one partition.
- Consumers commit offsets after reading a message so that other consumers in the consuumer group could skip that.
- Consumers will pick msgs from the last committed offset ensuring all the msgs get handled gracefully.

Resources
- Apache Kafka for Beginners: https://www.youtube.com/playlist?list=PLt1SIbA8guusxiHz9bveV-UHs_biWFegU 