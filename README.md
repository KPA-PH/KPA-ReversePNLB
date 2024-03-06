
# KPA-ReversePNLB

**Reverse Proxy:** Also distributes traffic. However, it is primarily concerned with limiting and safeguarding server access. Or, it's hiding your Server IP Address.

**Load Balancer:** Concerned with distributing traffic/requests. Prevent bottlenecks, maximize throughput, and optimize resource consumption.

**shMonitor or Server Health Monitor:** continuously checks the server's health, then removes it from the load balancer list in real-time if it becomes offline. Gracefully.

Reverse Proxy and Network Load balancers are available on the market, like AWS, Asure, Goole, Etc. I am aware of it. However, some did not meet my needs, and also, it was expensive.

That's why I built my version. Then, I used it for my project to test it. After a few days, I implemented it in our company. We have been using it for days, and everything is as good as expected. 

I am not worried anymore about server downtime because I know I have a load balancer + server health monitor and can receive Email/SMS notifications if one of my servers has been down.

I can check the server's health in real time as well. Not to mention that I can do anything with my load balancer anytime I want.

> Note: On this version, I stopped the Email/SMS Notification. I am still encountering an issue.

## How to use it?

Download all files and save them to your preferred folder location. 

Then, open IIS, Site -> Add Website -> point to the folder location. 

Then, bind the IP with Port or use your Domain/Hostname.

> Please remember to set the permissions.

> Note: Tested on Windows 10/11 and Windows Server 2016/2019/2022. However, you can still add your server to the load balancer list/config, even if your website/app is from Linux/Nginx/Apache. Or run it using NPM/Node.

> **Available soon for Linux**

## Prerequisite

You must download and install the dotnet runtime. See the download link below:

[Download .Net 8 runtime (Hosting Bundle)](https://dotnet.microsoft.com/en-us/download/dotnet/thank-you/runtime-aspnetcore-8.0.1-windows-hosting-bundle-installer "Dotnet 8")

# KPA-shMonitor

## How to use it?

Before you run the **(shMonitor.exe)**, you must set your **(config.json)**. Enter your server IP addresses. See the sample below:

## Sample config.json

```
{
    "bind_ip": "0.0.0.0",
    "port": 20032,
    "channel": "ANY-STRING-UPDATE-ME",
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
                    "server_hostname": "http://127.0.0.1:8080",
                    "server_health_check": "http://127.0.0.1:8080/health"
                },
                {
                    "server_name": "AWS-SG Server",
                    "server_location": "EC2 | sg-asia-1",
                    "server_ip_address": "127.0.0.1",
                    "server_hostname": "http://127.0.0.1:8080",
                    "server_health_check": "http://127.0.0.1:8080/health"
                },
                {*** You can add more here. Remove this when you use it. ***}
            ]
        }
    ]
}
```

- **bind_ip** and **port** - for web access
- **channel** - for socket channel, any string as long unique
- **error_notify** - for Email and SMS notification if something went wrong with the servers. However, this is not working at this moment.
- **servers** - for all servers to be load-balanced
-- **name** - Any name
-- **health_check_time** - default 5 seconds
-- **addresses** - [
    -- **server_name** - server name
    -- **server_location** - server location
    -- **server_ip_address** - server ip
    -- **server_hostname** - http only
    -- **server_health_check** - http or https | You can create any path or any.html / *.extention. Be sure that the HTTP response is 200 code.
]

# Contact me

- Email: talkme@mail.kpa.ph
- Mobile#: +63 960 561 4295

# Donate

GCash / Maya: +63 960 561 4295

[Paypal](https://paypal.me/kpa21 "Paypal")