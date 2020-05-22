# Hello World Rest API running on port 80

Run rest.webservices.restfulwebservices.RestfulWebServicesApplication as a Java Application.

- http://localhost/hello-world

```txt
Hello World
```

- http://localhost/hello-world-bean

```json
{"message":"Hello World - Changed"}
```

- http://localhost/hello-world/path-variable/clientId

```json
{"message":"Hello World, clientId"}
```

# Create Docker based Nexus repository
- docker volume create --name nexus-data
- docker run -d -p 8081:8081 --name nexus -v nexus-data:/nexus-data sonatype/nexus3
- URL : http://{Server_IP}/8081
- UserName : admin
- Password : admin

# Create Docker Based Sonarqube
- docker run -d --name sonarqube -p 9000:9000 -p 9092:9092 sonarqube
- URL : http://{Server_IP}/9000
- UserName : admin
- Password : admin

# Sonar quality gate integrate with jenkins pipeline
To create the webhook form the SonarQube interface to, to do so you can perform the following steps
1. Login to SonarQube with admin user
2. Navigate to the webhooks page : Administration->Configurations->webhooks
3. Create a new webhook: Click on create new webhook and then fill the below form and hit create button. The webhook URL should follow this form https://${jenkins_domain}/sonarqube-webhook/. The / at the end of the user is very important and without it, you may experience some errors triggering the webhooks.

# Create docker based mail server to send email notification from jenkins.
- docker run -d -p 1025:1025 -p 8085:8025 mailhog/mailhog
- URL : http://{Server_IP}/8085
- SMTP Port : 1025
- Ref : https://hub.docker.com/r/mailhog/mailhog/
