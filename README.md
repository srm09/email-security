# CNS - Email security

## Part 1 - Break password by brute force method
The code to break the password is in `break.py` file. Before running the Python script, run
```
pip install -r requirements.txt
python break.py
```
The above script generates a .txt file which has the decoded message and the key used for decoding is appended to the name of the file.
For instance, if `key` is the password, then the file having the decoded secret message is `file_key.txt`

## Part 2 - Generation of key pair and CSR
```
# To generate the 1024-bit RSA key pair
openssl genrsa -out key.pem 1024

# To generate the output of key in text format
openssl rsa -in key.pem -text -noout > out.txt

# To generate a Certificate Signing Request (CSR)
openssl req -new -sha256 -key key.pem -out custom.csr

# To generate the output of CSR in text format
openssl req -noout -text -in custom.csr > opt_csr.txt

# To password protect the pem file
openssl rsa -in key.pem -des3 -out enc-key.pem
```

## Part 3 - Sending and receiving encrypted emails
