# Networks

Définir en amont la configuration dhcp

[![](https://neptunet.fr/wp-content/uploads/2019/10/tableau-DHCP-full.png)](https://neptunet.fr/wp-content/uploads/2019/10/tableau-DHCP-full.png)


``` Powershell
Get-NetAdapterBinding -ComponentID ms_tcpip6

Disable-NetAdapterBinding -Name "Ethernet" -ComponentID ms_tcpip6

```

``` Powershell
Remove-NetIPAddress –InterfaceIndex 6 –IPAddress 192.168.100.14 –PrefixLength 24

New-NetIPAddress –InterfaceIndex 6 –IPAddress 192.168.100.13 –PrefixLength 24 –DefaultGateway 192.168.100.1

Set-NetIPInterface -InterfaceIndex 6 -Dhcp {Enabled/Disabled}
```