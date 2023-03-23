Placeholder to discuss future ALTO work. The discussion is open till end of May 2023.


# Proposal # 1: Support ATLO Operations

## Rationale

*	Many I-Ds are being proposed to ALTO.
*	Some deployments/products are being disclosed.
*	Having a referent WG is a signal that the IETF is ready to support operations and fix flaws/limitations that will be reported.
*	ALTO integration complications were out of the scope. Documenting those with a set of deployment choices may be a helper for other deployments.
*	There is constant engagement and dedication of a core team to deliver ALTO specs.

## Proposed direction of work

*	Recharter the WG with a focus on ALTO maintenance and integration with data sources. Dedicated YANG modules will be produced.

# Proposal # 2: Revitalize ALTO

## Rationale

*	Some of the proposed ALTO work is research-oriented (PANRG, would be more appropriate for some items), while other may be conducted in new WGs (e.g., CATS).
*	Some of the key foundations of ATLO might not be valid after 15 years.
*	Closing the WG is not a failure, but a sign of ALTO specification maturity.
*	Revitalizing the ALTO effort is thus needed.

## Proposed direction of work

*	Consider closing ALTO right after the completion of OAM/Transport items.
*	Move ALTO maintenance to TSVWG.
*	Use the ALTO/TSVWG mailing lists to socialize deployment experience.
*	Based on the maintenance that might be shown in TSVWG and shared deployments, reassess the interest of the community in enriching ALTO with additional features by organizing a formal BoF.

# Proposal #3: Support ALTO extensions for the new industry needs

## Rationale:

*	Many I-Ds have been proposed describing the importance of leveraging ALTO key core architecture to enable the new industry needs, where close cooperation between the application and the network is critical.
*	Allowing these extensions would enable the group to grow and unlock its true potential, also attracting other industry players that have been writing ALTO I-Ds, but not fully joined us yet because their proposals were tagged as being out of the scope for the current charter.
*	Lots of positive energy and determination in the WG, as we understand the potential positive impact (better application performance).
*	The proposed work can't be done in other groups, and even if we tried to do so, it would be improper from an architecture/engineering standpoint. For instance, trying to move the exposure of compute information for determining edge services to CATS is not viable since "Exposure of network and compute conditions to applications is not in the scope of CATS" [1]. ALTO is inherently/by definition very well positioned here, since it's designed to expose such kind of information to the application, that is key to the industry problems we are working to resolve.  
*	There is a natural, coherent story for ALTO, which started from P2P networks, then CDNs, and now it's moving into edge computing, where the application requires more than ever to cooperate closely to meet stringent throughput and delay requirements. 
*	There is a belief that the ALTO WG has been running for a very long time, but this in general is not a good technical reason to base a rechartering decision on. From the abovementioned trend standpoint, keeping ALTO open to provide the IETF a platform for close application-network integration appears more important than ever before.

## Proposed direction of work:

*	Recharter the WG with a focus on ALTO to cover both maintenance and the new industry needs (where such needs are currently being discussed in the ALTO WG internal meetings and mailing list, see also my next comment on logistics).
