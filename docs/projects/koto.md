## KOTO

KOTO is an international collaboration of an experiment based at the JPARC HEP facility in Japan.


## Access Point

KOTO submits out of the Connect node: login.collab.ci-connect.net. To request an account, visit the portal at https://ci-connect.net and 
ask to join the [PATh Collaborations](https://www.ci-connect.net/groups/root.collab) group. [KOTO](https://www.ci-connect.net/groups/root.collab.KOTO) is a subgroup under PATh collaborations and a separate request needs to be made to join by clicking the request memberhip button.  

## Jobs to the OSPool

Inlined below is a submit script to run a KOTO job on the OSPool

    #!/bin/bash
    Universe = Vanilla
    Executable     = run_koto.sh
    Requirements = HAS_SINGULARITY == TRUE
    +SingularityImage = "/cvmfs/singularity.opensciencegrid.org/ppaschos/koto-dev:latest"
    transfer_input_files = e14_201605.mac
    Error   = output.err.$(Cluster)-$(Process)
    Output  = output.out.$(Cluster)-$(Process)
    Log     = output.log.$(Cluster)
    should_transfer_files = YES
    WhenToTransferOutput = ON_EXIT
    request_cpus = 1
    request_memory = 2GB
    request_disk = 2GB
    +ProjectName="collab.KOTO"
    Queue 1

KOTO uses a software stack that is included in the Singularity image - shown in the script above. The image is deployed on the remote execution nodes and jobs run within the Singularity container. The input file, e14_201605.mac, is sent to the execution node as part of the job. The execution script, run_koto.sh, sets the environment and includes all invocations to executables. The following script, run_koto.sh, runs a benchmark example from the E14 library.

    #!/bin/bash
    echo $HOSTNAME
    source /opt/koto/root/v6.22.02/bin/thisroot.sh
    source /opt/koto/geant4/10.05.p01/bin/geant4.sh
    echo "PATH --> " $PATH
    echo "LD_LIBRARY_PATH --> " $LD_LIBRARY_PATH
    echo "ROOTSYS --> " $ROOTSYS
    echo "G4 data environent"
    env | grep G4
    export E14_TOP_DIR="/opt/koto/e14/201605v6.2/e14"
    echo "E14_TOP_DIR=" $E14_TOP_DIR
    source /opt/koto/e14/201605v6.2/setup.sh
    output="output.root"
    nevent=1000
    seed=0
    echo "Running Code"
    /opt/koto/e14/201605v6.2/e14/examples/gsim4test/bin/gsim4test e14_201605.mac ${output} ${nevent} ${seed} ${seed}


## Storage access

Besides their home directories on login.collab.ci-connect.net, users have access to local storage in /scratch/<user_id> and distributed storage in /collab/user/<user_id>. In addition, the collaboration has access to /collab/project/KOTO for sharing data products between the users. 

The distributed storage is http accessible: http://stash.osgstorage.org/collab/KOTO and data can be downloaded using a browser or command line utilities like wget or curl.
