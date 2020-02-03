## Links
https://docs.gitlab.com/ee/ci/docker/using_docker_build.html

## Prerequisite
Install docker on gitlab server

## Procedure
1. Confirm gitlab runnner parameter via gitlab-UI -> Admin Area -> Runners, `Set up a shared Runner manually`
1. make command as below
```
sudo gitlab-runner register -n \
  --url <Runner-URL> \
  --registration-token <Runner-TOKEN> \
  --executor shell \
  --description "My Runner"
```
1. execute above command
```
$ sudo gitlab-runner register -n \
>   --url http://10.0.0.130/ \
>   --registration-token dk7AjXm33SCUVm4D7giY \
>   --executor shell \
>   --description "my decker runner"
Runtime platform                                    arch=amd64 os=linux pid=26839 revision=003fe500 version=12.7.1
Running in system-mode.

Registering runner... succeeded                     runner=dk7AjXm3
Runner registered successfully. Feel free to start it, but if it's running already the config should be automatically reloaded!
```
1. add user to docker group / confirm
```
sudo usermod -aG docker gitlab-runner
sudo -u gitlab-runner -H docker info
```


