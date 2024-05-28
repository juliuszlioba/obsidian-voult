### Full list of articles
[Getting Started With Cloud Computing](https://www.digitalocean.com/community/tutorial_series/getting-started-with-cloud-computing)
### Individual articles
[Set Up a Firewall with UFW](https://www.digitalocean.com/community/tutorials/how-to-set-up-a-firewall-with-ufw-on-ubuntu-22-04)
[Install Nginx](https://www.digitalocean.com/community/tutorials/how-to-install-nginx-on-ubuntu-22-04)
[Secure Nginx with Let's Encrypt](https://www.digitalocean.com/community/tutorials/how-to-secure-nginx-with-let-s-encrypt-on-ubuntu-22-04)

Solution to problem when apt-get update gets error:
```
sudo cp /etc/resolv.conf /etc/resolv.conf-2023-06-06  
echo "nameserver 8.8.8.8" | sudo tee /etc/resolv.conf > /dev/null  
sudo apt update
```