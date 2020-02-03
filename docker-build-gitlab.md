## Links
https://docs.gitlab.com/ee/ci/docker/using_docker_build.html

## Procedure
1. Confirm gitlab runnner parameter via gitlab-UI -> Admin Area -> Runners, `
Set up a shared Runner manually`
1. make command
```
sudo gitlab-runner register -n \
  --url https://gitlab.com/ \
  --registration-token REGISTRATION_TOKEN \
  --executor shell \
  --description "My Runner"
```
