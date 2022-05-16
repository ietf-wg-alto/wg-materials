----

**Logistics:**

- **Meeting times:** Mon 9:00 to 10:00am PST, Wed 9:00 to 9:30am EST, Thu 10:00 to 10:30am EST

- **Location:** https://caltech.zoom.us/j/95461704189?pwd=Y0xjZFhpbjJaSHBINFZvRThMYS83Zz09

----

**5G Deployment: SRv6, OpenALTO, Polka, G2**

**Agenda:**

- Definition of Scope of Work

**Minutes:**

```
+----------------+       +----------------+     +------------------+          +---------+
|                |       |                |     |                  |          |         |
|  Visibility    +------->  Intelligence  +-----> Controllability  |          |    O    |
|                |       |                |     |                  |          |    r    |
+---------^------+       +----------------+     +--------+---------+          |    c    |
          |                                              |            <---->  |    h    |
          |                                              |                    |    e    |
+---------+----------------------------------------------v---------+          |    s    |
|                     Network (5G, SENSE, P4)                      |          |    t.   |
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
        - REST service control to communicate with OpenNSA
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
