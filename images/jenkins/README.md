# Jenkins Image

This Jenkins build comes with pre-installed plugins, as [officially recommended](https://github.com/jenkinsci/jenkins/blob/master/core/src/main/resources/jenkins/install/platform-plugins.json). In addition, plugins such as NodeJS are installed.

## Build

```
docker build -t jenkins-example .
```

## Run

```
docker run --rm -d \
    --privileged \
    -e JENKINS_URL=http://localhost:8080 \
    -e JENKINS_USER=admin \
    -e JENKINS_PASSWORD=admin \
    -v jenkins-data:/var/jenkins_home \
    -p 8080:8080 -p 50000:50000 \
    jenkins-example
```

Login at `http://localhost:8080` with your defined credentials.
