# Partie 1: Gestion des utilisateurs:

## Q.2.1.1 :

![image](https://github.com/Mr-Maglor/Checkpoint3/assets/159529274/ac48a105-930a-405a-9629-f80b2529ef8c)


## Q.2.1.2 :

Tout dépend de que l'on veut en faire, mais si pour admnisitrer le serveur il serait interessant de l'ajouter au groupe Root.
Via cette commande `usermod -aG root bruno `.

# Partie 2: Configuration de SSH :

## Q.2.2.1 :

- Allez dans le fichier de configuraiton SSH via la commande `nano /etc/ssh/sshd_config/`
- Rentez la ligne suivante : `PermitRootLogin No` 

![image](https://github.com/Mr-Maglor/Checkpoint3/assets/159529274/23251e63-04c3-4f6b-959f-015cc972f6b6)

- Tapez la commande suivante `systemctl restart sshd`, si il n'y a pas d'erreur cela veut dire que la commande a bien été prise en compte.  
![image](https://github.com/Mr-Maglor/Checkpoint3/assets/159529274/dada448f-f7af-4fa8-b9e9-c218323da51e)

## Q.2.2.2 :

- Ajoutez la ligne suivante dans le fichier de configuraiton `AllowUsers bruno`.  
![image](https://github.com/Mr-Maglor/Checkpoint3/assets/159529274/d290a8b6-d587-4982-83fe-7f2ab9214ac0)

- Tapez la commande suivante `systemctl restart sshd`, si il n'y a pas d'erreur cela veut dire que la commande a bien été prise en compte.  
![image](https://github.com/Mr-Maglor/Checkpoint3/assets/159529274/dada448f-f7af-4fa8-b9e9-c218323da51e)

## Q.2.2.3 :

- Sur un poste client générez une clé via la commande `ssh-keygen` puis l'envoyez vers le serveur via la commande suivante `ssh-copy-id user@IP_server` (remplacez les chmaps **user** et **IP_Server** avec vos informations)
- Sur le serveur, modifiez ls lignes suivantes dans le fichier de configuraiton comme ceci  `PubkeyAuthentication Yes` et PasswordAuthentication no `
![image](https://github.com/Mr-Maglor/Checkpoint3/assets/159529274/f560df33-5ea9-4bd7-8161-22800deb3a6d)
- Tapez la commande suivante `systemctl restart sshd`, si il n'y a pas d'erreur cela veut dire que la commande a bien été prise en compte.  
![image](https://github.com/Mr-Maglor/Checkpoint3/assets/159529274/dada448f-f7af-4fa8-b9e9-c218323da51e)
