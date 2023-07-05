Инструкции

##1) Установка докера и миникуба

For installation use 1.sh script, it will install docker minikube

##2) Установка Tekton

kubectl apply --filename https://storage.googleapis.com/tekton-releases/pipeline/latest/release.yaml
 
#tkn install
curl -LO https://github.com/tektoncd/cli/releases/download/v0.31.1/tektoncd-cli-0.31.1_Linux-64bit.deb
sudo dpkg -i ./tektoncd-cli-0.31.1_Linux-64bit.deb

tkn hub install task git-clone

tkn pipelinerun logs run-fast-api -f

#3)Python FastApi

