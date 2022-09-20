# Modèles réseaux

Comprendre le fonctionnement d'un réseau c'est connaître les protocoles qui sont utilisés et comment ils sont utilisés.
Un protocole peut 
	définir le format d'un message que l'on envoit et sa strucutre(ex: smtp l'adresse = nom@domaine.com)
	gestion d'erreur (ex : packet perdu lors du streaming vidéo ou du transfert de fichier)
	Partage de média des périphérique
	Mettre en place des sessions (échanges entre deux serveurs)
	fournit un langage commun pour decrire des fonctions et des fonctionnalités réseau

Utilisation des couches pour classer les protocoles et identifier l'interaction des protocoles entre les protocoles et entre les couches
Facilite la conception d'un protocole 
La mise en place des couches empeches que le changement d'une couche affecte les autres


## Modèle OSI

Fin des années 70, un organisme appelé l'ISO publie un modèle de référence pour l'interconnextion des systèmes ouverts (Open System Interconnection) : le modèle OSI.
Défini les couches protocolaires, le modèle est divisé en sept couches indépendantes :
Couches hautes :
	Application (protocole applicatif)
	Présentation
	Sessions (ouverture fermeture de sessions, crypte ou non)
	Transport
Couches basses :
	Réseau (A to B)
	Liaison (transmission au média)
	Physique (cables)

### Application

Interface utilisateur et application. Repose sur les couches inférieurs pour communiquer avec les autres points finaux.

Assure l'identification et la disponibilités des partenaires

### Présentation

Présente les données à la couche application. Permet de formater/interpreter le texte.

### Session

Met en place et ferme les sessions entre les endpoints. Elle a pour role de mettre en place les dispotifs d'échange d'une session (cryptage ou non)

### Transport

Permet de faire la liaisont entre l'OS et le matériel (l'applicatif et le matériel). Aiguille un paquet réseau vers l'application qui lui correspond. Assure la fragmentation et la fiabilité de la connexion. Permet d'établir une session.
Permet l'acheminement des paquets à la bonne application grace aux ports. On parle ici de socket quand une application attend l'arrivé d'un paquet sur un port précis (un port d'écoute)
Seulement deux protocoles existent

#### TCP

transmission fiable (retransmission en cas de perte) grâce au 3 way handshake
		flag premier echange : SYN SEQ = X (nb aléatoire)
		flag de réponse : SYN ACK SEQ = Y (nb aléatoire) ACK = X + 1
		flag de confirmation : ACK SEQ  = X + 1 ACK  = Y + 1
	Cloture de connexion
		flag : FIN SEQ = X
		flag : ACK = X + 1
		flag FIN SEQ = Y
		flag ACK = Y +1 (ferme le socket)
	Controle de flux
		Numéros de séquence (ordonner les paquets)
		Somme de controles
		Acquittement (les paquets qui restent à envoyé)
	Fenetrage
		Permet de définir une fenetre pour envoyé tout les paquets
			Correspond à la quantité de segment envoyé mesuré en octet que l'émetteur peut envoyer
			En cas de perte de paquet la taille de la fenetre défini le nombre de segment à renvoyé
		Défini au début d'une sessions
		Evolutive en fonction des besoin
		
Plus de bande passante (20 octets)
Paquet réordonnée à l'arrivé
Firewall accepte ou non la session 

#### UDP

transmission non fiable (send and forget)
Moins de bande passante (8 octets)
Paquet non ordonné (role de l'application)

### Réseau

Gère l'adressage logique des machines (IP)
Localisation des machines
Acheminement des paquets via le meilleur
Notion de routage
	Paquets nécessaire pour routage dynamique
	Pas de difffusion broadcast/multicast
	Analyse de l'entete IP
	Possibilités d'ACL
	Communication + routage
	Mise en place du QOS (Quality Of Service)
Agit au niveau trois
	La trame va être modifier dans le niveau inférieur

### Liaison

Lien avec le méteriel
Adressage physique
Formatage de la trame
2 sous couches :
	Couche MAC : comment placer les trames sur les médias
		Détection d'érreur
	Couche LLC  Comment découper les données transmises par la couche réseau
		Controle de flux
		Séquensage

### Physique

Le plus bas niveau
Envoie des bits et recoi sur un média
	Modulation d'amplitude
	Modulation de phase
	Modulation
Norme 802.3 : ethernet
Topologie 
	physique
		agencement des cables
	logique
		Chemin logique emprunté par un signal
	en bus
	en anneau
	en étoile
	maillée (haute dispo)



## Biblio

https://www.iso.org/home.html