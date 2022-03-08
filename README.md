# VOLTHA development scripts

This repository contains some scripts that I wrote to perform some repetitive tasks related to VOLTHA development. These may not work with your environment, they have been made quickly and without any testing.
The scripts assume that all repos can be found in the `$HOME/git` directory.

If you want to use these, you should add this folder to the `PATH` variable.

## Documentation
Apart from particular scripts, you can expect:
* `start_<something>` to run that with an helm chart
* `start_dev_<something>` to locally build a docker image of that and run its helm chart with the image
* `stop_<something>` to delete the helm chart

### Everything else

```
build_bbsim (tag)
    executes docker-build for bbsim and loads the image on kind nodes

clean_log (path)
    removes errors due to the jaeger host not being found, and strips bash color codes that are not displayed properly in IDEs from ONOS logs

cli_onos
    opens ONOS CLI by executing it in the container

disable_delete_olt
    disables and deletes the OLT with voltctl

enable_olt
    provisions and enables a BBSIM OLT

exec_bbsim
    opens bash in the container of bbsim to let you use bbsimctl

extract_clean_log (path)
    takes a .tar.gz log file from robot tests, extracts it in place and cleans it with clean_log 

git-graph
    can be executed with 'git graph' too, prints a visual representation of the commit history for the current branch

kind_rebuild
    restarts a kind cluster and starts infra, which takes a lot of time to set up. Assumes you have a $HOME/kind-cfg/3-node-cfg.yaml file

kubernetes_status
    runs watch kubectl get pods -A

log_bbsim
    follows bbsim logs

logflows (output_file)
    appends a snapshot of the flows of a logical device, olt and onu from voltctl to the output file

metadata_decoder (metadata_hex)
    binary file built in go that extracts the information in an ONOS flow metadata, as used by VOLTHA

port_forward
    runs port forwarding for ONOS cli, ONOS gui, and voltctl. Use stop_port_forward to kill everything

start_bbsim
    installs the master on the cluster

start_dev_bbf (tag)
    executes docker-build with the provided tag, loads the image on the kind nodes, and installs this local version on the cluster

start_dev_bbsim (tag)
    executes docker-build with the provided tag, loads the image on the kind nodes, and installs this local version on the cluster

start_dev_bbsimsadisserver (tag)
    executes docker-build with the provided tag, loads the image on the kind nodes, and installs this local version on the cluster

start_dev_openolt (tag)
    executes docker-build for openolt-adapter with the provided tag, loads the image on the kind nodes, and installs the voltha stack with this local version on the cluster

start_dev_voltha (tag)
    executes docker-build for voltha-go with the provided tag, loads the image on the kind nodes, and installs the voltha stack with this local version on the cluster

start_dev_volthaplusopenolt (tag)
    executes docker-build for openolt-adapter and voltha-go with the provided tag, loads the image on the kind nodes, and installs the voltha stack with this local version on the cluster

start_infra
    installs the master on the cluster

start_voltha
    installs the master on the cluster

stop_all
    delete infra, voltha and bbsim from the cluster

stop_bbf
    delete bbf-adapter from the cluster

stop_bbsim
    delete bbsim from the cluster

stop_infra
    delete infra from the cluster

stop_port_forward
    stop all port forwarding

stop_voltha
    delete voltha from the cluster

test_local (target)
    locally run a test target from voltha-system-tests with some additional parameters. Logs will go to $HOME/logs/robot

uncolor
    if the output of a program is piped through this script, it will strip bash color codes from it
```
