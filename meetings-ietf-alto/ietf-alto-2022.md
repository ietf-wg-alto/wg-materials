----
**Logistics:**

- **Meeting times:** Tue 9:00 to 10:00am EST

- **Location:** https://ietf.webex.com/ietf/j.php?MTID=ma0e97cc97c4cd71bb59cf1a094682686

- **Minute takers:** Jensen, Jordi, Kai, Luis, Mahdi, Qiao, Qin, Richard, Roland, Sabine.

- **Current minute taker:** Kai
 
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

**Minutes:**
John gave a wonderful talk on "5G End to End OTA PRP/NRP O-RAN testbed". The talk was mainly on the PRP/NRP platform. Designed to provide a composable and end-to-end programmable 5G platform, the platform is built with programmable switches and FPGAs to provide complete data plane programmability and Kubernetes to provide service orchestration. Some highlights include

- The platform now has 3 sites and 8 subnetworks
- Xilinx and Open-AIR put up a demo that FPGA acceleration achieves 10x speed-up in 5G streaming
- The 5G core is based on O-RAN but can potentially be compatible with other technologies. The platform also provides a field to test the interoperability of different 5G technologies
- The platform is running on top of a multi-domain network with multiple controllers but provides end-to-end SRv6 programmability through the SENSE/AutoGole fabric. There is also an ongoing effort to reprogram BGP for performance-aware flow steering
- The platform is used by NSF award-winning projects such as SAGE. Showcases include fire detection based on LoRA, multi-view camera stitching, and high frame-rate thermal dynamics

Questions and discussions (briefs):

- Jordi: What applications are running on the GPUs
- John: Pretty much any workload
- Jordi: How do you envision how ALTO/openALTO can be used in this architecture?
- John: ALTO can be used by the orchestrator for POD placement: create latency heatmap, split into 6 zones of service pools, and have k8s place the pods where they perform best. The clusters will have awareness to the network. The other application is when Rucio finds that a job cannot be delivered in time, reprogram BGP to get a different priority path. Have ALTO to help figure out the best paths to deliver among multiple channels
- Harvey: When the progress is insufficient, how does the job get accelerated? When you have an L2 overlay, what you do is to moderate the flow rate? Which tools we are going to use to accelerate the rate? 
- John: Creating multiple SENSE paths. Each one with a different QoS setting. You can tell BGP to transit the flow from one path to another.
- Harvey: We can use FireQoS (?) to moderate the rate
- John: This is one way to solve the problem. There are other options, e.g., using P4 switches.
- Jordi: We think of this as a really great platform to deploy the job in the WG. What John and his team is building is a highly controllable and programmable network. Some of the use cases are related to the drafts that we are writing, e.g., how to optimize applications running in the edge clouds. John mentioned the notion of visibility, intelligence, and control. Use ALTO to build a latency heatmap for POD placement. We look at this as a way to deploy the ALTO/openALTO work.
- Luis: How is SRv6 used in the platform? 
- John: We want to have SRv6 end-to-end. Calico VPP is the overlay network used in K8s. 
- Luis: Tuning the BGP, do you consider this with traffic engineering?
- John: What functions are missing in Calico VPP is another question. VPN is already there, some form of segment routing works but what actually works needs to be understood. 
- Luis: We are also working on O-ran. An ongoing work is to expose topology to help the O-RAN management.
- Richard: Potential architecture of overall network. Two types: private network, and public network (Internet). Do you envision this is a specific architecture or it can be generic? 
- John: We are providing a garden of architectures. We have a good commitment of latest accelerators and embrace constant changes by adding the new capabilities.
- Richard: ALTO path vector is a generalization of the BGP protocol. It's great that we have generic architecture.
- John: What we are looking into is to make k8s a network-aware orchestrator based on the ALTO protocol. We use namespace and federated through namespace.
- Harvey: To start imagine composable infra where different subsystems need to work under different contexts/use cases. Tools like the path vector which has the abstract concept of cost which allows stateful decisions. There is no single architecture. Success of SENSE is to engage many different regions of the world and deploy things. Get common things by doing. Start pursuing composable architecture.
- Richard: K8s is using predicates + ranking architecture. 
- Harvey: John mentioned few things. If you have an approaching deadline, it's not just a point decision, it's a lifecycle management system.
- John: We've already extended the k8s scheduler. Give priorities to different namespaces, different nodes. Inform the state of the workflow, with daemons integrated into nautilus. We have instrumented everything to discover what the cluster is telling us. Instead of having application to figure out what is best, we can have dedicated containers to do that.
- Richard: Do you consider the state sharing in etcd?
- John: Shared state is federated through the etcd
- Jordi: We track the [meeting minutes](https://github.com/ietf-wg-alto/wg-materials/blob/main/meetings-ietf-alto/ietf-openalto-5G-PRP-NRP-ORAN-2022.md) for the meeting on Monday. Putting the demo about the integration in SC'22.

The WG also provides updates on the board items.

Cost Mode: 
- Kai: cost mode is now in IEST evaluation

ANE name format:
- Sabine: follow option 1 on the ANE name format issue 

New transport:
- Richard: a new version will be uploaded
- Qin: once the new version is uploaded, it should be sent to HTTP2 WG for review

OAM:
- Jensen: dig into solving the configuration part
- Qin: if there is any open issue, discuss on the mailing list

NAI:
- Luis: already have 5 submissions, advertised again. The deadline is officially May 25

John mentioned that he and his team will continue to work on the Jupyter lab + ALTO integration, which will make PRP/NRP as a platform for future ALTO development/testing/hackathons.

WIP

----

**IETF ALTO Meeting: May 10, 2022**

**Agenda:**

- Reminder that using Github scrum is not a substitute for using ALTO mailing list. 
  Good practice: use ALTO mailing list with pointers to Github tickets.
  
- Confirm the NAI deadline
  
- Review of 'In Progress/Discussion' tasks: https://github.com/orgs/ietf-wg-alto/projects/1/views/2

**Minutes:**

Note Taker: Jordi Ros-Giralt

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
