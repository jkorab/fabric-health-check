A script to fix common corrupted ZooKeeper registry problems in FuseESB 7.1. This is really handy if for some reason you cannot upgrade to 7.2 (JBoss Fuse 6), in which most of these issues have been addressed.

# Instructions
This script requires that it is executed in a Fabric and that `zk:` commands are available.

To add the the commands to all servers (brute method), run the following command:

    > fabric:profile-edit --features fabric-zookeeper-commands/0.0.0 default

To run the script, save it in the `$ESB_HOME` directory, connect to the ESB console and run the following command:

    > source fabricHealthCheck.script
    
# Fabric ZK Issues Fixed
1. Fabric containers not assigned to versions. Can occasionally happen when creating and deleting nodes from the Fabric. Fix is to delete the server entry from the registry.
2. Versions that have been imported do not have a containers node and so mess up any containers that are upgraded to them - create one.
3. When a child container is created in a Fabric after a version has been created, an upgrade of the child to the version corrupts the `fabric:` commands.
