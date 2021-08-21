<style>h3{background:black;color:black}h3:hover{background:transparent;color:#b1bac4}</style>

## SOA-C02
1. **| T |** CloudWatch, standart host level metris<h3>CPU, Network, Disk, Status check</h3>
1. **| T |** CloudWatch, default storage time of logs<h3>Indefinetly</h3>
1. **| T |** CloudWatch, standard monitoring granularity<h3>5 minutes</h3>
1. **| T |** CloudWatch, detailed monitoring granularity<h3>1 minute minimum</h3>
   
   ---
1. **| T |** EBS, use case, SSD, General purpose<h3>System boot; Low-latency; Most workloads</h3>
1. **| T |** EBS, use case, SSD, Provisioned IOPS<h3>Critical bussiness; Sustained IOPS (+10k); Large database workloads</h3>
1. **| T |** EBS, use case, HDD, Throughput optimized<h3>Streaming workloads: fast, consistent and low cost throughput; Big data; Data warehouse; Log processing</h3>
1. **| T |** EBS, use case, HDD, Cold<h3>Throughput-oriented storage for large volumes with infrequently access data</h3>
1. **| T |** EBS, IOPS, SSD, General purpose<h3>Volume-proportional; 3 IOPS per GiB; max of 10k IOPS with 3k3 GiB</h3>
1. **| C |** EBS, volumes restored from snapshots<h3>Must be initialized and all data read beforehand</h3>
1. **| C |** EBS, increased size, S.O. not recognizing<h3>Extend volume's file system</h3>
1. **| T |** EBS, standart metrics<h3>Volume read/write ops; Volume Queue Length (num. of read/write ops requests waiting)</h3>
1. **| T |** EBS, [Severly] Degraded<h3>Warning</h3>
1. **| T |** EBS, Stalled or Not Available<h3>Impaired</h3>
   
   ---
1. **| T |** Elasticache, monitoring<h3>CPU utilization; Swap usage; Evictions; Concurrent connections</h3>
1. **| T |** Elasticache, Memcached, CPU utilization<h3>Multi-thread; up tp 90% of usage, and then add more nodes to the cluster</h3>
1. **| T |** Elasticache, Redis, CPU utilization<h3>Not multi-thread; to determine scaling, divide 90 by the num. of cores</h3>
1. **| C |** Elasticache, Memcached, Swap usage over 50Mb<h3>Increase memcached_connections_overhead</h3>
1. **| C |** Elasticache, Memcached, how to handle evictions<h3>Either scale up (increasing mem) or out (incresing num. of nodes)</h3>
1. **| C |** Elasticache, Redis, how to handle evictions<h3>Only scale out (incresing num. read replicas)</h3>
1. **| C |** Elasticache, experiencing high number of concurrent connections<h3>Either a large traffic spike or app is not realising connections as it should be (set an alarm on the num. of concurrent connections)</h3>
