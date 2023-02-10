# Instructions pour le TP 

Forker dans votre compte github le repo https://github.com/crunchy-devops/tp-coaching-webforce3.git  
Faire un git clone de ce repo en local dans votre directory c:\projet  
Faire un git clone dans la home directory de votre VM  
Ouvrir la directorie **tp-coaching-webforce3** dans PyCharm.

## Résultats et attentes
Vous devez compléter le fichier README.md avec toutes les instructions pour
faire les différents exercices.

## Exercice 1  - Scrum 
Voici les détails de ce mini-projet.  
*Installer sur une VM (que je vous ai fournie), un serveur Web en Python Flask fonctionnant sur le port 30101. 
Ce serveur écrit les actions des utilisateurs dans un disque attaché à la VM. 
écrire les instructions pour le pare-feu*

**Préparer le dashboard Scrum pour ce projet.**

Utilisez un outil de dashboard Scrum/Kanban de votre choix, ou simplement créer un project dans github
Faire une copie d'écran de votre dashboard et placez le fichier de l'image 
dans git/github pour qu'il soit versionné 


## Exercice 2  - Linux 
Mettre à jour les packages de votre VM ubuntu  
Vérifier la version de python3 déjà installée  
Le programme python est executé avec le nom python3, créer un alias nommé python valide pour le user ubuntu de votre VM 
vérifier en faisant  ```python -V```  
Faire un ```pip install flask``` , suivre les instructions pour installer pip si nécessaire

## Exercice 3  - Storage 

Recherche le disque supplémentaire de 1Gb connecté à la VM, précisez la commande utilisée
Formattez ce disque au format ext4  
Créer un <u> lien symbolique </u> nommé **log** depuis le projet tp-coaching-webforce3 sur votre vm 
vers ce disque


## Exercice 4   Git/Github 
Faire régulierement des commit/push dans github de votre machine local vers github
Comme vous avez fait un git clone de votre projet sur votre VM, vous devez
faire des git pull pour mettre jour votre Web serveur sans utiliser d'éditeur 
dans votre VM, ne pas faire de git push à partir de la VM sinon vous pouvez 
avoir des conflits à résoudre entre les push fait de votre machine locale et ceux fait à partir de la VM. 

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
Avec l'aide de la documentation Flask, et de la documentation python mettre des commentaires 
dans ce script.

Ajouter une variable d'environnement ```FLASK_APP=blogs```  
Lancer le web server avec la commande ```flask run --host=0.0.0.0 -p 30101```  
Verifier avec votre navigateur en utilisant l'url ```http://<ip_de_votre_vm>:30101/blogs```  

## Exercice 6   Pare-feu  
Trouvez la commande de gestion du firewall sous ubuntu 20.04
Fermer le port 5000 et  autoriser  le port 30101  








