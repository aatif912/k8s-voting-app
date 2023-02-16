setup your local env first. Reference - https://github.com/aatif912/setting-up-k8s-env/blob/main/README.md

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
