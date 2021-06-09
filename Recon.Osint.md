


Credit to https://awesome.re For great awsome wiki's, list's, guides and code. !!


# Awesome Penetration Testing [![Awesome](https://awesome.re/badge-flat2.svg)](https://awesome.re)


#
 Finding [Autonomous System (AS) Numbers](https://www.iana.org/assignments/as-numbers) will help us identify 
 netblocks belonging to an organisation which in-turn may lead to discovering services running on the hosts in the netblock.

*   Resolve the IP address of a given domain using `dig` or `host`

```
dig +short google.com

```


$ Find ASN for IP Address using the 'curl' cmd line tool. [ apt-get install curl -y]

curl -s http://ip-api.com/json/1.1.1.1 | jq -r .as




We can use WHOIS service or NSE scripts to identify all the netblocks that belong to the ASN number.

```
nmap --script targets-asn --script-args targets-asn.asn=15169
```

[ARIN WHOIS server] 	(https://www.arin.net/resources/services/whois_guide.html)

* A quick 'ARIN WHOIS server' search returns all the entries that has email address of a given domain name,
 which in this case is _icann.org._ We are extracting only the email addresses from the results, 
 Piped it into grep -E 'Regex + Uniq to sort results..		


```
whois -h whois.arin.net "e @ icann.org" | grep -E -o "\b[a-zA-Z0-9.-]+@[a-zA-Z0–9.-]+\.[a-zA-Z0–9.-]+\b" | uniq
```


Extracting email addresses from WHOIS by querying entries that contain email address of a specific domain. 
[https://cdn-images-1.medium.com/max/1600/1*oYGnT18lLtml0WUfGpACpA.png]


*   We can query [RADB WHOIS server](http://www.radb.net/support/query1.php) to return all the netblocks that belong to an Autonomous System Number(ASN)

```
whois -h whois.radb.net -- '-i origin AS111111' | grep -Eo "([0-9.]+){4}/[0-9]+" | uniq





