# Advisor

This Controller was based/forked from KARMAB (https://github.com/karmab/samplecontroller) and was modified to be used at QCON SP 2018 :)

All the credits goes here to the creator, and I've just modified this for my needs :)

# samplecontroller repository

[![](https://images.microbadger.com/badges/image/karmab/samplecontroller.svg)](https://microbadger.com/images/karmab/samplecontroller "Get your own image badge on microbadger.com")

This is a simple controller to demonstrate how to interact within kubernetes using python api and custom resource definitions

## Requisites

- a running kubernetes/openshift cluster
- a Namespace called `guitarcenter` (as I'm lazy and this is hardcoded :P )

## Running


```
kubectl create ns guitarcenter
kubectl create -f https://raw.githubusercontent.com/rikatz/samplecontroller/master/guitar.yml
kubectl create -f https://raw.githubusercontent.com/rikatz/samplecontroller/master/role.yaml
kubectl run crdcontroller --image=rpkatz/crdcontroller:v0.8 --restart=Always -n guitarcenter
kubectl run crdui --image=rpkatz/crdui:v0.6 --env=KUBERNETES_SERVICE_HOST=kubernetes.default -n guitarcenter
kubectl expose deployment crdui --port=9000 --target-port=9000 --type=NodePort -n guitarcenter
```

## UI

To ease testing, you can also use the provided UI to list, create and delete guitars. Access the UI through the created NodePort (`kubectl get svc -n guitarcenter crdui`)

## BONUS

You can also have a look at [initializer](initializer) for extra code around Initializers

## Copyright

Copyright 2017 Karim Boumedhel

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

