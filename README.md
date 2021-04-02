# mishipay_test

Describe how did you test it and provide output?
Tried to Access the Nginx UI with https protocol on Chrome which displayed Sample Web Application.
Link: https://35.208.214.184/

Weakness:
Scalability is not covered in this Dockerfile
Currently both HTTP & HTTPS are supported. In Production, HTTP Requests should be re-directed to HTTPS.
Self-signed Certificated needs to be replaced by Certificate Authority for better security.
