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
