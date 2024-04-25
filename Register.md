### fabric-ca-server-tls部署

```shell
root@iZn4aampde1w0vhbnmvrlaZ:~# cd /home/ubuntu/hyperledger/multinodes/fabric-ca-server-tls/
root@iZn4aampde1w0vhbnmvrlaZ:/home/ubuntu/hyperledger/multinodes/fabric-ca-server-tls# ls
ca-cert.pem       fabric-ca-server-config.yaml  IssuerPublicKey            msp
fabric-ca-server  fabric-ca-server.db           IssuerRevocationPublicKey  tls-cert.pem
root@iZn4aampde1w0vhbnmvrlaZ:/home/ubuntu/hyperledger/multinodes/fabric-ca-server-tls# ./fabric-ca-server init -b admin:adminpw
2024/04/24 19:38:27 [INFO] Created default configuration file at /home/ubuntu/hyperledger/multinodes/fabric-ca-server-tls/fabric-ca-server-config.yaml
2024/04/24 19:38:27 [INFO] Server Version: v1.5.7
2024/04/24 19:38:27 [INFO] Server Levels: &{Identity:2 Affiliation:1 Certificate:1 Credential:1 RAInfo:1 Nonce:1}
2024/04/24 19:38:27 [WARNING] &{69 The specified CA certificate file /home/ubuntu/hyperledger/multinodes/fabric-ca-server-tls/ca-cert.pem does not exist}
2024/04/24 19:38:27 [INFO] generating key: &{A:ecdsa S:256}
2024/04/24 19:38:27 [INFO] encoded CSR
2024/04/24 19:38:27 [INFO] signed certificate with serial number 137026232849041126119358008932390708276085905725
2024/04/24 19:38:27 [INFO] The CA key and certificate were generated for CA 
2024/04/24 19:38:27 [INFO] The key was stored by BCCSP provider 'SW'
2024/04/24 19:38:27 [INFO] The certificate is at: /home/ubuntu/hyperledger/multinodes/fabric-ca-server-tls/ca-cert.pem
2024/04/24 19:38:27 [INFO] Initialized sqlite3 database at /home/ubuntu/hyperledger/multinodes/fabric-ca-server-tls/fabric-ca-server.db
2024/04/24 19:38:27 [INFO] The issuer key was successfully stored. The public key is at: /home/ubuntu/hyperledger/multinodes/fabric-ca-server-tls/IssuerPublicKey, secret key is at: /home/ubuntu/hyperledger/multinodes/fabric-ca-server-tls/msp/keystore/IssuerSecretKey
2024/04/24 19:38:28 [INFO] Idemix issuer revocation public and secret keys were generated for CA ''
2024/04/24 19:38:28 [INFO] The revocation key was successfully stored. The public key is at: /home/ubuntu/hyperledger/multinodes/fabric-ca-server-tls/IssuerRevocationPublicKey, private key is at: /home/ubuntu/hyperledger/multinodes/fabric-ca-server-tls/msp/keystore/IssuerRevocationPrivateKey
2024/04/24 19:38:28 [INFO] Home directory for default CA: /home/ubuntu/hyperledger/multinodes/fabric-ca-server-tls
2024/04/24 19:38:28 [INFO] Initialization was successful
root@iZn4aampde1w0vhbnmvrlaZ:/home/ubuntu/hyperledger/multinodes/fabric-ca-server-tls# ls
ca-cert.pem       fabric-ca-server-config.yaml  IssuerPublicKey            msp
fabric-ca-server  fabric-ca-server.db           IssuerRevocationPublicKey
root@iZn4aampde1w0vhbnmvrlaZ:/home/ubuntu/hyperledger/multinodes/fabric-ca-server-tls# rm -r ca-cert.pem 
root@iZn4aampde1w0vhbnmvrlaZ:/home/ubuntu/hyperledger/multinodes/fabric-ca-server-tls# rm -r msp
root@iZn4aampde1w0vhbnmvrlaZ:/home/ubuntu/hyperledger/multinodes/fabric-ca-server-tls# ./fabric-ca-server start
2024/04/24 19:50:44 [INFO] Configuration file location: /home/ubuntu/hyperledger/multinodes/fabric-ca-server-tls/fabric-ca-server-config.yaml
2024/04/24 19:50:44 [INFO] Starting server in home directory: /home/ubuntu/hyperledger/multinodes/fabric-ca-server-tls
2024/04/24 19:50:44 [INFO] Server Version: v1.5.7
2024/04/24 19:50:44 [INFO] Server Levels: &{Identity:2 Affiliation:1 Certificate:1 Credential:1 RAInfo:1 Nonce:1}
2024/04/24 19:50:44 [WARNING] &{69 The specified CA certificate file /home/ubuntu/hyperledger/multinodes/fabric-ca-server-tls/ca-cert.pem does not exist}
2024/04/24 19:50:44 [INFO] generating key: &{A:ecdsa S:256}
2024/04/24 19:50:44 [INFO] encoded CSR
2024/04/24 19:50:44 [INFO] signed certificate with serial number 719624044835369296797467798644121424568069759160
2024/04/24 19:50:44 [INFO] The CA key and certificate were generated for CA tls-ca
2024/04/24 19:50:44 [INFO] The key was stored by BCCSP provider 'SW'
2024/04/24 19:50:44 [INFO] The certificate is at: /home/ubuntu/hyperledger/multinodes/fabric-ca-server-tls/ca-cert.pem
2024/04/24 19:50:44 [INFO] Initialized sqlite3 database at /home/ubuntu/hyperledger/multinodes/fabric-ca-server-tls/fabric-ca-server.db
2024/04/24 19:50:44 [INFO] The issuer key was successfully stored. The public key is at: /home/ubuntu/hyperledger/multinodes/fabric-ca-server-tls/IssuerPublicKey, secret key is at: /home/ubuntu/hyperledger/multinodes/fabric-ca-server-tls/msp/keystore/IssuerSecretKey
2024/04/24 19:50:44 [INFO] Idemix issuer revocation public and secret keys were generated for CA 'tls-ca'
2024/04/24 19:50:44 [INFO] The revocation key was successfully stored. The public key is at: /home/ubuntu/hyperledger/multinodes/fabric-ca-server-tls/IssuerRevocationPublicKey, private key is at: /home/ubuntu/hyperledger/multinodes/fabric-ca-server-tls/msp/keystore/IssuerRevocationPrivateKey
2024/04/24 19:50:44 [INFO] Home directory for default CA: /home/ubuntu/hyperledger/multinodes/fabric-ca-server-tls
Error: listen tcp 127.0.0.1:9443: bind: address already in use
root@iZn4aampde1w0vhbnmvrlaZ:/home/ubuntu/hyperledger/multinodes/fabric-ca-server-tls# ls
ca-cert.pem       fabric-ca-server-config.yaml  IssuerPublicKey            msp
fabric-ca-server  fabric-ca-server.db           IssuerRevocationPublicKey
root@iZn4aampde1w0vhbnmvrlaZ:/home/ubuntu/hyperledger/multinodes/fabric-ca-server-tls# rm -r ca-cert.pem 
root@iZn4aampde1w0vhbnmvrlaZ:/home/ubuntu/hyperledger/multinodes/fabric-ca-server-tls# rm -r msp
root@iZn4aampde1w0vhbnmvrlaZ:/home/ubuntu/hyperledger/multinodes/fabric-ca-server-tls# ./fabric-ca-server start
2024/04/24 19:52:25 [INFO] Configuration file location: /home/ubuntu/hyperledger/multinodes/fabric-ca-server-tls/fabric-ca-server-config.yaml
2024/04/24 19:52:25 [INFO] Starting server in home directory: /home/ubuntu/hyperledger/multinodes/fabric-ca-server-tls
2024/04/24 19:52:25 [INFO] Server Version: v1.5.7
2024/04/24 19:52:25 [INFO] Server Levels: &{Identity:2 Affiliation:1 Certificate:1 Credential:1 RAInfo:1 Nonce:1}
2024/04/24 19:52:25 [WARNING] &{69 The specified CA certificate file /home/ubuntu/hyperledger/multinodes/fabric-ca-server-tls/ca-cert.pem does not exist}
2024/04/24 19:52:25 [INFO] generating key: &{A:ecdsa S:256}
2024/04/24 19:52:25 [INFO] encoded CSR
2024/04/24 19:52:25 [INFO] signed certificate with serial number 666781219070836270225135903756310723398613290948
2024/04/24 19:52:25 [INFO] The CA key and certificate were generated for CA tls-ca
2024/04/24 19:52:25 [INFO] The key was stored by BCCSP provider 'SW'
2024/04/24 19:52:25 [INFO] The certificate is at: /home/ubuntu/hyperledger/multinodes/fabric-ca-server-tls/ca-cert.pem
2024/04/24 19:52:25 [INFO] Initialized sqlite3 database at /home/ubuntu/hyperledger/multinodes/fabric-ca-server-tls/fabric-ca-server.db
2024/04/24 19:52:25 [INFO] The issuer key was successfully stored. The public key is at: /home/ubuntu/hyperledger/multinodes/fabric-ca-server-tls/IssuerPublicKey, secret key is at: /home/ubuntu/hyperledger/multinodes/fabric-ca-server-tls/msp/keystore/IssuerSecretKey
2024/04/24 19:52:25 [INFO] Idemix issuer revocation public and secret keys were generated for CA 'tls-ca'
2024/04/24 19:52:25 [INFO] The revocation key was successfully stored. The public key is at: /home/ubuntu/hyperledger/multinodes/fabric-ca-server-tls/IssuerRevocationPublicKey, private key is at: /home/ubuntu/hyperledger/multinodes/fabric-ca-server-tls/msp/keystore/IssuerRevocationPrivateKey
2024/04/24 19:52:25 [INFO] Home directory for default CA: /home/ubuntu/hyperledger/multinodes/fabric-ca-server-tls
2024/04/24 19:52:25 [INFO] Operation Server Listening on 127.0.0.1:9453
2024/04/24 19:52:25 [INFO] generating key: &{A:ecdsa S:256}
2024/04/24 19:52:25 [INFO] encoded CSR
2024/04/24 19:52:25 [INFO] signed certificate with serial number 466303194182163083003641856053534007554447037543
2024/04/24 19:52:25 [INFO] Listening on https://0.0.0.0:7064

```



### fabric-ca-client部署

```shell
root@iZn4aampde1w0vhbnmvrlaZ:~# cd /home/ubuntu/hyperledger/multinodes/fabric-ca-client/
root@iZn4aampde1w0vhbnmvrlaZ:/home/ubuntu/hyperledger/multinodes/fabric-ca-client# ls
fabric-ca-client  int-ca  org1-ca  tls-ca  tls-root-cert
root@iZn4aampde1w0vhbnmvrlaZ:/home/ubuntu/hyperledger/multinodes/fabric-ca-client# export FABRIC_CA_CLIENT_HOME=$PWD
root@iZn4aampde1w0vhbnmvrlaZ:/home/ubuntu/hyperledger/multinodes/fabric-ca-client# cp /home/ubuntu/hyperledger/multinodes/fabric-ca-server-tls/ca-cert.pem /home/ubuntu/hyperledger/multinodes/fabric-ca-client/tls-root-cert/tls-ca-cert.pem
root@iZn4aampde1w0vhbnmvrlaZ:/home/ubuntu/hyperledger/multinodes/fabric-ca-client# cd tls-root-cert/
root@iZn4aampde1w0vhbnmvrlaZ:/home/ubuntu/hyperledger/multinodes/fabric-ca-client/tls-root-cert# lstls-ca-cert.pem
root@iZn4aampde1w0vhbnmvrlaZ:/home/ubuntu/hyperledger/multinodes/fabric-ca-client/tls-root-cert# cd ..
root@iZn4aampde1w0vhbnmvrlaZ:/home/ubuntu/hyperledger/multinodes/fabric-ca-client# ./fabric-ca-client enroll -d -u https://admin:adminpw@8.148.15.248:7064 --tls.certfiles tls-root-cert/tls-ca-cert.pem --enrollment.profile tls --mspdir tls-ca/tlsadmin/msp
2024/04/24 19:57:42 [DEBUG] Set log level: 
2024/04/24 19:57:42 [DEBUG] Home directory: /home/ubuntu/hyperledger/multinodes/fabric-ca-client
2024/04/24 19:57:42 [INFO] Created a default configuration file at /home/ubuntu/hyperledger/multinodes/fabric-ca-client/fabric-ca-client-config.yaml
2024/04/24 19:57:42 [DEBUG] Client configuration settings: &{URL:https://admin:adminpw@8.148.15.248:7064 MSPDir:tls-ca/tlsadmin/msp TLS:{Enabled:true CertFiles:[tls-root-cert/tls-ca-cert.pem] Client:{KeyFile: CertFile:}} Enrollment:{ Name: Secret:**** CAName: AttrReqs:[] Profile:tls Label: CSR:<nil> Type:x509  } CSR:{CN:admin Names:[{C:US ST:North Carolina L: O:Hyperledger OU:Fabric SerialNumber:}] Hosts:[iZn4aampde1w0vhbnmvrlaZ] KeyRequest:0xc000494d60 CA:<nil> SerialNumber:} ID:{Name: Type:client Secret: MaxEnrollments:0 Affiliation: Attributes:[] CAName:} Revoke:{Name: Serial: AKI: Reason: CAName: GenCRL:false} CAInfo:{CAName:} CAName: CSP:0xc000494da0 Debug:true LogLevel: Idemix:{Curve:amcl.Fp256bn}}
2024/04/24 19:57:42 [DEBUG] Entered runEnroll
2024/04/24 19:57:42 [DEBUG] Enrolling { Name:admin Secret:**** CAName: AttrReqs:[] Profile:tls Label: CSR:&{admin [{US North Carolina  Hyperledger Fabric }] [iZn4aampde1w0vhbnmvrlaZ] 0xc000494d60 <nil> } Type:x509  }
2024/04/24 19:57:42 [DEBUG] Initializing client with config: &{URL:https://8.148.15.248:7064 MSPDir:tls-ca/tlsadmin/msp TLS:{Enabled:true CertFiles:[tls-root-cert/tls-ca-cert.pem] Client:{KeyFile: CertFile:}} Enrollment:{ Name:admin Secret:**** CAName: AttrReqs:[] Profile:tls Label: CSR:&{admin [{US North Carolina  Hyperledger Fabric }] [iZn4aampde1w0vhbnmvrlaZ] 0xc000494d60 <nil> } Type:x509  } CSR:{CN:admin Names:[{C:US ST:North Carolina L: O:Hyperledger OU:Fabric SerialNumber:}] Hosts:[iZn4aampde1w0vhbnmvrlaZ] KeyRequest:0xc000494d60 CA:<nil> SerialNumber:} ID:{Name: Type:client Secret: MaxEnrollments:0 Affiliation: Attributes:[] CAName:} Revoke:{Name: Serial: AKI: Reason: CAName: GenCRL:false} CAInfo:{CAName:} CAName: CSP:0xc000494da0 Debug:true LogLevel: Idemix:{Curve:amcl.Fp256bn}}
2024/04/24 19:57:42 [DEBUG] Initializing BCCSP: &{ProviderName:SW SwOpts:0xc0003b3c50 PluginOpts:<nil>}
2024/04/24 19:57:42 [DEBUG] Initializing BCCSP with software options &{SecLevel:256 HashFamily:SHA2 FileKeystore:0xc0003ca7b0 DummyKeystore:<nil> InmemKeystore:<nil>}
2024/04/24 19:57:42 [INFO] TLS Enabled
2024/04/24 19:57:42 [DEBUG] CA Files: [/home/ubuntu/hyperledger/multinodes/fabric-ca-client/tls-root-cert/tls-ca-cert.pem]
2024/04/24 19:57:42 [DEBUG] Client Cert File: 
2024/04/24 19:57:42 [DEBUG] Client Key File: 
2024/04/24 19:57:42 [DEBUG] Client TLS certificate and/or key file not provided
2024/04/24 19:57:42 [DEBUG] Using curve amcl.Fp256bn for Idemix
2024/04/24 19:57:42 [DEBUG] GenCSR &{CN:admin Names:[{C:US ST:North Carolina L: O:Hyperledger OU:Fabric SerialNumber:}] Hosts:[iZn4aampde1w0vhbnmvrlaZ] KeyRequest:0xc000494d60 CA:<nil> SerialNumber:}
2024/04/24 19:57:42 [INFO] generating key: &{A:ecdsa S:256}
2024/04/24 19:57:42 [DEBUG] generate key from request: algo=ecdsa, size=256
2024/04/24 19:57:42 [INFO] encoded CSR
2024/04/24 19:57:42 [DEBUG] Sending request
POST https://8.148.15.248:7064/enroll
{"hosts":["iZn4aampde1w0vhbnmvrlaZ"],"certificate_request":"-----BEGIN CERTIFICATE REQUEST-----\nMIIBTDCB9AIBADBdMQswCQYDVQQGEwJVUzEXMBUGA1UECBMOTm9ydGggQ2Fyb2xp\nbmExFDASBgNVBAoTC0h5cGVybGVkZ2VyMQ8wDQYDVQQLEwZGYWJyaWMxDjAMBgNV\nBAMTBWFkbWluMFkwEwYHKoZIzj0CAQYIKoZIzj0DAQcDQgAEsiq5YbJuyG+5YkYk\nMGlh7/4JhZItPme0peWpdW7vGBIdY7aZd4jk+m2TmEz+ZErmYp/vcXy9cisi3FPr\nVLBx/KA1MDMGCSqGSIb3DQEJDjEmMCQwIgYDVR0RBBswGYIXaVpuNGFhbXBkZTF3\nMHZoYm5tdnJsYVowCgYIKoZIzj0EAwIDRwAwRAIgdsX/NBh8HwgQ4pYzkK9TAOoc\nJa4rOjTsKx2iCGcIuh0CIBZ93/R4INXpaVNAKv4j7ydBUIzJxLcJ/Bdn4Qp84N4t\n-----END CERTIFICATE REQUEST-----\n","profile":"tls","crl_override":"","label":"","NotBefore":"0001-01-01T00:00:00Z","NotAfter":"0001-01-01T00:00:00Z","ReturnPrecert":false,"CAName":""}
2024/04/24 19:57:42 [DEBUG] Received response
statusCode=201 (201 Created)
2024/04/24 19:57:42 [DEBUG] Response body result: map[Cert:LS0tLS1CRUdJTiBDRVJUSUZJQ0FURS0tLS0tCk1JSUNhekNDQWhLZ0F3SUJBZ0lVS29uSFMrRHNBdzZkdmNSOEh3aG45VUFQbnZjd0NnWUlLb1pJemowRUF3SXcKYURFTE1Ba0dBMVVFQmhNQ1ZWTXhGekFWQmdOVkJBZ1REazV2Y25Sb0lFTmhjbTlzYVc1aE1SUXdFZ1lEVlFRSwpFd3RJZVhCbGNteGxaR2RsY2pFUE1BMEdBMVVFQ3hNR1JtRmljbWxqTVJrd0Z3WURWUVFERXhCbVlXSnlhV010ClkyRXRjMlZ5ZG1WeU1CNFhEVEkwTURReU5ERXhORGN3TUZvWERUSTFNRFF5TkRFeE5UZ3dNRm93WFRFTE1Ba0cKQTFVRUJoTUNWVk14RnpBVkJnTlZCQWdURGs1dmNuUm9JRU5oY205c2FXNWhNUlF3RWdZRFZRUUtFd3RJZVhCbApjbXhsWkdkbGNqRVBNQTBHQTFVRUN4TUdZMnhwWlc1ME1RNHdEQVlEVlFRREV3VmhaRzFwYmpCWk1CTUdCeXFHClNNNDlBZ0VHQ0NxR1NNNDlBd0VIQTBJQUJMSXF1V0d5YnNodnVXSkdKREJwWWUvK0NZV1NMVDVudEtYbHFYVnUKN3hnU0hXTzJtWGVJNVBwdGs1aE0vbVJLNW1LZjczRjh2WElySXR4VDYxU3djZnlqZ2FRd2dhRXdEZ1lEVlIwUApBUUgvQkFRREFnT29NQjBHQTFVZEpRUVdNQlFHQ0NzR0FRVUZCd01CQmdnckJnRUZCUWNEQWpBTUJnTlZIUk1CCkFmOEVBakFBTUIwR0ExVWREZ1FXQkJURWVmMFhJN1ZuMmVIUVM5bDBUVXQ4WnNlYU5UQWZCZ05WSFNNRUdEQVcKZ0JUcHl6aEhPc0VGTENlZm9pR0p6SXlKV1JYZUpEQWlCZ05WSFJFRUd6QVpnaGRwV200MFlXRnRjR1JsTVhjdwpkbWhpYm0xMmNteGhXakFLQmdncWhrak9QUVFEQWdOSEFEQkVBaUFCbHZ2VnlxaFFrM3V5THhWSWs3YTRpb1BCCnpwb0tKV3JkQlFFT3dKOEN3QUlnTnA4citIVzB5SmVPbnhJTDRXMHp4bUwrR1hySjdrckx3aHdIWC9uQnVyQT0KLS0tLS1FTkQgQ0VSVElGSUNBVEUtLS0tLQo= ServerInfo:map[CAChain:LS0tLS1CRUdJTiBDRVJUSUZJQ0FURS0tLS0tCk1JSUNLRENDQWM2Z0F3SUJBZ0lVZE11QkFxRmk1d1J6SFVTMis0MjdOczV2VDhRd0NnWUlLb1pJemowRUF3SXcKYURFTE1Ba0dBMVVFQmhNQ1ZWTXhGekFWQmdOVkJBZ1REazV2Y25Sb0lFTmhjbTlzYVc1aE1SUXdFZ1lEVlFRSwpFd3RJZVhCbGNteGxaR2RsY2pFUE1BMEdBMVVFQ3hNR1JtRmljbWxqTVJrd0Z3WURWUVFERXhCbVlXSnlhV010ClkyRXRjMlZ5ZG1WeU1CNFhEVEkwTURReU5ERXhORGN3TUZvWERUTTVNRFF5TVRFeE5EY3dNRm93YURFTE1Ba0cKQTFVRUJoTUNWVk14RnpBVkJnTlZCQWdURGs1dmNuUm9JRU5oY205c2FXNWhNUlF3RWdZRFZRUUtFd3RJZVhCbApjbXhsWkdkbGNqRVBNQTBHQTFVRUN4TUdSbUZpY21sak1Sa3dGd1lEVlFRREV4Qm1ZV0p5YVdNdFkyRXRjMlZ5CmRtVnlNRmt3RXdZSEtvWkl6ajBDQVFZSUtvWkl6ajBEQVFjRFFnQUVlOEVMbm04aWZXaURGc3cvTnVEUU1FdncKRm8xdm4vOE8yL015VndaYUZjZjhLLzBrODlBOHBxeWhBNzkyT3h3a0JrdHRsMHpPQndoVWM5OUErWGV0TTZOVwpNRlF3RGdZRFZSMFBBUUgvQkFRREFnRUdNQklHQTFVZEV3RUIvd1FJTUFZQkFmOENBUUV3SFFZRFZSME9CQllFCkZPbkxPRWM2d1FVc0o1K2lJWW5NaklsWkZkNGtNQThHQTFVZEVRUUlNQWFIQkFpVUQvZ3dDZ1lJS29aSXpqMEUKQXdJRFNBQXdSUUloQU5NQXc5WTErS1h6QUZycDRPbzhWZW9mMHVJOXlkaWhTU3E4SEtCL3dLUEpBaUJQUXlPUApBd1FEckZXOFFjWGtZakY2K25VYVdKZ21oV2tmSEVzcFRaVGhlZz09Ci0tLS0tRU5EIENFUlRJRklDQVRFLS0tLS0K CAName:tls-ca IssuerPublicKey:CgJPVQoEUm9sZQoMRW5yb2xsbWVudElEChBSZXZvY2F0aW9uSGFuZGxlEkQKIKooVqRtmfeOw+GHmigQdO+2L2a/EQegyl8TzA5h1rqdEiA/SUV3mSfD7pQX0oNKn02Q6+2yvi+LbfQ/8h+BSJAp7xpECiDVudVvKzZYb+gMkviF7whtprvvDHN0ZAsuae5ofkJksxIgrYrWOHfxy1L8E1nBfSF/tdKmMr6M2HmqFup1iAGmFOwiRAogOjisccsWPVviotArt/2/VQ/7rSULxv4t6tf4fWLQh6ESIEoSrxAor5sZKOf0QXrpmADusOhXX5VXRzbzop42amAfIkQKIO3Fmkd/fUPKZV5xen8b1HcVVgaup2t1rF8tui/waeEAEiA/Cj7+lhpnG2ZZFcca5gfO+B7VhUakH/2dnk2o4uoc0CJECiBQ3v1Kz9FNmZmYgPGpIu/u7UXxU5miqi9HmLbzQLXe3RIgAOdQL5M7hV8TPsyCUBf6MB+imE6WysZ0F6NWIip9ai8iRAog37IZp6MT5ozdwjmrz80qHKiqQkgQuzbVyzuKef3v2wkSIB6PcvQZma85oeKtOxbjlX5P9EnMWuuir7DHzcja8QK7KogBCiCCAaa9OF67nzFjH+U/moUBdlb5kG0ugOW/HgfwbJ8EexIgBEzW+1kdS1NkuI38vyWeA6cmGZRtM3JEDpABb3mgcVAaIDTKVrgCurT7kKm7bDdkqVv2jpHeR90jtYjgZ43jAoQxIiAr1nz3Tji3+XMC+8tvPqOOqkTZ5glNrJGc3JnjEUKNlTJECiBFZgmy2EjROm92kwhBbZ/i/AG6KSdiKEhF0U8tcrgrcxIgHRsdW8BAI+wEigb3u1GndN0At4zBiqZ5igyeLQGDeQU6RAogw/xjbZIx7lnFlLmS+jB5wjt/mAGIM/LQy5zFtn3GgeESIJteErSgjMWebYUV5EJ4RJPeIYV33JsqOfzBMA8PqRomQiC+DY/gY5lTLd7cWTRCqWQ2NcZX3O2NslFvaDTVsDZDMkog9VWOctpCeCucNdrlNbNisuCrrgSvTZ+TWGfWJ6uBvmhSIPQXE8voNGoC9KNEfdtDlRhwVHbcF85HtF66vaXCF9Jr IssuerRevocationPublicKey:LS0tLS1CRUdJTiBQVUJMSUMgS0VZLS0tLS0KTUhZd0VBWUhLb1pJemowQ0FRWUZLNEVFQUNJRFlnQUU2dFhhNHQvK1lrQmU4dnRzVEgrdzhiYWdzTUwxa3dYUwpBaEdHTU9VYkRnU2Nna3FId0M3em9tWEdKVHp3aThxMkVodFZ1RVZNZWRONmdGOEpjWUVqYmZmTTkwRGFrS0NYCkdPUXRPNDYwNlRZdXg0YlRqMXdNRmF0SmxxMWxUK2NPCi0tLS0tRU5EIFBVQkxJQyBLRVktLS0tLQo= Version:]]
2024/04/24 19:57:42 [DEBUG] newEnrollmentResponse admin
2024/04/24 19:57:42 [INFO] Stored client certificate at /home/ubuntu/hyperledger/multinodes/fabric-ca-client/tls-ca/tlsadmin/msp/signcerts/cert.pem
2024/04/24 19:57:42 [INFO] Stored TLS root CA certificate at /home/ubuntu/hyperledger/multinodes/fabric-ca-client/tls-ca/tlsadmin/msp/tlscacerts/tls-8-148-15-248-7064.pem
2024/04/24 19:57:42 [INFO] Stored Issuer public key at /home/ubuntu/hyperledger/multinodes/fabric-ca-client/tls-ca/tlsadmin/msp/IssuerPublicKey
2024/04/24 19:57:42 [INFO] Stored Issuer revocation public key at /home/ubuntu/hyperledger/multinodes/fabric-ca-client/tls-ca/tlsadmin/msp/IssuerRevocationPublicKey
root@iZn4aampde1w0vhbnmvrlaZ:/home/ubuntu/hyperledger/multinodes/fabric-ca-client# ./fabric-ca-client register -d --id.name user1 --id.secret user1 -u https://8.148.15.248:7064  --tls.certfiles tls-root-cert/tls-ca-cert.pem --mspdir tls-ca/user1/msp
2024/04/24 19:59:47 [DEBUG] Set log level: 
2024/04/24 19:59:47 [DEBUG] Home directory: /home/ubuntu/hyperledger/multinodes/fabric-ca-client
2024/04/24 19:59:47 [INFO] Configuration file location: /home/ubuntu/hyperledger/multinodes/fabric-ca-client/fabric-ca-client-config.yaml
2024/04/24 19:59:47 [DEBUG] Checking for enrollment
2024/04/24 19:59:47 [DEBUG] Initializing client with config: &{URL:https://8.148.15.248:7064 MSPDir:tls-ca/user1/msp TLS:{Enabled:true CertFiles:[tls-root-cert/tls-ca-cert.pem] Client:{KeyFile: CertFile:}} Enrollment:{ Name: Secret:**** CAName: AttrReqs:[] Profile: Label: CSR:<nil> Type:x509  } CSR:{CN:admin Names:[{C:US ST:North Carolina L: O:Hyperledger OU:Fabric SerialNumber:}] Hosts:[iZn4aampde1w0vhbnmvrlaZ] KeyRequest:0xc00007b180 CA:<nil> SerialNumber:} ID:{Name:user1 Type:client Secret:user1 MaxEnrollments:0 Affiliation: Attributes:[] CAName:} Revoke:{Name: Serial: AKI: Reason: CAName: GenCRL:false} CAInfo:{CAName:} CAName: CSP:0xc00007b1c0 Debug:true LogLevel: Idemix:{Curve:amcl.Fp256bn}}
2024/04/24 19:59:47 [DEBUG] Initializing BCCSP: &{ProviderName:SW SwOpts:0xc0000a74d0 PluginOpts:<nil>}
2024/04/24 19:59:47 [DEBUG] Initializing BCCSP with software options &{SecLevel:256 HashFamily:SHA2 FileKeystore:0xc0004ab9a0 DummyKeystore:<nil> InmemKeystore:<nil>}
2024/04/24 19:59:47 [INFO] TLS Enabled
2024/04/24 19:59:47 [DEBUG] CA Files: [/home/ubuntu/hyperledger/multinodes/fabric-ca-client/tls-root-cert/tls-ca-cert.pem]
2024/04/24 19:59:47 [DEBUG] Client Cert File: 
2024/04/24 19:59:47 [DEBUG] Client Key File: 
2024/04/24 19:59:47 [DEBUG] Client TLS certificate and/or key file not provided
2024/04/24 19:59:47 [DEBUG] Using curve amcl.Fp256bn for Idemix
2024/04/24 19:59:47 [DEBUG] CheckIdemixEnrollment - ipkFile: /home/ubuntu/hyperledger/multinodes/fabric-ca-client/tls-ca/user1/msp/IssuerPublicKey, idemixCredFile: /home/ubuntu/hyperledger/multinodes/fabric-ca-client/tls-ca/user1/msp/user/SignerConfig
2024/04/24 19:59:47 [ERROR] Enrollment check failed: either because 'x509 enrollment information does not exist - certFile: /home/ubuntu/hyperledger/multinodes/fabric-ca-client/tls-ca/user1/msp/signcerts/cert.pem keyFile: /home/ubuntu/hyperledger/multinodes/fabric-ca-client/tls-ca/user1/msp/keystore/key.pem' or  'Idemix enrollment information does not exist'
Error: Enrollment information does not exist. Please execute enroll command first. Example: fabric-ca-client enroll -u http://user:userpw@serverAddr:serverPort
root@iZn4aampde1w0vhbnmvrlaZ:/home/ubuntu/hyperledger/multinodes/fabric-ca-client#  ./fabric-ca-client register -d --id.name user1 --id.secret user1 -u https://8.148.15.248:7064  --tls.certfiles tls-root-cert/tls-ca-cert.pem --mspdir tls-ca/tlsadmin/msp
2024/04/24 20:05:37 [DEBUG] Set log level: 
2024/04/24 20:05:37 [DEBUG] Home directory: /home/ubuntu/hyperledger/multinodes/fabric-ca-client
2024/04/24 20:05:37 [INFO] Configuration file location: /home/ubuntu/hyperledger/multinodes/fabric-ca-client/fabric-ca-client-config.yaml
2024/04/24 20:05:37 [DEBUG] Checking for enrollment
2024/04/24 20:05:37 [DEBUG] Initializing client with config: &{URL:https://8.148.15.248:7064 MSPDir:tls-ca/tlsadmin/msp TLS:{Enabled:true CertFiles:[tls-root-cert/tls-ca-cert.pem] Client:{KeyFile: CertFile:}} Enrollment:{ Name: Secret:**** CAName: AttrReqs:[] Profile: Label: CSR:<nil> Type:x509  } CSR:{CN:admin Names:[{C:US ST:North Carolina L: O:Hyperledger OU:Fabric SerialNumber:}] Hosts:[iZn4aampde1w0vhbnmvrlaZ] KeyRequest:0xc0004a1ce0 CA:<nil> SerialNumber:} ID:{Name:user1 Type:client Secret:user1 MaxEnrollments:0 Affiliation: Attributes:[] CAName:} Revoke:{Name: Serial: AKI: Reason: CAName: GenCRL:false} CAInfo:{CAName:} CAName: CSP:0xc0004a1d20 Debug:true LogLevel: Idemix:{Curve:amcl.Fp256bn}}
2024/04/24 20:05:37 [DEBUG] Initializing BCCSP: &{ProviderName:SW SwOpts:0xc000245890 PluginOpts:<nil>}
2024/04/24 20:05:37 [DEBUG] Initializing BCCSP with software options &{SecLevel:256 HashFamily:SHA2 FileKeystore:0xc00028cfe0 DummyKeystore:<nil> InmemKeystore:<nil>}
2024/04/24 20:05:37 [INFO] TLS Enabled
2024/04/24 20:05:37 [DEBUG] CA Files: [/home/ubuntu/hyperledger/multinodes/fabric-ca-client/tls-root-cert/tls-ca-cert.pem]
2024/04/24 20:05:37 [DEBUG] Client Cert File: 
2024/04/24 20:05:37 [DEBUG] Client Key File: 
2024/04/24 20:05:37 [DEBUG] Client TLS certificate and/or key file not provided
2024/04/24 20:05:37 [DEBUG] Using curve amcl.Fp256bn for Idemix
2024/04/24 20:05:37 [DEBUG] CheckIdemixEnrollment - ipkFile: /home/ubuntu/hyperledger/multinodes/fabric-ca-client/tls-ca/tlsadmin/msp/IssuerPublicKey, idemixCredFile: /home/ubuntu/hyperledger/multinodes/fabric-ca-client/tls-ca/tlsadmin/msp/user/SignerConfig
2024/04/24 20:05:37 [DEBUG] Client configuration settings: &{URL:https://8.148.15.248:7064 MSPDir:/home/ubuntu/hyperledger/multinodes/fabric-ca-client/tls-ca/tlsadmin/msp TLS:{Enabled:true CertFiles:[/home/ubuntu/hyperledger/multinodes/fabric-ca-client/tls-root-cert/tls-ca-cert.pem] Client:{KeyFile: CertFile:}} Enrollment:{ Name: Secret:**** CAName: AttrReqs:[] Profile: Label: CSR:<nil> Type:x509  } CSR:{CN:admin Names:[{C:US ST:North Carolina L: O:Hyperledger OU:Fabric SerialNumber:}] Hosts:[iZn4aampde1w0vhbnmvrlaZ] KeyRequest:0xc0004a1ce0 CA:<nil> SerialNumber:} ID:{Name:user1 Type:client Secret:user1 MaxEnrollments:0 Affiliation: Attributes:[] CAName:} Revoke:{Name: Serial: AKI: Reason: CAName: GenCRL:false} CAInfo:{CAName:} CAName: CSP:0xc0004a1d20 Debug:true LogLevel: Idemix:{Curve:amcl.Fp256bn}}
2024/04/24 20:05:37 [DEBUG] Entered runRegister
2024/04/24 20:05:37 [DEBUG] LoadMyIdentity 
2024/04/24 20:05:37 [DEBUG] Initializing client with config: &{URL:https://8.148.15.248:7064 MSPDir:/home/ubuntu/hyperledger/multinodes/fabric-ca-client/tls-ca/tlsadmin/msp TLS:{Enabled:true CertFiles:[/home/ubuntu/hyperledger/multinodes/fabric-ca-client/tls-root-cert/tls-ca-cert.pem] Client:{KeyFile: CertFile:}} Enrollment:{ Name: Secret:**** CAName: AttrReqs:[] Profile: Label: CSR:<nil> Type:x509  } CSR:{CN:admin Names:[{C:US ST:North Carolina L: O:Hyperledger OU:Fabric SerialNumber:}] Hosts:[iZn4aampde1w0vhbnmvrlaZ] KeyRequest:0xc0004a1ce0 CA:<nil> SerialNumber:} ID:{Name:user1 Type:client Secret:user1 MaxEnrollments:0 Affiliation: Attributes:[] CAName:} Revoke:{Name: Serial: AKI: Reason: CAName: GenCRL:false} CAInfo:{CAName:} CAName: CSP:0xc0004a1d20 Debug:true LogLevel: Idemix:{Curve:amcl.Fp256bn}}
2024/04/24 20:05:37 [DEBUG] Initializing BCCSP: &{ProviderName:SW SwOpts:0xc000245890 PluginOpts:<nil>}
2024/04/24 20:05:37 [DEBUG] Initializing BCCSP with software options &{SecLevel:256 HashFamily:SHA2 FileKeystore:0xc00028cfe0 DummyKeystore:<nil> InmemKeystore:<nil>}
2024/04/24 20:05:37 [INFO] TLS Enabled
2024/04/24 20:05:37 [DEBUG] CA Files: [/home/ubuntu/hyperledger/multinodes/fabric-ca-client/tls-root-cert/tls-ca-cert.pem]
2024/04/24 20:05:37 [DEBUG] Client Cert File: 
2024/04/24 20:05:37 [DEBUG] Client Key File: 
2024/04/24 20:05:37 [DEBUG] Client TLS certificate and/or key file not provided
2024/04/24 20:05:37 [DEBUG] Using curve amcl.Fp256bn for Idemix
2024/04/24 20:05:37 [DEBUG] Loading identity: keyFile=/home/ubuntu/hyperledger/multinodes/fabric-ca-client/tls-ca/tlsadmin/msp/keystore/key.pem, certFile=/home/ubuntu/hyperledger/multinodes/fabric-ca-client/tls-ca/tlsadmin/msp/signcerts/cert.pem
2024/04/24 20:05:37 [DEBUG] No credential found at /home/ubuntu/hyperledger/multinodes/fabric-ca-client/tls-ca/tlsadmin/msp/user/SignerConfig: open /home/ubuntu/hyperledger/multinodes/fabric-ca-client/tls-ca/tlsadmin/msp/user/SignerConfig: no such file or directory
2024/04/24 20:05:37 [DEBUG] No Idemix credential found at /home/ubuntu/hyperledger/multinodes/fabric-ca-client/tls-ca/tlsadmin/msp/user/SignerConfig
2024/04/24 20:05:37 [DEBUG] Register { Name:user1 Type:client Secret:**** MaxEnrollments:0 Affiliation: Attributes:[] CAName:  }
2024/04/24 20:05:37 [DEBUG] Adding token-based authorization header
2024/04/24 20:05:37 [DEBUG] Sending request
POST https://8.148.15.248:7064/register
{"id":"user1","type":"client","secret":"user1","affiliation":""}
2024/04/24 20:05:37 [DEBUG] Received response
statusCode=201 (201 Created)
2024/04/24 20:05:37 [DEBUG] Response body result: map[secret:user1]
2024/04/24 20:05:37 [DEBUG] The register request completed successfully
Password: user1


root@iZn4aampde1w0vhbnmvrlaZ:/home/ubuntu/hyperledger/multinodes/fabric-ca-client# ./fabric-ca-client enroll -d -u https://user1:user1@8.148.15.248:7064 --tls.certfiles tls-root-cert/tls-ca-cert.pem --enrollment.profile tls --csr.hosts 'host1,*.example.com' --mspdir tls-ca/user1/msp
2024/04/24 20:08:19 [DEBUG] Set log level: 
2024/04/24 20:08:19 [DEBUG] Home directory: /home/ubuntu/hyperledger/multinodes/fabric-ca-client
2024/04/24 20:08:19 [DEBUG] Client configuration settings: &{URL:https://user1:user1@8.148.15.248:7064 MSPDir:tls-ca/user1/msp TLS:{Enabled:true CertFiles:[tls-root-cert/tls-ca-cert.pem] Client:{KeyFile: CertFile:}} Enrollment:{ Name: Secret:**** CAName: AttrReqs:[] Profile:tls Label: CSR:<nil> Type:x509  } CSR:{CN:admin Names:[{C:US ST:North Carolina L: O:Hyperledger OU:Fabric SerialNumber:}] Hosts:[host1 *.example.com] KeyRequest:0xc0000c48c0 CA:<nil> SerialNumber:} ID:{Name: Type:client Secret: MaxEnrollments:0 Affiliation: Attributes:[] CAName:} Revoke:{Name: Serial: AKI: Reason: CAName: GenCRL:false} CAInfo:{CAName:} CAName: CSP:0xc0000c4900 Debug:true LogLevel: Idemix:{Curve:amcl.Fp256bn}}
2024/04/24 20:08:19 [DEBUG] Entered runEnroll
2024/04/24 20:08:19 [DEBUG] Enrolling { Name:user1 Secret:**** CAName: AttrReqs:[] Profile:tls Label: CSR:&{admin [{US North Carolina  Hyperledger Fabric }] [host1 *.example.com] 0xc0000c48c0 <nil> } Type:x509  }
2024/04/24 20:08:19 [DEBUG] Initializing client with config: &{URL:https://8.148.15.248:7064 MSPDir:tls-ca/user1/msp TLS:{Enabled:true CertFiles:[tls-root-cert/tls-ca-cert.pem] Client:{KeyFile: CertFile:}} Enrollment:{ Name:user1 Secret:**** CAName: AttrReqs:[] Profile:tls Label: CSR:&{admin [{US North Carolina  Hyperledger Fabric }] [host1 *.example.com] 0xc0000c48c0 <nil> } Type:x509  } CSR:{CN:admin Names:[{C:US ST:North Carolina L: O:Hyperledger OU:Fabric SerialNumber:}] Hosts:[host1 *.example.com] KeyRequest:0xc0000c48c0 CA:<nil> SerialNumber:} ID:{Name: Type:client Secret: MaxEnrollments:0 Affiliation: Attributes:[] CAName:} Revoke:{Name: Serial: AKI: Reason: CAName: GenCRL:false} CAInfo:{CAName:} CAName: CSP:0xc0000c4900 Debug:true LogLevel: Idemix:{Curve:amcl.Fp256bn}}
2024/04/24 20:08:19 [DEBUG] Initializing BCCSP: &{ProviderName:SW SwOpts:0xc0000df8f0 PluginOpts:<nil>}
2024/04/24 20:08:19 [DEBUG] Initializing BCCSP with software options &{SecLevel:256 HashFamily:SHA2 FileKeystore:0xc000179c20 DummyKeystore:<nil> InmemKeystore:<nil>}
2024/04/24 20:08:19 [INFO] TLS Enabled
2024/04/24 20:08:19 [DEBUG] CA Files: [/home/ubuntu/hyperledger/multinodes/fabric-ca-client/tls-root-cert/tls-ca-cert.pem]
2024/04/24 20:08:19 [DEBUG] Client Cert File: 
2024/04/24 20:08:19 [DEBUG] Client Key File: 
2024/04/24 20:08:19 [DEBUG] Client TLS certificate and/or key file not provided
2024/04/24 20:08:19 [DEBUG] Using curve amcl.Fp256bn for Idemix
2024/04/24 20:08:19 [DEBUG] GenCSR &{CN:admin Names:[{C:US ST:North Carolina L: O:Hyperledger OU:Fabric SerialNumber:}] Hosts:[host1 *.example.com] KeyRequest:0xc0000c48c0 CA:<nil> SerialNumber:}
2024/04/24 20:08:19 [INFO] generating key: &{A:ecdsa S:256}
2024/04/24 20:08:19 [DEBUG] generate key from request: algo=ecdsa, size=256
2024/04/24 20:08:19 [INFO] encoded CSR
2024/04/24 20:08:19 [DEBUG] Sending request
POST https://8.148.15.248:7064/enroll
{"hosts":["host1","*.example.com"],"certificate_request":"-----BEGIN CERTIFICATE REQUEST-----\nMIIBSTCB8QIBADBdMQswCQYDVQQGEwJVUzEXMBUGA1UECBMOTm9ydGggQ2Fyb2xp\nbmExFDASBgNVBAoTC0h5cGVybGVkZ2VyMQ8wDQYDVQQLEwZGYWJyaWMxDjAMBgNV\nBAMTBXVzZXIxMFkwEwYHKoZIzj0CAQYIKoZIzj0DAQcDQgAEzbSiAccTXw2lRogh\n5JD7bbXtpxhTKFu5PB26HpPA/JWh5yQ/wPHqWoQCbzLZJKqrDfdZVlNOnMnPsTRy\n2noLjaAyMDAGCSqGSIb3DQEJDjEjMCEwHwYDVR0RBBgwFoIFaG9zdDGCDSouZXhh\nbXBsZS5jb20wCgYIKoZIzj0EAwIDRwAwRAIgES77WwnLqlsV+m5xyXs1zDVAHJDk\nseogvvMADlYG7jwCIC2pqPuhl2Fdd5rzTECtgPRdqbTBRTs7usB0P7b2Ulcq\n-----END CERTIFICATE REQUEST-----\n","profile":"tls","crl_override":"","label":"","NotBefore":"0001-01-01T00:00:00Z","NotAfter":"0001-01-01T00:00:00Z","ReturnPrecert":false,"CAName":""}
2024/04/24 20:08:19 [DEBUG] Received response
statusCode=201 (201 Created)
2024/04/24 20:08:19 [DEBUG] Response body result: map[Cert:LS0tLS1CRUdJTiBDRVJUSUZJQ0FURS0tLS0tCk1JSUN3ekNDQW1tZ0F3SUJBZ0lVUjA0Ymh3bEZlWlMrUHl4TFhpSkIrUGZCamk4d0NnWUlLb1pJemowRUF3SXcKYURFTE1Ba0dBMVVFQmhNQ1ZWTXhGekFWQmdOVkJBZ1REazV2Y25Sb0lFTmhjbTlzYVc1aE1SUXdFZ1lEVlFRSwpFd3RJZVhCbGNteGxaR2RsY2pFUE1BMEdBMVVFQ3hNR1JtRmljbWxqTVJrd0Z3WURWUVFERXhCbVlXSnlhV010ClkyRXRjMlZ5ZG1WeU1CNFhEVEkwTURReU5ERXhORGN3TUZvWERUSTFNRFF5TkRFeU1EZ3dNRm93WFRFTE1Ba0cKQTFVRUJoTUNWVk14RnpBVkJnTlZCQWdURGs1dmNuUm9JRU5oY205c2FXNWhNUlF3RWdZRFZRUUtFd3RJZVhCbApjbXhsWkdkbGNqRVBNQTBHQTFVRUN4TUdZMnhwWlc1ME1RNHdEQVlEVlFRREV3VjFjMlZ5TVRCWk1CTUdCeXFHClNNNDlBZ0VHQ0NxR1NNNDlBd0VIQTBJQUJNMjBvZ0hIRTE4TnBVYUlJZVNRKzIyMTdhY1lVeWhidVR3ZHVoNlQKd1B5Vm9lY2tQOER4NmxxRUFtOHkyU1NxcXczM1dWWlRUcHpKejdFMGN0cDZDNDJqZ2Zzd2dmZ3dEZ1lEVlIwUApBUUgvQkFRREFnT29NQjBHQTFVZEpRUVdNQlFHQ0NzR0FRVUZCd01CQmdnckJnRUZCUWNEQWpBTUJnTlZIUk1CCkFmOEVBakFBTUIwR0ExVWREZ1FXQkJRU0t6MGpDWHhsS0dPRWE5eldQK1AzdTh1RE56QWZCZ05WSFNNRUdEQVcKZ0JUcHl6aEhPc0VGTENlZm9pR0p6SXlKV1JYZUpEQWZCZ05WSFJFRUdEQVdnZ1ZvYjNOME1ZSU5LaTVsZUdGdApjR3hsTG1OdmJUQllCZ2dxQXdRRkJnY0lBUVJNZXlKaGRIUnljeUk2ZXlKb1ppNUJabVpwYkdsaGRHbHZiaUk2CklpSXNJbWhtTGtWdWNtOXNiRzFsYm5SSlJDSTZJblZ6WlhJeElpd2lhR1l1Vkhsd1pTSTZJbU5zYVdWdWRDSjkKZlRBS0JnZ3Foa2pPUFFRREFnTklBREJGQWlFQXh0bmpEd0I1YWtkenY5L2tmMFI5S2loaGxHYnBJeUd6aTBFRQppbDQwWlRFQ0lEK0hodFZMR0lTU29neVRRMUIzaXZTMkt4MjJWSkxmd01aaGJNZE5SVWwyCi0tLS0tRU5EIENFUlRJRklDQVRFLS0tLS0K ServerInfo:map[CAChain:LS0tLS1CRUdJTiBDRVJUSUZJQ0FURS0tLS0tCk1JSUNLRENDQWM2Z0F3SUJBZ0lVZE11QkFxRmk1d1J6SFVTMis0MjdOczV2VDhRd0NnWUlLb1pJemowRUF3SXcKYURFTE1Ba0dBMVVFQmhNQ1ZWTXhGekFWQmdOVkJBZ1REazV2Y25Sb0lFTmhjbTlzYVc1aE1SUXdFZ1lEVlFRSwpFd3RJZVhCbGNteGxaR2RsY2pFUE1BMEdBMVVFQ3hNR1JtRmljbWxqTVJrd0Z3WURWUVFERXhCbVlXSnlhV010ClkyRXRjMlZ5ZG1WeU1CNFhEVEkwTURReU5ERXhORGN3TUZvWERUTTVNRFF5TVRFeE5EY3dNRm93YURFTE1Ba0cKQTFVRUJoTUNWVk14RnpBVkJnTlZCQWdURGs1dmNuUm9JRU5oY205c2FXNWhNUlF3RWdZRFZRUUtFd3RJZVhCbApjbXhsWkdkbGNqRVBNQTBHQTFVRUN4TUdSbUZpY21sak1Sa3dGd1lEVlFRREV4Qm1ZV0p5YVdNdFkyRXRjMlZ5CmRtVnlNRmt3RXdZSEtvWkl6ajBDQVFZSUtvWkl6ajBEQVFjRFFnQUVlOEVMbm04aWZXaURGc3cvTnVEUU1FdncKRm8xdm4vOE8yL015VndaYUZjZjhLLzBrODlBOHBxeWhBNzkyT3h3a0JrdHRsMHpPQndoVWM5OUErWGV0TTZOVwpNRlF3RGdZRFZSMFBBUUgvQkFRREFnRUdNQklHQTFVZEV3RUIvd1FJTUFZQkFmOENBUUV3SFFZRFZSME9CQllFCkZPbkxPRWM2d1FVc0o1K2lJWW5NaklsWkZkNGtNQThHQTFVZEVRUUlNQWFIQkFpVUQvZ3dDZ1lJS29aSXpqMEUKQXdJRFNBQXdSUUloQU5NQXc5WTErS1h6QUZycDRPbzhWZW9mMHVJOXlkaWhTU3E4SEtCL3dLUEpBaUJQUXlPUApBd1FEckZXOFFjWGtZakY2K25VYVdKZ21oV2tmSEVzcFRaVGhlZz09Ci0tLS0tRU5EIENFUlRJRklDQVRFLS0tLS0K CAName:tls-ca IssuerPublicKey:CgJPVQoEUm9sZQoMRW5yb2xsbWVudElEChBSZXZvY2F0aW9uSGFuZGxlEkQKIKooVqRtmfeOw+GHmigQdO+2L2a/EQegyl8TzA5h1rqdEiA/SUV3mSfD7pQX0oNKn02Q6+2yvi+LbfQ/8h+BSJAp7xpECiDVudVvKzZYb+gMkviF7whtprvvDHN0ZAsuae5ofkJksxIgrYrWOHfxy1L8E1nBfSF/tdKmMr6M2HmqFup1iAGmFOwiRAogOjisccsWPVviotArt/2/VQ/7rSULxv4t6tf4fWLQh6ESIEoSrxAor5sZKOf0QXrpmADusOhXX5VXRzbzop42amAfIkQKIO3Fmkd/fUPKZV5xen8b1HcVVgaup2t1rF8tui/waeEAEiA/Cj7+lhpnG2ZZFcca5gfO+B7VhUakH/2dnk2o4uoc0CJECiBQ3v1Kz9FNmZmYgPGpIu/u7UXxU5miqi9HmLbzQLXe3RIgAOdQL5M7hV8TPsyCUBf6MB+imE6WysZ0F6NWIip9ai8iRAog37IZp6MT5ozdwjmrz80qHKiqQkgQuzbVyzuKef3v2wkSIB6PcvQZma85oeKtOxbjlX5P9EnMWuuir7DHzcja8QK7KogBCiCCAaa9OF67nzFjH+U/moUBdlb5kG0ugOW/HgfwbJ8EexIgBEzW+1kdS1NkuI38vyWeA6cmGZRtM3JEDpABb3mgcVAaIDTKVrgCurT7kKm7bDdkqVv2jpHeR90jtYjgZ43jAoQxIiAr1nz3Tji3+XMC+8tvPqOOqkTZ5glNrJGc3JnjEUKNlTJECiBFZgmy2EjROm92kwhBbZ/i/AG6KSdiKEhF0U8tcrgrcxIgHRsdW8BAI+wEigb3u1GndN0At4zBiqZ5igyeLQGDeQU6RAogw/xjbZIx7lnFlLmS+jB5wjt/mAGIM/LQy5zFtn3GgeESIJteErSgjMWebYUV5EJ4RJPeIYV33JsqOfzBMA8PqRomQiC+DY/gY5lTLd7cWTRCqWQ2NcZX3O2NslFvaDTVsDZDMkog9VWOctpCeCucNdrlNbNisuCrrgSvTZ+TWGfWJ6uBvmhSIPQXE8voNGoC9KNEfdtDlRhwVHbcF85HtF66vaXCF9Jr IssuerRevocationPublicKey:LS0tLS1CRUdJTiBQVUJMSUMgS0VZLS0tLS0KTUhZd0VBWUhLb1pJemowQ0FRWUZLNEVFQUNJRFlnQUU2dFhhNHQvK1lrQmU4dnRzVEgrdzhiYWdzTUwxa3dYUwpBaEdHTU9VYkRnU2Nna3FId0M3em9tWEdKVHp3aThxMkVodFZ1RVZNZWRONmdGOEpjWUVqYmZmTTkwRGFrS0NYCkdPUXRPNDYwNlRZdXg0YlRqMXdNRmF0SmxxMWxUK2NPCi0tLS0tRU5EIFBVQkxJQyBLRVktLS0tLQo= Version:]]
2024/04/24 20:08:19 [DEBUG] newEnrollmentResponse user1
2024/04/24 20:08:19 [INFO] Stored client certificate at /home/ubuntu/hyperledger/multinodes/fabric-ca-client/tls-ca/user1/msp/signcerts/cert.pem
2024/04/24 20:08:19 [INFO] Stored TLS root CA certificate at /home/ubuntu/hyperledger/multinodes/fabric-ca-client/tls-ca/user1/msp/tlscacerts/tls-8-148-15-248-7064.pem
2024/04/24 20:08:19 [INFO] Stored Issuer public key at /home/ubuntu/hyperledger/multinodes/fabric-ca-client/tls-ca/user1/msp/IssuerPublicKey
2024/04/24 20:08:19 [INFO] Stored Issuer revocation public key at /home/ubuntu/hyperledger/multinodes/fabric-ca-client/tls-ca/user1/msp/IssuerRevocationPublicKey

```

