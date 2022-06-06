----

**Logistics:**

- **Meeting times:** Mon 9:00 to 10:00am EST, Wed 9:00 to 9:30am EST, Thu 10:00 to 10:30am EST

- **Location:** https://yale.zoom.us/my/yryang

- **Minute takers:** Alex, Jacobs, Jensen, Jordi, Kai, Mahdi, Shenshen, Richard.

- **Current minute taker:** Jensen

----

**IETF OpenALTO Meeting: June 6, 2022**

**Agenda:**

- SIGCOMM'22 NAI submission

**Minutes:**

Notes taker: Jensen

* Mahdi reported the progress on FTS global resource control design (https://github.com/openalto/ietf-hackathon/issues/47)
* Jensen introduced how the FTS optimizer works. Some issues were discussed:

  * From the latest released FTS source code (https://github.com/cern-fts/fts3/blob/v3.11.2/src/server/services/optimizer/OptimizerConnections.cpp#L127), we know the current FTS optimizer algorithm will adjust the decision (the number of connections) in a logical link based on the EMA of the throughput (if we avoid the success rate issue):
    * If the EMA increases, the optimizer will increase the decision until reaching the upper bound;
    * If the EMA decreases, it will check if the round log of the EMA decreases:
      * If true, decrease the decision until reaching the lower bound;
      * Otherwise, keep the value.
  * But in an older version of the FTS optimizer (https://github.com/cern-fts/fts3/blob/3.5/src/server/services/optimizer/OptimizerConnections.cpp#L148), it does not compare the round log of the EMA.
  * Consider a single logical link:
    * When there are running connections, the decision will be increased until reaching the upper bound;
    * TODO: look at the real impact of adding a new flow; the more flows, the more likely MD can cause under utilization
  * Then consider multiple logical links sharing the same bottleneck:
    * When new flows are added to a logical link, the decision of this logical link will be increased until reaching the upper bound;
      * In the latest FTS version, other logical links will not decrease the decision because of the round log
      * In the older version, other logical links will decrease the decision until one of the link reaches the bound (see the dashboard example: https://fts3-docs.web.cern.ch/fts3-docs/docs/optimizer/monitoring_view.png)
    * TODO: understand how the optimizers of different logical links affect each others.
    * TODO: understand when the decision will be decreased in the latest version.


----

**IETF OpenALTO Meeting: May 30, 2022**

**Agenda:**

- SIGCOMM'22 NAI submission

**Minutes:**

Notes taker: Shenshen

* Mahdi reported the progress on studying [a servey](https://jessiehuiwang.github.io/files/2019CN_interDC.pdf) and suggested hierachy network-wide scheduling. 
* Richard proposed Task 1-3 on Google doc (not sure if we can post the edit-link on this public repo) and discussed them with the team. Task 3 might be discussed in the next meeting.
* The paper (due: July 1st) is a grand vision paper with concrete pieces (demo 1-3). Richard suggested getting the implementation starts early (by Monday next week latest).
* Jensen will go over the progress on Task 2 (link posted on slack) on Wednesday. 


----

**IETF OpenALTO Meeting: May 23, 2022**

**Agenda:**

- SIGCOMM'22 NAI submission

**Minutes:**

Notes taker: Mahdi

Current ongoing work for submission to NAI has three tracks: 

1. **Manual Workflow Scheduling** Based on Jacob's LP proposal for which first formulation and protocol proposals can be found [here](https://docs.google.com/document/d/1ia8S0DzDdFNwuB9hCwCeoc3IAVvVRLB6qpBYKS-t3QU/edit) and [here](https://docs.google.com/document/d/1QlNsh2pNn0WzMP43okY37ODvnEuQrPxrF9aOJqUMVuo/edit).
	* 	**Current state** Needs checks of algorithm and clear write-up - followed by simulation experiments and analytical evaluations - Richard will impose a story - **Final step** To merge with Rucio downloader. 
2. **Automatic Workflow** Based on Jensen's formulation [here](https://www.overleaf.com/project/626fc17f4e3e279ce4df8949).
	* This divides the automatic workflow into two subproblems of destination selection and replication schedules. The second part is identical to work track #1. However, it differs from two perspectives. 
		1. The scale is higher (millions of flows) 
		2. In 1 we have assumed that the flows are primarily bottlenecked at the edge. (**Kai's comment:** Given L2 tunneling in Rucio transfers the edge bottleneck assumption also remains legitimate for this case.)  			
3. **Flow Scheduling** Alex's work is based on a three-level formulation of the flow optimization problem. 
	* **Current state:** Formulation is concrete and complete, but needs evaluations. Most likely to be submitted. 		

	
### Decisions
1. 	To temporarily abandon track 1, and focus on finalizing the manual workflow case. 
	* **Steps:** 	1- To clear the write-up of the algorithm and protocol. (check the linearity conditions.) 2- To do evaluations based on simulation. (Jensen). 3-To finish writes up given an imposed story which will be devised by Richard in the upcoming days. 


----

**IETF OpenALTO Meeting: May 16, 2022**

**Agenda:**

- SIGCOMM'22 NAI submission

**Minutes:**

Notes taker: Kai

* The team discussed the problem formulation for the positioning paper to be submitted to NAI'22.
* Jacob updated the progress on downloading use cases (which replica to choose to download to minimize the downloading time)
* Richard suggested to look into multi-level queue in OS and the estimation method of Hedera

----

**IETF OpenALTO Meeting: May 9, 2022**

**Agenda:**

- Review of pull requests
- Quick around the table status update
- Architecture
- Rucio / FTS 114 Hackathon story
- SIGCOMM'22 NAI submission
- Wrap up and next tasks

**Minutes:**

Notes taker: Jacob

* Administration: meeting minutes at ietf-wg-alto/wg-materials
* Pull requests review:
	* openalto/alto #5 (separate parser logic from server logic) getting close to completion -- only two outstanding conversations
		* small change in comments language
		* change name of algorithm from "JENSEN" to "NUM"
	* openalto/alto #8 -- CI/unit-test pull request
		* just merged! Now completed
	* openalto/ietf-hackathon #44: documentation
		* mostly just typos
	* also discussion of PR on the Rucio repo; Jensen waiting for response on Slack
* Quick around-the-table update
	* Jensen:
		* analyzed how FTS scheduler and optimizer works; see issue on GitHub
		* issue to discuss later about control framework
	* Richard:
		* IPFS:
			* opportunity: think about, for example, ALTO integration with IPFS
			* IPFS highly relevant; part of movement to make web distributed again
			* thus, recommend: *read about IPFS*
			* interesting goal: work with IPFS to integrate ALTO for peer selection -- perfectly able to be integrated, and complements ALTO-Rucio integration
			* we should invite the IPFS developers to work with us
			* in addition, recruit a student or two to work on this
* Discussion re: integrating ALTO with Rucio replica selection step and transfer scheduling step
	* Jensen: need to have an interface between Rucio and FTS in order to better understand how to select replicas
	* see Jensen's issue on GitHub -- nondeterminism in FTS scheduling means harder to predict replication rule TTC 
	* Jensen explained on how FTS works: #36 on openalto/ietf-hackathon
		* basic FTS concepts:
			* link: ordered pair (source set, destination set)
			* VO: virtual organization, that represents a science organization
			* VO shares: each VO gets some number of slots for a given link
			* weighted fairness determines how many shares each VO gets -- centralized controller
		* FTS decides which transfers should start first (transfer scheduler)
			* this invovles randomness in order to avoid starvation -- but makes it harder to predict rule TTC
			* then, after weighted fairness determines how many shares per VO, FIFO is used to maximize bandwidth
		* optimizer
			* tuning after the transfers have started
* Richard notes two fundamental new challenges: **multi-domain** and **multi-experiments**
* For Wednesday, focus on architecture/algorithm

----

**IETF OpenALTO Meeting: May 2, 2022**

**Agenda:**

- Quick around the table status update
- Architecture
- Rucio / FTS 114 Hackathon story
- SIGCOMM'22 NAI submission
- Wrap up and next tasks

**Minutes:**

Notes taker: Jordi

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

----

**05/02/2022**
---------------
**Agenda:**
- Quick around the table status update
- Architecture
- Rucio / FTS 114 Hackathon story
- SIGCOMM'22 NAI submission
- Wrap up and next tasks

**04/28/2022**
---------------
**Agenda:**
- PRs status:
    - Rucio PR: https://github.com/rucio/rucio/pull/5364
    - ALTO parser logic: https://github.com/openalto/alto/pull/5
    - Docs: https://github.com/openalto/ietf-hackathon/pull/44
- New student to work on devops
- Quick around the table status update
- Wrap up and next tasks

**04/25/2022**
---------------
**Agenda:**
- Quick around the table status update
- Show FTS3 scheduler code
- Ticket #20: John Graham asked whether we can start using PRP Kubernetes dev environment
- Initial status and scope of DOMA presentation (Wednesday at 10:00 AM ET this week)
- Architecture discussion
- Wrap up and next tasks

**04/20/2022**
---------------
**Agenda:**
- Quick around the table status update
- John Graham asked whether we can start using PRP Kubernetes dev environment
- Plan for the 4/21 sync up with Mario (the app-level queue status protocol as an ALTO service)
- Plan for the larger 4/27 CERN meeting (Wednesday next week)

**04/18/2022**
---------------
**Agenda:**
- Quick around the table status update
- Plan for the 4/21 sync up with Mario (the app-level queue status protocol as an ALTO service)
- Plan for the larger 4/27 CERN meeting (Wednesday next week)
- Go over the discussion on architecture

**04/14/2022**
---------------
**Agenda:**
- Monday 9-10am, Wed 9-9:30am, Thu 10-10:30am EST
- Quick around the table status update
- Staffing
- Currently work in progress tickets
- Proposed deadlines

**04/11/2022**
---------------
**Agenda:**

- Quick around the table status update.
- Code review: https://github.com/openalto/alto/pull/5 (Change architecture to separate parser logic from server logic).
- Review TODO Column: https://github.com/orgs/openalto/projects/1/views/2
- Hackathon 114 stories: (1) Rucio/CERN, (2) 5G, Edge Computing, SRv6/PCE.

**04/04/2022**
---------------
**Agenda:**

- Confirm meeting times (Mon 9:00-10:00am EST and Thu 10:00-10:30am) work for all
- Archive all completed tickets into the HKT113 dashboard
- Development and code review process
- Status of OpenALTO code base in https://github.com/openalto
- Discuss stories for HKT114
- Ticket assignments

**03/29/2022**
---------------
**Agenda:**

- Set up meeting times (day/time) that works for all
- Goals IETF Hackathon 114
- EPIC and Sprint planning for Hackathon 114

**03/16/2022**
---------------
**Agenda:**

- Welcome statement
    - Motivation
    - What is ALTO?
    - The ALTO Code Base Project
- Project management
    - Approach: team, project management, philosophy
    - Tools
    - Documentation
    - Meetings the next days and hackathon logistics
- IETF 113 Hackathon
    - Allocate time to do a first dry run
    - The "113 ALTO Hackathon Story"
    - Tasks scoping and Github tickets assignments


**03/15/2022**
---------------
**Agenda:**

- Wed 2nd kickoff logistics
- Dry runs
- Around the table status update
- Tasks scoping and Github tickets assignments
- Hackathon logistics

**03/14/2022**
---------------
**Agenda:**

- Welcome statement
    - Motivation
    - What is ALTO?
    - The ALTO Code Base Project
- Project management
    - Approach: team, project management, philosophy
    - Tools
    - Documentation
    - Meetings the next two weeks
- IETF 113 Hackathon
    - Allocate time to do a first dry run
    - The "113 ALTO Hackathon Story"
    - Tasks scoping and Github tickets assignments

**03/11/2022**
---------------
**Agenda:**

- Kickoff logistics

- IETF 113 Hackathon
    - The "113 ALTO Hackathon Story"
    - Tasks scoping and Github tickets assignments


**03/10/2022**
---------------
**Agenda:**

- IETF 113 Hackathon
    - The "113 ALTO Hackathon Story"
    - Tasks scoping and Github tickets assignments

**03/09/2022**
---------------

**Agenda:**

- Welcome statement
    - Motivation
    - Approach: team, project management, philosophy
- Project management
    - Meetings the next two weeks
    - Tools
    - Documentation
- IETF 113 Hackathon
    - The "113 ALTO Hackathon Story"
    - Tasks scoping and Github tickets assignments

