
# Linux Server Configuration Project

The purpose of this project is to deploy the previous Item Catalog project
on a Linux server with good security settings and running a web server serving
the Item Catalog application as a WSGI app

## Item Catalog Application

View the application page [here](http://104.248.138.105)

## Connecting to the Server

```
ssh grader@104.248.138.105 -p 2222 -i ~/.ssh/<generated key>
```

## Dependencies

```
pip install -r requeriments.txt
```

## Third Party Resources

### git

[Digital Ocean Turotial](https://www.digitalocean.com/community/tutorials/how-to-install-git-on-ubuntu-18-04-quickstart)

### Nginx

[Digital Ocean Tutorial](https://www.digitalocean.com/community/tutorials/how-to-install-nginx-on-ubuntu-18-04)

### PostgreSQL

[Digital Ocean Tutorial](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-postgresql-on-ubuntu-18-04)

### Serve Flask Applications with uWSGI and Nginx

[Digital Ocean Tutorial](https://www.digitalocean.com/community/tutorials/how-to-serve-flask-applications-with-uswgi-and-nginx-on-ubuntu-18-04)

## Configurations

### Change SSH port

Ran the following command:

```
sudo nano /etc/ssh/sshd_config
```

located the following line:

```
'# Port 22'
```

Removed the # and changed the port to 2222

### Disable remote root login

```
sudo nano /etc/ssh/sshd_config
```

Change '#PermitRootLogin yes' to PermitRootLogin no

### Disable Password Authentication on Server

```
sudo nano /etc/ssh/sshd_config
```

in the sshd_config file changed PasswordAuthentication Yes to:

```
PasswordAuthentication no
```

### Setup Firewall

Ran the following commands to allow all required ports to be open

```
sudo ufw default deny incoming
```

```
sudo ufw default allow outgoing
```

```
sudo ufw allow 2222/tcp
```

```
sudo ufw allow www
```

```
sudo ufw allow ntp
```

```
sudo ufw allow 'Nginx HTTP'
```

```
sudo ufw allow 'Nginx Full'
```



