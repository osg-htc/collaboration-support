## Uprade of OSDF to Pelican for Collaborations

The OSG Collab AP had an OSDF door deployed on the access point that provided users with authenticated access to a Ceph storage cluster for shared projects from HTCondor jobs to the OSPool running at remote Execution Points (EPs). Users running jobs on the OSPool access the filesystem either via a client tool (stashcp) or via an HTCondor plugin that is invoked in their submit scripts. The storage is also mounted on the AP at /ospool/uc-shared/project. 

The general purpose documentation found here (https://portal.osg-htc.org/documentation/htc_workloads/managing_data/osdf/) is also applicable for the users on the OSG Collab AP. It describes using the HTCondor plugin to move data to and from the OSDF Origin. 
In a nutshell:
  1. Use this for your job running on the OSPool to a file from your project directory:
  transfer_input_files = osdf:///ospool/apXX/data/<username>/<file>
  2. Use this for your jobs running on the OSPool to write a file into your project directory:
  OSDF_LOCATION = osdf:///ospool/
  transfer_input_files = $(OSDF_LOCATION)/<file>


