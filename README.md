# Cloud Networking & Web Server Deployment Project

## What I Built
A live, cloud-hosted web server using Amazon EC2 running NGINX, accessible over the public internet via a custom domain name configured with custom DNS A records.

## What I Learnt
* **Networking Foundations:** Gained hands-on experience with IP addressing, DNS record propagation, and traffic routing.
* **Cloud Infrastructure:** Provisioned AWS EC2 instances and managed security groups to control inbound/outbound traffic.
* **Linux System Administration:** Utilized package managers (`yum`/`apt`) to install, enable, and start web services via the command line.

## Commands Used
```bash
# Update and install NGINX on Linux
sudo yum install -y nginx
sudo systemctl enable nginx
sudo systemctl start nginx
```

## Challenges & Solutions
Challenge: Port 80 access blocked by default security group rules.
Solution: Configured custom AWS Security Group inbound rules to explicitly allow HTTP traffic on port 80 from anywhere (0.0.0.0/0).

