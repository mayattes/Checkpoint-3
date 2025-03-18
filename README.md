# Checkpoint-3

## Exercice 1 : Manipulations pratiques sur VM Windows (temps estimé : 1h30)
Pour cet exercice tu as besoin de la VM SRVWIN01.

### Partie 1 : Gestion des utilisateurs
L'utilisateur Kelly Rhameur a quitté l'entreprise.
Elle est remplacée par Lionel Lemarchand

#### Q.1.1.1 Créer l'utilisateur Lionel Lemarchand avec les même attribut de société que Kelly Rhameur.
![image](https://github.com/user-attachments/assets/05490966-9707-463a-b634-51bfca2e6269)

![image](https://github.com/user-attachments/assets/2521bb19-0d69-45f0-99e0-74bf4aa51fbe)
clic sur copier

![image](https://github.com/user-attachments/assets/e5787109-b1d0-44e6-be14-03b169af9f16)


#### Q.1.1.2 Créer une OU DeactivatedUsers et déplace le compte désactivé de Kelly Rhameur dedans.
![image](https://github.com/user-attachments/assets/fc91cf89-302f-4317-875d-66af676466b5)

![image](https://github.com/user-attachments/assets/ba06d73b-ef33-445d-9cd2-5e8da8635d20)


#### Q.1.1.3 Modifier le groupe de l'OU dans laquelle était Kelly Rhameur en conséquence.

![image](https://github.com/user-attachments/assets/00a8360d-cc8e-4594-ab20-1a29acb8c73c)

#### Q.1.1.4 Créer le dossier Individuel du nouvel utilisateur et archive celui de Kelly Rhameur en le suffixant par -ARCHIVE.
![image](https://github.com/user-attachments/assets/63fdf93e-c2e5-4adb-b853-b1410df55571)

### Partie 2 : Restriction utilisateurs
#### Q.1.2.1 Faire en sorte que l'utilisateur Gabriel Ghul ne puisse se connecter que du lundi au vendredi, de 7h à 17h.
![image](https://github.com/user-attachments/assets/a7c89447-1e35-4104-8880-314d95af8981)

#### Q.1.2.2 De même, bloquer sa connexion au seul ordinateur CLIENT01.
![image](https://github.com/user-attachments/assets/1ad3f152-8c02-4c54-94dc-b458acbf016b)


#### Q.1.2.3 Mettre en place une stratégie de mot de passe pour durcir les comptes des utilisateurs de l'OU LabUsers.
![image](https://github.com/user-attachments/assets/16749a5b-805b-4634-b52e-51cd16807e3e)

### Partie 3 : Lecteurs réseaux
#### Q.1.3.1 Créer une GPO Drive-Mount qui monte les lecteurs E: et F: sur les clients.
![image](https://github.com/user-attachments/assets/36bc7be3-bb70-4b5c-82e2-c343189548e7)

![image](https://github.com/user-attachments/assets/f60b9656-d63b-40f2-898d-67313c91d77c)

## Exercice 2 : Manipulations pratiques sur VM Linux (temps estimé : 2h30)
Pour cet exercice tu as besoin de la VM SRVLX01.

### Partie 1 : Gestion des utilisateurs
#### Q.2.1.1 Sur le serveur, créer un compte pour ton usage personnel.
Sudo adduser koumba
#### Q.2.1.2 Quelles préconisations proposes-tu concernant ce compte ?
 Donner des privilèges élevée:
Cmd: sudo usermod -aG sudo koumba

Vérification du groupe:
Cmd: groups nom_utilisateur

### Partie 2 : Configuration de SSH

Un serveur SSH est lancé sur le port par défaut.
Il est possible de s'y connecter avec n'importe quel compte, y compris le compte root.

#### Q.2.2.1 Désactiver complètement l'accès à distance de l'utilisateur root.
Dans le fichier /etc/ssh/sshd_config, décommenter et modifier la ligne PermitRootLogin no

#### Q.2.2.2 Autoriser l'accès à distance à ton compte personnel uniquement.
Dans le fichier /etc/ssh/sshd_config, ajouter la ligne AllowUsers koumba

#### Q.2.2.3 Mettre en place une authentification par clé valide et désactiver l'authentification par mot de passe
Cmd: ssh-keygen -t “numéro de clé”

### Partie 3 : Analyse du stockage

#### Q.2.3.1 Quels sont les systèmes de fichiers actuellement montés ?
![image](https://github.com/user-attachments/assets/6871303a-416f-44cf-936f-4de732af0745)

#### Q.2.3.2 Quel type de système de stockage ils utilisent ?
![image](https://github.com/user-attachments/assets/01c58067-2ad0-4d40-80e8-714c5b482629)

#### Q.2.3.3 Ajouter un nouveau disque de 8,00 Gio au serveur et réparer le volume RAID
![image](https://github.com/user-attachments/assets/6ae4d0fa-a03e-41f4-b9b3-4f07c2900481)

#### Q.2.3.4 Ajouter un nouveau volume logique LVM de 2 Gio qui servira à héberger des sauvegardes. Ce volume doit être monté automatiquement à chaque démarrage dans l'emplacement par défaut : /var/lib/bareos/storage.
![image](https://github.com/user-attachments/assets/023234a3-5fb8-4e10-9732-8368ae389353)

![image](https://github.com/user-attachments/assets/0bfb56c5-6670-4579-af5a-f91b111e78a2)

![image](https://github.com/user-attachments/assets/66dbbbd3-0b4c-4b24-b2d2-7b565093ac69)

![image](https://github.com/user-attachments/assets/4ebf451e-49c1-4e46-8286-f832d4fbdc6d)

![image](https://github.com/user-attachments/assets/c876ae6d-8b0e-4880-ab41-8cb324cd5085)

#### Q.2.3.5 Combien d'espace disponible reste-t-il dans le groupe de volume ?
![image](https://github.com/user-attachments/assets/b58de41a-f248-4588-838f-4b7a5731bf58)


### Partie 4 : Sauvegardes
Le logiciel bareos est installé sur le serveur.
Les composants bareos-dir, bareos-sd et bareos-fd sont installés avec une configuration par défaut.

#### Q.2.4.1 Expliquer succinctement les rôles respectifs des 3 composants bareos installés sur la VM.
##### Bareos Director
C'est le chef d'orchestre. Il est responsable de la planification, du contrôle et du lancement des tâches de sauvegardes. Il contrôle l'ensemble des autres composants. Il est installé sur le serveur en charge de la gestion des sauvegardes.

##### Bareos File Daemon
Ce composant est installé sur chaque machine devant être sauvegardée.
Il est en charge de collecter les informations à sauvegarder et de les envoyer au Bareos Storage Daemon

##### Bareos Storage Daemon
Bareos permet d'effectuer des sauvegardes sur différents types de supports (bandes magnétiques, disques, stockage distant...). L'écriture sur ces supports 

### Partie 5 : Filtrage et analyse réseau

#### Q.2.5.1 Quelles sont actuellement les règles appliquées sur Netfilter ?
![image](https://github.com/user-attachments/assets/5de99913-58b6-4eb5-a43d-9b0f5331b0b9)

#### Q.2.5.2 Quels types de communications sont autorisées ?
Toutes
#### Q.2.5.3 Quels types sont interdit ?
aucune
#### Q.2.5.4 Sur nftables, ajouter les règles nécessaires pour autoriser bareos à communiquer avec les clients bareos potentiellement présents sur l'ensemble des machines du réseau local sur lequel se trouve le serveur.
![image](https://github.com/user-attachments/assets/0cd5473a-0449-4938-a735-bd20d2ea91b7)


Rappel : Bareos utilise les ports TCP 9101 à 9103 pour la communication entre ses différents composants.

### Partie 6 : Analyse de logs
#### Q.2.6.1 Lister les 10 derniers échecs de connexion ayant eu lieu sur le serveur en indiquant pour chacun :

La date et l'heure de la tentative
L'adresse IP de la machine ayant fait la tentative
![image](https://github.com/user-attachments/assets/2ffea8b9-636c-4e95-8f53-fbf9ea18cb3f)
