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

Note Taker: Kai



Qin: Formulate the discussion (IETF 116). Focus on two deployments: CERN and Telefonica.
Qin: We can raise use cases and write problem statements.
Qin: Any idea on how to make the meeting more efficient?
Richard: Scheduled a meeting with Ingmar and Danny. May be one more deployment report. 

Telefonica - Luis
CERN - Mihai/Mario/Richard
NRP - Jordi
Benox - Ingmar/Danny

Richard: Start to put unified vision and related work.
Richard: Visibility, prediction and control. Visibility is one small piece. G2 provides predictability which should be discussed. Then people will know that predicability is one focus of ALTO.
Also talk about applications built on top of ALTO. We may use the term proposed by Google -- application defined networking. 
There are two pieces: 1. scheduling: use the visibility to define the applications' behaviors; 2. 

Qin: For prediction, coordinate with PANRG. For control, probably beyond the current charter.
Richard: Not expanding the scope but to show how ALTO fits in the bigger picture.
Qin: Commerical use cases to convince AD and the community. Cooridinate with the CATS to see how to work together. Security may be part of the multi-domain setting. One of the CATS chairs will attend the ALTO session for discussion. Open doors to transport-enhanced networking.
Richard: I can send some feedback and review to the CATS group.
Jordi: What is the best way to coordinate with CATS? Is there an open discussion to have?
Qin: No discussion is initiated. Both WG focus on overlay networking.
Luis: The difference is that in ALTO the metrics are directly exposed but in CATS the metrics are derived. One key point is that which WG will define the metrics.
Sabine: I follow the CATS drafts. The appendix they provide hints on how to combine metrics. It's in a very preliminary stage. There is room to jointly define metrics. In particular, whether the metrics are consumed off path (ALTO) of in path (CATS). What types of metrics are collected and how to make them update to date fast enough.
Richard: What exactly is the transport the CATS WG envision? In ALTO WG, we propose solutions such as MoWIE to enable on-path signaling. A big aspect of new transport is to enable fast streaming.
Qin: Original proposal is to use BGP. The challenge is that BGP cannot be used to carry multiple metrics. Not sure what signaling is proposed for the overlay. Maybe someone from the ALTO WG to take a look at the CATS metrics. 
Luis: We should not see CATS as owner of us. CATS can consume ALTO information. ALTO can be a tool for CATS but not the other way around. ALTO is not behind CATS but more up front.
Jordi: There is a lot of common ground there to define metrics.
Sabine: One of the CATS use case is compatible in ALTO, for example, edge selection. IPPM would be the one natural starting point and be extended to include computing metrics.
Richard: Kafka has concepts such as the broker, connect, adapter. Maybe CATS framework is similar to the Kafka architecture. One question of CAN is that after making the computing resources available, but the computing resources are owned by different parties. The problem is that it is a highly heterogeneous environment. The problem is that how to share the computing resources? Not sure if this is within the scope of CATS.
Sabine: ALTO is useful as it exposes information to 3rd parties. The use cases are carefully sorted out in the CATS document. The big issue of heterogneity is that even if you have access, it is important to make sure the consumer of the information understands what the information means. ALTO can play a fundamental role there because it exposes information that is explainable. It means you understand what is the semantics.
Qin: We should raise the issues in the CATS meeting. ALTO is driving fast and we want to solve the multi-domain issue. Need to justify the use cases. Is there any technical issue for us to support the end-to-end visibility?
Qin: For agenda, we want to focus on deployment.
Jordi: What is the goal for the deployment report? In IETF, we have the ALTO session, a side meeting held by Fujitsu, CATS. For the ALTO session, we drive the discussion with deployment. In the CERN deployment, it would be to justify the multi-domain case. For the telefonica deployment, it is to open discussions on compute.
Richard: For the CERN deployment, should the architectures be discussed on how ALTO fits into it or the multi-domain issue?
Qin: Use the framework to motivate the multi-domain use case. Emphasize that in the use case we already implement multi-domain use case to justify it as a new charter item.
Ayoub: March 28, 1:00 - 18:30
Ayoub: The agenda includs 1. TEN concept and prob statement; 2. Robust localization as a use case; 3. Trust measurement: issues and challenges; 4. Presenters from other WG; 5. Open discussion.
Ayoub: Is there any references to the trust in multi domain settings?
Richard: There is some object (packets, web page). The setting is to assess the trust level of the objects. One way is to do the assessment from the network infrastructure.
Ayoub: I can explain the items in another 1-on-1 meeting.
Richard: I can send the references of the multi-domain.
Qin: Maybe take out the multi-domain setting?
Ayoub: What do you suggest for the last item?
Jordi: Maybe Brian Trammell?
Ayoub: Brian is a good choice. He authored one of the PANRG documents which mentions trustworthiness in PAN.
Richard: I can make the connection. Endpoint property map can provide accurate information about the location. 
Sabine: Do you consider making a presentation in the PANRG? There is a call for presentation.
Motoyoshi: We are interested in the zero trust topic.






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
