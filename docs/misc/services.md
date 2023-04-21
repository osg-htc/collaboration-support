## Services


### Collab Access Point (AP)

Onboarding to the OSG managed and Collaboration dedicated Access Point. Users will be trained in job submission and software development appropriate for the dHTC jobs. 
In addition, the project will be support with visible performance metrics coming from the central OSG Accounting dashboard [Gracc](https://gracc.opensciencegrid.org/d/000000074/gracc-home?orgId=1).
Collaboration support staff will in a position to provide consultation services on how to best optimize the workflow, help with debugging on any issues
encountered and facilitate coordination with other institutional partners that require access to procuded data products.


### Data management and storage

All projects will be provisioned with distributed storage on the Open Science Data Federation (OSDF) and local storage on the AP. Collaboration support will
will work with the collaboration in managing the storage within limits agreed during the onboarding process. Staff will train users on how to best 
use data management tools to monitor, track and distribute data to jobs or other insittutional storage location. 
Collaboration support staff will also work with the PI in understanding the long term needs of the project and architect solutions where the collaboration can
further into integrate with the OSDF federation. These include assistance in setting up Origins of data which will distribute them to network of Caches which are 
placed in close proximity to execution points. Collaboration Support staff, in coordination with other OSG teams will also assist in provisioning services of 
institutional managed Caches in proximity to location where compute cycles are available. Additional tools such Rucio are also available to provide a service on 
distributing data without the need for an Origin. Data in this case is hosted in part at each member institution with Rucio providing a centralized 
management service of where the data are and where do they need to be replicated - either for use in dHTC jobs or local batch systems.

#### Integration of Collaboration owned resources

This process results in a pool of resources where a job submission from an AP, e.g. the Collab AP, would be run with priority because the collaboration owns 
the available compute cycle. This is accomplised by deploying Compute Entry (CE) points on the edge infrastructure of institutions. A project is affiliated with 
an entity named Virtual Organization, which is used to allow factory operators to directly run the projects jobs on the dedicated compute resources behind the CE. 
An international collaboration can then achieve global computing scale if CEs are deployed nearby member institutions, all running jobs on their local clusters 
for the collaboration. Those clusters can either be wholly owned by the collaboration or the latter might have a compute allocation there.
In the end the project can leverage both the Open Science Pool and it's own pool to maximize throughput.
