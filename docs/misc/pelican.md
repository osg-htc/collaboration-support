## Uprade of the OSDF origin to Pelican for Collaborations

The OSG Collab AP had an **OSDF** door deployed on the access point (ap23.uc.osg-htc.org) that provided users with authenticated access to a Ceph cluster, that provides high capacity storage to shared project directories. HTCondor jobs running in the OSPool at remote **Execution Points (EPs)** (remote worker nodes) can access the filesystem either via a client tool or via an HTCondor plugin that is invoked in their submit scripts. The storage is also mounted on the AP at /ospool/uc-shared/project. 

On **11/21/2024**, OSG/PATh staff migrated the OSDF door from the OSG Collab AP to a separate infrastructure to allow upgrading the origin to the Pelican Platform (https://pelicanplatform.org/) and provide shared project access to users at other APs (ap20.uc.osg-htc.org and ap21.uc.osg-htc.org).

The migration should have been transparent to the OSG Collab AP. If using the HTCondor plugin, no changes are needed in your submission scripts. For reference, the general purpose documentation found here (https://portal.osg-htc.org/documentation/htc_workloads/managing_data/osdf/) is also applicable to the users of the OSG Collab AP. It describes using the HTCondor plugin to move data to and from the OSDF/Pelican Origin. 

In a nutshell:
  1. Include the following in your submit script for an OSPool job to transfer a file from your project directory at the origin to the EP environment:
  
    transfer_input_files = osdf:///ospool/uc-shared/project/<your_project>/<file>
  5. Include the following in your submit script for an OSPool job to transfer a file to your project directory at the origin from an EP enviroment:

    OSDF_LOCATION = osdf:///ospool/uc-shared/project/<your_project>/<file>
    transfer_input_files = $(OSDF_LOCATION)/<file>
The upgrade to the Pelican platform, which uses federated urls for the origin, still keeps the same prefix *osdf://*. After the upgrade, *osdf://* simply points to *pelican://osg-htc.org/* 

If you are using a client in your runtime script at the EP, then the previous tool, **stashcp**, will continue to work as long as the version is > 6.12 except recursive access (*-r* flag). Thefore, we recommend that groups migrate to using the pelican client instead. 

| stashcp    | pelican |
| -------- | ------- |
| `stashcp -d osdf:///ospool/uc-shared/project/<your_project>/<file> .`  |   `pelican object get -d osdf:///ospool/uc-shared/project/<your_project/<file> .` |
|  `stashcp -d <file> osdf:///ospool/uc-shared/project/<your_project/<file>` |    `pelican object put -d <file> osdf:///ospool//uc-shared/project/<your_project/<file>` |


The pelican equivalent of the stashcp client read command: `stashcp -d osdf:///ospool/uc-shared/project/<your_project>/<file> .` is  `pelican object get -d osdf:///ospool/uc-shared/project/<your_project/<file> .`
Similarly, the pelican equivalent of the stashcp write comamnd, `stashcp -d <file> osdf:///ospool/uc-shared/project/<your_project/<file>` is `pelican object put -d <file> osdf:///ospool//uc-shared/project/<your_project/<file>`

If your container image was built using one of the OSG base environments, then the pelican client tool is already included. The pelican client can be installed from the osg repo with `dnf install pelican`. Refer to this documentation (https://osg-htc.org/docs/common/yum/) to add the osg repository.

