# mishipay_test

Describe how did you test it and provide output?
Deployed a Node JS Application on Port 5000 accessible from Chrome UI.
Nginx was configured as reverse proxy with SSL making the Node JS Application accessible on HTTP Port 80 instead of its original Port 5000.
This way IP of Node JS Servers are not revealed.

Docker Command to Run Nodes JS Container:
docker run -d  --rm -p 5000:5000 --name nodejsserver  nodejs:latest

Docker Command to Run Nginx Container:
docker run -d --rm -p 80:80 -p 443:443 --link nodejsserver --name nginx-proxy nginx:latest

Weakness:
Scalability is not covered in this Dockerfile
Currently both HTTP & HTTPS are supported. In Production, HTTP Requests should be re-directed to HTTPS.
Self-signed Certificated needs to be replaced by Certified Authority for better security.
