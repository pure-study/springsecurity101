# springsecurity101-cloud-oauth2-server

***Note***: If this project is running in a container, the DB port in [application.yml](src/main/resources/application.yml)
needs to be aligned with what's exposed by the DB container itself. If this is running in IDE or out of container, the 
port needs to be the mapped port of your local computer.

*Side Note*: See when this [issue](https://github.com/containerd/nerdctl/issues/2386) of "nerdctl" would be solved.

```shell
mvn clean package
nerdctl build -t springsecurity101/oauth2-server:1.0.0 .
# docker build -t springsecurity101/oauth2-server:1.0.0 .
```