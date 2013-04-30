A script to fix common corrupted ZooKeeper registry problems in FuseESB 7.1.

# Instructions
This script requires that it is executed in a Fabric and that `zk:` commands are available.

To add the the commands to all servers (brute method), run the following command:

    > fabric:profile-edit --features fabric-zookeeper-commands/0.0.0 default

To run the script, save it in the `$ESB_HOME` directory, connect to the ESB console and run the following command:

    > source fabricHealthCheck.script
    
# Issues Fixed
1. Fabric containers not assigned to versions. Can occasionally happen when creating and deleting nodes from the Fabric. Fix is to delete the server entry from the registry.

