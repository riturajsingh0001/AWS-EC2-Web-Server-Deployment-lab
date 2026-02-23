You are required to deploy a basic web server using AWS EC2.
Perform the following tasks:
1.	Launch an EC2 instance using Amazon Linux.
2.	Configure the security group to allow:
o	SSH (22)
o	HTTP (80)
3.	Connect to the instance using SSH.
4.	Install Apache web server.
5.	Create a webpage that displays:
o	Your Name
o	Student ID
6.	Access the webpage from a browser.
7.	Demonstrate it to the examiner.

Answer:
STEP 1: Login to AWS
1.	Go to https://aws.amazon.com
2.	Click Sign In to Console
3.	Enter your credentials
4.	In the search bar, type EC2
5.	Click EC2
________________________________________
STEP 2: Launch EC2 Instance
1. Click "Launch Instance"
2. Name Your Instance
Enter:
WebServer-Practical
3. Choose Amazon Machine Image (AMI)
Select:
Amazon Linux 2 AMI
4. Choose Instance Type
Select:
t2.micro (Free Tier Eligible)
5. Create Key Pair
Under Key Pair:
1.	Click Create new key pair
2.	Name: webserver-key
3.	Key pair type: RSA
4.	File format: .pem
5.	Click Create Key Pair
IMPORTANT:
The key will download automatically. Save it safely. You cannot download it again.
6. Configure Security Group (Firewall)
Under Network Settings, click Edit and add:
Add Rule 1 (SSH)
•	Type: SSH
•	Port: 22
•	Source: My IP
Add Rule 2 (HTTP)
•	Type: HTTP
•	Port: 80
•	Source: Anywhere
7. Click "Launch Instance"
Wait until instance state shows:
Running
________________________________________
STEP 3: Connect to EC2 Using SSH
1.	Select your instance
2.	Click Connect
3.	Copy the SSH command provided
For Windows (Git Bash / PowerShell)
Navigate to folder where key is downloaded:
cd Downloads
Change permission:
chmod 400 webserver-key.pem
Connect using:
ssh -i webserver-key.pem ec2-user@your-public-ip
Replace your-public-ip with actual Public IPv4 address.
Type:
yes
when prompted.
You are now connected to the server.
________________________________________
STEP 4: Install Apache Web Server
Run the following commands:
sudo yum update -y
sudo yum install httpd -y
Start Apache:
sudo systemctl start httpd
Enable Apache at boot:
sudo systemctl enable httpd
________________________________________
STEP 5: Create Webpage
Go to web directory:
cd /var/www/html
Create file:
sudo nano index.html
Add the following content:
Save and exit:
CTRL + X
Press Y
Press Enter
________________________________________
STEP 6: Access Website in Browser
1.	Go to AWS Console → EC2 → Instances
2.	Copy the Public IPv4 address
3.	Open browser and type:
http://your-public-ip
Example:
http://3.110.45.120
Your webpage should now be visible.
________________________________________
STEP 7: Demonstrate to Examiner
Show the following:
•	Running EC2 instance
•	Security Group rules (Port 22 and 80 open)
•	Successful SSH connection
•	Apache service running
•	Website accessible in browser
•	Your Name and Student ID displayed
________________________________________
COMMON ERRORS & SOLUTIONS
Problem: Website not loading
Solution: Check if HTTP (Port 80) is allowed in Security Group
Problem: SSH connection refused
Solution: Check if SSH (Port 22) is allowed
Problem: Permission denied for key
Solution: Run chmod 400 on key file
Problem: Apache not working
Solution: Restart Apache
sudo systemctl restart httpd
________________________________________
IMPORTANT: After practical
To avoid charges:
Go to EC2 → Instances → Select instance → Click Terminate
________________________________________

## Detail Report Uploaded in PDF format

