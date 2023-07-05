Инструкции

#1) Установка докера и миникуба

/#!/bin/bash

set -ex

apt-get -y update

## docker install
apt-get install ca-certificates curl gnupg

install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | gpg --dearmor -o /etc/apt/keyrings/docker.gpg
 chmod a+r /etc/apt/keyrings/docker.gpg

echo \
  "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
  tee /etc/apt/sources.list.d/docker.list > /dev/null

apt-get update

apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

## install minikube
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
install minikube-linux-amd64 /usr/local/bin/minikube

minikube start

##config kubectl on minikube
minikube kubectl -- get po -A

alias kubectl="minikube kubectl --"

#2) Установка Tekton

kubectl apply --filename https://storage.googleapis.com/tekton-releases/pipeline/latest/release.yaml
 
##tkn install
curl -LO https://github.com/tektoncd/cli/releases/download/v0.31.1/tektoncd-cli-0.31.1_Linux-64bit.deb
sudo dpkg -i ./tektoncd-cli-0.31.1_Linux-64bit.deb

#3)Python FastApi