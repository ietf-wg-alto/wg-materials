----

**Logistics:**

- **Meeting times:** Mon 9:00am to 10:00am PST

- **Location:** https://caltech.zoom.us/j/95461704189?pwd=Y0xjZFhpbjJaSHBINFZvRThMYS83Zz09

----

**Agenda 12/05/2022:**

- Control knobs and applications

**Minutes:**

Applications:
- Hololens 
- Deadline bound traffic

Control knobs:
- Path selection
- Rate selection
- Access link selection
- Service selection
- Topology reconfiguration

-------

**Agenda 05/18/2022:**

- Definition of Scope of Work

**Minutes:**

```
+----------------+       +----------------+     +------------------+          +---------+
|                |       |                |     |                  |          |    O    |
|  Visibility    +------->  Intelligence  +-----> Controllability  |          |    r    |
|                |       |                |     |                  |          |    c    |
+---------^------+       +----------------+     +--------+---------+          |    h    |
          |                                              |            <---->  |    e    |
+---------+----------------------------------------------v---------+          |    s    |
|                     Network  (5G, Edge Cloud, WAN)               |          |    t.   |
+------------------------------------------------------------------+          +---------+       

Visibility:
    - IETF ALTO / OpenALTO
    - BGP-LS
    - sFlow, NetFlow
    - Perfsonar
    - Traceroute
    - What G2 consumes
    - Kubernetes statistics
    - LibreNMS
    - P4 / Inband telemetry

Intelligence:
    - NetPredict
    - G2
    - Bilevel optimization (Yale)
    - Metrics (stateful decision
    - Elastic flow / Elastic stack
    - Hecate

Controllability:
    - SENSE / OpenNSA
    - SRv6 (at the edges of SENSE tunnel)
    - BGP / PCEP 
    - Polka
    - P4
    
Network:
    - SONIC
    - freeRouter 
    - Calico VPP
    - BStruct-Mininet (dev environment)

Orchestration:
    - Composable architecture
    - Kubernetes
    - Interoperation
    - Integration
    - Git-ops
    
```
