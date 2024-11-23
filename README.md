# Kubernetes

Services:
--Cluster Ip : only used for internal port communication and highly secured.
--Node Port : only we can use this in testing purpose, external communication & it's not safe , it'll expose direct node IP to public. port  number always shows 30000+. we've provide firewall rules to access node port, then we can access the application publicly, to expose node port in public it's a breach in networking. it's less secure
--Load Balancer : In prod we use this LB. external commmunication but it's expensive.