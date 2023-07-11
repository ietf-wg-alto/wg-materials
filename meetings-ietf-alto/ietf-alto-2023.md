----
**Logistics:**

- **Meeting times:** Tue 9:00 to 10:00am EST

- **Location:** https://ietf.webex.com/ietf/j.php?MTID=ma0e97cc97c4cd71bb59cf1a094682686

- **Minute takers:** Ayoub Messos, Jensen, Jordi, Kai, Lauren, Lei Yixue, Luis, Mahdi, Motoyoshi Sekiya, Qiao, Qin, Richard, Roland, Sabine, Tong Meng, Yuhang, Ziyang Xing. 

------------------------------

**IETF, ALTO Meeting: July 11, 2023**

**Agenda**

- Address comments from RFC Editor on ALTO Performance Metrics drafts.
- IETF 117 work plan. Goal is to sort out concrete proposal to provide input to rechartering. The number of recharter items should be limited to one or two based on discussion. Med suggests us to focus on motivation, problem description and charter item proposal. We will not go into detailed to discuss the solution space. ALTO deployment catalyst will be the focus. 

- ALTO Future Work: 
  - List of topics: https://mailarchive.ietf.org/arch/msg/alto/uIFD6Dhikfu4J4PYcpJTbsiXbnE/
    - Topic A: https://mailarchive.ietf.org/arch/msg/alto/nSBb2fJwwEEEeZ-Xxw-OmHhJdTs/ 
    - Topic B: https://mailarchive.ietf.org/arch/msg/alto/IXYPC1joF17oPJ7MWz5NDplAqKk/
    - Topic C: WIP
    - Topic D: https://mailarchive.ietf.org/arch/msg/alto/IEAyQ2kv49AvT1hIGfYkHWLxisY/
  - Root document for topics discussion: https://docs.google.com/document/d/1rpziU7NZEE8f84XkJSjMhEIHUA5G7rXkGB5c_7UFxUY/edit
  - Root ticket for ALTO future work proposals: https://github.com/ietf-wg-alto/wg-materials/blob/main/FutureALTO/alto-direction-of-work.md
- Preps for IETF 117:
  - Drafts and presentations that the ALTO group plans to work on
  - Hackathon projects
  - Agenda

**Minutes:** (*Note taker: Kai*)
Focus: Preparation of IETF 117 and recharter conversation

Action items:

- Richard will set up the meeting with CATS and send an invite to the mailing list
- Identify the leader of the BGP community document. Come up with two concrete proposals.(Richard volunteers)
- Chunchi will engage with Ayoub to work on the item.

Discussions:

- Meeting with CATS on how to coordinate between Luis's document and CATS's document(s)
  - Metrics related to computing are defined in both working groups and need to be coordinated
  - Adrian will have 5 min to present at ALTO during IETF 117
  - Richard suggests having a working session with CATS members earlier before IETF
  - Sabine: The CATS draft does not list the metrics. CATS is looking at low-level metrics for traffic steering, not necessarily the same way in ALTO.
  - Sabine: Both approaches are complementary. It is necessary to define the intersection and the (difference). For intersected metrics, there might be inter-dependency between the two WGs. For unrelated metrics, both WG can proceed on their own.
- IETF 117 agenda
  - Jordi: Focus on priorities. 1 or 2 topics in IETF:
    1. Suggestion by Med: motivation, problem description and charter item proposal
    2. Deployment catalyst.
  - Deployment catalyst discussion:
    - Richard: A large amount of successful protocols are about HOW not WHAT. Deployment catalyst is difficult because it is missing HOW in ALTO.
    - Qin: (Agree with the argument) To promote the ALTO deployment, focus on integration and operation.
    - Jordi suggests targeting this as an informational document
  - BGP community/BGP-LS & ALTO:
    - Qin: Propose BGP community for ALTO map and BGP-LS integration with ALTO. Discuss the problem space and motivation.
    - Qin: Luis might be overloaded and another person is needed to lead the efforts
    - Richard volunteered to take the responsibility
  - Discussion on integration with compute
    - Qin: Concern is that IETF does not have protocols to connect computation.
    - Jordi: Two elements: 1. How to get information. 2. How to expose that information. There is a need to understand the space with some informational documents.
    - Richard: Protocol is connecting the dots: you have something already and define how things can be done. But no dots for computing in IETF now.
    - Discussion by Richard, Jorid and Qin suggests an investigation of existing standards on exposing compute (as an informational document) is highly useful
      - initial sources: COINRG, CATS (in progress), ETSI, 5G,
      - Jordi suggested having a survey of use cases to obtain a list of required metrics
      - Qin suggested the boundary between ALTO and CATS is that CATS defines the metrics and common abstractions of computing while ALTO defines how to connect/query the metrics (?)
    - Jordi suggested focusing on new elements that weren't covered in IETF 116 for this topic
  - Green networking
    - Richard: A large concern is energy consuming. Will that be a good starting metric to work on? 
    - Qin: IETF already has this energy mib (?) IETF has a side meeting. Green networking has been discussed in nmrg.
  - Security
    - Qin: The security part by Fujitsu is still in the research stage. Luis has prepared some slides to discuss security consolidation. Potential discuss on using JOSE object for ALTO.
    - Chunchi will take the lead for integration ALTO with JOSE (?) and engage Ayoub.

**IETF, ALTO Meeting: June 27, 2023**

**Minutes:** (*Note taker: Ryan*)
The meeting began with a discussion of IETF 117 logistics, then covered the four directions the WG is working towards (A,B,C,D), and then concluded by discussing three specific hackathon projects. 

IETF 117 Logistics (9:00-9:20)
- Although the WG hoped to get a 1.5 hour block, it was assigned a 1-hour block for IETF 117, as the revision was late. The scheduled time is Monday, July 24, from 17:30-18:30 pm PT (local time) (Qin)
- Future discussions
	- New charter/directions
	- New tradition of looking back (Richard)
	- Adding security, encoders, transport on top of data sources, and BGP.

Current state of “​​Topic A: Integration of new data sources and their exposure.”
- Rephrasing of current title: 
	- New data sources suggests that the focus is on getting information from southbound APIs (Richard)
	- Concerns about getting information (Sabine)
	- Data metrics (Kai)
	- Possible overlaps with maintenance (direction B)
	- TODO: follow the suggestion by the WG chairs.
- Infrastructure
	- Model of sites with resources, and links connecting sites. 
	- Resources are compute, storage, and transport.
	- Connectivity is a relatively uniform resource, whereas compute can be heterogeneous (CPUs, GPUs, TPUs, etc.).
- Kubernetes as a solution very similar to ALTO
	-- Node = PID, but Kubernetes has attributes/labels that help handle heterogeneity (https://kubernetes.io/docs/concepts/overview/working-with-objects/labels/)
	- Commands such as exists/contains
	- ETCD ~ ALTO Server
	- openstack/opennebula
	- Visibility. Kubernetes low-level pods
	- ALTO offers possibility of hierarchy of metrics with several abstraction levels (Sabine)
		- KPIs
	- Resources at edge vs. cloud (Jordi)
		- At cloud they can be packaged nicely
		- Dealing with finite control. Selecting which resources to use is a combinatorial problem with exponential growth in difficulty. What is meaningful/maintainable.
		- Label, selector (Kubernetes) for combinatorial problems
		- Integral vs. link
		- A cloud related project: https://www.caida.org/projects/cloudtrace/ (Richard)
- Server Edge Discovery (existing draft on topic)
	- Modeling: constant map, property map
	- Online networker
- Edge Service Draft
	- 1: New use case motivations
	- 2: New capabilities

Current state of “Topic B: Maintenance of ALTO protocol”
- BGP Community (Qin)
- How related to PID. What will solution look like (Qin)?
- BGP LS successful. A possibility is to BGP-ALTO as north bound: using BGP to communicate network map, cost map.
- Luis clarifies that there are two aspects of ALTO security: the security of ALTO protocol in operations, and using ALTO to convey security information. Topic B should be the first aspect and Topic C for the second aspect (Ayoub).

Current state of “Topic C: Trusted related ALTO properties”
- New mailing list created (Ayoub) so that there is now one for all four directions
- New trust and security. New solutions and services.
- Suggestion to add summary to the [planning document](https://docs.google.com/document/d/1rpziU7NZEE8f84XkJSjMhEIHUA5G7rXkGB5c_7UFxUY/edit#heading=h.wbkp0e3rua1) (Jordi)

Current state of “Topic D: New architectural extensions”
- NA. Not discussed.

Hackathon items
- A. Visibility of cost map w/ perfSONAR
	- Latency, bandwidth
	- Iperf3 
	- Trace route for multi hops
	- ALTO server on perfSONAR w/ elastic search
	- OWP3
- B: build selection Rucio algorithm. 
	- Use distances cost map from ALTO and source selection
- C: FTS scheduling control
	- Using alto 
	- [Cautious] model
	- Control bandwidth partition inside large autonomous system cluster 

TODO: Register hackathon projects on the IETF community wiki: 
https://wiki.ietf.org/en/meeting/117/hackathon

Links from chat:
- a cloud related project: https://www.caida.org/projects/cloudtrace/
- Reference on services and modeling: https://github.com/esnet/nml-mrml/blob/master/reference/NML-Topology-0001.pdf

------------------------------

**IETF, ALTO Meeting: June 20, 2023**

**Agenda:**

- Transport and OAM documents
    - Transport: https://github.com/ietf-wg-alto/draft-ietf-alto-new-transport/issues 
- OAM: https://github.com/ietf-wg-alto/draft-ietf-alto-oam-yang/issues 
- ALTO Future Work: 
    https://mailarchive.ietf.org/arch/msg/alto/uIFD6Dhikfu4J4PYcpJTbsiXbnE/
    https://github.com/ietf-wg-alto/wg-materials/blob/main/FutureALTO/alto-direction-of-work.md
- Preps for IETF 117:
  - Drafts and presentations that the ALTO group plans to work on
  - Agenda
- New revision of Green Networking Metrics draft in opsawg: https://datatracker.ietf.org/doc/draft-cx-opsawg-green-metrics/

**Minutes**

*Note taker: Richard

- Charter documents: transport and OAM updates
  - OAM: Jensen and Med had a discussion on the draft and submit the revision to IESG. The document is now waiting for AD review.
  - Transport: Richard sent a note to Martin Thompson, to provide the justification on introducing server push using PUSH PROMISE. It includes two basic reasonings: lower load, and the feature is optional; Kai updated that Med sent two pull requests and sent the latest version for AD review, and wait for updates.

- Updates on future work on ALTO
  - Overview: Jordi started with an update on the planning: Please follow the ongoing conversation on the WG mailing list initiated by Sabine, engaged by Jordi and Luis; the WG welcomes conversations by all; please socialize the ideas; leadership is important and please take ownership; this WG meets each week, and we do not know any other IETF WG that meets each week, but because we meet each week, we do not use the mailing list, which may appear to be inactive by those not attending the weekly meeting.

  - Individual topics:
      - Jordi summarized that from the mailing list, item 3 appears to be the most preferred; please do discussions, propose a charter item and then write documents; The goal is to go to 117 and should be prepared. 
      - Richard commented that one of his focus points will be on data sources, which can be more informational than standard. Luis advised that there can be two types of approaches: bottom-up (individuals propose ideas), and top-down (chairs/AD guidance).  
     - Luis suggests that we should take a look at chair-mentioned items such as BGP communities, and security; mid-term: such as data sources, please go to the mailing list.

- Work organization: Meeting notes work plan: Ayoub gave the suggestion that note taker shares the note to the mailing list, some kind of annotated meeting minutes. Roland clarified that the sharing notes can be double sent, or summary/highlights, or up to note taker. Organizing discussions: Luis/Jordi: email as record, GitHub tickets to organize; Jordi creates 4 tickets, and puts links to doc.

- Issues, leads, and working documents: 
  - Topic A:
     - GitHub issue: https://github.com/ietf-wg-alto/wg-materials/issues/48
     - Topic coordinator: Jordi, Kai

   - Topic B:
     - GitHub: https://github.com/ietf-wg-alto/wg-materials/issues/49 
     - Topic coordinator: Roland, Sabine

   - Topic C:
     - GitHub: https://github.com/ietf-wg-alto/wg-materials/issues/50
     - Topic coordinator: Ayoub, Junichi, Motoyoshi
   
   - Topic D:
      - GitHub: https://github.com/ietf-wg-alto/wg-materials/issues/51
      - Coordinator: Luis, Jordi
        
  - Discussion Google doc:
  	- https://docs.google.com/document/d/1rpziU7NZEE8f84XkJSjMhEIHUA5G7rXkGB5c_7UFxUY/edit?usp=sharing

  - Goals: Enabling conversations and concrete documents (compute, edge service, etc), need to focus; real good way to make progress is internet-draft (ID) as ground truth, from dynamic to stable, with focus on writing drafts for concrete results).

------------------------------

**IETF, ALTO Meeting: June 13, 2023**

**Agenda:**

- Progress of OAM and new transport drafts
- Potential topics for Proposal #3: Support ALTO Extensions for the New Industry Needs 
- Plan to participate hackathon

**Minutes**

*Note taker: Dong, Shenshen, Ryan*

Progress of drafts:
- New Transport (Kai):
    - A new version is uploaded
    - Most of the issues were addressed
    - Use different status codes to indicate different types of errors
    - Use a single connection for each session
- OAM (Jenson):
    - Upload a new version of OAM
    - Provide two data modules, need to clarify the two yang modules

Additional items:
- Richard: 
    - Use server push to reduce latency and server load
    - Propose to use of Informational North Bound API
    - Consider cascading alto for multi-domain setting
- Sabine: 
    - Decide how kick start the discussion for use cases, also related to CATS
    - Use positioning to show where alto is better, where others(CATS) is better.
- Jordi: 
    - Connect edge framework for use cases with open-source community
- Qin:
    - Try to engage with cats people, integration new data sources, complement alto as extensions
    - Reconsider collaboration with 3gpp, maybe dig into Movie for looking for new performance metrics

------------------------------

**IETF, ALTO Meeting: June 6, 2023**

**Agenda:**
- Working item
- Future of WG
- cats metrics discussion

**Minutes**

*Note taker: Richard*

- WGLC last call is over
- OAM updates: Additional reviews, including individual reviews by Mahdi, and comments by Med
Plan is to provide a new version by this week. 

- Transport updates: new comment by Mahdi, and one from Meng from Huawei. Mentioned reviews by Qiufang, as WG last call reviews. Med created github issues. Kai submitted revisions to address the issues. One technical issue (#30) on the github, adding paragraph, why creating a single connection. Spencer is ok with ART review. Richard will add the paragraph on why single connection.

- Future of the WG: https://github.com/ietf-wg-alto/wg-materials/blob/main/FutureALTO/alto-direction-of-work.md
  - Update: Med initial two directions, and Jordi added the third
  - Richard: potential to think about decouple concepts (e.g., distance), drivers (BGP-LS), and bits-and-bytes (ALTO protocol, or spreadsheet)
  - Sabine: what people like/dislike the encoding, or there exist other bodies; people want interop info. Do we have mechanism to easily translate into standard format? How the mechanisms such as meta info are used/needed by infrastructure operators? We should look into some informational documents on ALTO encoding. CATS can benefit from querying ALTO servers. A more normative way to look the proposals in direction 3.
  - Jordi: Chairs directed the WG to check why ALTO can integarte with data sources. There is an element that we can enhance the adoption of the protocol. Compute is on the standard track. Sabine: to take into account, already in the ALTO edge services, how to use ALTO info? We need several levels of abstractions. How feasible to obtain the info?
  - Ayoub: Interested in Proposal #3. Have practical discussions on the 3 proposed directions. Put pros and cons for each proposed direction. 
  - Jordi: Direction 2 is not ideal. WG is the right WG to attack the important problem of application-network integration. Not optimal from architecture or engieering. For the next decade, one mission is to build edge cloud infrastructure. To do a really good job, we really need visibility (where is compute, networking) to the infrastructure. Homework: (1) work on the proposal level; to work on the edge services draft, to position the compute the draft for ALTO, and also the performance metrics draft; (2) Fujitsu puts a security draft, to have security in the new charter. Work offline, w/ Luis and others. Sabine two questions: (1) What is the take, by the Fujitsu team, on the security considerations on all recent related documents/RFCs? Ayoub: So far not bottom up, can discuss more. Take a look at risks at the RFC security sections, what can be extended/analyzed. Motoyoshi: if a new architecture (e.g., edge cloud) comes, what are the security concerns?
  - Schedule a meeting w/ Sabine, Luis and Jordi on compute/edge.
  - Bring some visbility to the WG. Sabine can summarize the comments to the WG mailing list.
  - Ayoub/Sabine: Wednesday 9:00-9:30 am meeting.
- Energy efficiency: Sabine considers this crucial. Roland: Many efforts on energy in DT operations. Although each piece can be small, they together can make a difference. 

------------------------------

**IETF, ALTO Meeting: May 23th, 2023**

**Agenda:**

- Retrospective on ALTO Interim #4
- 2nd WGLC on new transport and OAM docs
- Review outstanding WGLC github tickets / pull requests:  
  - Transport: https://github.com/ietf-wg-alto/draft-ietf-alto-new-transport/issues 
  - OAM: https://github.com/ietf-wg-alto/draft-ietf-alto-oam-yang/issues 
- Preparations for the forthcoming ALTO Interim (May 30th at 10am EST) Meeting #5

**Minutes**

*Note taker: Jensen*

Summary of last interim meeting:
- OAM:
  - Close to ready.
  - TODO: upload a new version and start 2nd round WGLC.
- New transport:
  - TODO: schedule a meeting with Martin Thompson to discuss the update soon.

Preparation for 2nd WGLC:

- OAM:
  - Received 4 more thorough reviews and one more quick review.
  - All reivews have been replied.
  - yry: There are a lot of design decision made from multiple design choices without clarification. Will IESG fight back?
  - Qin: If IESG provides any concrete concerns, we can disucss and address them. WG members can also send their concerns and discuss on the mailing list.
  - The basic principle of this document is to align with the base protocol but also allowed to be extended by the private (vendor) modules.
- New transport:
  - Kai went over the changes that addressed comments from Adrian and Qiufang.
  - The changes have been updated to GitHub: https://github.com/ietf-wg-alto/draft-ietf-alto-new-transport

Peparation for next interim meeting:
- Trusted network
- Data source collection

Additional items:
- Richard mentioned netbox and webhook method that can be helpful for new transport.
  - Richard and John Graham will discuss netbox related topic next week.
- Potential updates for individual drafts:
  - Jordi will update the service edge draft.
- Sabine suggested that we should engage CATS WG more.


------------------------------

**IETF, ALTO Meeting: May 16th, 2023**

**Agenda:**

- Preparation of the forthcoming ALTO Interim (May 16h at 10am EST) Meeting #4


**Minutes**

*Note taker: Richard*

- Transport updates (Kai)
  - Need to get updates from reviewers; 
  - TSV review by Barnard and wait for update
  - HTTP review meeting with Martin Thompson
  - Med suggests that transport design team should discuss with Martin Thompson and clarify design motivation and choice

- OAM updates (Jensen)
  - Qin: updates on security, agrees with Med, need YANG expert to close the issue
  - Almost closes all of the reviews; 
  - Open issue: Clarify typedef (proposal remove pattern)
  - Open issue: add notification; Qin comment: check alarms YANG data model and see if we can reuse
  - Qin: close the 3 open issues as soon as possible.

- Planning for the next interim meeting (Ayoub, Qin)
  - Flesh out the security/trust during the final interim meeting; please consider multi-domain
  
------------------------------

**IETF, ALTO Meeting: May 9th, 2023**

**Agenda:**

- Retrospective on ALTO Interim #3
  - Integration with data sources: https://docs.google.com/spreadsheets/d/1P4GrhQz_t17jIWg-3b1ycldhBWEEgIAAUZe2vjeO_1U/edit#gid=0
  - Reviving draft-contreras-alto-bgp-communities & draft-zhang-alto-bgp-ls:
    - https://datatracker.ietf.org/doc/html/draft-contreras-alto-bgp-communities-00
    - https://datatracker.ietf.org/doc/html/draft-zhang-alto-bgp-ls
  - Action Items: Compute metrics
- ALTO for Querying LMAP Results:
    - https://datatracker.ietf.org/doc/draft-xie-alto-lmap/
- CATS metrics discussion
- Review of outstanding WGLC github tickets / pull requests:
	- Transport: https://github.com/ietf-wg-alto/draft-ietf-alto-new-transport/issues
	- OAM: https://github.com/ietf-wg-alto/draft-ietf-alto-oam-yang/issues
- Preparation of the forthcoming ALTO Interim (May 16h at 10am EST) Meeting #4


**Minutes**

*Note taker: Roland*


Retrospective on ALT Interim #3:

- Discussion regarding the impression of Interim #3
- Action Items: Compute metrics
	
	
ALTO for Querying LMAP Results:

- Presentation of Qiufang Ma regarding LMAP, https://github.com/QiufangMa/alto-lmap
- LMAP: Large-Scale Measurement of Broadband Performance
- Proposal of measurement framework to improve QoE
- Check if LMAP can be an interesting WG item
- Questions & ideas for next versions: 
	- Information about motivation and where LMAP is used.
	- How to correlate the measurements, handling of PIDs?
	- Explain why this data source is relevant?
	- How integration with data sources simplifies ATLO deployments?
	- Section 6.2 - additional cost map metrics - is interesting.
	- Add chapter regarding security considerations.


CATS metrics discussion:

- See: https://mailarchive.ietf.org/arch/msg/cats/KEovVYox1iWzlyJ54dmmY2xdB1M/
- Small group had a call last week to discuss metrics for CATS
- draft-du-cats-computing-modeling-description
- CATS is oriented to traffic steering
- Use case "delay" (round-trip, one-way) has been identified
- Proposal: network and service delay metric both


WG Charter Items:
- New Transport:
  - ART review triggered
- OAM:
  - Discussions on the mailing list regarding security
  - Upload of new version soon


Interim Meeting Preparation:
- Discussion and preparation next week in ALTO weekly, 30 minutes might be sufficient before Interim
- Please upload the slides ahead of the meeting



------------------------------
**IETF, ALTO Meeting: May 2nd, 2023**

**Agenda:**

- Review outstanding WGLC github tickets / pull requests: 
  - Transport: https://github.com/ietf-wg-alto/draft-ietf-alto-new-transport/issues
  - OAM: https://github.com/ietf-wg-alto/draft-ietf-alto-oam-yang/issues
- Preparations for the forthcoming ALTO Interim (May 3rd at 10am EST) Meeting #3:
  - Integration with data sources: https://docs.google.com/spreadsheets/d/1P4GrhQz_t17jIWg-3b1ycldhBWEEgIAAUZe2vjeO_1U/edit#gid=0
  - Reviving draft-contreras-alto-bgp-communities & draft-zhang-alto-bgp-ls:
    - https://datatracker.ietf.org/doc/html/draft-contreras-alto-bgp-communities-00
    - https://datatracker.ietf.org/doc/html/draft-zhang-alto-bgp-ls
- Group's work awareness:
  - Internet Protocol Journal article on ALTO accepted for publication

**Minutes**

*Note taker: Jensen*

WG Charter Items:

- New Transport:
  - Kai and Lachlan have replied to WGLC reviews. Waiting for feedback
  - Richard will discuss with Martin Thomathon
- OAM:
  - All the director reviews have been addressed and got confirmation.
  - Some remaining chair reviews are to be closed soon
  - A new version is target to be uploaded in this week

Interim Meeting Preparation:

- Data Sources:
  - Jordi and Luis will summarize the information collected in the spreadsheet
  - Feedback from mailing list are merged
- BGP-LS
  - Jensen will lead the discussion about the complete solution of generation ALTO maps using BGP-LS
  - Kai suggested to focus on the general process using common information model of BGP-LS
  - Richard: how to handle multi-domain?
  - Qin: shall we bring the BGP-LS YANG data model extension to IETF?
  - Richard will invite Danny from BENOCS to join the discussion and bring the insight and experience from FlowDirector implementation
- BGP Community:
  - Luis will prepare slides and lead the discussion about how to leverage BGP community information in ALTO
- Logistics:
  - Qin: everyone please tests the meetecho connection before the interim meeting


------------------------------
**IETF, ALTO Meeting: April 25th, 2023**

**Agenda:**

- Review outstanding WGLC github tickets / pull requests: 
    - Transport: https://github.com/ietf-wg-alto/draft-ietf-alto-new-transport/issues
    - OAM: https://github.com/ietf-wg-alto/draft-ietf-alto-oam-yang/issues
- Preparations for the forthcoming ALTO Interim Meeting #3:
   - Integration with data sources: https://docs.google.com/spreadsheets/d/1P4GrhQz_t17jIWg-3b1ycldhBWEEgIAAUZe2vjeO_1U/edit#gid=0

**Minutes**

*Note taker: Kai*

Transport:

- negotiation of HTTP versions
- Richard: what is the principle for the solutions?
- Qin: The principle is to reuse the IRD to announce any capabilities.
- Kai: There are two cases: For https services, version negotiation can be done using TLS; for http services, HTTP versions that are supported by the server are announced through the IRD.
- Qin: Need to confirm with Spencer before getting back to Martin.
- Lachlan: We have moved forward with the options for removing the metadata.

Logistics:

- Jordi: We need to forward the activities from the github to the mailing list.
- Qin: Subscribing the mailing list to the github issues may be too noisy.
- Jordi: I can forward the mails to the mailing list.

OAM:

- Jensen: Two issues raised in the OPSDIR review
- Jensen: Not sure about the scalability issue.
- Jensen: Two kinds of scalabilities: 1) the number of entities in a domain or even multi-domain, or 2) large number of client connections. Need to include load-balancing configurations in the model. Question is whether to include such configurations in the document.
- Qin: It could be deploying multiple server in multiple domain or in a single domain. The impression is to support multi-server deployment -- each in one domain -- and support server-server communication. 
- Jensen: For multi-domain setting, the model does not provide a single mechanism. Each domain will have their own model(s). For a single domain, load-balancing may be configured.
- Qin: Confirm with Dan about the issue. If the issue is on server-server communication, need to discuss with Martin and get feedback.
- Richard: Have multiple OAM servers -- usually for scalability and availability. Two choices: caching or replication. Which one?
- Jensen: How the data model can address the scalability issue?
- Kai: I just checked the review and it seems that the scalability Dan is referring to is from a paragraph in the current document. Seems that we need to clarify what the word means rather than give a solution.
- Richard: We need to clarify what scalability means in the paragraph.

Data sources:

Jordi: Call for participation and feedback for the data source document.
Ayoub: What kind of inputs are required? 3, 8 and 11 are related to the interest of Fujitsu.
Luis: If there are particular comments, add comments to the google sheet.
Ayoub: Find use cases?
Luis: Use cases, extensions or problems/limitations.
Ayoub: Have local discussions on how to integrate trust in the ALTO protocol.
Qin: Seems that the document is trying to define a framework to integrate different data sources into ALTO. BGP-LS and BGP communities are missing pieces in the ALTO protocol, for example, creating PID for BGP community.
Luis: We are in the first step to understand potential data sources ("what") before designing how to incorperate these data sources ("how").
Qin: There are some solutions for some of the data sources. What is missing is the metrics for the trust.
Jordi: The document is providing an umbrella for potential data sources. What can be done is to zoom in some of the data sources. Two-level approach: first define "what" and then work on solutions on specific data sources.


------------------------------
**IETF, ALTO Meeting: April 18th, 2023**

**Agenda:**

- Review outstanding WGLC github tickets / pull requests: 
    - Transport: https://github.com/ietf-wg-alto/draft-ietf-alto-new-transport/issues
    - OAM: https://github.com/ietf-wg-alto/draft-ietf-alto-oam-yang/issues
- Preparations for the forthcoming ALTO Interim Meeting #3:
   - Integration with data sources: https://docs.google.com/spreadsheets/d/1P4GrhQz_t17jIWg-3b1ycldhBWEEgIAAUZe2vjeO_1U/edit#gid=0


**Detailed Agenda on April 18th:**

- Round Table over current activities
- Interim Meeting


**Minutes:**

Note Taker: Roland

**Round Table:**

Transport Document

	Lachlan is updating the document including feedback
	Issues:
	- Session Semantics
	- Concerns from Martin Duke: should not give the client the whole meta data
	- Concurrency
	Conclusion:
	- Have a dedicated session regarding the issues in a small round and forward conclusions on the list
	
OAM Document

	Yangdoctors review has been done
	Issues:
	- Meta data values
	
Priorities are to finalize and close both documents as requested by the WG Chairs.

**Interim Meeting:**
On May 3rd is the next interim meeting, see info on mailing list.
Material: https://docs.google.com/spreadsheets/d/1P4GrhQz_t17jIWg-3b1ycldhBWEEgIAAUZe2vjeO_1U/edit#gid=0

	- Variety of information and data sources that could be of interest for ALTO
	- Discussion with the chairs in IETF is ongoing e.g., bottleneck structures
	- Idea to strengthen how ALTO can be used better in production environment
	- Comments:
		- long term approach, ALTO can play the role of NETWORK EXPOSURE FUNCTION
		- network and cost map might be limited use cases
		- comments are welcome i.e., feedback in our next week meeting
		- check: bgp communities and LS to revisit both draft as suggested by the WG Chairs
			(draft-contreras-alto-bgp-communities & draft-zhang-alto-bgp-ls)
		
**Potential Future Activities:**
	What is the next programmable frontier e.g., layer 4 as control point? 
	Please, think about it.

------------------------------

**IETF, ALTO Meeting: March 21th, 2023**

**Agenda:**

- Dashboard: https://github.com/orgs/ietf-wg-alto/projects/1/views/2
- IETF 116 Agenda
- Chartered items
- Deployment
- Hackathon
- Recharter items for IETF 116
  - Multi-domain use cases
  - compute and network information exposure
  - Trust


**Minutes:**

Note Taker: Jensen

- IETF 116 Meeting Agenda
  - Qin: not only deployment update, but also some other charter item discussions
- Multi-domain ALTO
  - Richard will sync up with Benocs and update to WG
    - 10:30 am ET
  - Collab on multi-domain TE with ESnet/NRP/GRP
    - Ranking info
    - Routing info: multi-domain sharing of routing
    - Topo/network graph info: multi-domain TE (sharing of topo)
- WGLC for two WG charter items
  - WGLC issues are also tracked in GitHub
- IETF Hackathon
  - Two hackathon projects will be presented: oam yang model and new transport
  - Kai: what will be good use cases (settings, demo workflow) to demonstrate these two projects? need discussions offline
  - A zookeeper based distributed backend has been implemented to support new transport
  - Progress are tracked in GitHub: https://github.com/openalto/alto/issues?q=is%3Aopen+is%3Aissue+label%3AIETF-Hackathon-116
- Open discussion
  - Qin: More discussions should go to WG mailing list
  - Sabine: engage cross-group discussions


----
**Logistics:**

- **Meeting times:** Tue 9:00 to 10:00am EST

- **Location:** https://ietf.webex.com/ietf/j.php?MTID=ma0e97cc97c4cd71bb59cf1a094682686

- **Minute takers:** Ayoub Messos, Jensen, Jordi, Kai, Lauren, Lei Yixue, Luis, Mahdi, Motoyoshi Sekiya, Qiao, Qin, Richard, Roland, Sabine, Tong Meng, Yuhang, Ziyang Xing. 

------------------------------

**IETF, ALTO Meeting: March 14th, 2023**

**Agenda:**

- Dashboard: https://github.com/orgs/ietf-wg-alto/projects/1/views/2
- IETF 116 Agenda
- Chartered items
- Deployment
- Recharter items for IETF 116
  - Multi-domain use cases
  - compute and network information exposure
  - Trust


**Minutes:**

Note Taker: 


------------------------------

**IETF, ALTO Meeting: March 7th, 2023**

**Agenda:**

- Dashboard: https://github.com/orgs/ietf-wg-alto/projects/1/views/2
- Chartered items
- Deployment
- Recharter items for IETF 116
  - Multi-domain use cases
  - compute and network information exposure
  - Trust


**Minutes:**

Note Taker: Y. Richard

IETF 116 planning:
Ayoub: trust side meeting at IETF 116, please attend
Qin: Identity IAB discussion, related with trust, please consider
Richard: zero knowledge as a tool for WG to consider

Engage with CAN -> renamed to CATS (computing aware traffic steering)
Jordi and Luis involve and present at CATS meeting, 

multidomain (Richard), compute (Jordi and Luis), and trust (Ayoub) as 3 key topics for ietf 116

Deployment page update: Adding Benocs as a section

Chartered items:
  Transport update: Implementation using zoo keeper. 
  Deployment update: update at IETF 116 of hackathon, give short summary in session
  OAM implementation asked by Med: Jensen updates in progress

Hackathon:
  Please kindly register the OAM and transport projects to the IETF hackathon 116 wiki page: 
    https://wiki.ietf.org/en/meeting/116/hackathon

CERN deployment
  Three threads: visibility, FTS scheduling, and Rucio orchestration help/senior member guidance needed.

Multi-domain use case: posted by Richard on WG mailing list, Tong will help to discuss multi-domain use case 
Suggest Mowie (Yunfei) and Tong sync up to have a clear update on 3GPP (mengtong1@huawei.com). 

OAM access control: Jensen proposes a new design, and will share on the mailing list. Qin suggests adding the new design in the document and asking Last Call reviewers pay more attention to this.

Drafts to be updated before cut off: Luis's draft; multi-domain (-00 draft) problem statement; Ayoub draft on trust (focus on side meeting)

------------------------------

**IETF, ALTO Meeting: February 28th, 2023**

**Agenda:**

- Chartered items
- Deployment
- Recharter items for IETF 116
  - Multi-domain use cases
  - compute and network information exposure


**Minutes:**

Note Taker: Richard

- Transport protocol
  Use new repo to check in to the repo ttps://github.com/ietf-wg-alto/draft-ietf-alto-new-transport

- OAM
  Many editing to address comments

  Q: How to handle fine-grained, dynamic access control
     e.g., access control based on the usr who queries for an enpoint property

       IP address -> associated w/ owner
       binding: alto client IP address -> IP address that you can query (ecs)
       POST URI
       {input: client-ip}

        assert: alto_client.ip == post.uri.input.client_ip

  yang model:
      design 1: specify in the yang model (embedded model) [enumerate yang data]
      design 2: specify using external binding through an external database
        assert: verified( ext-valid()  == true

  access control using dynamic fields
    alto client properties, resource_id, input fields of resource

- Deployment
   Telefonica update
   Jordi summary
   Richard updates openalto.org
   Benocs deployment, Sabine

- Multi-domain use case
  Tong Meng (Huawei)
  Wireless is last mile, immersive and interactive apps need better QoS
  Multi-path
  Network info to expose: differentiated QOS services

  App traffic optimize
    QoS-aware scheduling    
    Combined QoS services

  Two types of multi-domain use cases: Asymmetric and symmetric

  Integrating trust in multi-domain use cases

------------------------------

**IETF, ALTO Meeting: February 21th, 2023**

**Agenda:**

- Chartered items
- Review of 'In Progress/Discussion' tasks: https://github.com/orgs/ietf-wg-alto/projects/1/views/2


**Minutes:**

Note Taker: Kai Gao


Logistics:

- Interim meeting:
  - Goal: complete the new round of feedback
  - Qin: move the deployment item to face-to-face meeting. Introduce alto deployment to demonstrate the valid use cases
  - Luis & Richard will update the wiki page of ALTO deployment
- Yokohama IETF:
  - Qin asked whether there the Fujitsu teams have plans on Trust-driven networking during IETF 116
  - Ayoub mentioned to have a slot in the ALTO session and his collegues are preparing for the bits and bytes session. Two demos are being prepared including one using ATLAS probing platform to show location correlated trust.
  - Qin suggested to have a hybrid meeting in the next IETF.
  - Motoyoshi said once the ALTO meeting is decided, the Fujitsu team will book some time for the side meeting.
  - For the time of the TDN side meeting, Qin suggested scheduling the meeting before ALTO and Motoyoshi mentioned potential slots on Tuesday afternoon or evening.
  - Once the IETF agenda is fixed, Fujitsu team will post the meeting schedule to the mailing list.
- Charter items 
  - new transport:
    - remaining issues:
      - what is the mental model?
      - incremental representational state transfer
      - Network resource data represented as a DAG
        - node - version (tag)
        - edge - transport data/transition from one version to another
	- node content is path-independent
	- invariants maintained by server:
	  - continuity: n1->n2
	  - always a direct link to n1
	  - right-shift only
      - Data representation: a virtual "directory" system
      - Node/edge encoded in URI
    - Jordi: does continuity imply feasibility?
    - Richard: If removed 101, but 102 is dangling. Then there is no feasibility.
    - Jordi: What if there are multiple paths? Which one will be returned?
    - Richard: The meta will return the graph indicating all the paths. Client can decide how to download.
    - Kai: Do we enable IREST for IREST?
    - Richard: We do not enable server push for the meta data
    - Jordi: Do we consider performance, e.g., getting the data for 106?
    - Richard:  Recommended is to use the shortest path. 
    - Qin: Maybe too complex. Post the version to the mailing list and get feedback.
    - Qin: Add a change log to summarize the changes in the new draft.
    - Jensen: https://author-tools.ietf.org/iddiff?url1=draft-ietf-alto-new-transport-05&url2=https://github.com/ietf-wg-alto/wg-materials/raw/main/working-documents/new-transport/draft-ietf-alto-new-transport-05%20Lachlan%20Edit.txt&difftype=--html
  - OAM:	
    - Add role to do the role-based
  - Richard: Is the purpose of the Interim meeting to finalize both documents?
  - Qin: Request review after the interim meeting. Issue WGLC.
  - Sabine will provide feedback on Wednesday.
  - Roland: Provide the feedback over the mailing list.
  - Qin: Need volunteer for the interim meeting.
  
------------------------------

**IETF, ALTO Meeting: February 14th, 2023**

**Agenda:**

- Round-table updates
- Chartered items
- Review of 'In Progress/Discussion' tasks: https://github.com/orgs/ietf-wg-alto/projects/1/views/2


**Minutes:**

Note Taker: Roland Schott


**Attendees:**
Sabine, Motoyoshi, Qin, Jordi, Richard, Luis, Jensen, Ayoub, Roland

**Agenda on 14th:**

1-	Round table / Priority Items

2-	Chartered items

3-	Interim Meeting

4-	AoB


**1. Priority Items:**

Preparation of next interim and IETF ALTO meeting.
Only 1h for the ALTO meeting in Yokohama. Idea to align with CAN activity.
One additional point is the multi-domain use case being of interest for
the ALTO community. 
Discussion regarding the content to be presented in the next group meetings.
Bottlenecks might be storage, network capacity etc....
One of the major use cases for concurrent links is congestion control of those bottlenecks especially storage.
CERN and Rucio activities of Richard are examples to improve the behavior here.

**2. Chartered items:**

*2.1- O&M:
	Jensen (Reviewer of the O&M document)
	
	- Send info to the mailing list and include delta info
	- Request for volunteers to provide feedback in the next days
	- Provide feedback until next Tuesday latest, please (=> Luis, Jordi, Sabine and others are welcome)
	- Qin needs slides for the interim on Sunday
	- Check draft regarding interdependencies or complexity e.g., multi-cast


*2.2- Transport documents (Richard)

	- Jordi, Adrian and Med sent feedback to the authors (=> answer needs to be sent to the list)
	- Summary of major changes needs to be sent to the list (Med request => Richard, Kai, Roland will synch regarding response)
	- Goal to provide responses to the feedback on the list at the beginning of next week, before interims meeting
		
*2.3- Deployment

 	- Populate deployments to the wiki
	
*2.4- ALTO Performance Metric 

	- Work is ongoing, but dependency to other documents and feedback

**3. Interim Meeting:**

Focus on charted items and less on deployments

**4. AoB:**

Idea to go with ALTO to a conference called Mobicom - one of the flagship conferences.
Focus there is lying on wireless and 5G.

https://www.sigmobile.org/mobicom/2023/

https://dl.acm.org/doi/proceedings/10.1145/3447993

https://educationscientists.com/mobicom/

------------------------------

**IETF, ALTO Meeting: February 7th, 2023**

**Agenda:**

- Round-table updates
- Chartered items
- Review of 'In Progress/Discussion' tasks: https://github.com/orgs/ietf-wg-alto/projects/1/views/2


**Minutes:**

Note Taker: Ayoub Messos


**Attendees:**
Qin, Jordi, Richard, Sabine, Roland, Jensen, Kai, Ayoub (taking minutes)
**Agenda:**
1-	Round table / Priority Items
2-	Chartered items:

----------------------------------------------------------------
**1. Priority Items**

	- Date for the "interim meeting" 23rd or 24th of Feb (to be closed very soon).
	- Focus on the Chartered items and have them validated:
		- ALTO new Transport draft update
		- ALTO O&M data model draft update
		- ALTO Deployment
		
- Qin, Jordi, Richard, Sabine:
	- ALTO New Transport
		- Richard uploaded a new version of the draft.
		- Review is needed from partners.
		- Need some volunteers to help review both documents:
			- ALTO New Transport : Sabine, Jordi, (Luis?)
			
			
	- New time is the 23th of Feb: 9pm EST (3pm CET) (Qin will send the invite shortly)
	
	- Discussions for plans and the tentative agenda for the meeting in IETF 116 in Yokohama.
		- 1 hour meeting is planned. 

- Richard <> Qin:
	- Discussion about: "Multi domain contact use case": the sparsity of information (issue#1), ambiguity of information(issue#2)
		- Scenario 1:
		- Scenario 2: Multi-Domain Settings (2 ALTO entities in 2 different domains)

------------------------------------------------------
**2. Chartered items: **

*2.1- O&M:
	Jensen (Reviewer of the O&M document)
	- Already have 2 colleagues helping with the review, but might need other volunteer!
	- Update about the progress on the latest O&M document.
	- Will uploaded the new version before Friday for others to review.
	
	- Qin will send the template for Jensen's consideration and will ask some other people to help with review.
	- Richard will also provide some review.


*2.2- Transport documents (Richard)
	- Already submitted a newer version with a lot of changes with the help of Roland and Kai.
	- Provides details about the updates related to references and InfoWorkFlow.
	- Comments from Qin about: Lifecyle /  maybe a diagram would be helpful/ Transport State: Create, Read or Delete / use of absolute uri and relative uri /
	- Taking the discussion about the use of "Absolute/Relative" State to the mailing list for further discussions.
	- Should decide: What to include as part of the current draft and what to cover as part of a future document/work. (a full comprehensive read is needed)

*2.3- Deployment


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

**Agenda:**

- Round-table updates
- Chartered items
- Review of 'In Progress/Discussion' tasks: https://github.com/orgs/ietf-wg-alto/projects/1/views/2

Chartered items
--- Transport - Richard 
new name added way of publishing...
major change: 4 requirements = tips. R5 optional (no MUST)
R14 = MUST
overall, pip can request server from anywhere. session-based transport. 
ready to be posted when tips are done. 
qin: intro still keeps SSE fig => will be deleted. no need compare w SSE. 
richard: abstract positions wrt SSE that is great. Pb: SSE not allows naming individual updates. Thus all pushed updt are anonymus updates => client cannot pull them (no ID).
=> tips incl allowing distribution of ID from server to client. server can now push. 
qin: diff in workflow? 
richard: use tips, ID see fig before section 3
qin: SSE needs 2 channels: ctrl + data. new transport does not need to introduce any specific channel, just a transp queue 
richard: bundled in same connection
qin: hopefully post this week?

--- O&M - Jensen
simplified Yang model for ctrl part. 
client auth delegated to other server. no need passwd & user name => role-name. example in appendix
auth server can be 3rd party, see fig 3. 
qin: why use oauth in ALTO scenario? 
jensen: can be different server. 
qin: not convinced oauth is more relevant. Commented on the list. compliancy w base protocol is needed. base prot does not use "access control" term. Can be rather TLS. need double check. 
jensen: will discuss on mailing list. 
kai: ...
jensen: can use other prot, user & passwd. can drop oauth if too complex. 
qin: use TLS maybe. better not expand to oauth. 
kai: jensen put text in appendix showing how can extend to oauth. oauth = example
qin: ok if appendix as an example. 
jensen: can upload after meeting to have feedback. 

qiufang: ALTO server can push (reactive) data and pull (proactive)?? . There should be these 2 modes for ALTO server, with relevant config eg how often pull data. also need to specify data store. 
qin: URI not enough to spec yang data store, you need target path to locate...
kai: data store only specifies the type. 
qiu: to identify data store.... 
qin: maybe add example in appx. we can schedule editing session. 

--- ALTO deployments: 
qin: reminder we have wiki page. please populate your section. right now, NRP documented only (nat research platform)
richard: can add info on CERN. 
jordi: is a wiki page ok as a deployment deliverable?
qin: is ok, we also need Luis input. we also have Internet protocol journal (IPJ) paper. 
qin: wiki needs distinguish ALTO deployment (cern, telefonica) from  implementations experiments. IETF wants shutdown old wiki pages. We need complete migration and advise secretary. 
jordi: will edit to separate. 

---  IPJ article
qin: exchanged w editor who provided suggestions. 

AOB: richard will discuss next meeting. 
we also have Marcos Schwarz
Ayoub: could not catch up, hopefully will update next week integrate fujistsu work in ALTO WG. need talk w jordi and luis. 
Meeting concluded


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
