----
**Logistics:**

- **Meeting times:** Tue 9:00 to 10:00am EST

- **Location:** https://ietf.webex.com/ietf/j.php?MTID=ma0e97cc97c4cd71bb59cf1a094682686

- **Minute takers:** Ayoub Messos, Jensen, Jordi, Kai, Lauren, Lei Yixue, Luis, Mahdi, Motoyoshi Sekiya, Qiao, Qin, Richard, Roland, Sabine, Yuhang, Ziyang Xing. 

------------------------------

**IETF, ALTO Meeting: January 31, 2023**

**Agenda:**

- Round-table updates
- Chartered items
- Review of 'In Progress/Discussion' tasks: https://github.com/orgs/ietf-wg-alto/projects/1/views/2


**Minutes:**

Note Taker: Jensen

WG charter items:
- New transport (Richard):
  - Allow client to request information of each update queue; client can delete the queue later.
  - Incremental update queue
  - Use stack to maintain queue status
  - Kai: whether to reuse info in IRD
- OAM (Jensen):
- Deployment (Jordi & Luis):
  - Kai and his students have migrated Client/Server/App implementation table from the old wiki page
  - Luis will update telefonica deployment
WG Recharter:
  - Richard introduced the on-going network-aware, application-layer connection control work
  - Richard talked about a tree-structure resource constraint spec mentioned by CERN
    - Another potential use case: pods network traffic shaping
    - Whether it should be consider as a charter item in the future

------------------------------

**IETF, ALTO Meeting: January 24, 2023**

**Agenda:**

- Round-table updates
- Chartered items
- Review of 'In Progress/Discussion' tasks: https://github.com/orgs/ietf-wg-alto/projects/1/views/2


**Minutes:**

Transport:
- RY: targeting sending a new version today.

O&M:
- [RY] O&M is very overarching, a lot of content. Is it standard or experimental.
- [JZ] The target is standard
- [JR] Any plans to implement a portion of the O&M in the standard to OpenALTO?
- [RY] Would be very positive and we can consider

Deployments:
- [JR] reminder to update the wiki with your deployments info: https://wiki.ietf.org/en/group/ALTO/deployment

[RY] CERN/OpenALTO Project:
- Two pieces: (1) Scheduler and (2) data orchestrator
- ALTO for visibility and scheduling. 

- [QW] Time slot request for next IETF meeting
- [QW] Goal for next IETF meeting for transport should be working group last call
- [RY] We will push for it
- [QW] Who will be going to Japan? We need to start organizing.

[RY] Three directions:
- General path model for multidomain visibility. Can be presented at PANRG too. Presentation with CERN, NRP, etc.
- Collecting visibility info about environmental impact. For hackathon, to work together to get energy impact
- Trust

------------------------------

**IETF, ALTO Meeting: January 17, 2023**




------------------------------

**IETF, ALTO Meeting: January 10, 2023**

**Agenda:**

- Round-table updates
- Chartered items
- Update on ALTO Multi-Domain activity
- Review of 'In Progress/Discussion' tasks: https://github.com/orgs/ietf-wg-alto/projects/1/views/2


**Minutes:**

Note Taker: Roland

Participants:
Lauren, Kai, Chunshan Xiong, Jensen, Jordi, Mahdi, Marcos Schwarz, Motoyoshi Sekiya, Qin, Richard, Roland


*-**Round-table updates:**-*

Motoyoshi:
Preparation of a presentation regarding "Secure Trusted Networks" for the next IETF Bits & Bytes.

Roland:
Still working on ALTO new transport, no major updates compared to meeting last week.

Jordi:
Everyone who is working on ALTO deployment should update the Wiki, too.

Jensen:
OAM document, going over the document reviewing data model.

Chunshan (chunshan.xiong@cictmobile.com):
Background information on 5G in China, 5G service is currently not heavily used and operators want
to push the usage of 5G network. Segment Routing (SR) will be deployed and the 5G capabilities are increased
for use case like gaming. 
Question of Richard: What is the relevant capability of SR that is beneficial for this use cases?
Answer: Helping to reduce bandwidth for real-time communication. 

*Start Discussion:*

Discussion on congestion and congestion prediction and estimation of capacity on the path and if it is in line
with the ALTO bottleneck discussion in this group.

Congestion Control -> impact on RTT

Bottleneck Structure -> predict future behaviour

More offline-discussion is needed for clarification.

*End Discussion:*

Lauren:
Open-ALTO project came up with requirements on Multi-Domain.
e.g., easy to use, stable design, correctness.
Suggestions of the group regarding the requirements are welcome.
Ambition is to demonstrate for Rucio.
Idea to write a paper and go to IRTF.
Pseudo-Code is available and can be shared.

Qin:
Not ready to go for re-chartering of ALTO and need to finish already chartered items first.
New Transport still requires a revision.

Mahdi:
OAM still needs some updates and comments.

Conclusion: => prioritisation of chartered items is necessary.

------------------------------
