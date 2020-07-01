## LSST via Duke

LSST is supported by OSG Collaboration Services via the duke.lsst osg project

Sign up to get access to the OSG submit node here: [Duke CI-Connect Access Portal](http://login.duke.ci-connect.net)

## News

You can now use stashcp to transfer data to and from OSG as part of your computational workflow. You must transfer your 
input files to a new namespace. 

From your active session on the duke login node the namespace is located in: /collab/users and /collab/project/lsst
Users can create their own private directories in users or shared directories in lsst. New accounts will create the user
directories automatically and provide read,write permissions in the project/lsst folder

To transfer files to a remote site via a job enter this stashcp command in your execution script:

stashcp /osgconnect/collab/users/<your_directory>/<your-file> .
 
 To transfer files, such as output, from the remote site where your jobs is running to your space on stash, enter 
 this command in your execution script
 
 stashc <file> stash:///osgconnect/collab/users/<your_directory>/.
