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
### 1. Domain Name
In order to use a domain name to find your website instead of your IP, you need to buy one from a domain registrar.
- If the domain name is bought from cloudflare, then you can skip to nslookup.
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
3. Git clone this repo, cd to this directory, and execute `docker compose up`.
```
git clone "https://github.com/Rob12312368/SelfHostWebsite.git"
cd ./SelfHostWebsite 
docker compose up
```
4. If it works, congrats! You now have two containers running. One is the wordpress container for you to build your website, and the other one is the mysql database for wordpress to interact with.
5. If you are confused with the ports, how containers interact, etc. I created an illustration for your reference. Hope this helps you understand what we have done so far.
![image](https://github.com/Rob12312368/SelfHostWebsite/assets/56261402/502aa2e8-5841-49e6-ab9d-62eabc184b4c)

   

### 3. WordPress
1. Access your website by typing **localhost:8080** on your browswer.
2. After you log into your wordpress account, go to settings.
3. Because we want to enforce https for the site, you need to change the *WordPress Address* and *Site Address* from whatever it was to **https://yourDomainName**  
![image](https://github.com/Rob12312368/SelfHostWebsite/assets/56261402/7c70650f-e86f-496e-83ec-7ad12c7e8c18)

### 4. Cloudflare
1. Sign up a cloudflare account at [cloudflare tunnel page](https://www.cloudflare.com/products/tunnel/), and go to [select account page](https://one.dash.cloudflare.com/?to=/:account/access/tunnels) to select an account for creating the tunnel.
2. You will see a dashboard, and there is a small button called **add tunnel**
   ![image](https://github.com/Rob12312368/SelfHostWebsite/assets/56261402/fa7450a2-797b-44ea-80f0-13865ca0559a)
3. Then, name your tunnel.
   ![image](https://github.com/Rob12312368/SelfHostWebsite/assets/56261402/0669239c-f22b-4697-8818-efe457de46d4)
4. Copy the command and execute to start your container for the tunnel.
   ![image](https://github.com/Rob12312368/SelfHostWebsite/assets/56261402/a670c3e6-7f6e-412b-8d5f-ab91a8778adb)
5. At last (most important one), set your public host name and service.
   - The public host name is to tell cloudflare what url to get access to your lan(local area network).
     1. Therefore, you can leave **Subdomain** and **Path** blank in this tutorial.
     2. For **Domain**, choose the one you set up earlier. For me, it is tsaoching.work.
   - The service is to tell cloudflare where your service is in a lan, including the private ip and port number.
     1. For **Type**, we choose HTTP because wordpress uses that protocol on default.
     2. URL is your private ip and port number in this format "ip:port". In this tutorial, since we open wordpress service on 8080, it is "ip:8080".
     3. To find your private ip, you can type `ip address`, and look for a line starting with **inet ...**. The address right after is your private ip. Usually, your private ip may change from time to time, so you need to set up ip reservation on your router.
![image](https://github.com/Rob12312368/SelfHostWebsite/assets/56261402/2ef9b550-fb55-423d-aa11-122800a627aa)

### 5. DONE!!!
Now you should be able to view your page through your domain name. If you have any questions, leave a comment under the blog post.



