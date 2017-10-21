# Build a k8s cluster in ACS with a windows pool and linux pool

* Deloy cluster via ARM deployment
    * az group deployment create -g rg-acs-winpluslinux --template-file deployment.json --parameters azuredeploy.params.kubernetes.json
* Label nodes based on OS
    * kubectl label nodes <node-name> <label-key>=<label-value>
* Create namespace for test app
    * kubectl create ns winapp
* Helps to change default context to the namespace just created
    * kubectl config set-context $(kubectl config current-context) --namespace=winapp
* Create Default HTTP backend and NGINX Ingress Controller
    * Use the examples provided in chapter 5 from Eddie and Brian's hackfest.  Be sure to add nodeSelector that specifices OS: linux
* Create a deployment (again steal from hackfest ch5 and hack away) that includes Linux and Windows based PODS and services for each
    * Use the examples provided in chapter 5 from Eddie and Brian's hackfest.  Be sure to add nodeSelectors as appropriate 
    microsoft/iis:nanoserver is a good hello world for the windows pod
* Create ingress rules 
    * Rob Eddie and Brian once again, just make sure you replace www.<ALB_EXT_IP_ADDRESS>.xip.io with your ALB external IP

