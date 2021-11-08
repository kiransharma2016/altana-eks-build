# altana-eks-build
Contains a bundle that has tf code for building  eks cluster, deploying nginx, services and ingress 

####

Prerequisites


1. Upgrade the AWS CLI on your sysem to CLI v.2x if older versin is installed 
2. Configure the AWS CLI using the credentials of the user you just created.
3. Install eksctl on your system
4. Install kubectl on your system


Note: I am assuming you have terraform insalled in the sytem where you are testing this. If not, also intall Terraformm .13.1 or higher. 


Down load the zip file from git "git clone https://github.com/kiransharma2016/altana-eks-build.git"
go inside the directory altana-eks-build
unzip eks-build.zip
got to eks-cluster-build directory. 

if terraform is in path, you can simply run like this


terraform init
terraform apply 


After build
===========
Check in the directory where you run the tf code, a file called "kubeconfig_altana-eks-WXg442Sv" is created. The portion after kubeconfig- is the name of the cluster . For example in this case, altana-eks-WXg442Sv is the cluster name.

First, please check the cluster status 

aws eks  --profile kiran --region us-east-1 update-kubeconfig --name altana-eks-WXg442Sv

D:\eks\assignment\ekstest>aws eks describe-cluster --region us-east-1 --name altana-eks-WXg442Sv --query "cluster.status"
"ACTIVE"

This means the cluster is deployed successfully and is running. 

I have provided a script to update the kubeconfig for local user. The script is called setup-kubectl.bat
Updat the cluster name and run it. I will look like this:

D:\eks\assignment\ekstest>aws eks  --profile kiran --region us-east-1 update-kubeconfig --name altana-eks-WXg442Sv
Added new context arn:aws:eks:us-east-1:458233755827:cluster/altana-eks-WXg442Sv to C:\Users\kiran\.kube\config


After kubeconfig is updated, you can run these commands to check the pods, nodes, services, ingress etc
