# Deploy automatically K3s cluster on Openstack using Heat

Heat templates will automatically deploy defined set of master and worker nodes, and join them in a cluster.  
K3s installer script is used during Kubernetes bootstrapping, first master nodes is bootstrapped, and then other masters, and later workers.  


### TODO

Update templates to:
- add more definitions on parameters to custom resource templates
- check option if possible to use dynamic and static IP addresses in deployment
- check if Octavia can be deployed and used as CloudLB for deployed cluster


### Deploy template

Parameters should be customized for each deployment via environment file such as included `env.yaml`.
You can make a copy of env file for each deployed cluster, with different parameters, and deploy multiple clusters using same template, only with different ENV files.

You can split some common(shared) parameters in separate ENV files, as they are also composable.

Deploy cluster with following command:
```
# Source overcloud environment
source <openstack-rc-file>

# Deploy template
openstack stack create <stack_name> -t deployment.yaml -e env.yaml --wait
```


### Authors

- Karlo Tisaj