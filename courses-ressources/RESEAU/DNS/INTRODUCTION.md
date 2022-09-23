# INTRODUCTION

**DNS** stands for **Domain Name System**. A Domain Name is a human language representation of an IP address. An IP Address is what every computer on the internet uses to address itself when interacting with other computers, using a network protocol called TCP/IP. IP (v4) addresses look like a series of numbers and decimal points, such as 123.123.123.12.

When someone types in a domain name like _www.domain.com_, their browser communicates with a series of root domain name servers that act as a reference book, providing the IP address associated with that domain name. The browser then uses that IP to communicate directly to the server that the website is hosted on.

In this way, DNS acts as a middle-man, translating user requests into IP addresses. This is what allows people to connect to websites over the internet. Without DNS, people would be required to memorize and enter long IP addresses when connecting to other websites instead of just typing in the website’s name.

# How Does DNS Work?

In a usual DNS query, the URL typed in by the user has to go through four servers for the IP address to be provided. The four servers work with each other to get the correct IP address to the client, and they include:

1.  **DNS recursor**: The DNS recursor, which is also referred to as a DNS resolver, receives the query from the DNS client. Then it communicates with other DNS servers to find the right IP address. After the resolver retrieves the request from the client, the resolver acts like a client itself. As it does this, it makes queries that get sent to the other three DNS servers: root nameservers, top-level domain (TLD) nameservers, and authoritative nameservers.
2.  **Root nameservers**: The root nameserver is designated for the internet's DNS root zone. Its job is to answer requests sent to it for records in the root zone. It answers requests by sending back a list of the authoritative nameservers that go with the correct TLD.
3.  **TLD nameservers**: A TLD nameserver keeps the IP address of the second-level domain contained within the TLD name. It then releases the website’s IP address and sends the query to the domain’s nameserver.
4.  **Authoritative nameservers**: An authoritative nameserver is what gives you the real answer to your DNS query. There are two types of authoritative nameservers: a master server or primary nameserver and a slave server or secondary nameserver. The master server keeps the original copies of the zone records, while the slave server is an exact copy of the master server. It shares the DNS server load and acts as a backup if the master server fails.

### Authoritative DNS Server

To use the phone book analogy, think of the IP address as the phone number and the person’s name as the website’s URL. Authoritative DNS servers have a copy of the “phone book” that connects these IP addresses with their corresponding domain names. They provide answers to the queries sent by recursive DNS nameservers, providing information on where to find specific websites. The answers provided have the IP addresses of the domains involved in the query.

Authoritative DNS servers are responsible for specific regions, such as a country, an organization, or a local area. Regardless of which region is covered, an authoritative DNS server does two important jobs. First, the server keeps lists of domain names and the IP addresses that go with them. Next, the server responds to requests from the recursive DNS server regarding the IP address that corresponds with a domain name. 

Once the recursive DNS server gets the answer, it sends that information back to the computer that requested it. The computer then uses that information to connect to the IP address, and the user gets to see the website.

### Recursive DNS Server

After a user types in a URL in their web browser, that URL is given to the recursive DNS server. The recursive DNS server then examines its cache memory to see whether the IP address for the URL is already stored. If the IP address information already exists, the recursive DNS server will send the IP address to the browser. The user is then able to see the website for which they typed in the URL.

On the other hand, if the recursive DNS server does not find the IP address when it searches its memory, it will proceed through the process of getting the IP address for the user. The recursive DNS server's next step is to store the IP address for a specific amount of time. This period of time is defined by the person who owns the domain using a setting referred to as time to live (TTL).

# DNS TERMINOLOGY

The following is a list of important terms and concepts related to the Domain Name System.

-   **TLD (Top Level Domain)** – the TLD is the last part of a domain name, such as .com, .net, .org, a two letter country domain, or one of several other TLDs out there.  
     
-   **SLD (Second Level Domain)** – the SLD is the most human readable part of the domain name. In a domain name _like www.domain.com_, “_domain_” is the SLD. An SLD can contain any alphanumeric character in it (a-z, 0-9), dashes or minuses ( – ), or underscores ( _ ), but it cannot have spaces between characters.  
     
-   **Sub-Domain (Third Level Domain)** –  sub-domains are technically called Canonical Domains (or CNAMEs) for short. A sub-domain is like having an extra domain name and can be almost anything you like. In a domain name like _www.subdomain.domain.com_, “_subdomain_” is the sub-domain. Other than that, it works the same as a regular domain name.  
     
-   **Addon Domain** – an addon domain is a separate domain, hosted on your primary domain and controlled through the same control panel, which appears to visitors as a completely separate website. Addon domains allow site owners to host multiple websites without requiring separate control panels for each. To use addon domains, you must have registered domain names for each and they should all use the same name servers as your primary domain.  
      
-   **Parked Domain**  – a parked domain is a secondary domain name that points to your primary domain. These domains display the same website as your primary domains and do not have separate web statistics, but can have their own email boxes.  
       
    For example, if you’re the owner of mywebsite.net, you can purchase mywebsite.com and set it up as a parked domain. In this example, should a user then search for your website with the “.com” instead of the “.net”, your parked domain would show them the same content as if they had gone to your primary domain.  
      
-   **A-Records (Address Records)** – A-records are the most important part of a DNS record. A-records point to a specific IP address. Your short domain name (without the www), NS, and FTP should all have A-records. Subdomains sometimes have A-records too. An A-record can point to any IP-address.  
     
-   **CNAME-Records (Canonical Domain Records)** – CNAMEs include subdomains and Aliases, and are used to point to a domain name or to a file within a domain. However, CNAMEs should always point to an A-record, not another CNAME. It is a common practice to create a CNAME for www and for subdomains that are actually hosted by your domain. CNAMES can also be used as temporary aliases to point your domain to another domain.  
        
    ***Note:** when pointing a CNAME, always put a period after the domain (ie: ftp -> CNAME -> domain.com.)  
     
-   **MX-Records (Mail Exchange Records)** – MX-records point to the name of an email server and hold a priority number for that server. MX-records must point to an A-record or in some situations an IP-address.  
       
    For more information on MX-records, check out our guide on [Configuring an MX Record](https://www.hivelocity.net/kb/how-to-configure-an-mx-record/).  
     
-   **PTR Record (Reverse DNS Record)** – A PTR record is a reverse mapping from IP to name. For instance, when a lookup is made on the IP of _1.2.3.4_, it should come back with _host.mydomain.com_. It is a very good idea to have the hostname of your server match the PTR record assigned to it’s IP. This can only be changed by the owner of the IP address.  
     
-   **DNS Cluster** – A DNS cluster is a network of nameservers that share records between each other. This allows for a greater degree of physical separation between servers without sacrificing DNS functionality. When established correctly, it can even allow visitors faster access to a website by provided multiple outlets for processing DNS requests.  
       
    For more information on DNS Clusters, check out our guide on [Setting DNS Clusters in WHM](https://www.hivelocity.net/kb/setting-dns-clusters-in-whm/).  
     
-   **Round Robin DNS** – Round robin DNS is a method by which a DNS record has more than one value. The result is, when a request is made to the DNS server which serves this record, the answer given alternates for each request. For instance, if you had two webservers that you wished to distribute requests between, you could set up your DNS zone like this:  
       
    **www   IN   A   1.2.3.4**
    
    **IN   A    2.3.4.5**  
       
    In this instance, when a query is made to the DNS server, it will first give the IP of 1.2.3.4 for the www host. However, the next time a request is made for the IP of www, it will serve 2.3.4.5. This process will alternate back and forth for each subsequent query.
    
    While a round robin DNS setup allows for greater load balancing, it should be noted that if one of the hosts becomes unavailable, the DNS server will not know this. Should this happen, the DNS will continue to alternate giving out the IP of the downed server.

# All About the DNS Zone File

DNS zone files are defined in [RFC 1035](https://tools.ietf.org/html/rfc1035) and [RFC 1034](https://tools.ietf.org/html/rfc1034). A zone file contains mappings between domain names, IP addresses and other resources, organized in the form of resource records (RR).

To see the actual zone file for a domain, and test DNS zone transfers, you can perform a zone file lookup using one of many DNS tools.

## DNS Zone Types

There are two types of zone files:

-   A DNS Primary File which authoritatively describes a zone
-   A DNS Cache File which lists the contents of a DNS cache—this is only a copy of the authoritative DNS zone

## DNS Zone Records

In a zone file, each line represents a DNS resource record (RR). A record is made up of the following fields:

name

ttl

record class

record type

record data

-   **Name** is an alphanumeric identifier of the DNS record. It can be left blank, and inherits its value from the previous record.
-   **TTL (time to live)** specifies how long the record should be kept in the local cache of a DNS client. If not specified, the global TTL value at the top of the zone file is used.
-   **Record class** indicates the namespace—typically IN, which is the Internet namespace.
-   **Record type** is the DNS record type—for example an A record maps a hostname to an IPv4 address, and a CNAME is an alias which points a hostname to another hostname.
-   **Record data** has one or more information elements, depending on the record type, separated by a white space. For example an MX record has two elements—a priority and a domain name for an email server.

## Zone File Structure

DNS Zone files start with two mandatory records:

-   **Global Time to Live (TTL)**, which specifies for how records should be kept in local DNS cache.
-   **Start of Authority (SOA) record**—specifies the primary authoritative name server for the DNS Zone.

After these two records, the zone file can contain any number of resource records, which can include:

-   **Name Server records (NS)—**specifies that a specific DNS Zone, such as “example.com” is delegated to a specific authoritative name server
-   **IPv4 Address Mapping records (A)—**a hostname and its IPv4 address.
-   **IPv6 Address records (AAAA)—**a hostname and its IPv6 address.
-   **Canonical Name records (CNAME)—**points a hostname to an alias. This is another hostname, which the DNS client is redirected to
-   **Mail exchanger record (MX)—**specifies an SMTP email server for the domain.

## Zone File Tips

-   When adding a record for a hostname, the hostname must end with a period (.)
-   Hostnames which do not end with a period are considered relative to the main domain name—for example, when specifying a "www" or “ftp” record, there is no need for a period.
-   You can add comments in a zone file by adding a semicolon (;) after a resource record.

# **Preliminary Requirements for DNS Configuration** 

Before you can configure your DNS, you’ll need to gather some basic information. Some of these requirements must be pre-approved by InterNIC for use on the Internet. If you’re configuring your server for internal use only, you can decide which names and IP addresses to use yourself.

To start, you must have the following information:

-   Your domain name (approved by InterNIC)  
     
-   The IP address and host name of each server that you want to provide name resolution for

***Note:** Your servers may include mail servers, public access servers, FTP servers, WWW servers, and others.

Additionally, before you can configure your computer as a DNS, you’ll need to verify that the following conditions are true:

-   First, you’ll need to ensure that your operating system is configured correctly. In the Windows Server 2003 family, the DNS service relies on the correct configuration of the operating system and its services, such as TCP/IP. If you have a new installation of a Windows Server 2003 operating system, you can use the default service settings, removing the need to take additional action.  
     
-   Next, make sure you’ve allocated all the available disk space.  
     
-   Lastly, check that all existing disk volumes use the NTFS file system. FAT32 volumes are not secure, and do not support file and folder compression, disk quotas, file encryption, or individual file permissions.