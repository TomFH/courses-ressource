# INSTALLATION

``` powershell
Install-WindowsFeature DHCP -IncludeManagementTools

Add-DhcpServerSecurityGroup

```

# CONFIGURATION

![[Pasted image 20220923094132.png]]

- Get-DhcpServerv4Scope : Lister les étendues DHCP  
- Add-DhcpServerv4Scope : Créer une étendue DHCP  
- Remove-DhcpServerv4Scope : Supprimer une étendue DHCP  
- Set-DhcpServerv4OptionDefinition : Configurer les options (DNS Passerelle, nom de domaine)  
- Get-Command *Dhcp* : Lister les commandes DHCP supplémentaires (pour avoir d'autres commandes sympa comme Add-DhcpServerv4ExclusionRange )

## CONFIGURATION DE L'ETENDU

On va **créer une étendue appelée “LAN“** qui distribuera la plage d’adresse allant de _10.0.10.1 à 10.0.10.200_ et on va **activer cette étendue** :

``` PowerShell
Add-DhcpServerv4Scope -Name "LAN" -StartRange 10.0.10.1 -EndRange 10.0.10.200 -SubnetMask 255.255.255.0 -State Active
```

Ensuite, on va mettre en place une **plage d’exclusion sur l’étendue** pour notre réseau _10.0.10.0_ :

``` PowerShell
Add-DhcpServerv4ExclusionRange -ScopeID 10.0.10.0 -StartRange 10.0.10.1 -EndRange 10.0.10.20
```

On va spécifier que pour cette étendue, on aura une **option Routeur** (_option numéro 3_) avec pour valeur, l’**adresse IP de la passerelle** :

``` PowerShell
Set-DhcpServerv4OptionValue -ScopeID 10.0.10.0 -OptionID 3 -Value 10.0.10.1
```

Et enfin on ajoute une **option de serveur**, l’option **Serveur DNS** :

``` PowerShell
Set-DhcpServerv4OptionValue -DnsServer 10.0.10.11
```

**Attention, en PowerShell, le serveur DNS doit être accessible ou cette étape ne passe pas contrairement au mode graphique !**

On peut ajoute une **réservation pour l’imprimante** réseau du service :

``` PowerShell
Add-DhcpServerv4Reservation -ScopeId 10.0.10.0 -IPAddress 10.0.10.1 -ClientId "00-15-5D-17-94-01" -Name "ROUTER" -Description "Routeur pfsense"
```

## VERIFICATION

Petit tour d’horizon de quelques **commandes utiles pour contrôler son DHCP** en PowerShell.

Vérifier une **étendue** :

``` PowerShell
Get-DhcpServerv4Scope -ScopeID 192.168.10.0
```

[![](https://neptunet.fr/wp-content/uploads/2019/10/dhcp-pws9.png)](https://neptunet.fr/wp-content/uploads/2019/10/dhcp-pws9.png)

Vérifier les **plages d’exclusions d’une étendue** :

```  PowerShell
Get-DhcpServerv4ExclusionRange -ScopeId 192.168.10.0
```

[![](https://neptunet.fr/wp-content/uploads/2019/10/dhcp-pws11.png)](https://neptunet.fr/wp-content/uploads/2019/10/dhcp-pws11.png)

Vérifier les **réservations d’une étendue** :

```  PowerShell
Get-DhcpServerv4Reservation -ScopeId 192.168.10.0
```

[![](https://neptunet.fr/wp-content/uploads/2019/10/dhcp-pws2.png)](https://neptunet.fr/wp-content/uploads/2019/10/dhcp-pws2.png)

Vérifier les **options d’une étendue** :

```  PowerShell
Get-DhcpServerv4OptionValue -ScopeId 192.168.10.0
```

[![](https://neptunet.fr/wp-content/uploads/2019/10/dhcp-pws12.png)](https://neptunet.fr/wp-content/uploads/2019/10/dhcp-pws12.png)

Vérifier les **options de serveur** (_même commande que la précédente mais sans préciser d’adresse d’étendue_) :

```  PowerShell
Get-DhcpServerv4OptionValue
```

[![](https://neptunet.fr/wp-content/uploads/2019/10/dhcp-pws13.png)](https://neptunet.fr/wp-content/uploads/2019/10/dhcp-pws13.png)

Vérifier les **baux délivrés dans une étendue** :

```  PowerShell
Get-DhcpServerv4Lease -ScopeId 192.168.10.0
```

[![](https://neptunet.fr/wp-content/uploads/2019/10/dhcp-pws10.png)](https://neptunet.fr/wp-content/uploads/2019/10/dhcp-pws10.png)

Obtenir des **statistiques sur les étendues** (_nombres d’adresses IP libres, en cours d’utilisation ou réservées_) :

```  PowerShell
Get-DhcpServerv4ScopeStatistics
```

[![](https://neptunet.fr/wp-content/uploads/2019/10/dhcp-pws14.png)](https://neptunet.fr/wp-content/uploads/2019/10/dhcp-pws14.png)

## Industrialiser le processus
  
L'avantage de PowerShell, c'est qu'on va pouvoir créer à la volée facilement X étendues en quelques secondes.  
Voici un exemple de script PowerShell qui va créer les étendues pour les réseaux de 151 à 155 :

``` PowerShell
$tab = 151, 152, 153, 154, 155   

foreach ($res in $tab) {

	Add-DHCPServerv4Scope -Name "LAN$res" -StartRange 192.168.$res.200 -EndRange 192.168.$res.220 -SubnetMask 255.255.255.0 -State Active   
	
	Set-DhcpServerv4Scope -ScopeId 192.168.$res.0 -LeaseDuration 1.00:00:00   
	
	Set-DHCPServerv4OptionValue -ScopeId 192.168.$res.0 -Router 192.168.$res.254
}
```

``` PowerShell
Get-DhcpServerv4Lease
```