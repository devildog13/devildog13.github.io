




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
