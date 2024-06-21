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
- Sur le serveur, modifiez ls lignes suivantes dans le fichier de configuraiton comme ceci  `PubkeyAuthentication Yes` et `PasswordAuthentication no`
![image](https://github.com/Mr-Maglor/Checkpoint3/assets/159529274/52419cb0-50b6-401a-be77-fa5167179da2)

- Tapez la commande suivante `systemctl restart sshd`, si il n'y a pas d'erreur cela veut dire que la commande a bien été prise en compte.  
![image](https://github.com/Mr-Maglor/Checkpoint3/assets/159529274/dada448f-f7af-4fa8-b9e9-c218323da51e)


# Partie 3 : Analyse du stockage :

## Q.2.3.1 :

Le ssystèmes de fichiers montées sont du EXT4, EXT2 et Swap
![image](https://github.com/Mr-Maglor/Checkpoint3/assets/159529274/523834d2-adde-4f5a-a972-c2c12ac02921)

## Q.2.3.2 :

On a du RAID1 et du LVM 
![image](https://github.com/Mr-Maglor/Checkpoint3/assets/159529274/59200727-1f22-47e3-8432-f5256522f81b)

Q.2.3.3 

Le nouveau disque apparait sour le nom de sdb (utilisez la commande `lsblk`pour le vérifiez).  
- Partionnez le nouveau disque dur via la commande `fdisk /dev/sdb` avec les options suivantes :  
![image](https://github.com/Mr-Maglor/Checkpoint3/assets/159529274/1258f23e-d720-4feb-a195-e89f7643d6a2)

- Ajoutez le nouveau disque au RAID via la commande suivante `mdadm --manage /dev/md0 --add /dev/sdb1` et tapez la commande `mdadm --detail /dev/md0`pour vérifiez que tout est correct et le RAID réparé.  
![image](https://github.com/Mr-Maglor/Checkpoint3/assets/159529274/deec5ba6-8d99-4ffb-8ded-a3bbfb4f9751)  
L'état affiche Clean tout est réparé.

Q.2.3.4  

- Il faut créer le nouveau volume via la commande suivante `lvcreate -n Sauvegarde -L 2g cp3-vg ` (Sauvegarde représente le nom du volume créée).  
![image](https://github.com/Mr-Maglor/Checkpoint3/assets/159529274/79f9a099-a320-46bf-b9d8-856a57d00fc1)  

- Formatez le nouveau volume via la commande suivante :  `mkfs -t ext4 /dev/cp3-vg/Sauvegarde `  
![image](https://github.com/Mr-Maglor/Checkpoint3/assets/159529274/903237d2-e461-4690-9432-553cfb9474ce)

- Il faut ensuite montez le volume dans bareos, via la commande suivante :  `mount /dev/cp3-vg/Sauvegarde /var/lib/bareos/storage `
Si aucun message d'erreur c'est que le montage a été effectué.

- Modifidez ensuite le fichier fstab pour automatiser le montage :
![image](https://github.com/Mr-Maglor/Checkpoint3/assets/159529274/2f618186-bc6e-459e-9803-d813b4279b8f)  

- Ensuite on envoie la commande `mount -a`pour vérifier qu'il n'y a pas d'érreurs.

Q.2.3.5  

On lance la commande `vgdisplay` et on voit qu'il reste 1.79 Go de libre.
![image](https://github.com/Mr-Maglor/Checkpoint3/assets/159529274/0a995153-7e04-4673-b779-658cfbed247f)

# Partie 4 : Sauvegardes :

Q.2.4.1  

Non prévu dans les choses à réviser pour le chekckoint 3. 
![image](https://github.com/Mr-Maglor/Checkpoint3/assets/159529274/255ea6a7-fde5-4f88-90eb-cb38f0b9ffbe)
![image](https://github.com/Mr-Maglor/Checkpoint3/assets/159529274/e1b14323-adbf-4688-b90d-ddc4f7057299)

De plus je n'ai jamais réussit à faire ni la quête, ni l'atelier Bareos.
Donc je ne peux répondre à cette question.

# Partie 5 : Filtrage et analyse réseau

Q.2.5.1

- On voit les règles grâce à la commande suivante  `nft list ruleset`
![image](https://github.com/Mr-Maglor/Checkpoint3/assets/159529274/770d19a3-f7d7-4fff-9d10-cc6ddb7c78ec)
Les règles que je comprends sont les suivantes :
-    Tout les paquets autre que ceux autorisé sont bloqué en entrée
-    Procole ICMP autorisé en entrée (ping ipv4)
-    Procole ICMP IPV6 autorisé en entrée (ping pipv6)
-    Communication avec l'adresse loopback autorisée en entrée
-    Port TCP 22 ouvert en Entrée
-   je n'arrive pas à decripter les deux ligne suivantes :
  ![image](https://github.com/Mr-Maglor/Checkpoint3/assets/159529274/b44f88c7-0eb2-43e5-bd10-0d7b134e36b7)  
Je sais juste que ça accepte quelque chose avec un état **established** en entrée et refuse quelque chose avec un état **Invalid**.


Q.2.5.2

Les communications autorisée en entrée sont les suivantes :
-  Protcol SSH via le port TCP 22
-  ping en IPV4 et IPV6

Q.2.5.3

Tout les paquets non autorisée en entrée seront interdit plus quelque chose avec l'état *Invalid**

Q.2.5.4

En théorie les regles sont définis dans le fichier suivant : `/etc/nftables.conf` mais il est vide :
![image](https://github.com/Mr-Maglor/Checkpoint3/assets/159529274/db7c2f50-756c-490c-bd53-c9e58fe9fd57)
Donc cela veut dire qu'il y a un autre fichier de configuration qui prend la main sur le paramétrage de base de NFT Tables, mais impossible de savoir ou il est.
En théorie il faut ajouter les règles suivantes dans la chaine suivante : `chain in_chain` et les placez à la fin après `ip6 nexthdr ipv6-icmp accept `
- tcp dport 9101 accept
- tcp dport 9102 accept
- tcp dport 9103 accept

# Partie 6 : Analyse de logs

Q.2.6.1
![image](https://github.com/Mr-Maglor/Checkpoint3/assets/159529274/b5333f1c-a306-4d03-9690-506d9418a172)




