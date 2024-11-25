## Upgrade of the OSDF origin to Pelican for Collaborations

The OSG Collab AP had an **OSDF** door deployed on the access point (ap23.uc.osg-htc.org) that provided users with authenticated access to a Ceph cluster, that provides high capacity storage to shared project directories. HTCondor jobs running in the OSPool at remote **Execution Points (EPs)** (remote worker nodes) can access the filesystem either via a client tool or via an HTCondor plugin that is invoked in their submit scripts. The storage is also mounted on the AP at /ospool/uc-shared/project. 

On **11/21/2024**, OSG/PATh staff migrated the OSDF door from the OSG Collab AP to a separate infrastructure to allow upgrading the origin to the Pelican Platform (https://pelicanplatform.org/) and provide shared project access to users at other APs (ap20.uc.osg-htc.org and ap21.uc.osg-htc.org).

The migration was designed to be transparent to users of the OSG Collab AP.

## HTCondor Plugin Users: No changes are needed in your submission scripts. 

The [OSDF documentation](https://portal.osg-htc.org/documentation/htc_workloads/managing_data/osdf/) remains applicable and describes how to use the HTCondor plugin to move data to and from the OSDF/Pelican origin.

Here are key examples for transferring files using the HTCondor plugin:

  1. Transfer a file from the project directory to the EP environment:
  
    transfer_input_files = osdf:///ospool/uc-shared/project/<your_project>/<file>
  5. Transfer a file to the project directory from the EP environment:

    OSDF_LOCATION = osdf:///ospool/uc-shared/project/<your_project>/<file>
    transfer_input_files = $(OSDF_LOCATION)/<file>

Note: The Pelican platform uses federated URLs for the origin, but the prefix osdf:// remains unchanged. After the upgrade, osdf:// maps to pelican://osg-htc.org/.

### Transition from Stashcp to Pelican
If your runtime scripts at the EP rely on the stashcp tool, it will continue to work (version 6.12 or higher), except for recursive access (-r flag). However, we recommend transitioning to the Pelican client for improved compatibility and features.

Command Comparison

| Stashcp Command    | Pelican equivalent |
| -------- | ------- |
| `stashcp -d osdf:///ospool/uc-shared/project/<your_project>/<file> .`  |   `pelican object get -d osdf:///ospool/uc-shared/project/<your_project/<file> .` |
|  `stashcp -d <file> osdf:///ospool/uc-shared/project/<your_project/<file>` |    `pelican object put -d <file> osdf:///ospool//uc-shared/project/<your_project/<file>` |

### Installing the Pelican Client

If your container image is built using an OSG base environment, the Pelican client is already included. Otherwise, you can install it from the OSG repository:

    dnf install pelican 

Refer to the [OSG Yum documentation](https://osg-htc.org/docs/common/yum/) to configure and add the osg repository.

For detailed instructions on using the Pelican platform, visit the [Pelican Platform Documentation](https://docs.pelicanplatform.org/).
