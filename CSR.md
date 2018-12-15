1. What is CSR?
2. What all it contains?
3. Why is it needed?
4. How is it used?
5. Why do people generate it on the same host as the usage?

Explore all this and write a blog in it




# CSR

What's in a CSR?
The CSR contains all the necessary information needed by the CA to authenticate your organization such as your domain name, business name and location.

When generating your CSR you will be asked for input. Below are some common fields with descriptions and examples.

1 . Information about the Company : 
Common Name (CN) : The fully qualified domain name (FQDN) of your server.
example test.openspecimen.org

Organization (O) : The legal name of your organization. Do not abbreviate and include any suffixes, such as Inc., Corp., or LLC. For EV and OV SSL Certificates, this information is verified by the CA and included in the certificate.
Example : Krishagni solutions.

Organizational Unit (OU) : The division of your organization handling the certificate.
Example : IT

City/Locality (L) : The city where your organization is located. This shouldn’t be abbreviated.
Example : Pune

State/County/Region (S) :The state/region where your organization is located. This shouldn't be abbreviated.
Example : Maharashtra

Country (C) : The two-letter code for the country where your organization is located.
Example : IN, US

Email Address : An email address used to contact your organization.
Example : john@gmail.com

2. The public key that will be included in the certificate. SSL uses public-key, or asymmetric, cryptography to encrypt transmitted data during an SSL session. The public key is used to encrypt and the corresponding private key is used to decrypt.


3. Information about the key type and length. The most common key size is RSA 2048, but some CAs support larger key sizes (e.g. RSA 4096+) or ECC keys.









