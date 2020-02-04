https://gitlab.com/gitlab-org/gitlab/issues/12300  
http://10.0.0.130/help/user/project/clusters/add_remove_clusters.md#add-existing-cluster  
http://10.0.0.130/help/user/project/clusters/index#pointing-your-dns-at-the-external-endpoint  
https://rancher.com/blog/2019/connecting-gitlab-autodevops-authorized-cluster-endpoints/


## Configure gitlab runner k8s
https://docs.gitlab.com/runner/install/kubernetes.html

1. set `values.yaml`
```
## The GitLab Server URL (with protocol) that want to register the runner against
## ref: https://docs.gitlab.com/runner/commands/README.html#gitlab-runner-register
##
gitlabUrl: http://10.0.0.130/

## The registration token for adding new Runners to the GitLab server. This must
## be retrieved from your GitLab instance.
## ref: https://docs.gitlab.com/ee/ci/runners/
##
runnerRegistrationToken: "dk7AjXm33SCUVm4D7giY"

## Set the certsSecretName in order to pass custom certificates for GitLab Runner to use
## Provide resource name for a Kubernetes Secret Object in the same namespace,
## this is used to populate the /etc/gitlab-runner/certs directory
## ref: https://docs.gitlab.com/runner/configuration/tls-self-signed.html#supported-options-for-self-signed-certificates
##
certsSecretName: gitlab-domain-cert

## Configure the maximum number of concurrent jobs
## ref: https://docs.gitlab.com/runner/configuration/advanced-configuration.html#the-global-section
##
concurrent: 10

## Defines in seconds how often to check GitLab for a new builds
## ref: https://docs.gitlab.com/runner/configuration/advanced-configuration.html#the-global-section
##
checkInterval: 30

## For RBAC support:
rbac:
  create: false

  ## Run the gitlab-bastion container with the ability to deploy/manage containers of jobs
  ## cluster-wide or only within namespace
  clusterWideAccess: false

  ## If RBAC is disabled in this Helm chart, use the following Kubernetes Service Account name.
  ##
  # serviceAccountName: default

## Configuration for the Pods that the runner launches for each new job
##
runners:
  ## Default container image to use for builds when none is specified
  ##
  image: ubuntu:18.04

  ## Run all containers with the privileged flag enabled
  ## This will allow the docker:stable-dind image to run if you need to run Docker
  ## commands. Please read the docs before turning this on:
  ## ref: https://docs.gitlab.com/runner/executors/kubernetes.html#using-docker-dind
  ##
  privileged: true

  ## Namespace to run Kubernetes jobs in (defaults to 'default')
  ##
  namespace: gitlab-runner

  ## Build Container specific configuration
  ##
  builds:
    # cpuLimit: 200m
    # memoryLimit: 256Mi
    cpuRequests: 100m
    memoryRequests: 128Mi

  ## Service Container specific configuration
  ##
  services:
    # cpuLimit: 200m
    # memoryLimit: 256Mi
    cpuRequests: 100m
    memoryRequests: 128Mi

  ## Helper Container specific configuration
  ##
  helpers:
    # cpuLimit: 200m
    # memoryLimit: 256Mi
    cpuRequests: 100m
    memoryRequests: 128Mi
```
1. create namespace
1. install helm
```
$ helm install --namespace gitlab-runner gitlab-runner -f values.yaml gitlab/gitlab-runner
NAME: gitlab-runner
LAST DEPLOYED: Tue Feb  4 08:30:19 2020
NAMESPACE: gitlab-runner
STATUS: deployed
```
1. 
