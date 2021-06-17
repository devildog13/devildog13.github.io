# devildog13.github.io
                     
                     
    devildog13 = 'Chris Hunter :Scotland'



Chris's Learning path, Code and Guides. 



Here is the home of some of my code samples, learning content for programming etc.and loads -
of cool guides I've found online subjects include pentesting with Kali Linux and my learning 
path to code in Python, bash and Interesting Cyber Security Solutions, Vulns + new projects etc..

Most of the code n guides I've found online from Cyber-Security blogs and other
cool sites I have researched.. 

I will update as my  quest continues... 







Note:
     Credit will be given to the Authors/Owners of any code,posts or 
     Articles on my Blog page, with Author,links + web-page[s] 
       - After all, Credit where its due ! :)
                






Credit to https://awesome.re For great awsome wiki's, list's, guides and code. !!


# Awesome Penetration Testing [![Awesome](https://awesome.re/badge-flat2.svg)](https://awesome.re)


#
 Finding [Autonomous System (AS) Numbers](https://www.iana.org/assignments/as-numbers) will help us identify 
 netblocks belonging to an organisation which in-turn may lead to discovering services running on the hosts in the netblock.

*   Resolve the IP address of a given domain using `dig` or `host`

```
dig +short google.com


```


 Find ASN for IP Address using the 'curl' cmd line tool. [ apt-get install curl -y]
```
curl -s http://ip-api.com/json/1.1.1.1 | jq -r .as
```



 We can use WHOIS service or NSE scripts to identify all the netblocks that belong to the ASN number.

```
nmap --script targets-asn --script-args targets-asn.asn=15169
```


[ARIN WHOIS server] 	(https://www.arin.net/resources/services/whois_guide.html)

 A quick 'ARIN WHOIS server' search returns all the entries that has email address of a given domain name,
 which in this case is _icann.org._ We are extracting only the email addresses from the results, 
 Piped it into grep -E 'Regex + Uniq to sort results..		


```
whois -h whois.arin.net "e @ icann.org" | grep -E -o "\b[a-zA-Z0-9.-]+@[a-zA-Z0–9.-]+\.[a-zA-Z0–9.-]+\b" | uniq
```


Extracting email addresses from WHOIS by querying entries that contain email address of a specific domain. 
[https://cdn-images-1.medium.com/max/1600/1*oYGnT18lLtml0WUfGpACpA.png]



#  We can query [RADB WHOIS server] to return all the netblocks that belong to an Autonomous System Number(ASN)
                                                                        (http://www.radb.net/support/query1.php)
```
whois -h whois.radb.net -- '-i origin AS111111' | grep -Eo "([0-9.]+){4}/[0-9]+" | uniq

```

FINING the Autonomous System Number(ASN)}


 Listing all the netblocks under an ASN using a query against RADB WHOIS server

* We can query ARIN WHOIS server to return all POC, ASN, organizations, and end user customers for a given KEYWORD.

```
whois -h whois.arin.net "z wikimedia"

```

Nmap Examples     
-------------

Basic Nmap scanning examples, often used at the first stage of enumeration.

Command |	Description

'''
nmap -sP 10.0.0.0/24
'''

## Ping scans the network, listing machines that respond to ping.
```

nmap -p 1-65535 -sV -sS -T4 target
```


## Full TCP port scan using with service version detection - usually my first scan, I find T4 more accurate than T5 and still "pretty quick".
```

nmap -v -sS -A -T4 target

```

## Prints verbose output, runs stealth syn scan, T4 timing, OS and version detection + traceroute and scripts against target services.

```
nmap -v -sS -A -T5 target

```


## Prints verbose output, runs stealth syn scan, T5 timing, OS and version detection + traceroute and scripts against target services.

```
nmap -v -sV -O -sS -T5 target
```


# [Find web-servers]


nmap -Pn -p80 -oX logs/pb-port80scan.xml -oG logs/pb-port80scan.gnmap 216.163.128.20/20

#-> This scans 4096 IPs for any web servers (without pinging them) and saves the output in grepable and XML formats.
















