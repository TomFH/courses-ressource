# INSTALLATION

**pfSense** est un routeur / pare-feu basé sur **FreeBSD**. Il s’administre à distance via une interface Web.

Il utilise le pare-feu à états Packet Filter, des fonctions de routage et de NAT lui permettant de connecter plusieurs réseaux informatiques. Il comporte l’équivalent libre des outils et services utilisés habituellement sur des routeurs professionnels propriétaires.

pfSense intègre aussi un gestionnaire de paquets pour installer des fonctionnalités supplémentaires, comme un proxy, serveur VoIP …

Démarrer la VM

[![](https://www.pc2s.fr/wp-content/uploads/2018/10/pfsense-2.jpg)](https://www.pc2s.fr/wp-content/uploads/2018/10/pfsense-2.jpg)

**Accepter** la licence

[![](https://www.pc2s.fr/wp-content/uploads/2018/10/pfsense-3.jpg)](https://www.pc2s.fr/wp-content/uploads/2018/10/pfsense-3.jpg)

Install pfSense : **OK**

[![](https://www.pc2s.fr/wp-content/uploads/2018/10/pfsense-4.jpg)](https://www.pc2s.fr/wp-content/uploads/2018/10/pfsense-4.jpg)

Sélectionner **French** dans le menu déroulant

[![](https://www.pc2s.fr/wp-content/uploads/2018/10/pfsense-5.jpg)](https://www.pc2s.fr/wp-content/uploads/2018/10/pfsense-5.jpg)

Sélectionner : **Continue with fr.kbd keymap**

[![](https://www.pc2s.fr/wp-content/uploads/2018/10/pfsense-6.jpg)](https://www.pc2s.fr/wp-content/uploads/2018/10/pfsense-6.jpg)

**Auto (ZFS)** pour pfSense version 2.6 et ultérieure ou **Auto (UFS) BIOS** pour version inferieure

[![](https://www.pc2s.fr/wp-content/uploads/2018/10/pfsense-7.jpg)](https://www.pc2s.fr/wp-content/uploads/2018/10/pfsense-7.jpg)

Patientez pendant l’installation

[![](https://www.pc2s.fr/wp-content/uploads/2018/10/pfsense-8.jpg)](https://www.pc2s.fr/wp-content/uploads/2018/10/pfsense-8.jpg)

Sélectionner : **No**

[![](https://www.pc2s.fr/wp-content/uploads/2018/10/pfsense-9.jpg)](https://www.pc2s.fr/wp-content/uploads/2018/10/pfsense-9.jpg)

Sélectionner : **Reboot**   (Ne pas oublier d’éjecter le CD)

[![](https://www.pc2s.fr/wp-content/uploads/2018/10/pfsense-10.jpg)]

# CONFIGURATION

Récupérez les informations liées à votre propre réseau. Dans ce mode opératoire, nous utiliserons les éléments suivants :

-   IP pfSense (LAN): 10.0.10.1/24
-   IP Réseau INTERNET (WAN) : 192.168.23.128/24
-   IP PASSERELLE Internet : 192.168.23.51/24 (Adresse de votre Routeur, Box Internet)
-   IP DNS1 Internet : 192.168.23.51 (Passerelle d’accès a internet / Routeur, Box)
-   IP DNS2 Internet  : 8.8.8.8 (DNS Google)

Une fois l'installation fini et la vm redemarré, saisissez “**n**” pour “no” pour la création de **VLAN**

[![](https://www.pc2s.fr/wp-content/uploads/2018/10/pfsense-11.jpg)](https://www.pc2s.fr/wp-content/uploads/2018/10/pfsense-11.jpg)

Sélectionner la carte réseau internet **WAN : hn0** – (Voir dans Hyper-V l’adresse MAC qui correspond a votre carte)

[![](https://www.pc2s.fr/wp-content/uploads/2018/10/pfsense-12.jpg)](https://www.pc2s.fr/wp-content/uploads/2018/10/pfsense-12.jpg)

Sélectionner la carte réseau local **LAN : hn1** – (Voir dans Hyper-V l’adresse MAC qui correspond a votre carte)

[![](https://www.pc2s.fr/wp-content/uploads/2018/10/pfsense-13.jpg)](https://www.pc2s.fr/wp-content/uploads/2018/10/pfsense-13.jpg)

Appliquer les changements : “**y**” pour “yes”

[![](https://www.pc2s.fr/wp-content/uploads/2018/10/pfsense-14.jpg)](https://www.pc2s.fr/wp-content/uploads/2018/10/pfsense-14.jpg)

Retour au Menu

## CONFIGURATION DU RESEAU LAN

Sélectionner : **2** (Set interface IP address)

[![](https://www.pc2s.fr/wp-content/uploads/2018/10/pfsense-16.jpg)](https://www.pc2s.fr/wp-content/uploads/2018/10/pfsense-16.jpg)

Sélectionner la carte réseau local LAN : **2**

[![](https://www.pc2s.fr/wp-content/uploads/2018/10/pfsense-17.jpg)](https://www.pc2s.fr/wp-content/uploads/2018/10/pfsense-17.jpg)

Saisissez l’adresse **IP** souhaitée : 192.168.2.1 (pour notre exemple)

[![](https://www.pc2s.fr/wp-content/uploads/2018/10/pfsense-18.jpg)](https://www.pc2s.fr/wp-content/uploads/2018/10/pfsense-18.jpg)

Saisissez le masque sous réseau au format CIDR : **24**

[![](https://www.pc2s.fr/wp-content/uploads/2018/10/pfsense-19.jpg)](https://www.pc2s.fr/wp-content/uploads/2018/10/pfsense-19.jpg)

Laissez vide pour ne pas définir la passerelle : Tapez **ENTREE**

[![](https://www.pc2s.fr/wp-content/uploads/2018/10/pfsense-20.jpg)](https://www.pc2s.fr/wp-content/uploads/2018/10/pfsense-20.jpg)

Laissez vide pour ne pas définir d’adresse IPV6 : Tapez **ENTREE**

[![](https://www.pc2s.fr/wp-content/uploads/2018/10/pfsense-21.jpg)](https://www.pc2s.fr/wp-content/uploads/2018/10/pfsense-21.jpg)