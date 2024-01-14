# SelfHostWebsite

## Overview
In this tutorial, I am going to tell you how I self-host [my website](https://tsaoching.work). It is fairly easy and straightforward, so do not feel intimidated and let's get it!

## Tools And Framework
First of all, I want to introduce the tools and framework I used, including
1. **Docker**
   - Using container just makes things so much easier. The isolation of container assures the program you run inside the container does not mess up with things outside. Also, you get to install packages without complicated set up.
3. **Wordpress**
   - It is a convenient framework allowing its users to create website at ease. If you want to write blog post like me regularly, it is good to have a framework providing you the GUI to write posts.
5. **Cloudflare Tunnel**
   - Self-hosting means exposing your service to the public to some extent, so having cloudflare filters incoming requests is a great idea. Though it is not perfect (nothing is perfect in this world haha), it can protect your device to a certain level.

## Process
### 1. Doman Name
In order to use domain name to find your website instead of your IP, you need to buy one from a domain registrar.
- If the domain name is bought from cloudflare, then you are done with this part.
- If not, you need to add cloudflare's nameserver to your domain regiestrar's nameserver. This is to tell your domain registrar to direct the incoming request to cloudflare so that cloudflare can filter out malicious connection and direct the request to your site. Usually, the registrar has a friendly GUI for you to set this up.
- To check if your nameserver is set up successfully, type `nslookup yourDomainName`. You may see something similar to the following
  ```
   Server:		127.0.0.53
   Address:	127.0.0.53#53
   
   Non-authoritative answer:
   Name:	tsaoching.work
   Address: 172.67.184.96   # This is the IP address of cloudflare's machine. Your IP is hidden!
   Name:	tsaoching.work
   Address: 104.21.19.8
   Name:	tsaoching.work
   Address: 2606:4700:3030::6815:1308
   Name:	tsaoching.work
   Address: 2606:4700:3031::ac43:b860

  ```
### 2. Docker
1. Go to [docker official page](https://docs.docker.com/engine/install/) to install docker, and go to [docker official page](https://docs.docker.com/compose/install/) to install docker compose.
2. Follow the instructions on the site to make sure you have installed docker successfully.
3. Git clone this repo, cd to this directory, and execute `docker compose up` to see if it works.
```
git clone "https://github.com/Rob12312368/SelfHostWebsite.git"
cd ./SelfHostWebsite 
docker compose up
```
4. If it works, congrats! You now have two containers running. One is the wordpress container for you to build your website, and the other is mysql database for wordpress to interact with.

### 3. WordPress
(to be continued)
