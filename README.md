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

