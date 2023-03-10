
# Procédure d'installation du serveur IRC

## Installation du service inspircd

Installation du service et ouverture des ports.

```bash
sudo apt-get update
sudo apt install inspircd
sudo ufw status verbose
sudo ufw allow 6667/tcp
sudo ufw reload
```
## Ajuster le fichier de configuration

Donner un nom au serveur et une adresse

```bash
sudo cp /etc/inspircd/inspircd.conf /home/nadine
sudo jed /etc/inspircd/inspircd.conf
```

```xml
<server name="irc.little.courses"
        description="Serveur de Nadine"
        id="1AB"
        network="NadineNet">

<admin name="Super Admin"
       nick="superadmin"
       email="nadineducegep@gmail.com">
  ```

```bash
sudo service inspircd restart
```

## Tester avec un client

Installer weechat et se connecter au serveur localement

```bash
sudo apt install weechat
weechat
> /server add ici localhost/6667
> /connect ici
> /join #cafe
```
## Ouvrir sur le monde

Rediriger les DNS de la nouvelle url

Namecheap :
```
+ CNAME   irc   little.courses.
```
Permettre à inspircd d'accepter les connexion externes avec le masque de &lt;bind&gt;

```xml
<bind address="" port="6667" type="clients">
```     
        
```bash
sudo service inspircd restart
```
Tester avec weechat à partir d'un ordinateur linux local

=> ATTENTION - s'assurer d'être sur un réseau qui ne bloque pas les ports
        

