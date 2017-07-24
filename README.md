eZscanner
=========

Description
-----------
eZscanner is an open source automated eZpublish vulnerability scanner, that is capable of looking for most common vulnerabilities.
It allows automatic scanning of default paths, views, user related pages, along with [CVE-2012-1565](http://blog-oppida.blogspot.fr/2012/03/ezpublish-object-remote-full.html) (ezjscore information disclosure) and [CVE-2008-6844](https://www.exploit-db.com/exploits/7406/) (privilege escalation exploit).

This tools also detects any email or user:hashed password combination found using CVE-2008-6844 and transforms these in a hashcat usable format for easier cracking.

Usage
-----
eZscanner can be used to do the following:
* **Lazy** scanning: `python ezscanner.py -t [URL]`. This will automatically scan for:
  * default paths
  * user related pages
  * the first 200 first eZpublish views (and return their titles if they exist, as they may disclose information)
  * the first 300 eZjscore calls, and auto-increment if anything is found (CVE-2008-6844 vulnerability)

![lazy](https://s2.postimg.org/781dxh1ih/ezscanner_lazy.png)

* **Custom** scanning: disable default modules with `-nob` (or `--no-basics`) and pick the ones your want:
  * Bruteforce publicly accessible views `--bf-views [RANGE]`
  * Bruteforce eZjscore API (CVE-2012-1565) `--bf-ezjscore-range [RANGE]`
  * Try to register as admin (CVE-2008-6844) `--exploit-register 'username:password:email'`


Other options:
* Increase verbosity `-v`
* Save logs to [url].log `-l`
* Use a proxy `--proxy`
* Set cookies `--cookies` (example: cookie1=v1&cookie2=v2)
* Set timeout `--timeout` 

Requirements
------------
This script was designed to run with minimal requirements.
* python (2.7)
* requests module for python

Installation
------------
* Clone this repository
```
$ git clone https://github.com/ThmsLa/eZscanner.git
```
  
* Install the python requirements
```
$ pip install requests
```
  
Copyright and license
---------------------
All product names, logos, and brands are property of their respective owners.  
All resources published in eZscanner are free software: you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation, either version 3 of the License, or (at your option) any later version.
See the GNU General Public License for more details.
  
  
Contact
-------
* Thomas Labadie < thomas.labadie at wavestone d0t com >
