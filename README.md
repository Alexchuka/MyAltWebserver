# Assignment Steps!

Step 1: Logged on to my AWS-created EC2 instance with Termius and Added my Server:

<img width="1066" alt="image" src="https://github.com/user-attachments/assets/d504e4c6-aa5c-4148-a807-a7f0d54edcf9" />

Step 2: Verify my connection using the commands `whoami` and `hostname`:

<img width="851" alt="image" src="https://github.com/user-attachments/assets/1975ef0b-30e7-4a98-bf41-a3521e40a4f4" />

Step 3:  Run the `sudo apt update` command to install Apache:

<img width="950" alt="image" src="https://github.com/user-attachments/assets/e68b6e06-156a-4b16-b12f-6a4c4f15f2e4" />

Step 4: Ran the command `sudo apt install apache2` to install the Apache Web Server:

<img width="1109" alt="image" src="https://github.com/user-attachments/assets/5c5a21e0-77f9-437b-9a15-52cfb3947d85" />

<img width="1153" alt="image" src="https://github.com/user-attachments/assets/4ffc0ab7-60b9-4481-9f8f-31e740ec920c" />

<img width="1198" alt="image" src="https://github.com/user-attachments/assets/604422cc-ec5f-486a-bf64-aed25a6bd08d" />

<img width="1031" alt="image" src="https://github.com/user-attachments/assets/9605166f-dc98-44f7-83d5-3c65be63c30d" />

Step 5: Started and Enabled Apache Services: 

`sudo systemctl start apache2`
`sudo systemctl enable apache2`

<img width="958" alt="image" src="https://github.com/user-attachments/assets/70026d12-4f7b-4d13-b53d-e06a338958f8" />

Step 6: Verified my installation: https://18.175.111.255/ by creating inbound rules allowing traffic on Port 80 for HTTP, Port 443 for HTTPS, and Custom ICMP Rule – IPv4 for ping.!

<img width="1199" alt="image" src="https://github.com/user-attachments/assets/978f0cb1-27ae-4283-96e2-88673c294f0c" />

Tested and it works:

<img width="1058" alt="image" src="https://github.com/user-attachments/assets/48005d91-d149-4bd6-8164-8ca8d6223247" />

Step 7: Created an HTML File called `index.html` on my local computer using VSCode.

<img width="1180" alt="image" src="https://github.com/user-attachments/assets/0a1d208f-5660-4064-a104-7293377cf518" />

Step 8: Uploaded my HTML File from my Local Computer to my AWS Ubuntu server using SCP following the steps below:

1. Used the Syntax: `scp -i /path/to/your-key.pem /path/to/local-file.html ubuntu@<server-ip>:/path/to/destination/`

2. Edited the Synax on my computer: `scp -i ~/Documents/Altschool\ Training/linux/AltKey.pem ~/Documents/Altschool\ Training/linux/index.html ubuntu@18.175.111.255:/var/www/html/`

I got the error messages: 
	`scp: dest open "/var/www/html/index.html": Permission denied
	 scp: failed to upload file /Users/chukanwachukwu/Documents/Altschool Training/linux/index.html to /var/www/html/`
Needed to allow permissions to the Ubuntu user as it only allowed the root user.

3. Logged on to my server: `ssh -i AltKey.pem ubuntu@18.175.111.255`

4. Ran the commands to check and allow permission:
`ls -ld /var/www/html/
sudo chown -R ubuntu:www-data /var/www/html/
sudo chmod 755 /var/www/html/`

<img width="655" alt="image" src="https://github.com/user-attachments/assets/ed512bcf-a2cc-40ce-bce5-3f7ed37197d0" />

6. Ran the upload file again 
`scp -i ~/Documents/Altschool\ Training/linux/AltKey.pem ~/Documents/Altschool\ Training/linux/index.html ubuntu@18.175.111.255:/var/www/html/`

<img width="1224" alt="image" src="https://github.com/user-attachments/assets/cc15f337-15ab-4a80-b47e-56022ad62997" />

It Worked!

Step 9: Edit the HTML file with the command:
`Sudo nano /var/www/html/index.html`

<img width="1227" alt="image" src="https://github.com/user-attachments/assets/30a164b6-4e92-4f24-8d2d-dee98c40553f" />

Used `Control + X` to exit.
The page was successfully deployed to http://18.175.111.255/

<img width="1423" alt="image" src="https://github.com/user-attachments/assets/71fe505a-0ba4-4625-b86d-a282b189815a" />

Step 10:  Configured HTTPS for my web server following the below steps:

1. Installed Certbot for Apache with the command:
  `sudo apt install certbot python3-certbot-apache`

<img width="1206" alt="image" src="https://github.com/user-attachments/assets/d290c91a-90a7-40e3-b92a-4aa3fec6d8cc" />

3. Obtain and install Certificate using the command:
   `sudo certbot --apache`
   
<img width="763" alt="image" src="https://github.com/user-attachments/assets/c9574b3d-712f-4324-be75-67dc20cae85f" />

Couldn't continue because I did not have a domain name, need to get one. 

3. I activated my domain `chuhubspace.com` hosted on Azure and created a host `A` record with my IP Address `18.175.111.255`

Ran the command `sudo certbot --apache` and we successfully enabled HTTPS on my domain.

<img width="933" alt="image" src="https://github.com/user-attachments/assets/0ce8b7bb-9d6e-4e90-81d8-346a0061093f" />

Here is a screenshot of the results.


<img width="1437" alt="image" src="https://github.com/user-attachments/assets/0a42025b-ef85-414e-b304-324fe0a56e2c" />










