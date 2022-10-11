----
**Logistics:**

- **Meeting times:** Tue 9:00 to 10:00am EST

- **Location:** https://ietf.webex.com/ietf/j.php?MTID=ma0e97cc97c4cd71bb59cf1a094682686

- **Minute takers:** Jensen, Jordi, Kai, Lei Yixue, Luis, Mahdi, Qiao, Qin, Richard, Roland, Sabine, Yuhang, Ziyang Xing. 

------------------------------

**IETF ALTO Meeting: October 11, 2022**

**Agenda:**

- Review of 'In Progress/Discussion' tasks: https://github.com/orgs/ietf-wg-alto/projects/1/views/2
- Path vector RFC
- New transport
- OAM
- Deployment (integration with Rucio/FTS, Telefonica, NRP)

Note taker: Jordi

Minutes: 

Internet

Telefonica ALTO deployment:
- Launch date towards end of October
- Hope we can report developments in IETF 115

OAM:
- Summarize existing work status
- IANA registry
- IRR (Internet Routing Register)
- Our proposal is to add a new field called server discovery and behind it specify different methods that the client can discover the server
- How to connect the algorithms that constructs the ALTO services. Algorithms should have their own configurations that can be extended. Specify the fields that are required from other ALTO servers. 
- Do you think we should put the example in the main text or move to the appendix?
    - Qin: suggest moving to the Appendix

Transport:
- Feedback from Martin: wants to tweak charter to focus  on version independent mechanims
- Two solutions: with and without put
- Kai and team can focus on without put case
- I hope this can be another work item for the recharter
- If you can deliver no put option and make it complete.
- Goal of 115 is to introduce this new recharter.

Path Vector:
- RFC already published
- Let's remove it from the dashboard

Currently ongoing deployments:
- Telefonica
- CERN/LHCONE
- NRP/Qualcomm

Recharter:
- Approach: drive conversations starting from what we learn from the deployments to identify gaps/needs.
- HTTP transport put case
- Multidomain settings, security is a big issue
    - Telefonica is working on some ideas about security based on deployment experience.
- Bottleneck structures

IETF hackathon
- CERN / LHCONE: Looking glass parser for ALTO
- National Researc Platform / Bottleneck structure


------------------------------

**IETF ALTO Meeting: October 4, 2022**

**Agenda**:

- Deployment
- OAM
- IETF 115 planning

Note taker: Kai

**Minutes**:

- Deployment
  - The goal is to deploy ALTO in CERN, ESNet and potentially PRP as well. There are two types of information that is provided for the path from a source to a destination
    1. controlled assets (selective exposure): whether the path uses links from a given set
    2. end-to-end metrics (aggregated): e.g., number of hops, fiber wavelength
  - Question from Luis: What is the current process?
    - For the CERN deployment, the mapping from traffic to controlled assets (e.g., inter-domain links) are obtained from LookingGlass servers. Information for next hops is obtained from IRR (e.g., using `whois`).
    - For ESNet, the information is a static topology file. The server needs to search the attachment points first and then compute the shortest paths.
  - Comment from Luis: BGP-LS is not deployed in some infrastructure and the ALTO server needs information from static views.
  - Comment from Luis: Some logically separated networks may go through the same infrastructure
- OAM
  - Update: A new field is added to support cross-domain server discovery. The configuration specifies a list of endpoint addresses (e.g., IPv4 prefixes) that should be mapped to the server.
  - Question from Richard: What does the endpoint in the field mean? Does the mapping refer to, for example, the information from the CRIC database?
    - Yes. The information is to allow building DNS entries for cross-domain discovery.
  - Question from Richard: Can we use IRR to discover the servers?
    - It is possible. But xdom-disc is already an ALTO standard.
  - Further questions would be exchanged on the mailing list
- IETF 115 Planning:
  - ALTO transport has the highest priority. Need to discuss with AD on how to split the document, and show that each document is useful.
  - ALTO OAM: The agreement is to keep the generic parts and move specific options to the appendix. Updates on the github should be made more transparent to the WG.
  - ALTO deployment discussion: CERN & telefonica will be the focus
  - Recharter discussion: Probably not the time to discuss recharter. Delivering ALTO transport is important as a foundation to start recharter discussion.
  - Missing piece: how to provide better security and confidentiality for ALTo servers


------------------------------
**IETF ALTO Meeting: September 27, 2022**

**Agenda**:

- Review of 'In Progress/Discussion' tasks: https://github.com/orgs/ietf-wg-alto/projects/1/views/2
- Path vector RFC
- New transport
- OAM
- Deployment (integration with Rucio/FTS)

Note taker: Mahdi

**Minutes**:


----
**Logistics:**

- **Meeting times:** Tue 9:00 to 10:00am EST

- **Location:** https://ietf.webex.com/ietf/j.php?MTID=ma0e97cc97c4cd71bb59cf1a094682686

- **Minute takers:** Jensen, Jordi, Kai, Lei Yixue, Luis, Mahdi, Qiao, Qin, Richard, Roland, Sabine, Yuhang, Ziyang Xing.

------------------------------
**IETF ALTO Meeting: August 16, 2022**

**Agenda**:

- New transport
- OAM
- Deployment (integration with Rucio/FTS)

Note taker: Kai

**Minutes**:

- New transport
  - The decision is to not focus on the push-update. A summary email will be sent to the mailing list.
  - In the first version, the updates will be sent to the client using HTTP PUT: A client sends a POST to subscribe and the server sends PUT message(s) with different media types to update the data on the client side.
  - No need for HTTP/2 and beyond

  - Question: Enable ALTO clients to write to ALTO server (e.g., using PUT command)?
  - What need to be done: URL naming convention between ALTO client/server

  - Question: How to organize the documents for new transport?
  - Two options:
    - 3 document: base (namespace), push promise, server put
    - 2 document: base, server put
  - Chair suggests bringing the options to the mailing list
  - Mention the new capability of client PUT 
- OAM
  - The opeartor need to configure the algorithm and the data model
  - Two approaches:
    1. Read directly (e.g., from a YANG model)
    2. Use a data broker (as a uniform data model) for multiple sources
  - Introduce a new configuration item called "data-store"
    - The "data-id" and "data-type" are read-only and set by the implementation
  - Question: Does this document define standards or investigate the design space?
  - Concerns were raised that the current specification may be too detailed and implementation specific
  - Suggestion: Put the optional configurations into the appendix and keep only the base in the main text
- Integration with Rucio/FTS
  - Planned for IETF 115 and 116 (development and hackathon)
  - Effort to collect statistics and prepare A/B test
  - First milestone: single virtual organization (VO), fixed routing, multiple networks
  - Question: How to handle multi-domain deployment (globally for a single experiment, or uniform deployment), e.g., ATLAS v.s. CMS?
  - Protocols invovled: base protocol, performance metrics, unified properties, path vector and some non-standard extensions (e.g., flow cost service and multi-domain ALTO)
  - The planning will be shared to the mailing list (with involved teams)

------------------------------

**IETF ALTO Meeting: August 9, 2022**

**Agenda:**

- Chartered documents: 
    - Review of 'In Progress/Discussion' tasks: https://github.com/orgs/ietf-wg-alto/projects/1/views/2
    - HTTP Transport 
    - OAM
- Cellular case

**Minutes:**

Notes taker: Jordi

- HTTP (Richard and Roland):
    - Using put to implement incremental push update
    - We don't want to include a new container. 
    - So the only way is to do put.
    - PUT URI - PUT URI - PUT URI
    - How does the client know what's the URI for each push
    - Client must have a way to agree on URI with server
    - We follow semantics of HTTP (no exploiting of protocol ambiguity)
    - Server sending state to the client. Put is idempotent.
    - What if the system gets out of sync
    - Need to provide mechanism to provide full snapshot from time to time
    - Bring this to the mailing list


- OAM (Jensen):
    - Q5. Since there is no server-to-server protocol defined for ALTO yet, one option is to not standardized server-to-server OAM.
    - Q6. Do we need a data broker for ALTO server
    - Jensen to bring this question to the mailing list

- MPQUIC (Ziyang):
    - Consider putting another demo for 115.
    - Provide updates to the ALTO WG
    - WG will seek ways to integrate Ziyang's demo into some of the deployments that are going on.


------------------------------

**IETF ALTO Meeting: August 2, 2022**

**Agenda:**

- Chartered documents: 
    - Review of 'In Progress/Discussion' tasks: https://github.com/orgs/ietf-wg-alto/projects/1/views/2
    - Transport 
    - OAM
- Cellular case

**Minutes:**

Notes taker: Jordi

- Summary of ALTO meeting on July 26 in Philadelphia:
    - Need to be:
        - Focused
        - Be pragmatic 
        - Deliver 
    - Approach:
        - Chartered milestones 
        - Deployments
        - Evangelize
    - Improve workflow:
        - Need traffic in the mailing list 
        - Outcome of decisions in the mailing list and request if any comments

- Transport Draft :
    - Feedback from IETF: restructuring 
    - Incremental push updates from SSE
    - 7285 client pull protocol. Two issues: latency and overhead (blocked transmission)
    - 8895 To solve the issue introduced SSE server push
    - Reviewers feedback: Why don't you use server put. 
    - Question 1: should we split transport doc into two docs?
        - What are the two docs:
            - Data model / URI.
            - Transport that is independent of HTTP version.    
        - Approach: take current doc and take data model schema into a new doc and create a separate doc with a server-put centric design
    - Question 2: Design that is independent of the transport version (works for all).
        - Kai: I think we should keep it separate. Server put
        - Put is overwrite. Information resource we all (client and server) know exists. Put overwrites the state. So put is idempotent.
        - Post is additional. Incremental, not idempotent.
        - If state is overwritten, serialization is needed.
- Let's take  these conversations to the mailing list.

------------------------------

**IETF ALTO Meeting: July 19, 2022**

**Agenda:**

- Chartered documents: 
    - Review of 'In Progress/Discussion' tasks: https://github.com/orgs/ietf-wg-alto/projects/1/views/2
- IETF 114
- SIGCOMM NAI workshop
- New I-Drafts

**Minutes:**

Notes taker: Jensen


1. Richard and Roland will answer to the artart early reviews for new-transport document.
2. Jensen reported discussions about O&M document on the mailing list. Jensen will send the summary email to the mailing list as soon.
3. Jordi / Luis / Ziyang / Jensen will coordinate the ALTO deployment report.
4. Qin required that all the IETF 114 presenters should send the first version of the slides before this Sunday.
5. Qin mentioned another potential option where to publish the ALTO article: APNIC blog (https://blog.apnic.net/)
6. Richard / Sabine/ Yixue will start the conversion about the cellular use cases and the MoWIE work on the mailing list.

------------------------------

**IETF ALTO Meeting: July 12, 2022**

**Agenda:**

- IETF 114
- Chartered documents
- Review of 'In Progress/Discussion' tasks: https://github.com/orgs/ietf-wg-alto/projects/1/views/2
- SIGCOMM NAI workshop
- New I-Drafts

**Minutes:**

Note taker: Yuhang

1. Richard gave a quick presentation of two demos on FTS.

2. Qin thinks the first demo that we can say PHASE I is already done in IETF 113 and we focus on new functionalities in IETF 114.

3. Sabine/Richard/Yixue: Discussed the MoWIE draft regarding Princeton's work and Zili's work. The updated drafts have reflected the work about the PBE-CC e.g. which can be exposed and carried out for cellular network.

4. Yixue asks if the updated MoWIE draft can be presented in IETF 114.  Richard will check with Qin about whether/how in the summary part.

5. Disscussons on Alto new transport:
Richard needs to address the comments and other open issues before IETF 114 meeting.
It is suggested that Richard or Roland should get all people on the discussion to synchronize the comments

6. Jensen should summarize the current open issues as to the main list.

7. Richard will discuss and address some feedback from the ALTO O&M data model draft update.

8. SIGCOMM NAI: Richard and Luis invited people from Google and Microsoft to join the conversation with offline discussion.

9. Regarding to the Wiki or Internet-Draft about ALTO deployments and challenges, it is recommended to further check what is a real deployment and what is not a real deployment.

------------------------------

**IETF ALTO Meeting: July 5, 2022**

**Agenda:**

- IETF 114
- Chartered documents
- Review of 'In Progress/Discussion' tasks: https://github.com/orgs/ietf-wg-alto/projects/1/views/2
- SIGCOMM NAI workshop
- New I-Drafts

**Minutes:**

Note taker: Sabine

ABBREV:
- aos 	ALTO Server
- aoc	ALTO Client
- pip	people
- ry: 	Richard
- jz	Jensen
- tc	Tencent
WG	working group

GITHUB
https://github.com/ietf-wg-alto/wg-materials/blob/main/meetings-ietf-alto/ietf-alto-2022.md

- min taker : sabine
people:  jordi, richard, jensen,  Lei Yixue, luis, mahdi, qiao, yale ryan yang, Yuhang, roland, sabine

- charter items
Qin wants see updates on open issues. 

TICKETS
- ALTO cost mode: T18. moved to RFC queue. Milestone done

- T32 CDNI related registry. sec 6 
CDNI adds new footprint type:
link to cdni doc: https://www.rfc-editor.org/authors/rfc9241.html#name-query-footprint-properties-

Question to cdni ml. 
eml link: TBC
New cdni footprint type: question should we register to ALTO EDT (entity domain type) registry? 
option: write doc later on that defines this ALTO EDT associated with footprint type  

T29 - UP => 9240
all authors approved publication as RFC

ALTO O&M
Jensen gives updates. 
added new server grouping to handle server set-up. 
+ new metrics

ry: what if want deploy AOS in multiple domains to work together?
jz: this doc is for a single AOS. no decided if multiple docs. 
qin: should add to open issues + discuss on list. section 5.5 server to server communication
ry: how config AOC. new feature rucio download. how to config params.?
AOS uri, how specify? 
qin: seems relate to access ctrl. see alto base protoc, maybe already specified.
jz: aoc also needs params 
rucio doc: 
how define simple and consistent commands 
automation by config aoc. command line or browser, 
qin:  see ZTP zero touch protocol => open issue
sabine: whether in/out scope, we should see what happens with more complex commands (eg w constraints, filtering)
aoc is ancillary to an apps. 

T19 transport
ry & roland will post new tread on http3. Roland ok needs feedback from WG. 
will post update and open discussion. 
who sould we reach out to besides alto wg? 
qin: will ping Med to engage more http3 folks

alto docs
ry: jordi on bttleneck structs? maybe no time until next monday

MOWIE 
- Tencent authors need do some updates: 3gpp, cost metrics. maybe finish tomorrow or later. 
July 11 is tough deadline. will see how far can go. 
qin: concerned. need better sync-up, organize discussion framework, wants hear more voices. Zhili suggests maybe ALTO115. qin: people must converge. Sabine did another draft. need show and do join effort.
sab & gang li have a draft. alibaba team, princeton team

ry: do we want them to present at IETF114?
qin: go to list, have discussion. off line not efficient. get all pip on same page
tc sent e-mail to princteon no asw. same princeton and alibaba. 
qin : pb indeed. 
tc: sab and li gang already invilved in mowi thread. 
qin: want see how this fits in alto. 

tcLei: next step? 
qin: go to list and share your draft and issues. get pip interested. 
ry: first send to me. 
qin: need make disc happen naturally. not only presentations. need new blood
tcLei: discuss w sab and cmcc. contribs already 

ry needs approve CDNI doc. 

------------------------------

**IETF ALTO Meeting: June 28, 2022**

**Agenda:**

- Chartered documents
- Review of 'In Progress/Discussion' tasks: https://github.com/orgs/ietf-wg-alto/projects/1/views/2
- SIGCOMM NAI workshop
- IETF 114
- New I-Drafts
- Others in the Scrum dashboard

**Minutes:**

Note taker: Roland

**Agenda Item - Chartered Documents & ALTO Dashboard:**

- Go through the dashboard and the documents
- Info regarding RFC 9240 can be found on: https://www.rfc-editor.org/auth48/rfc9240
- Info regarding RFC 9241 can be found on: https://www.rfc-editor.org/auth48/rfc9241
- ALTO Transport draft was adopted by the WG, see: https://datatracker.ietf.org/doc/draft-ietf-alto-new-transport/
  or github: https://github.com/ietf-wg-alto/draft-ietf-alto-new-transport
- Discussion regarding ALTO and PBE-CC team and how the conversation can be intensified
  - Richard can take the lead in the discussion with Alibaba and Princeton teams
  - Further activities can start in about 1 or 2 weeks
  - Qin reminds that we already had a meeting with both teams, idea that slides or an IETF draft will be generated by the teams, that we can start discussion on these 
    additional topics
  - Clarification regarding the contact persons is needed
- ALTO article
  - Publish ALTO article, work is going on
  - Feedback form Med (Mohamed Boucadair) expected
  - Update our ALTO Wiki 

**Agenda Item - SIGCOMM NAI Workshop**

- Try to engage people to participate and contribute
- Idea to get contribution from Meta/Metaverse
- Travel permissions are still an issue
- Try to get a VP level person from Meta
- Several VP levels speaker will take part of the conference
- Potential keynote speaker: Werner Vogels (VP & CTO at Amazon)
  - Option for remote presentation 

**Agenda Item - IETF 114:**

- Discussion, if the MoWIE work shall be presented in the ALTO WG IETF 114 meeting slot
- Concerns that the time slot might be too small

**Agenda Item - New I-Drafts:**

- Design team for cellular network information
  - Connection to 3GPP required and coordination of the design teams
- Discussion on MoWIE draft
  - 3GPP is offering APIs, suggestion to integrate these in the ALTO work
 
 **Agenda Item - Others in the Scrum dashboard**
 
- Discussion regarding proposal FTS and global resource allocation
- Idea of TCP controller getting all information of the networks and how much bandwidth is used or available, respectively
- Discussion is related to RUCIO and SIGCOMM NAI
- Clarification of cooperation with San Diego Supercomputer Center is intended
- Question regarding Rucio/FTS interoperation:
   - How much do we as ALTO WG want to be integrated in the routing part?
- FTS is the control plane regarding the maximum number of TCP sessions
- Each source and destination maintain several concurrent sessions and ALTO comes into the play for optimization of the routing matrix
   - Adjustment of TCP sessions
- Roland stated that the idea to bring this into the Hackathon of IETF 114 is a reasonable place to show implementations. Scalability issues need to be considered. In principle centralization is not a new idea.


----

**IETF ALTO Meeting: June 21, 2022**

**Agenda:**

- Chartered documents
- Review of 'In Progress/Discussion' tasks: https://github.com/orgs/ietf-wg-alto/projects/1/views/2
- SIGCOMM NAI workshop
- IETF 114
- New I-Drafts
- Others in the Scrum dashboard

**Minutes:**

Note taker: Richard

Cellular network information design team: Yuhang from Tencent; schedule a meeting w/ Alibaba and Tencent;

An update of https://datatracker.ietf.org/doc/html/draft-li-alto-cellular-use-cases is posted, which is a second draft based on MOWIE. It has substantial work to move to standard. The authors invite people to look at the draft, which includes motivation, use cases, and each section highlights the need, which is available from 3GPP but not ALTO. Sabine encourages feedback and Qin (chair) encourages more collaboration from all members.

Authors need to approve the items in the RFC editor queue items: CDNi (Jan and Jensen approved; others need to approve, remind Richard and Kevin Ma, Jo); Unified Property (need to remind all authors to approve, look at the last modification, in terms of the formatting such as those turned into tables).

ALTO new transport adopted as WG document and need to update the new version -01 with new WG file name, collect all open issues in the appendix, discuss them on mailing list---each issue a separate thread, create github to track each issue.

ANE name in the path vector could benefit from the relaxation in the format of the ANE names in the base protocol RFC7285. In particular, only modification on the PIDName. Need to take care of backward compatibility. Option 1 modifies base protocol; Option 2 introduces Bis. A suggestion is to look at the approach of cost mode. Post an errata first to get attention and feedback.

A suggestion is to add the following best practice: add a link on the git to the email discussion.

OAM draft authors check w/ the netmod mailing list and discuss. Jensen already asked questions by posting to yangd doctor mailinglist. Suggest to post to netmod.

Update ALTO journal article based on Med's latest version and post by next weekly meeting.

Please engage more with the CAN BoF discussion. CAN has more remaining issues to be closed. There can be both centralized (e.g., ALTO) and distributed (e.g., any) solutions. Discussion of on-path or off-path solutions. Need fast reaction.

Discussion on how much WG need to focus on WG items (e.g., CAN and edge discovery).


----

**IETF ALTO Meeting: June 14, 2022**

**Agenda:**

- Chartered documents
- Review of 'In Progress/Discussion' tasks: https://github.com/orgs/ietf-wg-alto/projects/1/views/2
- SIGCOMM NAI workshop
- IETF 114
- New I-Drafts
- Others in the Scrum dashboard

**Minutes:**

Note taker: Qin

1. Jensen will take care of CDNI and address two remaining discussion points from RFC Editors.

2. Sabine will take care of Unified Property draft and provide feedback to RFC Editors in June 14.

3. Jensen gave a quick update of ALTO OAM and will raise discussion on the list.

4. Roland gave a quick update of ALTO transport progress and Richard and Kai needs to follow up with IPR call. Roland and Richard need to create a section to track the open issues and make update to the draft after the draft getted adopted.

5. ART review will be requested after ALTO Transport draft gets adopted.

6. Sabine will help review ALTO transport draft since she is believing it will be important topic related

to MOWIE.

7. CAN status update and the relation with ALTO has been discussed. It was agreed that ALTO can play an

important role in Edge discovery which is related to Luis's draft.

8. It was suggested to invite Danny and Rucio and CERN people to provide ALTO integration update which

is targeted to commerical use.

----

**IETF ALTO Meeting: June 6, 2022**

**Agenda:**

- Review of 'In Progress/Discussion' tasks: https://github.com/orgs/ietf-wg-alto/projects/1/views/2
- Chair request: Focus/prioritize ALTO Transport and ALTO OAM.  
- SIGCOMM NAI workshop

**Minutes:**

Note taker: Qiao

1. Richard to introduce Jordi to Princeton and Tencent team so they can work together on writing IETF drafts. (I missed the first 10-15 minutes of the meeting, so this point may not be precise.)
2. Open ticket on Unified Property:
   Sabine: in the base protocol, ANE has the same format of PID (i.e., no dots). So we need to fix the incorrect ANE names in the examples of the current UP draft, and propose a more flexible ANE name format as a small update (i.e., protocol maintenance) in the future charter. Similar things can be done for the cost-mode draft.
   Kai and Richard have the same opinion as well.
   Sabine to post this in the mailing list.
3. ALTO cost mode, no objection, already pass IESG
4. MIT Technology Review article: Richard to lead this effort. Jordi suggests doing the interview style, because the group may not have enough bandwidth. Qin suggests we focus more on other work such as ALTO article for the Internet protocol journal. Jordi is going through the admin process in his company to get clearance.
5. NAI:
   (1) Luis:NAI review assigned, 13 submissions, plan to accept ~6;
   (2) Invited paper:
       1 by Richard, Jordi about Rucio/FTS/CERN (waiting for Ruciao/CERN's response),
       1 by Telefonica, Deutsche Telekom, Linux Foundation and Cisco, this is about consuming network capability through interfaces.
       For the 3rd invited paper, Richard suggests two candidates:
         candidate 1: Facebook on entitlement/contract between planning/ops/apps of network  
         candidate 2: Harvey about the composable architecture of different experiments (e.g., CERN, SLAC and UCSD)
       Richard will reach out to Facebook first
   (3) Keynote speaker: Richard to approach Jon Crowcroft@Cambridge
       Others: Richard to collect this year's accepted paper authors to decide.
6. ALTO new transport:
   Richard: mostly done by adoption, now it's about re-iteration. Qin: need people to review it and provide feedback
7. Richard suggests inviting Nick Zhang's group to talk about their recently accepted SIGCOMM paper on deep queue (Q?) network
8. Jensen talks about his progress in the data model/service model of the OAM draft. He will summarize it in a ticket. 

----

**IETF ALTO Meeting: May 31, 2022**

**Agenda:**

- PBE-CC Team discussion
- IETF ALTO discussion

**Minutes:**

Note taker: Mahdi

**1. Discussions**

- Professor Kyle Jamieson comment's on ALTO and NG-Scope: Two directions to implement [NG-Scope](https://arxiv.org/pdf/2201.05281.pdf) to do the telemetry and send the information on the client-side. 

1. At the UE (client-side) (Needs firmware design and changes to quickly capture the dynamics and react.)
2. Separated from the RAN infrastructures - Sits near the client and provides telemetry. 

- Dr. Yaxiong Xie comments on NG-Scope: Cellular networks are centrally controlled, where BSs do resource allocation, bit-rate adaptation, etc., so the idea of NG-Scope is to extract information from control messages. One way to integrate with ALTO is to feed the collected data into the ALTO server and retrieve it back. But the main question is where to collect information and where to deploy it?

- An example that aggregates the data at the receiver and provides information for fair CC at the client side is given [here](https://dl.acm.org/doi/pdf/10.1145/3387514.3405880).

- Two fundamental questions are raised here: 

1. What information to collect? 
2. The scheme should be flexible and support "Carrier-aggregation" (Professor Jamieson's comment as a proper pathway for the integration of ALTO and NG-Scope). 

- As a multitude of CC algorithms are used by multiple vendors on a wide variety of application 

- An appropriate API is quintessential to aggregating the information. (One possible focus subject for ALTO as proposed by professor Jamieson.)

- Tencent has experience with radio information aggregation in two ways.  

* From BS to applications (for both out-band and in-band paths)
* RLI (Radio link information) to UEs. 

- Zili Meng's description of the Shortest Control Loop paper tries to address two main issues: Conventional feedback loops may face long delays due to long Sending + Marking + Receiving chains' delays, and possible drastic drops in the sending rates (by a factor of 10). The idea is to avoid queuing delays and send feedback directly to the sender.

**2. Directions**

- Professor Yang proposal: To possibly write a draft on how the NG-Scope-related protocol would look like in terms of API and the protocol requirements. As IETF promotes modular schemes this specification can be divided into three submodels, namely CC (as the application), information signaling, and the messaging protocol. 

- Chair's suggestions (Dr. Qin Wu): Before writing a draft we need to further elaborate on the discussions, and to perform a survey to summarize the work and analyze the requirements. WG should also seek feedback from 3GPP, and IESG transport and CC control groups (Tencent's group has the experience of working with 3GPP).

- Dr. Sabine Randriamasy: Since the ALTO WG is currently chartered, WG can work on physical layer information exposure as a use case, for now, to pave the way.  As an ALTO extension, which supports the application in cellular networks this use case should cover the following area.

1. Introduce the use case. 
2. Perform the gap analysis. 
3. Justify that ALTO is useful for this use case. 

- In terms of network abstractions and exposure, we should know how to stitch that information to guarantee cohesion among multiple domains.

**Links:**

- [MoWIE paper](https://dl.acm.org/doi/10.1145/3405672.3409489): Adaptive network information exposure in mobile networks.

- [NG-Scope paper](https://dl.acm.org/doi/10.1145/3405672.3409489): First-ever channel capacity telemetry tool in cellular networks

- [NG-Scope codebase](https://github.com/YaxiongXiePrinceton/NG-Scope)

- [RFC 8888](https://datatracker.ietf.org/doc/rfc8888/) Interactive real-time CC using RTP (messaging format)

- [PBE-CC](https://dl.acm.org/doi/10.1145/3387514.3405880) CC in cellular networks using physical layer BW measurements

----

**IETF ALTO Meeting: May 24, 2022**

**Agenda:**

- Review of 'In Progress/Discussion' tasks: https://github.com/orgs/ietf-wg-alto/projects/1/views/2
- Chair request: Focus/prioritize ALTO Transport and ALTO OAM.  
- SIGCOMM NAI workshop

**Minutes:**

Note Taker: Luis

- ALTO Transport (Roland / Richard): update behind schedule. To be recovered during next weeks. Updates include description of transport queue information, communication flows, appendix on ALTO and http/3, etc.
- ALTO OAM (Jensen): working on open issues raised during last IETF meeting (data model for client side, config server level management). Checking related work (e.g., NETCONF) to improve the model. More disucssions needed.
- ALTO cost mode (Kai): still waiting for further feedbacks. Now 8 YES, No objections so far.
- ALTO tutorial: to be consider for the NAI workshop, depending on the number of submitted papers.
- SIGCOMM NAI workshop (Luis / all): deadline on MAy 25th, 6 papers submitted by now, around 6 more known to be submitted. To take decisions once we have clear the final status in terms of number of submissions. Consider ALTO tutotial, invited papers (one now identified), etc. 
- ALTO article for Internet Protocol journal
- Guest speakers (Richard): 
   * Talk from Princeton team scheduled for next week. Considering also participation/talks from Alibaba and Tencent. Discussions can help to profile topics for rechartering, specifically in this case leverage on ALTO for visualization of physical information. Target date: May 31th.
   * Additional talk from Microsoft. Target date: June 7th. 
- Rucio info in ALTO format (Jordi / Richard): pursuing unified single model.

----

**IETF ALTO Meeting: May 17, 2022**

**Agenda:**

- John Graham 5G Project in PRP: IETF ALTO, SRv6, Bottleneck Structure Graphs
- Review of 'In Progress/Discussion' tasks: https://github.com/orgs/ietf-wg-alto/projects/1/views/2

**Minutes:**

Note Taker: Kai

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
