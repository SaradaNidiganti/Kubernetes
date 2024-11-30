# Kubernetes

Services:
--Cluster Ip : only used for internal port communication and highly secured.
--Node Port : only we can use this in testing purpose, external communication & it's not safe , it'll expose direct node IP to public. port  number always shows 30000+. we've provide firewall rules to access node port, then we can access the application publicly, to expose node port in public it's a breach in networking. it's less secure
--Load Balancer : In prod we use this LB. external commmunication but it's expensive.

Ingress Controller: supports Load balancer layer 7, Application gate way , http/https.
--path based
--Hostname based
--we've to install the ingress controller from "https://github.com/kubernetes/ingress-nginx"-->"https://github.com/kubernetes/ingress-nginx/blob/main/deploy/static/provider/cloud/deploy.yaml" copy this yaml file and deploy these resources.
--
Cert Manager: kubectl apply -f https://github.com/cert-manager/cert-manager/releases/download/v1.16.2/cert-manager.yaml

The ACME URL for our ACME v2 staging environment is:

https://acme-staging-v02.api.letsencrypt.org/directory

ConfigMaps: 
Secrets:
Volumes & Env-variables

NameSpaces: are used to do logical partisioning of a cluster mainly by using 1.Access control,2.Resource utilization control,3. Network communication control,
--In Kubernetes, namespaces provide a mechanism for isolating groups of resources within a single cluster. Names of resources need to be unique within a namespace, but not across namespaces. Namespace-based scoping is applicable only for namespaced objects (e.g. Deployments, Services, etc.) and not for cluster-wide objects (e.g. StorageClass, Nodes, PersistentVolumes, etc.)
--Namespaces are intended for use in environments with many users spread across multiple teams, or projects
--For a production cluster, consider not using the default namespace. Instead, make other namespaces and use those.
--Avoid creating namespaces with the prefix kube-, since it is reserved for Kubernetes system namespaces.
--Namespaces & DNS: When you create a Service, it creates a corresponding DNS entry. This entry is of the form <service-name>.<namespace-name>.svc.cluster.local, which means that if a container only uses <service-name>, it will resolve to the service which is local to a namespace. This is useful for using the same configuration across multiple namespaces such as Development, Staging and Production. If you want to reach across namespaces, you need to use the fully qualified domain name (FQDN).
--1. AccessControl: role, rolebinding, clusterRole, clusterRolebinding
--role authentication(gcp/azure/aws/AD), role authorization (role & role binding)
  --1.created a name space eg: dev-ns-team
  --2.created and then applied a role and rolebinding manifest files
  --3. apply IAM rules to new user/groups
--2. Resource utilization control: resource quota and resource limit control
    --ResourceQuota:


