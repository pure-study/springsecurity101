# springsecurity101

A custom test of [JosephZhu1983/SpringSecurity101](https://github.com/JosephZhu1983/SpringSecurity101)

Some test commands:
```shell
# Generate keys and certs
keytool -genkey -alias jwt -keyalg RSA -keypass changeit -keystore jwt.jks
# Export and transform to public key
keytool -list -rfc -storepass changeit -keystore jwt.jks | openssl x509 -inform pem -pubkey

# DB
mysql -u root -ppassword oauth
select * from oauth_approvals;

# Test requests
curl -X POST --data-urlencode "grant_type=password" \
            --data-urlencode "client_id=userservice1" \
            --data-urlencode "client_secret=1234" \
            --data-urlencode "username=writer" \
            --data-urlencode "password=writer" \
            http://localhost:8080/oauth/token

curl -X POST --data-urlencode "client_id=userservice1" \
            --data-urlencode "client_secret=1234" \
            --data-urlencode "token=eyJh..." \
            http://localhost:8080/oauth/check_token

curl -X POST --data-urlencode "grant_type=client_credentials" \
            --data-urlencode "client_id=userservice2" \
            --data-urlencode "client_secret=1234" \
            http://localhost:8080/oauth/token

# Browser:
http://localhost:8080/oauth/authorize?response_type=code&client_id=userservice3&redirect_uri=https://baidu.com

# Test requests:
curl -X POST --data-urlencode "grant_type=authorization_code" \
            --data-urlencode "client_id=userservice3" \
            --data-urlencode "client_secret=1234" \
            --data-urlencode "code=F5deAn" \
            --data-urlencode "redirect_uri=https://baidu.com" \
            http://localhost:8080/oauth/token

#### user service
curl http://localhost:8081/hello
curl http://localhost:8081/user
curl http://localhost:8081/user -H 'Authorization: Bearer eyJh...'
curl -X POST http://localhost:8081/user -H 'Authorization: Bearer eyJh...'
curl -X GET http://localhost:8081/user/name -H 'Authorization: Bearer eyJh...'

```