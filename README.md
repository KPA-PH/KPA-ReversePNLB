
# KPA-ReversePNLB

**KPA-ReversePNLB** or **(Reverse Proxy and Network Load Balancer)** - A forward proxy, often called a proxy, proxy server, or web proxy, is a server that sits in front of a group of client machines. When those computers request sites and services on the Internet, the proxy server intercepts those requests and then communicates with web servers on behalf of those clients, like a middleman.

A load balancer serves as the single point of contact for clients. The load balancer distributes incoming traffic across multiple targets.

Reverse Proxy and Network Load balancers are available on the market, like AWS, Asure, Goole, Etc. I am aware of it. However, some did not meet my needs, and also, it was expensive.

That's why I built my version. Then, I used it for my project to test it. After a few days, I implemented it in our company. We have been using it for days, and everything is as good as expected. 

Today, I am not worried about server downtime because I receive Email/SMS notifications if one of my servers has been down. I can check the server's health in real time as well.

> Note: On this version, I stopped the Email/SMS Notification. I am still encountering an issue.

## How to use it?

Download all files and save them to your preferred folder location. 

Then, open IIS, Site -> Add Website -> point to the folder location. 

Then, bind the IP with Port or use your Domain/Hostname.

> Note: Tested on Windows10/11 and Windows Server 2016/2019/2022

> **Available soon for Linux**


## Prerequisite

[Download .Net 8 runtime (Hosting Bundle)](https://dotnet.microsoft.com/en-us/download/dotnet/thank-you/runtime-aspnetcore-8.0.1-windows-hosting-bundle-installer "Dotnet 8")

# KPA-shMonitor

**SHMonitor** or **(Server Health Monitor)** is a software that runs in the background always to check all my servers' health and see if one has been down or gone offline. Then, it will update the ReverseProxy Load Balancer or remove all offline servers. Real-time

## How to use it?

Before you run the **(shMonitor.exe)**, you must set your **(config.json)** to enter your server IP addresses. 

## Sample config.json

```
{
    "bind_ip": "0.0.0.0",
    "port": 20032,
    "channel": "kpa-4b6f588b-d57b-4a93-8836-8c564f39e33c",
    "error_notify": {
        "emails": "talkme@mail.kpa.ph",
        "mobiles": "639605614295"
    },
    "servers": [
        {
            "name" : "Website Name",
            "health_check_time": 5,
            "addresses": [
                {
                    "server_name": "AWS-US Server",
                    "server_location": "EC2 | us-west-1",
                    "server_ip_address": "127.0.0.1",
                    "server_hostname": "http://127.0.0.1:8080"
                },
                {
                    "server_name": "AWS-SG Server",
                    "server_location": "EC2 | sg-asia-1",
                    "server_ip_address": "127.0.0.1",
                    "server_hostname": "http://127.0.0.1:8080"
                },
                {*** You can add more here. Remove when you use it. ***}
            ]
        }
    ]
}
```

- **bind_ip** and **port** - for web access
- **channel** - for socket channel, any string as long unique
- **error_notify** - for Email and SMS notification if something went wrong with the servers. However, this is not working at this moment.
- **servers** - for all servers to be load-balanced


# Contact me

- Email: talkme@mail.kpa.ph
- Mobile#: +63 960 561 4295

# Donate

GCash / Maya: +63 960 561 4295

[Paypal](https://paypal.me/kpa21 "Paypal")