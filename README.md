setup your local env first. Reference - https://github.com/aatif912/setting-up-k8s-env/blob/main/README.md

Create a cluster in Azure using portal:
![image](https://user-images.githubusercontent.com/13832737/219465379-4a9d4127-e496-4950-8ffe-8c1eb8f5d08b.png)

`az login`

`az account set -s <subid>`

`az account show`

`az aks get-credentials --name voting-app-cluster --resource-group voting-app`

![image](https://user-images.githubusercontent.com/13832737/219471488-85c4e0f6-3dce-4c9c-8058-30bde181eb8f.png)
