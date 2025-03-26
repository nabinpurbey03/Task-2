# Task2 : Writing an Ansible playbook (Manual Process):
*Automated script is given below at last*
## 1. Launching an EC2 instance using any AMI of my desire 
- launched ubuntu server on my VMware
- updated System using
<pre>sudo apt update</pre>
- nginx already installed, verified using
<pre>nginx -v</pre>
- configured the default nginx fiel
<pre>
server {
    listen 80;
    server_name _;

    location /page1 {
        root /var/www/task1;
        index index.html;
    }

    location /page2 {
        root /var/www/task2;
        index index.html;
    }
}
</pre>

- Created a file using
<pre>
sudo mkdir var/www/task1/index.html
sudo mkdir var/www/task2/index.html
</pre>

- Enabling ssl certificate via nginx default
<pre>
server {
    listen 443 ssl;
    server_name nabinpuybey.com.np;

    ssl_certificate /etc/letsencrypt/live/nabinpuybey.com.np/fullchain.pem;
    ssl_certificate_key /etc/letsencrypt/live/nabinpuybey.com.np/privkey.pem;

    location / {
        root /var/www/task1;
        index index.html;
    }
}

server {
    listen 80;
    server_name nabinpuybey.com.np;
    return 301 https://$host$request_uri;
}
</pre>
