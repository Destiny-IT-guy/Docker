# docker images

For a college project we had to make a k3s clusters with multiple different services like prometheus, grafana, GLPI and grafana. During the class I got stressed and kind of forgot I knew how to use docker so I searched online for images of every service. The project was successful but there was a small problem. The last part was to use a security tool to scan for vulnerabilities and fix them. Since the images weren't mines I had to do so much research to fix them. The security tools was trivy cause it was free. But This time I wanted to try and make all of my images myself and maybe later ill do a trivy scan and show you how to fix vulnerabilities but today ill show you some of the images I made.

## Grafana

I assume you all know how to use docker but before we start you must have docker and docker compose installed. Also every will ubuntu cause I am used to the OS. This is an images of my file

![alt text](images/grafana-file.png)
The link at the bottom of the file is a a guide to install grafana on ubuntu. I just modified some part to make it work in docker.<br> I will make an image named grafana<br><br>

![alt text](images/grafana-images.png)
The dockerfile name is test1 and the image in my local docker is grafana.<br> Now I will just run the command to make a container and show you the functional grafana.<br>

![alt text](images/grafana-container.png)<br><br>
![alt text](images/grafana1.png)<br> enter admin and admin for both <br><br>
![alt text](images/grafana2.png)<br><br>
![alt text](images/grafana3.png)
This should prove our image works.

## prometheus

This one is harder I couldn't just follow a guide like grafana cause there are some commands like systemd that doesn't work in docker so it looks a little different but I tried to make it a simple as possible.

![alt text](images/prometheus%20file.png)

![alt text](images/prometheus1.png)

![alt text](images/prometheus2.png)

# mysql and glpi

This part is a little easier but first I will show the glpi file then I will show you my docker compose file. The mysql file you can just take from the official site to make it easier but let me show you how I did it.

![alt text](images/glpi%20file.png)

![alt text](images/glpi%20images.png)

![alt text](images/dockercompose.png)
This is my docker compose file where I will make my 2 containers for both services

![alt text](images/mysql.png)
This is a file where I make my user for my database. I am pretty sure you can make it in the dockercompse file but ill stick with what I did.

![alt text](images/dockercomposef.png)
I just made my 2 containers for each services

![alt text](images/glpi.png)
When I go on the correct port I should see something like this

![alt text](images/glpi2.png)
Here I enter the information of my database like the ip and port the user glpi and its password

![alt text](images/glpi4.png)
And then there is glpi that is connected to a external database. The main login is glpi and glpi.

In the future I want to use at least the glpi grafana and maybe prometheus images for my kubernetes cluster.

### save the images
To save these images I uses this dockersave command to save each image

```bash
docker save -o glpitest.tar glpitest
docker save -o prome.tar prome
docker save -o grafana.tar grafana
docker save -o mysql.tar mysql:8.0
```
