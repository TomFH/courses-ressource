# INTRO

``` PowerShell

Install-WindowsFeature DNS -IncludeManagementTools

Get-DnsClientServerAddress

```

**DNS** stands for **Domain Name System**. A Domain Name is a human language representation of an IP address. An IP Address is what every computer on the internet uses to address itself when interacting with other computers, using a network protocol called TCP/IP. IP (v4) addresses look like a series of numbers and decimal points, such as 123.123.123.12.

When someone types in a domain name like _www.domain.com_, their browser communicates with a series of root domain name servers that act as a reference book, providing the IP address associated with that domain name. The browser then uses that IP to communicate directly to the server that the website is hosted on.

In this way, DNS acts as a middle-man, translating user requests into IP addresses. This is what allows people to connect to websites over the internet. Without DNS, people would be required to memorize and enter long IP addresses when connecting to other websites instead of just typing in the website’s name.


La commande « **Add-DnsServerPrimaryZone** » sert à créer une zone principale.

Créer une zone de recherche directe « **nticprof.com** »  en spécifiant le nom de fichier de zone « **nticprof.com.dns** » et en activant les mises à jour dynamiques sécurisées et non sécurisées.

``` PowerShell
Add-DnsServerPrimaryZone –Name nticprof.com –ZoneFile nticprof.com.dns –DynamicUpdate NonSecureAndSecure
```
