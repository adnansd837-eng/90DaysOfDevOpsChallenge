
# Day 08 – Cloud Server Setup: Docker, Nginx & Web Deployment

## Objective

Today I launched a cloud server, connected to it using SSH, installed Docker and Nginx, configured the firewall, and checked that the website was accessible from the internet. I also viewed and saved the Nginx logs.

---

# Step 1: Launch Cloud Instance

I created an Ubuntu EC2 instance on AWS.

* OS: Ubuntu 24.04 LTS
* Instance Type: t2.micro (Free Tier)
* Authentication: Key Pair (.pem file)

After launching the instance, I copied the public IP address.

---

# Step 2: Connect to Server using SSH

### Command

```bash
ssh -i my-key.pem ubuntu@<Public-IP>
```

### What happened?

I successfully logged into my cloud server and started working from the terminal.

---

# Step 3: Update the Server

### Commands

```bash
sudo apt update
sudo apt upgrade -y
```

### Why?

I updated the package list and installed the latest security updates before installing any software.

---

# Step 4: Install Docker

### Commands

```bash
sudo apt install docker.io -y
sudo systemctl start docker
sudo systemctl enable docker
```

### Verify Docker

```bash
docker --version
sudo systemctl status docker
```

### What I learned

Docker allows me to run applications inside containers without installing everything directly on the server.

---

# Step 5: Install Nginx

### Commands

```bash
sudo apt install nginx -y
sudo systemctl start nginx
sudo systemctl enable nginx
```

### Verify Nginx

```bash
sudo systemctl status nginx
```

The service showed **active (running)**.

---

# Step 6: Configure Security Group

I added an inbound rule for:

* HTTP (Port 80)
* Source: Anywhere (0.0.0.0/0)

Then I opened:

```text
http://<Public-IP>
```

I saw the **Welcome to Nginx** page.

---

# Step 7: View Nginx Logs

### Check Logs

```bash
sudo cat /var/log/nginx/access.log
```

or

```bash
sudo tail -20 /var/log/nginx/access.log
```

### Save Logs

```bash
sudo cp /var/log/nginx/access.log ~/nginx-logs.txt
```

### Download to Local Machine

```bash
scp -i my-key.pem ubuntu@<Public-IP>:~/nginx-logs.txt .
```

---

# Commands Used

```bash
ssh -i my-key.pem ubuntu@<Public-IP>

sudo apt update
sudo apt upgrade -y

sudo apt install docker.io -y
docker --version
sudo systemctl start docker
sudo systemctl enable docker

sudo apt install nginx -y
sudo systemctl start nginx
sudo systemctl enable nginx
sudo systemctl status nginx

sudo cat /var/log/nginx/access.log
sudo tail -20 /var/log/nginx/access.log

sudo cp /var/log/nginx/access.log ~/nginx-logs.txt

scp -i my-key.pem ubuntu@<Public-IP>:~/nginx-logs.txt .
```

---

# Challenges Faced

* At first, I couldn't open the Nginx webpage because port **80** was not allowed in the Security Group.
* After adding the HTTP inbound rule, the webpage loaded successfully.
* I also learned that services must be running before checking them in the browser.

---

# What I Learned

* How to launch an Ubuntu cloud server.
* How to connect to a remote server using SSH.
* How to install and manage Docker.
* How to install and start the Nginx web server.
* How to configure Security Groups for web access.
* How to check and save Nginx log files.
* Basic cloud server management and troubleshooting.

---


