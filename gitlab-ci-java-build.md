## Install for GitLab runner shell for gitlab server
- docker
  - install docker-ce
  - configure docker proxy/insecure registry
  - useradd -aG docker gilab-runner
- install java
  - yum install java-11-openjdk
- install oc
- install kubectl
- move kubeconfig

## add gradle proxy setting
https://docs.gradle.org/current/userguide/build_environment.html#sec:accessing_the_web_via_a_proxy
