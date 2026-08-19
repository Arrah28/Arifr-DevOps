Website Deployment Learning Log

**1. What We Learned**
• DNS Resolution: We learned how Cloudflare connects a domain name to an EC2 instance's Public IP address.

• EC2 Networking: We identified that Security Groups in AWS are crucial firewalls that must explicitly allow inbound traffic on Port 80 (HTTP) and 443 (HTTPS).

• Nginx Basics: We practiced installing and managing a web server on Amazon Linux 2023.

• Troubleshooting 521 Errors: We learned that a 521 error from Cloudflare signifies that the origin server is reachable by DNS, but the web server itself is failing to respond to connection requests.


**2. Mistakes & How We Fixed Them**
• Mistake: Assuming the user data script successfully started Nginx.

  • Fix: Manually connected to the EC2 instance via EC2 Instance Connect and verified the status using `systemctl status nginx`.

• Mistake: Ignoring browser caching and automatic HTTPS enforcement.

  • Fix: Specifically tested using `http://` to bypass HSTS/HTTPS blocks and verified the server via its public IP (`44.201.65.109`).

• Mistake: Misunderstanding the 521 error cause.

  • Fix: Verified that the AWS Security Group rules were correct and that Nginx was actually active on the instance.



**3. Deployment Steps & Code Used**
1. Update and Install Nginx:

```

sudo dnf install -y nginx

```

2. Enable and Start Service:

```

sudo systemctl enable nginx

sudo systemctl start nginx

```

3. Verify Locally:

```

curl localhost

```



**4. Best Practices for Next Time**
• Verify Service Status: Always check if your web server is actually running (`systemctl status`) immediately after launch.

• Test via Public IP First: Before pointing a domain or enabling a proxy, test connectivity directly via the AWS Public IP address.

• Manage SSL Early: When using Cloudflare's proxy (orange cloud), ensure you have SSL/TLS settings configured correctly in the Cloudflare dashboard to prevent connection errors.

• Use `dnf` over `yum`: For Amazon Linux 2023, `dnf` is the preferred package manager.

