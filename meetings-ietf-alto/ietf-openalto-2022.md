**Meetings held on:** Mon 9am, Wed 9am and Thu 10am EST.

**Location:** https://yale.zoom.us/my/yryang

----

**IETF OpenALTO Meeting: May 2, 2022**

**Agenda:**

- Quick around the table status update
- Architecture
- Rucio / FTS 114 Hackathon story
- SIGCOMM'22 NAI submission
- Wrap up and next tasks

**Minutes:**

- Jacob, Jensen and Mahdi provide an update on the three outstanding pull requests.
- Everyone provides an update on what they are working on.
- Kai shares the work he and his students are doing on ALTO/DNS:
    - Two ways to integrate ALTO in DNS:
        - DNS server uses ALTO client to pull cost map and return an 
          ordered lists of URLs back to the DNS client based on cost 
          metrics. Seamless to the DNS client.
        - DNS server acts as ALTO server and provides ALTO-type responses 
          back to the DNS client using high-performance DNS style 
          query/response messages. 
    - Richard provides feedback and recommendations on approach
- Discussion about potential paper topics for SIGCOMM NAI:
    - Potential topic 1: ALTO data plane signaling. 
    - Potential topic 2: Rucio/FTS/OpenALTO architecture and positioning paper.
    - There is consensus on working on topic 2.
