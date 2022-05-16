----
**Logistics:**

- **Meeting times:** Tue 9:00 to 10:00am EST

- **Location:** https://ietf.webex.com/ietf/j.php?MTID=ma0e97cc97c4cd71bb59cf1a094682686

- **Minute takers:** Jensen, Jordi, Kai, Luis, Mahdi, Qiao, Qin, Richard, Roland, Sabine.

- **Current minute taker:** Jensen


 
----
**Future Meeting (Planning): IETF ALTO Meeting: May 24, 2022**

**Agenda:**

- Tentative: Wireless physcical layer exposure + ALTO

----
**Future Meeting (Planning): IETF ALTO Meeting: May 31, 2022**

**Agenda:**

- Tentative: Modeling progress (Discrete event simulation, continuous simulation, packet simulation) + ALTO

----

**Future Meeting (Planning): IETF ALTO Meeting: June 7, 2022**

**Agenda:**

- Tentative: Application-driven in-network measurements + ALTO

----
**IETF ALTO Meeting: May 17, 2022**

**Agenda:**

- John Graham 5G Project in PRP: IETF ALTO, SRv6, Bottleneck Structure Graphs
- Review of 'In Progress/Discussion' tasks: https://github.com/orgs/ietf-wg-alto/projects/1/views/2

----

**IETF ALTO Meeting: May 10, 2022**

**Agenda:**

- Reminder that using Github scrum is not a substitute for using ALTO mailing list. 
  Good practice: use ALTO mailing list with pointers to Github tickets.
  
- Confirm the NAI deadline
  
- Review of 'In Progress/Discussion' tasks: https://github.com/orgs/ietf-wg-alto/projects/1/views/2

**Minutes:**

- ANE name: https://github.com/ietf-wg-alto/draft-ietf-alto-unified-props-new/issues/1  
- Will take simple action 
- Requested 2-hour slot for IETF 114 
- Invite people to present first in our weekly meeting, then to the IETF  
- Major trend in community how to understand how a network works
- ALTO is modeling tool 
- Combination of 3: visibility, intelligence, controllability 
- Discrete simulation is superslow 
- Modeling: accuracy issue 
- Continuous discrete differential equation simulation, could be good for ALTO 
- ALTO just focuses on query interface, you need to build the database 
- For long we care a lot about northbound, we need to care more about southbound 
- We have ALTO OAM 
- Invite key people to discuss this to build the model 
- MIT / digital twin 
- Use ALTO / MOWIE for gaming 
- Solve lack of interaction with 3GPP 
- Flow level continuous simulator 
- We also want to cover compute-aware networking, network as a service. We need to balance. 
- A third direction: Application specifies needs using a language and compile it down to the network 

----

**IETF ALTO Meeting: May 3, 2022**

**Agenda:**

- Update on new bookkeeping records for agenda/minutes 
- Update around the table
- Minutes/Feedback from DOMA meeting on April 27
- WG document: OAM
- NAI submissions

**Minutes:**

Note Taker: Jensen Zhang

Jordi introduced how the current meeting minutes workflow works.

> People will rotate to be the note taker. Jensen will be the note taker for this time.

A quick round table:
- Jordi and Richard presented ALTO in DOMA meeting. Kai and many other people also helped the preparation of the presentation.
- Jensen organized issues to meet the next IETF milestone for the ALTO O&M draft.
- Luis updated the NAI workshop organization.
- Mahdi updated the documentation for OpenALTO tutorial.
- Qiao mentioned that he and his students were working on a multi-domain work for the coming NAI submission.
- Roland updated progress on the new transport update.
- Sabine updated her work on a new potential extension for ALTO.
- Richard brought updates about conversations with both DOMA/CERN and military people.

Sabine raised an issue for ANE name:
- Connected to issue #22: https://github.com/ietf-wg-alto/wg-materials/issues/22
- The specification of ANE name in the PV document reuses the PID name encoding in RFC7285, which reserves the usage of '.' seperator. The example in Sec 10.9 may violate the specification.
- Kai gave comments on potential solutions. But need futher discussions offline.
- Richard posted a question: The current inter-domain protocol, BGP, is designed on PV protocol, which is based on the dynamic programming algorithm. It may not be efficient for nowadays applications. Can we redesign the propogation process for the inter-domain protocol?
  - Richard will explain this question clearly after the meeting.

Jordi helped to go over the other in-progress items in the ALTO Srum Dashboard.

Kai suggested to improve the meeting process, e.g., put a time limit for each item, and move some low-priority work offline.
