# Partie 1: Gestion des utilisateurs:

## Q.1.1.1 :

- Faire une recherche pour trouver Kelly Rhameur grâce à l'outil de recherche de l'Active Directory (Action puis find)
- Allez dans l'onglet **Organization** de Kelly Rhameur pour trouver dans quelle OU elle est situé :  
![image](https://github.com/Mr-Maglor/Checkpoint3/assets/159529274/d94987ca-8fed-46b8-b721-0f7bca46c13f)

- on voit quel appartient au département *Direction des Ressources Humaines*, donc elle sera dans l'OU *DirectionDesRessourcesHumaines*.  
- Faire ensuite un copié de son compte via le menu *action* et choisir *Copy*.  
- une nouvelle fenêtre apparait et remplir les champs du nouvel utilisateur :  
![image](https://github.com/Mr-Maglor/Checkpoint3/assets/159529274/de3d45b6-bdd4-42f5-92c6-29a359edd96b)

- Kelly Rhameur étant Manageur de certains utilisateur, il faut passer Lionel Lemarchand en tant que manager de ces même utilisateurs :  
- Il faut double cliquer sur le profil de Kelly Rhameur, puis aller dans l'onglet **Organization**, dans la section **Direct Reports**, on voit les utilsiateurs qui dépendent d'elle.  
![image](https://github.com/Mr-Maglor/Checkpoint3/assets/159529274/b24eb008-dd48-4477-95c3-35324e8b7ebc)

- Double-cliquez sur chacun, allez dans l'onglet **Organization**,  et dans la partie **Manager** cliquez sur **Change** et aller chercher l'utilsateur Lionel Marchad, rentrez **lionel.marchand** dans le champs de texte et cliquez sur **check names** et le bon profil sera automatiquement sélectionné.  
![image](https://github.com/Mr-Maglor/Checkpoint3/assets/159529274/a86e4787-8aa1-42d4-95c1-6520a70ad5fa)

- le résultat final devrait être cela, pensez à bien comparez les deux profils pour faire les mêmes paramétrages :  
![image](https://github.com/Mr-Maglor/Checkpoint3/assets/159529274/749b3765-1560-4329-bb4b-2dfcf8d60b37)


## Q.1.1.2 :

- Sélectionnez **TSSR.LAN** , puis via le menu Action choisir **NEW** et ensuite **Organization Unit**.  
- Rentrez le nom de la nouvelle OU **DeactivatedUsers**, et laissez bien la case coché pour éviter du supprimer l'OU par inadvertance.  
![image](https://github.com/Mr-Maglor/Checkpoint3/assets/159529274/c172c315-0d46-43e1-b459-f16ea728a8a7)

- Retourner dans l'OU **DirectionDesRessourcesHumaines**, faire un clique droit sur Kellu Rhameur et sélectionnez **Disable Account*.  
- Faites ensuites un glissez-déposez de Kelly Rhameur vers la nouvelle OU Créée.  
![image](https://github.com/Mr-Maglor/Checkpoint3/assets/159529274/e32e33db-49c2-4649-b0a5-9d677651dc12)


## Q.1.1.3 :

- Retournez dans  l'OU **DirectionDesRessourcesHumaines**.  
- Double-cliquez sur le groupe **GrpUsersDirectionDesRessourcesHumaines**.  
- Allez dans l'onglet  **Members**.  
- Sélectionner Kelly Rhameur puis **Remove**.  
![image](https://github.com/Mr-Maglor/Checkpoint3/assets/159529274/0ddfd93b-4219-4a4d-b627-aa2d5cadb803)


## Q.1.1.4 :

- Dans le disque **F:**, créez un nouveau dossier du nom de **lionel.marchand**.  
- Renommer le dossier individuel de Kelly Rhameur comme cela : **kelly.rhameur -ARCHIVE**.  
![image](https://github.com/Mr-Maglor/Checkpoint3/assets/159529274/226dd35a-3b21-4d93-86d3-82dd265d6dc3)

# Partie 2: Restriction utilisateurs:


## Q.1.2.1 :

- Allez dans les propriétés de l'utilsateur Gabriel Ghul, puis dans l'onglet **Account**.
- Selectionnez **Logon Hours**.
- Dans un premier temps, sélectionnez **Logon Denied* et sélectionnez toutes les cases.
- Ensuite sélectionnez **Logon Permitted** et choisir les plages voulu (lundi au vendredi de 7 à 17h).
![image](https://github.com/Mr-Maglor/Checkpoint3/assets/159529274/a08f6b21-437b-4b7b-848b-a60bf72c06fc)


## Q.1.2.2 :

- Allez dans les propriétés de l'utilsateur Gabriel Ghul, puis dans l'onglet **Account**.  
- Selectionnez **Logon On To**.  
- Selectionnez **The following Computer**  
- Dans le champs de texte rentez **CLIENT01** et cliquez sur **Add*.  
![image](https://github.com/Mr-Maglor/Checkpoint3/assets/159529274/f74781f7-0c99-4720-bfc7-aa9532b49895)


## Q.1.2.3 :

- Au préalable créez un groupe dans l'OU *LabUsers* via le menu **Action**, puis *New** et enfin *Group**.
- Laissez les options par défaut et le nommez **GrpLabUser** :  
![image](https://github.com/Mr-Maglor/Checkpoint3/assets/159529274/54a8c0d8-fcfc-49f4-b8c5-3027ce079440)

- Ensuite dans les Propriété de ce nouveau groupe, allez dans l'onglet **Members** et àjoutez tout les groupes principaux des OU principales (même methode que pour ajouter un mangager à un utilsiateur**) :  
![image](https://github.com/Mr-Maglor/Checkpoint3/assets/159529274/8f5d7f1c-43c8-4947-81b4-7900ed07f5e8)

- Via le **Server Manager** et le menu **Tools*.
- Ouvrez **Active Directory Administrative Center**.
- Choisissez **TSSR(Local)**.
- Puis **System** et enfin  **Password Setting Container**
- Sur le menu de droite, cliquez sur **New** et **Password Settings**
- La fenêtre suivante apparait :  
![image](https://github.com/Mr-Maglor/Checkpoint3/assets/159529274/1c5dcd34-1157-4fcb-ab60-88b6bb3f4f7c)

- Libre à vous de définir votre stragégie de mot de passe, ou de suivre notre exemple :  
![image](https://github.com/Mr-Maglor/Checkpoint3/assets/159529274/4cf9707c-31a7-45a4-b108-46e8b14192e4)

- Voila la stratégie mise en place :
-   10 caractères minimum avec caractères spéciaux
-   2 différents mots de passe conservé
-   changement de mot de passe tout les 180 jours et 30 jour minium pour changer de mot de passe
-   5 tentative avant blocage de compte, délais de 30 minutes avant de reset le compteur de tentative de connexion échoué et il faut un compte administrateur pour debloquer le compte une fois vérrouillé.
- Ensuite dans la case **Direct Applies To**, choisir **Add**
![image](https://github.com/Mr-Maglor/Checkpoint3/assets/159529274/4fb0d7c0-13a7-465e-85da-b4e0bb622584)

- Si les groupes ont fait correctement, tout les utilisateurs de l'ou *LabUsers* auront cette nouvelle stratégie de mot de passe.
- Si ce n'est pas le cas, vérifiez que les utilsateurs soient bien affectés à des groupes et les affecté à leur groupes respectifs.


# Partie 3: Lecteurs réseaux :


## Q.1.3.1 :
- Selectionnez chacun des lecteurs, via un clique droit ouvrir le menu des Propirétés.  
- Allez dans l'onglet **Sharing** et cliquez sur **Advanced Sharing** et cochez **Share This Folder**.  
- Validez votre choix.  
![image](https://github.com/Mr-Maglor/Checkpoint3/assets/159529274/35dbb396-5b8e-48f3-af2c-1bc5de711ba3)

- Via le **Server Manager** et le menu **Tools*.  
- Ouvrez **Group Policy Management** et sélectionnez **Group Policy Objects**.  
- Faire un clique droit et sélectionez **New**, nommez la GPO **Drive-Mount**.  
- Faites un clique droit puis sélectionez **Edit** sur cette nouvelle GPO.  
- Cliquez sur **User Configuration** puis **Preferences** ensuite **Windows Settings** et finalement  **Drive Maps**.  
![image](https://github.com/Mr-Maglor/Checkpoint3/assets/159529274/90376832-33f8-41c9-82da-965661733ba1)  

- Dans la fenêtres, faites un clique droit puis selectionnez **New** et **Mapped Drive**.  
- Faites le même paramétrage :  
![image](https://github.com/Mr-Maglor/Checkpoint3/assets/159529274/5f3edc3b-5df0-4191-bc8a-5a75b06e9d34)  
![image](https://github.com/Mr-Maglor/Checkpoint3/assets/159529274/21a5eb0b-f71a-4f52-abc2-80ddc2ea8d35)  

- Faire de même pour l'autre lecteur.  
![image](https://github.com/Mr-Maglor/Checkpoint3/assets/159529274/aee85b0b-a76f-4086-9f56-456a7dfe40c6)  
![image](https://github.com/Mr-Maglor/Checkpoint3/assets/159529274/fa68d4e2-dca2-4ee0-a972-043bbf4b185f)  

- Fermer la fenêtre de cette GPO.  
- Selectionnez **LabUser**, faites un clique droit et choisir **Link an Existing GPO**.  
- Choisir **Drive-Mount**.  
![image](https://github.com/Mr-Maglor/Checkpoint3/assets/159529274/658d4e45-7bbe-4c86-93f0-f4949550e91c)  
![image](https://github.com/Mr-Maglor/Checkpoint3/assets/159529274/1af05c7a-a709-4401-949c-fce3ebc47037)  


  











