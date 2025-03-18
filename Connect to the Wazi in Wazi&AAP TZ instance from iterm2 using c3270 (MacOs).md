## Create a tso User

Go to your reservation details and click on the Ansible Automation Platform UI link
![Screenshot 2025-03-17 at 15.04.12.png](https://github.com/AlexisP1909/Access-Wazi-TZ-from-iTerm2/blob/main/Screenshot%202025-03-05%20at%2010.19.02.png)
Use admin as your username
```
admin 
```

Your password is your **AAP User Password**

Go in templates and find tso Commands
![Screenshot 2025-03-17 at 15.30.56.png]([Screenshot 2025-03-17 at 15.14.07.png](https://github.com/AlexisP1909/Access-Wazi-TZ-from-iTerm2/blob/main/Screenshot%202025-03-17%20at%2015.14.07.png))
run TSO command template with the following command
```
ALTUSER <Your user id> PHRASE('<the password you choose>') NOEXPIRE RESUME
```

Your user is IBMUSER and your password is the one you have set. It works to access tso and CICSTS (i didn't test other ways to interact with the system)

## Get the Certificate
Open your OWN techzone reservation.
**Go to the Ansible Automation Platform cockpit UI** by clicking your link.

The creds are the AAP User name (for SSH Access) and the AAP User password.

Again you need to go get them from your AAP reservation.
![Screenshot 2025-03-17 at 15.04.12.png](https://github.com/AlexisP1909/Access-Wazi-TZ-from-iTerm2/blob/main/Screenshot%202025-03-05%20at%2010.19.02.png)

Once in the Cockpit **go to terminal** (you will need to scroll down on the left side menu for it to appear).


Paste the following command to retrieve the certificate
```
sudo cat /root/certificates/certificate.pem
```

Copy the 2 certificates in a single new file and give it a name like wazi_cert.pem. (copy from ---BEGIN CERTIFICATE to the **2ND** --END CERTIFICATE)
![[Screenshot 2025-03-17 at 15.14.07.png]]
Copy the path of the file somewhere, you will need it soon
## Create Iterm2(terminal) profile to connect to Wazi on IBM Cloud
Install Iterm2 (if you do not have it)

Open profiles from the top bar (or command + O). Click on edit Profiles,
Import the json profile from the file [ItermWaziProfile.json](https://github.com/AlexisP1909/Access-Wazi-TZ-from-iTerm2/blob/main/ItermWaziProfile.json) 
![[Screenshot 2025-03-17 at 14.58.29.png]]
## Modify parameters to suit your TZ (Techzone) instance

![Screenshot 2025-03-05 at 10.15.38.png](https://github.com/AlexisP1909/Access-Wazi-TZ-from-iTerm2/blob/main/Screenshot%202025-03-05%20at%2010.15.38.png)
Modify the **Send text at start** field
```
c3270 -noverifycert -cafile YOUR/PATH/TO/CERT/certificate.pem -port 992 L:YOUR_ZOS_PUBLIC_IP_ADDRESS
```

You will find the zos public IP address from your techzone reservation.

(where you found the usernames & passwords for AAP)
(don't confuse it with the AAP public IP & make sure no space has appeared between the : and the first digit)

In iterm 2 go back to Profiles and click on the profile you have set. You should have a c3270 terminal up and running.
![[Pasted image 20250317154023.png]]
