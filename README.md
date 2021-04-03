# mishipay_test

Describe how did you test it and provide output?
Deployed a Node JS Application on Port 5000 accessible from Chrome UI.
Nginx was configured as reverse proxy with SSL making the Node JS Application accessible on HTTP Port 80 instead of its original Port 5000.


Weakness:
Scalability is not covered in this Dockerfile
Currently both HTTP & HTTPS are supported. In Production, HTTP Requests should be re-directed to HTTPS.
Self-signed Certificated needs to be replaced by Certified Authority for better security.
