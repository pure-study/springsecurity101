# springsecurity101-cloud-oauth2-client

Edit `/etc/hosts` to add this entry before container testing of this project. It relates to the configurations in
[application.yml](src/main/resources/application.yml).
```shell
127.0.0.1   oauth2-server
```

Container testing commands:
```shell
mvn clean package
nerdctl build -t springsecurity101/client:1.0.0 .
```