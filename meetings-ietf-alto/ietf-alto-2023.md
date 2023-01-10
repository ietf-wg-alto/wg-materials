----
**Logistics:**

- **Meeting times:** Tue 9:00 to 10:00am EST

- **Location:** https://ietf.webex.com/ietf/j.php?MTID=ma0e97cc97c4cd71bb59cf1a094682686

- **Minute takers:** Chunsan Xiong, Jensen, Jordi, Kai, Lauren, Lei Yixue, Luis, Mahdi, Qiao, Qin, Richard, Roland, Sabine, Yuhang, Ziyang Xing. 


------------------------------

**IETF, ALTO Meeting: January 10, 2023**

**Agenda:**

- Round-table updates
- Chartered items
- Review of 'In Progress/Discussion' tasks: https://github.com/orgs/ietf-wg-alto/projects/1/views/2

**Minutes:**

(Minutes taker started 20 minutes into the call, so the following notes are incomplete)

[Chunsan]
- China and SR for 5G

[Richard]
- How is SR being used?

[Chunsan]
- SR based gaming
- SR based content streaming 
- Use case: using ALTO to know available bandwidth, so the server can match the codec rate.

[Jordi]
- ALTO provides static info, need to know dynamic info. Need to discuss what features are needed to cover this use case.

[Lauren]

ALTO Multidomain for CERN. Requirements:

- Allowing to retrieve all the info from the agents
- Easy to use by the clients
- Stable, as the network grows
- Correct

Use path graphs with merging method to meet all the requirements
Working on Req 2 (easy to use)
All other reqs are met

Written a general structure and got feedback.

[Qin]

Let's continue to focus on chartered items: OAM, transport, deployments.

------------------------------

**IETF, ALTO Meeting: January 3, 2023**

**Agenda:**

- Round-table updates
- Chartered items
- Review of 'In Progress/Discussion' tasks: https://github.com/orgs/ietf-wg-alto/projects/1/views/2

**Minutes:**

- New transport
  - Richard submitted a new revision
  - A summary of changes
    - Title changed to Transport Information Publication Service
    - Emphasize the introduction of naming (uri/resource identifier) of incremental updates for multiple resources
  - Jordi: Will the tranport part be handled by some other documents?
  - Richard: Yes. This document only gives the naming and the data can be retrieved using HTTP/1.x or HTTP/2+
  - Roland: The idea is to make incremental updates independent of the transport mechanisms.
  - Jordi: Are there any gaps between AD's comment?
  - Richard: We think there is no gap now.
  - Richard: We write a document to specify how to use the mapping from TIPS to do the transport
  - Roland: We can rely on the standardized protocol
  - Roland: The new version addresses the comments from Mark.
  - Kai: There might be a conflict of abbreviations
  - Roland: We can use "A-TIPS"
  - Jordi: What is the timeline?
  - Richard: Get the documents done in two days.
- OAM
  - Jensen almost finished the access control
  - Two options from previous discussions
    - Define how to authenticate the client
    - Use ACL
  - Chair's feedback is to check RFC 7317
  - Kai: Does this indicate that the credentials are exposed in configuration files?
  - Jensen: Not necessarily in the configuration files. The servers may use databases to specify the information.
  - John: There are multiple ways including assigning tags to the clients/devices, e.g., [NetBox](https://netbox-3.nrp-nautilus.io). Role gives another layer of control.
  - Richard: Who is using the spec?
  - Jensen: It is based on OpenConfig
  - Richard: Typical access control is a single domain. ALTO is more like a multi-domain effort.
  - John: What we've done with NetBox is to use CILogOn.
  - Richard: Need some justification of the design.
  - Jordi: Base this document on some running code will be good.
  - Jordi: Looks like we need more feedback on this. It's always better to leverage some tools we already have instead of reinventing the wheel.
  - John: NetBox just uses CILogon with a lot of international participants.
  - Jordi: Take a look at NetBox and maybe integrate with some ideas.
- Deployment
  - The old wiki has been migrated to the new wiki
  - Call for continuous updates of the wiki
  - Richard: Add a optional section to identify issues in the current deployment.
  - Jordi: Put some contents from last IETF's presentation?
  - Richard: Lauren is working on developing software on CERN. She will give some updates next week.
  - John: Add some documentations on how to access the OpenALTO services, like the [example here](https://ucsd-prp.gitlab.io). We can throw users to use these services.
  - John: In the spec, how many simultaneous users can be supported?
  - Richard: Is there any discussion on the scalability in OAM?
  - Jensen: There are statistics on the information.
  - John: After the automation with NetBox, API gets totally destroyed when hunderds of machines make request to it. Convert API calls into GraphQL calls. Efficiency in GraphQL tremendeously helps us. It's a service that can be distributed using k8s. The biggest question is how fast do you expect the client to be talking to the server.
  - John: What would be the pacing to the ALTO server when requests come from high performance applications?
  - Richard: We need to do some performance benchmarking.

Note taker: Kai
