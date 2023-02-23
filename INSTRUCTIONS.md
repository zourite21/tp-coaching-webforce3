# Instructions pour le TPs 

Forker dans votre compte github le repo https://github.com/crunchy-devops/tp-coaching-webforce3.git  
Faire un git clone de ce repo en local dans votre directory c:\projet  
Faire un git clone dans la home directorie de votre VM fournie 
Ouvrir la directorie **tp-coaching-webforce3** dans PyCharm.

## Résultats et attentes
Vous devez compléter le fichier README.md avec toutes les instructions nécessaires pour
faire les différents exercices.

## Exercice 1  - Scrum 
Voici les détails de ce mini-projet.  
*Installer sur une VM (fournie), un serveur Web en Python Flask fonctionnant sur le port 30101. 
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
Monter (mount) ce disque sur le point montage /home/ubuntu/tp-coaching-webforce3/log


## Exercice 4  - Git/Github 
Dans PyCharm allez dans File->Settings->Version control->github  
Appuyer sur la croix, en haut a gauche de cette fenetre et selectionnez log in with token.   
entrez votre token github  
Vous pouvez maintenant faire des git commit et git push depuis PyCharm   

Faire régulierement des commit/push dans github de votre machine local vers github
Comme vous avez fait un git clone de votre projet sur votre VM, vous devez
faire des git pull pour mettre jour votre Web serveur sans utiliser d'éditeur 
dans votre VM, ne pas faire de git push à partir de la VM sinon vous risquez 
d'avoir des conflits à résoudre entre les push faits de votre machine locale et ceux faits à partir de la VM. 

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
Avec l'aide de la documentation Flask, et de la documentation Python mettre des commentaires 
dans ce script.

Ajouter une variable d'environnement ```FLASK_APP=blogs``` , mettre cette variable dans le fichier ~/.bashrc
de votre user ubuntu  
Lancer le web server avec la commande ```flask run --host=0.0.0.0 -p 30101```  
Vérifier avec votre navigateur en utilisant l'url ```http://<ip_de_votre_vm>:30101/blogs```    
Vérifier que le fichier record.log existe bien dans la directory log    


## Exercice 6  - Pare-feu  
Trouvez la commande de gestion du firewall sous ubuntu 20.04  
Exemple : fermer le port 5000 et autoriser le port 30101  
Vérifier l'application Web sur ces ports  

---

## Ansible 1  Installation avec virtualenv 
Mettre en place ansible dans votre VM. 
Nous allons créer un virtualenv python pour installer la derniere version 
d'Ansible
```shell
cd ~/tp-coaching-webforce3
python3 -m venv venv  # set up the module venv in the directory venv
source venv/bin/activate  # activate the virtualenv python
pip3 install wheel  # set for permissions purpose
pip3 install --upgrade pip # update pip3
pip3 install ansible # install ansible 
pip3 install requests # extra packages
pip3 install natsort # require for an ansible filter
ansible --version # check the version number
```
## TP ansible 1 
Dans une sous directory de votre projet tp-coaching-webforce3 nommée **ansible**   
Créer un fichier ansible-1.yaml qui automatise l'exercice 2 ci-dessus.  
1. Le script doit mettre à jour les packages ubuntu.   
2. Vérifier la version de python3  
3. Créer un alias dans ~/.bashrc  
4. installer le package pip
Testez votre script

## TP ansible 2 
Dans une sous directory de votre projet tp-coaching-webforce3 nommée **ansible**   

Trouvez le fichier ansible-2-filtre.yml qui affiche les devices en mode raw
1. Analysez le fichier ansible-2-filtre.yml
2. Dans la directory filter_plugins etudier le code de la fonction get_device
3. Regardez egalement le fichier ansible.cfg, mettre des commentaires dans le README.md
Ce filtre doit etre utilise en local, pas sur une machine remote

Une maniere qui cette fois fonctionne en remote est le script ansible-2.yml  
4. Analysez le fichier ansible-2.yml  
5. Executez le  
6. Le script ansible-2-filter.yml ne formatte pas le disk. Modifier le script ansible-2-filter.yaml pour qu'il formatte le disque en
en vous inspirant du script ansible-2.yml 


## TP ansible 3 
Dans une sous directory de votre projet tp-coaching-webforce3 nommée **ansible**   
Créer un fichier ansible-3.yaml qui automatise l'exercice 6 ci-dessus.  
1. activer le firewall d'ubuntu
2. fermer le port 5000
3. ouvrir le port 30101  
Testez votre script



