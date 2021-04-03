# mishipay_test

Part 1:

Created a Docker image:
○ Use ubuntu as the base image
○ Install nginx web server
○ Deploy any web application you want
○ Add https support

Describe how did you test it and provide output?
Deployed a Node JS Application on Port 5000 accessible from Chrome UI.
Nginx was configured as reverse proxy with SSL making the Node JS Application accessible on HTTP Port 80 instead of its original Port 5000.
This way IP of Node JS Servers are not revealed.

Docker Command to Run Nodes JS Container:
docker run -d  --rm -p 5000:5000 --name nodejsserver  nodejs:latest

Docker Command to Run Nginx Container:
docker run -d --rm -p 80:80 -p 443:443 --link nodejsserver --name nginx-proxy nginx:latest

Weakness in Dockerfile:
Scalability is not covered in this Dockerfile
Currently both HTTP & HTTPS are supported. In Production, HTTP Requests should be re-directed to HTTPS.
Self-signed Certificated needs to be replaced by Certified Authority for better security.


Part 2:

A pipeline which will run unit tests upon git push to a certain repository

Tried to configure Pre-Push Hook so that when git Push happens, it checks as per the logic configured in hook.



A pipeline which will do to the following:
○ Provision the container from Part 1
○ Deploy a web application on the provisioned instance

I have created Jenkins Pipeline using the Jenkins UI automating the Part 1 and deploying the web application.
