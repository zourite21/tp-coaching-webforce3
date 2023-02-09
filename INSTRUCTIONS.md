# Instructions pour le TP déjà

Forker dans votre compte github le repo https://github.com/crunchy-devops/tp-coaching-webforce3.git
Faire un git clone de ce repo en local dans votre directory c:/projet
Faire un git clone dans la home directory de votre VM
Ouvrir la directory tp-coaching-webforce3 dans PyCharm.

## Résultats et attentes
Vous devez compléter le fichier README.md avec toutes les instructions pour
faire les différents exercices.

## Exercice 1  - Scrum 
Voici les détails de ce mini-projet.  
*Installer sur une VM (que je vous ai fournie), un serveur Web en Python Flask fonctionnant sur le port 30101. 
Ce serveur écrit les actions des utilisateurs dans un disque attaché a la VM. 
écrire les instructions pour le pare-feu*

**Préparer le dashboard Scrum pour ce projet.**

Utilisez un outil de dashboard Scrum/Kanban de votre choix, 
faites une copie d'écran de votre dashboard et placez le fichier de l'image 
dans git/github pour qu'il soit versionné 


## Exercice 2  - Linux 
Mettre à jour les packages de votre VM ubuntu
Verifier la version de python déjà installée, si elle existe 
Installer la version 3.11 de python (mais pas les packages additionels) avec l'aide de ce document
https://linuxways.net/ubuntu/how-to-install-python-3-11-on-ubuntu-20-04/


## Exercice 3  - Storage 

Recherche le disque supplémentaire connecté à la VM, precisez la commande utilisee
Formattez ce disque au format ext4, 
Créer un lien symbolique nommé **log** depuis le projet tp-coaching-webforce3 sur votre vm 
vers ce disque


## Exercice 4   Git/Github 
Faire régulierement des commit/push dans github
Comme vous avez fait un git clone de votre projet sur votre VM, vous devez
faire des git pull pour mettre jour votre Web serveur sans utiliser d'éditeur 
dans votre VM, ne pas faire de git push à partir de la VM sinon vous pouvez 
avoir des conflits à résoudre. 

## Exercice 5  - Python
Créez un fichier blogs.py
Copier le script python suivant

```python
from flask import Flask
import logging
 
app = Flask(__name__)
 
logging.basicConfig(filename='log/record.log', level=logging.DEBUG, format=f'%(asctime)s %(levelname)s %(name)s %(threadName)s : %(message)s')
 
@app.route('/blogs')
def blog():
    app.logger.info('Info level log')
    app.logger.warning('Warning level log')
    return f"Welcome to the Blog"
 
app.run(host='localhost', debug=True)
```
Trouvez la syntaxe de ligne app.run pour que serveur écoute sur le port 30101

Avec l'aide de la documentation Flask, et python mettre des commentaires 
dans ce script.


## Exercice 6   Pare-feu  
Trouvez la commande de firewall sous ubuntu 20.04
Pourquoi on ne peut pas fermer tous les ports et autoriser que le port 30101 ? 
Autorisez le port 30101 (entre autre !!)







