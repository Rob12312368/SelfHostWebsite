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
###. Docker
     1. Go to [docker official page](https://docs.docker.com/engine/install/) to install docker, and go to [docker official page](https://docs.docker.com/compose/install/) to install docker compose.
     2. Follow the instructions on the site to make sure you have installed docker successfully.
     3. Git clone this repo, cd to this directory, and execute `docker compose up` to see if it works.
     ```
     git clone "https://github.com/Rob12312368/SelfHostWebsite.git"
     cd ./SelfHostWebsite 
     docker compose up
     ```
    4. If it works, congrats! You now have two containers running. One is the wordpress container for you to build your website, and the other is mysql database for wordpress to interact with.
