## Collab Access Point (AP)

Onboarding to the OSG managed and Collaboration dedicated Access Point. Users will be trained in job submission and software development appropriate for the dHTC jobs. In addition, the project will be supported with visible performance metrics coming from the central OSG Accounting dashboard [Gracc](https://gracc.opensciencegrid.org/d/000000074/gracc-home?orgId=1).
Collaboration Support (CS) staff will provide consultation services on how to best optimize the workflow, help with debugging any issues encountered and facilitate coordination with other institutional partners that require access to produded data products.


## Data management and storage

All projects will be provisioned with distributed storage on the Open Science Data Federation (OSDF) and local storage on the AP. Collaboration support will work with the collaboration in managing the storage within the limits agreed upon during the onboarding process. Staff will train users on how to best 
use data management tools to monitor, track and distribute data to jobs or other institutional storage locations. 
Collaboration support staff will also work with the PI in understanding the long-term needs of the project and architect solutions where the collaboration can integrate with the OSDF federation. These include assistance in setting up Origins of data which will distribute them to the network of Caches which are placed in close proximity to execution points. CS staff, in coordination with other OSG teams, will also assist in provisioning services of 
institutional managed caches in proximity to locations where compute cycles are available or deploy [Hosted CEs](https://osg-htc.org/docs/compute-element/hosted-ce/) on behalf on the collaboration. Additional tools, such as Rucio, are also available to provide a service for 
distributing data without the need for an Origin. Data in this case is hosted in part at each member institution with Rucio providing a centralized 
management service of where the data are and where they need to be replicated - either for use in dHTC jobs or local batch systems.

Follow this [link](https://atlas-kibana.mwt2.org:5601/s/x1t/app/dashboards?auth_provider_hint=anonymous1#/view/ce7055b0-2560-11ed-afcf-d91dad577662?_g=(refreshInterval%3A(pause%3A!t%2Cvalue%3A0)%2Ctime%3A(from%3Anow-6w%2Cto%3Anow))) to look at the Kibana dashboard tracking FTS transfers for Icecube, LIGO and XENON and Rucio information on XENON. 

## Integration of Collaboration owned resources

This process results in a pool of resources where a job submission from an AP, e.g. the Collab AP, would be run with priority because the collaboration owns the available compute cycle. This is accomplished by deploying Compute Entry (CE) points on the edge infrastructure of institutions. A project is affiliated with an entity named Virtual Organization, which is used to allow factory operators to directly send the project's jobs to the dedicated compute resources behind the CE. An international collaboration can then achieve a global computing scale if CEs are deployed nearby member institutions, all running jobs on their local clusters for the collaboration. Those clusters can either be wholly owned by the collaboration or the latter might have a compute allocation there. In the end, the project can leverage both the Open Science Pool and it's own pool to maximize throughput.
