# attis
Amazon Cloud Training Registration Application &amp; Orchestration App use to create student accounts in AWS.

* Create IAM user
* Add IAM user to Developer user group
* Creates password
* Creates access and secret key
* Emails new user their credentials

## Build
### Package
To create an executable jar.
```
./mvnw package
```
### Test
To run unit tests.
```
./mvnw test
```
### Run
```
java -Dspring.mail.username=<mail username> -Dspring.mail.password=<mail passowrd> -Dmessage.send.from=<sent form> -jar target/attis-0.0.1-SNAPSHOT.jar
```
### Docker Image
```
./mvnw spring-boot:build-image
```
### Run Docker Container
```
docker run --rm -it -p80:8080 -e AWS_ACCESS_KEY_ID=<access key> -e AWS_SECRET_ACCESS_KEY=<secret key> -e SPRING_MAIL_USERNAME=<mail user> -e SPRING_MAIL_PASSWORD=<mail password> -e MESSAGE.SEND.FROM=<efrom email>  javajudd/attis
```
### Push Docker Image to hub.docker.com
```
docker push javajudd/attis:<version>
docker tag javajudd/attis:<version> javajudd/attis:latest
docker push javajudd/attis:latest
```

### Example root user
```
export AWS_DEV_AMI=ami-081f2c86d8b025c4b
export AWS_ACCESS_KEY_ID=<access key>
export AWS_SECRET_ACCESS_KEY="<secret key>"
java -Daws.access.key.id=<access key> -Daws.secret.access.key="<secret key>" -Daws.dev.ami=ami-081f2c86d8b025c4b -Dspring.mail.username=<email user> -Dspring.mail.password=<email password> -Dmessage.send.from=aws@juddsolutions.com -Dserver.port=80  -jar attis.jar
```