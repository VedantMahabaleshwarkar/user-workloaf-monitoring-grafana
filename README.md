# user-workloaf-monitoring-grafana


## Install the operator

Install the community Grafana Operator by navigating to your Openshift Console -> Operators -> OperatorHub -> Search and install the Grafana Operator 


## Create a Grafana Instance 

`oc project opendatahub`
`oc apply -f grafana-config.yaml`

Edit the grafana.yaml to select your login meathod for the grafana UI 
`oc apply -f grafana.yaml`
`oc adm policy add-cluster-role-to-user cluster-monitoring-view -z grafana-serviceaccount` 

Get the authorization token to be able to connect to the User Workload Monitoring Stack by running : 

`TOKEN=$(oc sa get-token grafana-serviceaccount -n opendatahub)`

Enter the TOKEN value in place of the ${BEARER TOKEN} in the grafana-datasource-uwm.yaml file 

`oc apply -f grafana-datasource-uwm.yaml` 
