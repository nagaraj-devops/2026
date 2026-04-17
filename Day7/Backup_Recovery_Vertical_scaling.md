# Backup and Recovery by manual
# Instance type
# Vertical scaling



## user_date / shell script
```
#!/bin/bash
yum update -y
yum install -y httpd.x86_64
systemctl start httpd.service
systemctl enable httpd.service
echo “HIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIII” > /var/www/html/index.html
```
