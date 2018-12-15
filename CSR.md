# CSR

Hello readers,

In this week one of our clients requested us a CSR file, I was having a basic idea of what it is and what it is used for. 
We generate CSR file to get the SSL certificates for our website or server. Today's blog is about What is CSR? How it is generated? What this file contains in it? etc..


### What is CSR ? 

A Certificate Signing Request is a file that contains information a Certificate Authority (or CA, the companies who issue SSL certificates) need to create your SSL certificate. The purpose of the CSR is to have a standardized method for providing this information to CAs. A CSR is quite literally a request to have a certificate created and digitally signed by a CA. 

When generating your CSR you will be asked for input. Below are some common fields with descriptions and examples.

`Common Name (CN)`: The fully qualified domain name (FQDN) of your server.
Example test.openspecimen.org

`Organization (O)`: The legal name of your organization. Do not abbreviate and include any suffixes, such as Inc., Corp., or LLC. For EV and OV SSL Certificates, this information is verified by the CA and included in the certificate.
Example: Krishagni solutions.

`Organizational Unit (OU)`: The division of your organization handling the certificate.
Example: IT

`City/Locality (L)`: The city where your organization is located. This shouldn’t be abbreviated.
Example: Pune

`State/County/Region (S)`: The state/region where your organization is located. This shouldn't be abbreviated.
Example: Maharashtra

`Country (C)` : The two-letter code for the country where your organization is located.
Example: IN, US

`Email Address`: An email address used to contact your organization.
Example: john@gmail.com

### What does it contains?

There are three important parts to a CSR: 
+ Your public key. 

+ The fully-qualified domain name(s) you want your certificate to be used with. 

+ Other information about you and your organization/website (including the legally registered name and the city/state/country where its registered). 

Let’s break those parts down. The public key is an encryption key – one-half of the “key pair” that is used with SSL certificates. This is used to encrypt the data sent to your server. When you create a CSR you also create this key pair at the same time. The public key is included in the CSR and the SSL certificate you receive, allowing users connecting to your site to transfer data securely. 
The other half of the key pair is the private key. Note that while this is also created at the same time as the CSR, it is not a part of the CSR. The private key is a separate file (usually in the .key format). The private key is used to decrypt the data that the public key encrypted. As the name suggests, you keep this key to yourself and do not send it to your CA or anyone else. You will need the private key later in the process when you install your SSL certificate. 

The fully-qualified domain name(s), or FQDNs, are the hostname(s) where you will use your certificate. The FQDN should consist of the subdomain and parent domain, such as “www.example.com” or “mail.example.co.uk.” Do not include the scheme (“http://”). Some SSL certificates allow you to secure multiple FQDNs with one certificate – usually marketed as “SAN certificates” or “multi-domain certificates.” 

The final piece of the CSR is “subscriber information” – an email address, legally registered business name, and location. This information may be included in your certificate if you purchased an “OV” or “EV” certificate, which validates your website is operated by a registered company/organization. However, not all certificates include this information and if it does not apply to you, you can leave it blank. Many providers also allow you to update this information later if it is incorrect.


### How does CSR file look ? 

```
-----BEGIN NEW CERTIFICATE REQUEST-----MIIDVDCCAr0CAQAweTEeMBwGA1UEAxMVd3d3Lmpvc2VwaGNoYXBtYW4uY29tMQ8w 
DQYDVQQLEwZEZXNpZ24xFjAUBgNVBAoTDUpvc2VwaENoYXBtYW4xEjAQBgNVBAcT 
CU1haWRzdG9uZTENMAsGA1UECBMES2VudDELMAkGA1UEBhMCR0IwgZ8wDQYJKoZI 
hvcNAQEBBQADgY0AMIGJAoGBAOEFDpnOKRabQhDa5asDxYPnG0c/neW18e8apjOk 
1yuGRk+3GD7YQvuhBVS1x6wkw1D2RnmnZgN1nNUK0cRK7sIvOyCh1+jgD7u46mLk 
81j+b4YSEmYZGPLIuclyocPDm0hXayjCUqWt7z6LMIKpLym8gayEZzz9Gn97PsbP 
kVFBAgMBAAGgggGZMBoGCisGAQQBgjcNAgMxDBYKNS4xLjI2MDAuMjB7BgorBgEE 
AYI3AgEOMW0wazAOBgNVHQ8BAf8EBAMCBPAwRAYJKoZIhvcNAQkPBDcwNTAOBggq 
hkiG9w0DAgICAIAwDgYIKoZIhvcNAwQCAgCAMAcGBSsOAwIHMAoGCCqGSIb3DQMH 
MBMGA1UdJQQMMAoGCCsGAQUFBwMBMIH9BgorBgEEAYI3DQICMYHuMIHrAgEBHloA 
TQBpAGMAcgBvAHMAbwBmAHQAIABSAFMAQQAgAFMAQwBoAGEAbgBuAGUAbAAgAEMA 
cgB5AHAAdABvAGcAcgBhAHAAaABpAGMAIABQAHIAbwB2AGkAZABlAHIDgYkAk0kf 
HSkr4jsEVya3mgUoyaYMO456ECNZr4Cb+WhPgexfjOO5qwOG1oDOTaKycrkc5pG+ 
IPBQnq+4cotT8hWJQwpc+qGb8xUETpxCokhrhN5079vFXq/5dsHkmtOTwkSqSnz9 
yruVoxYeDQ8jI3KG3HTgxwFto8oZnm+E+Y4oshUAAAAAAAAAADANBgkqhkiG9w0B 
AQUFAAOBgQAuAxetLzgfjBdWpjpixeVYZXuPZ+6jvZNL/9hOw7Fk5pVVXWdr8csJ 
6JUW8QdH9KB6ZlM4yg8Df+vat1/DG6GuD2hiIR7fQ0NtPFBQmbrSm+TTBo95lwP+ ZSZTusPFTLKaqValdnS9Uw+6Vq7/I4ouDA8QBIuaTFtPOp+8wEGBHQ==
-----END NEW CERTIFICATE REQUEST-----
```

### How to generate CSR file ?

`openssl req -out <domain_name>.csr -new -newkey rsa:2048 -nodes -keyout <domain_name>.key`

Fill all the information as mentioned in the above blog. as an output of the above command, you will see 2 files generated in
current directory.


### Why do people generate it on the same host as the usage?

When generarting a CSR file, another key file is generated which is key file. This file is not shared with anyone not even with CA. while issuing SSL certificate we just need to provide only CSR file to CA. Private key and resulting public key are a matching pair. We can generate the CSR on which ever machine we want only thing is Private key and public key (CSR) has to be matching pair.


I hope now you have got a better idea about the CSR files.

#### Happy learning :)
