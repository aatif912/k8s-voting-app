Setup your local env first. Reference - https://github.com/aatif912/setting-up-k8s-env/blob/main/README.md

Create a cluster in Azure using portal:
![image](https://user-images.githubusercontent.com/13832737/219465379-4a9d4127-e496-4950-8ffe-8c1eb8f5d08b.png)

`az login`

`az account set -s <subid>`

`az account show`

`az aks get-credentials --name voting-app-cluster --resource-group voting-app`

![image](https://user-images.githubusercontent.com/13832737/219471488-85c4e0f6-3dce-4c9c-8058-30bde181eb8f.png)

Additional step : We still are not able to connect to cluster 

![image](https://user-images.githubusercontent.com/13832737/219496832-2c80fae3-e377-4577-ac41-4b793c538f7f.png)

Some issue with the context, so we do a workaround for it, create an env var 'KUBECONFIG' and point it to the config file which in my case is present at 
`/mnt/c/users/AatifAkhter/.kube/config` and in windows system `C:\Users\AatifAkhter\.kube\config`

`export KUBECONFIG="/mnt/c/users/AatifAkhter/.kube/config"`

Now it works-

![image](https://user-images.githubusercontent.com/13832737/219497411-7f14a74a-1c84-436b-a4a4-1f83293c4935.png)

Time to deploy

`k create -f voting-app-deploy.yaml`

`k create -f voting-app-service.yml`

`k create -f redis-deploy.yaml`

`k create -f redis-service.yaml`

`k create -f postgres-deploy.yaml`

`k create -f postgres-service.yaml`

`k create -f worker-app-deploy.yaml`

`k create -f result-app-deploy.yaml`

`k create -f result-app-service.yaml`

After all components are deployed chack status of all resources one using- 

`k get all`

![image](https://user-images.githubusercontent.com/13832737/219510878-66221152-4c43-4e95-a459-77ef2874ca03.png)

Notice the external IP of sevices `voting-service` and `result-service` 

![image](https://user-images.githubusercontent.com/13832737/219511026-b67ee1b3-51ac-43a2-bf62-34e2fa6e51b3.png)


Browse on these external IPs and you get the content

![image](https://user-images.githubusercontent.com/13832737/219511118-250cca4c-79d5-4699-822a-1a836c4c70d3.png)

![image](https://user-images.githubusercontent.com/13832737/219511162-a74a713c-6d11-4a5d-af8d-069f35718aae.png)



