----

**Logistics:**

- **Meeting times:** Mon 9:00 to 10:00am EST, Wed 9:00 to 9:30am EST, Thu 10:00 to 10:30am EST

- **Location:** https://yale.zoom.us/my/yryang

- **Minute takers:** Jensen, Alex, Jacobs, Jordi, Kai, Mahdi, Ryan, Shenshen, Richard.

- **Current minute taker:** Ryan

---------------------

**Meeting minutes (ALTO-IETF hackathon meeting) Monday Aug 8, 2022**

**Minutes:**

Notes taker: Ryan

* Implementability. Possible Solutions:
	1. Network rate limit control knob. 
	2. Multiple controllers
* Logistics
	1. Meeting Louis
* Proposal (Jordi): using 2013v4 with TC
* Direction
	1. Big breakthroughs come from either supporting new workloads or using new hardware. Our workload is big data sciences.
* Big Science Big Data
	1. Supply side/resource environment: multidomain networks
		a. Controllability is limited due to multiple controllers.
	2. Demand: workload
		a. Largest IoT on Earth (within the experimental data)
		b. BSBD has larger and more predictable workload ()
	3. Further discussion of differences between DC, TCN, and FTS in TCN project notes.
* Goals 
	1. deploy ALTO
	2. Meeting with Mario: Thursday, 10:00am ET = 16:00 CET.
	3. Integrate with routing control plane
		a. Develop Route Plugin for SENSE and for PCE (Integrate w/ routing control plane)
		b. Intelligence: computing mesh
			i. Current models: traditional PCE, Sincronia, FB Entitlement, BS
		c. Rate and Route are complementary control variables.
		d. Related, Soon-To-Be-Publisehd Work: Cebinae (Sigcomm)
	
	goals: deploy ALTO + zero order, minimize disruption to FTS, capacity planning, bandwidth enforcement.

---------------------

**Meeting minutes (ALTO-IETF hackathon meeting) Monday Aug 1, 2022**

**Minutes:**

* Two issues of ALTO WG emphasized by the AD: 

	1. 	We are slow in terms of devising and deployment.
	2. We are not actively engaged in the discussions. (empty discussion queue.) 

* Deployment tracks toward IETF 114: 

	1. Telefonica CDN use case (Louis's team works). Internal team will not focus on this track (relatively closed code sources + already in good hands/shape.)
	2. FTS/TCN track. 
	3. MPQUIC/MPTCP track (We may also want to focus on this track, since it is a promising branch, ALTO might as well be used as a mean to provide information in cellular handovers. -inherently multi-path tunneling-). 

* Tracks to follow for TCN: 

	1. **Analytical:** FTS analysis (Richard mentioned) + Zero order subtleties + Convergence proofs (I have added to the list of TODOs). 
	2. **Deployment track:** Technical content, system model/architecture/ results. 

* Technical issues of TCN: (brought up by Richard) 
	
	1. How to coordinate with ESnet/ SDSC team and integrate TCN with their efforts. (Richard's comment: Frequent path changes may become futile when new transfers are being submitted every minute. - My comment: Also, frequent routing changes may nullify zero-order state adaptations.)
	2. Limited controllability: Selected control knob (no TCP connections) significantly limit the feasible regions, thus throttles the controllability criterion we were rooting for. 
	
		**Solutions:** A. To only support relative throughput weights as input conditions (currently deployed) **Sematincs:** Scheduling scheme should be work-conserving. B.  To request bounded aggregated BW from data path. C. To use time-devision mutliplexing to achieve more fine-grained control. 
	
	  

**Decisions:**

1. To participate in SDSC/ESNet meeting/ speed should be aligned with internal deployment's progress so we can actively get engaged. (Kai's suggestions.)


**IETF OpenALTO Meeting: July 18, 2022**

**Agenda:**

- Preps for IETF 114 ALTO Hackathon
- IETF 114 ALTO Hackathon dashboard: https://github.com/orgs/openalto/projects/1/views/2

**Minutes:**

Notes taker: Kai / Jordi

* Message that we can/want to send:
    * <= unit (e.g., 100 Mbps): resource control
    * \>= unit (e.g., 100 Mbps): integrated service (admission contrl)

* <= unit; No weight, no guarantte

    * resource control beyond bw, e.g., mem buffer size use ("imple a shell, query the socket buffer size and report to the control)
    * mem_size <= 1 GB  => unit / socket buffer size query (CAN) 

* In the controller, there is a simple resource mapping logic:
    * pipe -> resource list (alto) => resource mapping logical
        * vector n (the number of connections for each pipe, indexed by pipe): n
        * bw pipe -> resource list: matrix
            * network resource (pipe -> network entities)
                * pipe -> [0, 1, 0, ...]   // this pipe uses those links with entry 1
                * pipe: tput of this pipe
* mem resource (pipe -> mem of each RSE)

Main topics of the meeting: setting goals for the Hackathon (basic & stretch)

- Resource model:

  1. Enable options in the configuration file
  2. Show in the demo that the target resource control can be achieved

  Mahdi mentioned absolute value is necessary when some links are not controlled by TCN.

  **Decision: use the resource control model (<= XXX unit, using absolute value)**

- Resource types:
  
  1. Collect information (bandwidth, TCP buffer size) for each link
  2. Enable query of the information 

  **Decision: supporting multiple resource types is a stretch goal**

- ALTO messaging format:

  **Decision: path vector with modification to support multiple (src, dst) pairs instead of cross-product**

- Zero-order protocol:

  1. Concern is raised about the robustness of the control algorithm

  **Decision: implement a two state-based control protocol (estimate state and running state)**

  Implementing a continuous control protocol is set as a stretch goal.





---------------------

**IETF OpenALTO Meeting: July 11, 2022**

**Agenda:**

- Preps for IETF 114 ALTO Hackathon

**Minutes:**

Notes taker: Jordi

- Use cases for demo

    Use case 1: FTS global resource control using ALTO

    Use case 2: Rucio automatic replica workflow using ALTO

Actual notes were taken in this doc: https://docs.google.com/document/d/1xNSxM5WWWBW5BjFqoncXMcs9HtjzA_LGFUcp4NU3nzk/edit

---------------------

**IETF OpenALTO Meeting: June 20, 2022**

**Agenda:**

- Preparing for meeting with FTS team

**Minutes:**
Notes taker: Jensen

* Q: What is the major findings to talk to FTS?
  * FTS makes the guarding of throughput decreasing (round log) so that
    decreasing the decision is extremely harder
  * FTS is based on gradient algorithms on each logical link individually
    * Not efficient (pareto-optimal)
    * Not control fairness at all
* Design Proposal:
  * We are going to introduce an aggregation function, then give gradient
    algorithms to reach pareto-optimal
  * Propose a mechanism for bandwidth control
  * Integrate Rucio into the control loop
  * Detailed discussion is on the slack channel (start from June 20 9:31 am ET)
* Q: what to do if we can modify both FTS and Rucio

----
**IETF OpenALTO Meeting: June 13, 2022**

**Agenda:**

- Reporting last-meeting assignments and planning for the next step.

**Minutes:**

Notes taker: Shenshen

* Jensen reported his experiments on FTS (the goal is to make sure we are not making up things). Setting: every 20 sec, sending files through 10M-limited links. 
    * **Highlights in Discussion:** (1) success rate and nFailedLastHour [link](https://gitlab.cern.ch/fts/fts3/-/blob/develop/src/db/mysql/OptimizerDataSource.cpp#L325); (2) why the case "decision: 8, running: 4" appears? probably due to the constraints on src; (3) why FTS starts with maximum [link](https://github.com/cern-fts/fts3/blob/v3.11.2/src/server/services/optimizer/OptimizerConnections.cpp#L193)? a related corner case [link](https://github.com/cern-fts/fts3/blob/v3.11.2/src/server/services/optimizer/OptimizerConnections.cpp#L121).
    * **Comments:** build a clear "physical" (not engineering) model and focus on stable states (rather than transient states).

* Madhi reported issues (posted on slack channel).
    * **Highlights in Discussion:** : (1) a conrner case [link](https://gitlab.cern.ch/fts/fts3/-/blob/develop/src/server/services/optimizer/OptimizerConnections.cpp#L315) related to the race condition; (2) FTS always maximizes the #connections (the knee point between the transfer bottleneck and storage/network bottleck).
    * **Comments:** (1) remove conrner cases and come up with the main setting; (2) operators may want coarse-grained operations; (3) what is FTS's model and what is a proper model [link](https://gitlab.cern.ch/fts/fts3/-/blob/develop/src/db/mysql/OptimizerDataSource.cpp#L285).
    * **TODO:** prove the convergence of maximum #connections.
    
----
**IETF OpenALTO Meeting: June 7, 2022**

**Agenda:**

- OpenALTO design and current development state (to identify the gaps for the hackathon 114). 

**Minutes:**

* **Open Daylight ALTO project** [link](https://wiki-archive.opendaylight.org/view/ALTO:Architecture) Is not being maintained anymore. Will be removed/ archived soon unless we provide test-cases and upgrades. 

	* **Design quesiton:** Should the environment be controller independent, or inside a particular controller architecture? 
	* 	**Decision:** OpenALTO should be independent, but have plugins to various controllers. 
	* Reason: Have to support multi-domain (controller) networks. 
	* Issue: Multiple controllers (ODL, ONOS, Wireless -ORAN-, G2-Mininet)

For now, we will base the devs on Mininet, because we should have our own demo env besides PRP. 

* **Practice:** [BENOCS paper](https://people.csail.mit.edu/gsmaragd/publications/CoNEXT2019/CoNEXT2019.pdf) -Page 7- A set of listeners submit changes to aggregator, that will update a reference DB. Previously we used ODL data store. This way we will be controler independent, besides a plugin to update the DB triggered by G2-Mininet  arch changes.)
	* 	**Question:** Best DS to use? **Redis** suggested by Kai, mainly for high performance. *Rationale:* To be viable in 5G congestion control ([PBE-CC](https://dl.acm.org/doi/pdf/10.1145/3387514.3405880)). 

**Current repositories:**

1. **Sextant:** Is a fork of the ODL ALTO repository with some minor BGP related changes. (Sextant provides ALTO server funcionalities.)
	* Sextant components: 
		1. Basic: Basic services like Network and Cost Maps. 
		2. Core
		3. Karaf: creates executable Karaf containers.  
		4. Release-features: Aggreagator for all the features.  
2. **ALTO:** ALTO client API, parsers, and mock server functionalities for testing. 
3. **Others:** Are ancilary ones created for specific demos (should be moved into the main repo, because they provide a single subtool. 

**TODO**

1. To integrate sextant and ALTO into a single OpenALTO repo (with northbound (APPs)/ Kernel/ southbound (Contollers)/ DB modules). [(Specified here)](https://docs.google.com/document/d/1p8u9I7RbI9yFTNnQEmdoZPslV3Wbnl0R_mkK-JHWGHA/edit). - Following best practice in design (Usecase driven multiple iterations)
2. Create a landing README that describes the ARCH and different components of the env. 
3. Move other repos to appropriate destinations. 

**Major decision (to be made)** Class centric vs Data Driven design: Unifying interfaces with known schemas enable multiple programming languages, and because each controller may support different PLs. 

---

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

