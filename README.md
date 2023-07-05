Инструкции

##1) Установка докера и миникуба

For installation use 1.sh script, it will install docker minikube

##2) Установка Tekton

kubectl apply --filename https://storage.googleapis.com/tekton-releases/pipeline/latest/release.yaml
 
#tkn install
curl -LO https://github.com/tektoncd/cli/releases/download/v0.31.1/tektoncd-cli-0.31.1_Linux-64bit.deb
sudo dpkg -i ./tektoncd-cli-0.31.1_Linux-64bit.deb

#3) Preparation before run run-pipeline.yaml

#create account with root access
kubectl apply -f kuber/rbac/service-account.yaml
kubectl apply -f kuber/rbac/cluster-role.yaml
kubectl apply -f kuber/rbac/cluster-role-binding.yaml
#create tasks and pipeline
tkn hub install task git-clone
kubectl apply -f ci/tasks/check-files.yaml
kubectl apply -f ci/tasks/create-image.yaml
kubectl apply -f ci/tasks/deploy-image.yaml
kubectl apply -f ci/pipeline.yaml



#check result of work 
tkn pipelinerun logs run-fast-api -f

