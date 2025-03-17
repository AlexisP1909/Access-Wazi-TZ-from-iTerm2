## I. Wazi tests
### a. Connect to Wazi

[[Connect to Wazi (macOs)]]

## Create Iterm2(terminal) profile to connect to Wazi on IBM Cloud
Import json profile
[[Json Iterm Wazi Profile]]

## Modify parameters to suit your TZ (Techzone) instance

![[Screenshot 2025-03-05 at 10.15.38.png]]
Modify Send text at start
```
c3270 -noverifycert -cafile YOUR/PATH/TO/CERT/certificate.pem -port 992 L:YOUR_IP_ADDRESS
```
## How to get the Certificate

Download auth cert to connect to AAP (THIS IS NOT THE CERTIFICATE FOR WAZI)

![[Screenshot 2025-03-05 at 10.19.02.png]]
Press the user ssh key button 
Copy the public IP address of the AAP
Copy the User for AAP

Connect to the AAP instance
```
ssh -i YOUR/PATH/TO/CERT/ssh_private_key.pem YOUR_USER@AAP_IP
```

If this doesnt work try to move the certificate to the .ssh folder on your mac 


copy the certificate
```
sudo cat /root/certificates/certificate.pem
```

**Get a password**
	go to AAP'
run TSO command template with the following command
```
ALTUSER <Your user id> PHRASE('<Your new passphrase>') NOEXPIRE RESUME
```
In our case
```
ALTUSER IBMUSER PHRASE('Your new passphrase') NOEXPIRE RESUME
```

```
Your new passphrase
```

## b. Connect to CICS
connect to CICSTS61
use tso creds
```
CEDA
```

## II. Install Java Liberty on CICS
[[Install Java Liberty on CICS]]



3.4 CICS* 
voir les datasets

Créer le dir
Redémarrer le serv CICS

Créer et appeler un JCL via AAp


Faire de l'uss
13.11

uss -> environnement unix de z/os

permet de voir file system avec chemin

CICSTS.V6R1M0.CICS.SDFHINST
m
DFHIJVMJ
v
l 111-122

