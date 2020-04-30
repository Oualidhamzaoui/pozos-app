# student-list 
This repo is a simple application to list student with a webserver (PHP) and API (Flask)
DevOps est un ensemble de pratiques qui combine le développement de logiciels et les opérations de technologie de l'information qui vise à raccourcir le cycle de vie du développement des systèmes et à fournir une livraison continue avec une haute qualité logicielle.

## Simple CI/CD pipeline

L'objectif de ce projet c'est d'avoir une pipeline CI/CD, dans laquelle si on fait des changements au niveau de notre repo GitHub, Jenkins va automatiquement déclencher le **build** et les tests, par la suite il va créer une image docker avec le **build code**, ensuite l'envoie de docker image à docker **registry** et enfin le déploiement de vers notre serveur avec ansible.

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a9efd41a-6c57-4690-8375-9b4396672b06/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a9efd41a-6c57-4690-8375-9b4396672b06/Untitled.png)

# GitHub

GitHub est une plateforme qui fournit un hébergement pour le contrôle des versions de développement logiciel à l'aide de Git.
Dans notre projet on vas commencer par créer une repo laquelle on va l'appeler `pozos-app`.

On peut même utiliser GitLab

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f9d09659-7e0d-4911-b376-7718ebd71435/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f9d09659-7e0d-4911-b376-7718ebd71435/Untitled.png)

En suite il faut initialiser le projet en local.

```powershell
git init
```

Si on a une documentation (e.g README.md) on va l'ajouter.

```powershell
git add README.md
```

On fait le commit suivi d'un motif "First commit".

```powershell
git commit -m "first commit"
```

 

`remote` c'est pour lier notre répertoire git avec le projet en local.

```powershell
git remote add origin https://github.com/BenHakimIlyass/pozos-app.git
```

Le push est pour but d'envoyer tout ce qui est dans le `stage` à la branche master

(Ici on a juste le `[README.md](http://readme.md)` )

```powershell
git push origin master
```

# Jenkins

Démarrage du docker image pour lancer Jenkins.

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/50e825c5-467f-4f43-9faa-f764ba75ef3d/1-cmd_running_jenkins_container.jpg](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/50e825c5-467f-4f43-9faa-f764ba75ef3d/1-cmd_running_jenkins_container.jpg)

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a795c262-3587-44bb-9c57-1cdd4b2b775c/2-generated_password_for_jenkins.jpg](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a795c262-3587-44bb-9c57-1cdd4b2b775c/2-generated_password_for_jenkins.jpg)

L'initialisation du mot de passe admin, en utilisant le mot de passe généré..

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/fac5e020-01e4-49b3-b749-e3d2703b4fdc/3-accessing_jenkins_through_web_navigator.jpg](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/fac5e020-01e4-49b3-b749-e3d2703b4fdc/3-accessing_jenkins_through_web_navigator.jpg)

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/0c206560-941a-45df-9f83-5f07cd65c23f/4-plugins_installation.jpg](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/0c206560-941a-45df-9f83-5f07cd65c23f/4-plugins_installation.jpg)

La création du 1er utilisateur oualid_ilyass sur Jenkins.

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/33f5b3f4-6b47-4cb2-a219-e8f6e3049f17/5-creation_admin.jpg](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/33f5b3f4-6b47-4cb2-a219-e8f6e3049f17/5-creation_admin.jpg)

Tableau de bord.

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/6234145d-0e1b-4953-a2f5-c4ea89d4bc5f/5-jenkins_hello-world.jpg](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/6234145d-0e1b-4953-a2f5-c4ea89d4bc5f/5-jenkins_hello-world.jpg)

La création d'une pipeline sous le nom Pozoz-Pipeline..

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/ae169b7b-bcfd-410c-bf92-36664d9dc0d8/6-creation_dune_nouvelle_pipeline.jpg](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/ae169b7b-bcfd-410c-bf92-36664d9dc0d8/6-creation_dune_nouvelle_pipeline.jpg)

Apres l'installation des plugins de Jenkins et la création du pipeline, il faut d'abord configurer chaque étapes.

La liaison avec GitHub sous l'adresse : `github.com/Oualidhamzaoui/pozos-app`

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/7e830e26-8383-4388-8704-ddff9319de85/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/7e830e26-8383-4388-8704-ddff9319de85/Untitled.png)

Comme cité dans le cahier de charge il faut démarrer le build chaque fois qu'on fait le push sur notre projet GitHub(Build trigger).

On a ajouté aussi le trigger du build quand on fait un merge request et quand on fait le merge.

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f7ff1de7-ec7e-4e84-ac93-b59a2386e53f/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f7ff1de7-ec7e-4e84-ac93-b59a2386e53f/Untitled.png)

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/1f68c422-e5d6-4e01-bd1c-09d706c67690/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/1f68c422-e5d6-4e01-bd1c-09d706c67690/Untitled.png)

Les spécifications de la liaison avec GitHub.

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f4aa4ebe-7c13-47cc-b55d-ec581d680686/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f4aa4ebe-7c13-47cc-b55d-ec581d680686/Untitled.png)

Pour tester notre liaison Jenkins avec GitHub il faut d'abord exposer l'adresse privé `[localhost](http://localhost)` a une adresse public accessible via le web.

Et la on a utilisé **ngrock**, mais le problème ici c'est qu'il faut générer une nouvelle adresse chaque 8 heures**.**

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/860dda14-7b17-4b64-b9e2-b8f721080943/8-exposing_the_localhost_to_web_using_ngrok(jenkins_accessible_par_web).jpg](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/860dda14-7b17-4b64-b9e2-b8f721080943/8-exposing_the_localhost_to_web_using_ngrok(jenkins_accessible_par_web).jpg)

Dans la partie Webhooks on voit que GitHub a pu accéder à notre Jenkins via l'adresse généré par ngrock.

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/025d76cc-7087-4a19-bf17-bd16fafdf3d2/8-step_2_webhook(success).jpg](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/025d76cc-7087-4a19-bf17-bd16fafdf3d2/8-step_2_webhook(success).jpg)

En utilisant le webhook , GitHub arrive a déclencher le build automatiquement sur notre serveur Jenkins.

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a9163d2b-5011-4991-b89b-6da1102bf979/WhatsApp_Image_2020-04-29_at_8.40.37_PM.jpeg](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a9163d2b-5011-4991-b89b-6da1102bf979/WhatsApp_Image_2020-04-29_at_8.40.37_PM.jpeg)

Notre répertoire GitHub avec tout les fichiers du projet.

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/3f133ea0-5d7b-4e2e-abf8-fae69627924f/WhatsApp_Image_2020-04-29_at_8.44.44_PM.jpeg](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/3f133ea0-5d7b-4e2e-abf8-fae69627924f/WhatsApp_Image_2020-04-29_at_8.44.44_PM.jpeg)

JenkinsFile  avec la configuration complète de la pipeline

```powershell
pipeline {
  
  environment {
    registry = "306655/image_api_repo"
    registryCredential = 'dockerhub'
  }
  agent any
  

  stages {  // Define the individual processes, or stages, of your CI pipeline
    
    stage('Checkout') { // Checkout (git clone ...) the projects repository //test git-push
      
      steps {
        checkout scm
        
      }
    }
    
    stage('Building image') { //building image
      steps{
        script {
          docker.build("306655/image_api_repo","./simple_api/")
       }
      }
    }
    
    stage ('Test image') { // test image 
      agent{
        docker {image'306655/image_api_repo'}
      }
      steps {
      sh "curl -u toto:python -X GET http://localhot:5000/pozos/api/v1.0/get_student_ages"}
    }
    
    stage ( 'push image' ) { //push image
      steps {
        script {
        docker.withRegistry('https://hub.docker.com/r/306655/image_api_repo','registryCredential') {
          dockerImage.push() }
        }
      }
    }
    
}
}
```

erreur :

Jenkins n'arrive pas a faire le build de l'image 

```
var/jenkins_home/workspace/simple-python-yo@tmp/durable-5fe0000e/script.sh: 2: /var/jenkins_home/workspace/simple-python-yo@tmp/durable-5fe0000e/script.sh: docker: not found
[Pipeline] sh
[simple-python-yo] Running shell script
+ docker pull index.docker.io/python
/var/jenkins_home/workspace/simple-python-yo@tmp/durable-95921c60/script.sh: 2: /var/jenkins_home/workspace/simple-python-yo@tmp/durable-95921c60/script.sh: docker: not found
```

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/03e342a9-2e2d-4ddf-92e8-2a48cc85ac19/WhatsApp_Image_2020-04-29_at_8.40.49_PM.jpeg](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/03e342a9-2e2d-4ddf-92e8-2a48cc85ac19/WhatsApp_Image_2020-04-29_at_8.40.49_PM.jpeg)

Apres beaucoup de recherche , on a compris que pour pouvoir effectuer le build  le contenaire Jenkins doit contenir des binaires docker et faire une canalisation entre les sockets du docker dans le contenaire avec les socket du docker dans la machine host.

On a fais un docker build avec le dockerfile qui se trouve ci-dessus pour obtenir le bon serveur jenkins fonctionel dans notre cas.

```docker
from jenkins/jenkins:lts
 
USER root
RUN apt-get update -qq \
    && apt-get install -qqy apt-transport-https ca-certificates curl gnupg2 software-properties-common 
RUN curl -fsSL https://download.docker.com/linux/debian/gpg | apt-key add -
RUN add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/debian \
   $(lsb_release -cs) \
   stable"
RUN apt-get update  -qq \
    && apt-get install docker-ce=17.12.1~ce-0~debian -y
RUN usermod -aG docker jenkins
```

Jenkins Dockerfile 

On a lancer l'image obtenu par ce Dockerfile avec la commande suivante : 

```docker
docker run -p 8083:8080 -v /var/run/docker.sock:/var/run/docker.sock --name jenkins1.4 86abae6b9c63
```

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/02e2ff5c-5340-496f-b651-efcd631b536f/WhatsApp_Image_2020-04-29_at_9.08.17_PM.jpeg](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/02e2ff5c-5340-496f-b651-efcd631b536f/WhatsApp_Image_2020-04-29_at_9.08.17_PM.jpeg)

Problème résolu , build avec succès.

Voila le script pour faire le test et le push d'image dans le Dockerhub

```docker
environment {
    registry = "306655/image_api_repo"
    registryCredential = 'dockerhub'
  }
```

```docker
stage ('Test image') { // test image 
      agent{
        docker {image'306655/image_api_repo'}
      }
      steps {
      sh "curl -u toto:python -X GET http://localhot:5000/pozos/api/v1.0/get_student_ages"}
    }
    
    stage ( 'push image' ) { //push image
      steps {
        script {
        docker.withRegistry('https://hub.docker.com/r/306655/image_api_repo','registryCredential') {
          dockerImage.push() }
        }
      }
    }
```

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/2af67617-0885-4fd5-b62c-66eb0e9a360d/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/2af67617-0885-4fd5-b62c-66eb0e9a360d/Untitled.png)

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/7db3d95d-12cd-4e1d-83c3-f7b034bab90f/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/7db3d95d-12cd-4e1d-83c3-f7b034bab90f/Untitled.png)

# Ansible

Ansible est un outil d'approvisionnement, de gestion de configuration et de déploiement d'applications open source.

## Configurations SSL

Le problème le plus connu dans l'informatique c'est savoir où stocker nos informations d'authentification et aussi dans Ansible il faut bien savoir comment le faire en toute sécurité, car les informations ont besoin être disponible pour Ansible pour que la connexion fonctionne.

Aditionellement, certaines tâches nécessitent une exécution privilégiée à l'aide de sudo, qui nécessite un autre mot de passe.

Voila la méthode la plus facile pour notre cas :

```
# *Dans le fichier d'inventaire*

[all:vars]
ansible_user=oualid-ilyass
ansible_pass=oi-pass
ansible_sudo_pass=oi-sudo-pass
```

Bien que conviennent, on dirait que nous pouvons tous comprendre pourquoi cela est dangereux. Une alternative consiste à placer les informations d'identification dans un fichier .ssh / config sur notre machine locale. Cela l'empêche d'être capturé dans le contrôle de version et divulgué au public.

## Déploiement

Ansible utilise un fichier d'inventaire pour gérer et organiser nos serveurs. Avant de pouvoir faire quoi que ce soit, nous devons créer un fichier d'inventaire(Inventory).

```
# *Dans le fichier d'inventaire*

[pozosApp]
192.168.57.102
```

pozosApp c'est ce que nous référençons chaque fois que nous voulons exécuter un playbook sur un serveur. En dessous, il y aura une liste d'adresses IP ou de noms d'hôte pour tout serveur qui devrait être regroupé sous le nom.

```powershell
# simple copier
ansible -v pozosApp -m copy -a "src=dist/ dest=/var/www/html mode=0755 
owner=oualid-ilyass group=oi-groupe" -i inventory -b
```

Donc là on a exécuté cette commande pour copier nos fichiers d'application statique dans le répertoire / var / www / html d'un serveur Web Apache par exemple.

Cette méthode est un peut compliquée dans les cas ou on aura des configurations supplémentaire. Donc c'est bien de créer un fichier de déploiement YAML dans lequel on peut déclarer tout nos configurations.

```yaml
# deploiment.yaml

---
- host: pozosApp
  task:
    - name: Copy files to remote host
      copy:
        src: dist/
        dest: /var/www/html
        owner: oualid-ilyass
        group: oi-groupe
        mode: 0755
```

La on va ajouter une étape supplémentaire pour installer le dossier de notre application et déployer le docker image.

```yaml
# simple-deploy.yml
---
name: Deploy the application to the "staging" server
  hosts: pozosApp
  tasks:
    - name: Create the application directory
      file:
        path: /home/pozos/
        state: directory
        owner: oualid-ilyass
        group: oi-groupe
    - name: Copy docker files over
      copy:
        src: ../../../docker/
        dest: /home/pozos/
        owner: oualid-ilyass
        group: oi-groupe
```

Mais dans notre cas on a besoin de déployer un container et pas juste des fichier, donc dans notre pipeline il faut ajouter les lignes suivantes :

```
stage('Destroy') {
            steps {
                echo '> Destroying the docker artifacts ...'
                sh 'make -sC docker/ destroy'
            }
        }
        stage('Deploy') {
            steps {
                echo '> Deploying the application ...'
                sh 'ansible-playbook /simple-deploy.yml -i /inventory.yml'
            }
        }
```

Pour déployer notre application à l'aide de notre playbook, nous exécutons la commande Ansible suivante.

```powershell
ansible-playbook -i inventory simple-deploy.yml
```

## Datadog

Installation dans docker, en utilisant notre clé d'api fournit par la plateforme.

```powershell
DOCKER_CONTENT_TRUST=1 
docker run -d --name dd-agent 
           -v /var/run/docker.sock:/var/run/docker.sock:ro 
           -v /proc/:/host/proc/:ro 
           -v /sys/fs/cgroup/:/host/sys/fs/cgroup:ro 
           -e DD_API_KEY=d5a8f5aab4e6d55dfad7322fc7d273ee -e DD_SITE="datadoghq.eu"
            datadog/agent:7
```

Par défaut dogstatd écoute dans localhost, si on veut qu'il fait écoute depuis les autres containers il faut ajouter :

```powershell
-e DD_DOGSTATSD_NON_LOCAL_TRAFFIC=true
```

On fait le bind (liaison) du port statsd du container avec l'adresse IP de la machine, en ajoutant :

```powershell
-p 8125:8125/udp
```

Et enfin on configure notre client pour envoyer des paquets UDP à la machine.

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/bd6542c3-e0ae-476e-ae4f-14177f2e8c95/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/bd6542c3-e0ae-476e-ae4f-14177f2e8c95/Untitled.png)

Après l'installation, notre agent va envoyer un rapport au serveur(accusé de réception).

On peut accéder à notre tableau de bord, comme dans l'image ci-dessus on voit l'état de notre infrastructure chaque 10 minutes, et l'utilisation du processeur en temp réel.

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/0c9203be-372b-4125-bc60-44f1f833d861/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/0c9203be-372b-4125-bc60-44f1f833d861/Untitled.png)

Pour faire le monitoring sur docker daemon, il faut suivre les étapes suivantes :

1-Ajouter un utilisateur en exécutant l'agent dans docker.

```powershell
usermod -a -G docker dd-agent
```

2-Configurer l'agent pour se connecter a docker.

```powershell
init_config:

instances:
    - url: "unix://var/run/docker.sock"
      new_tag_names: true
```

3-Redémarrage de notre agent.

Sous docker on peut juste lancer la commande de l'installation

```powershell
DOCKER_CONTENT_TRUST=1 \
docker run -d -v /var/run/docker.sock:/var/run/docker.sock:ro \
              -v /proc/:/host/proc/:ro \
              -v /sys/fs/cgroup/:/host/sys/fs/cgroup:ro \
              -e DD_API_KEY=d5a8f5aab4e6d55dfad7322fc7d273ee \
              datadog/agent:latest
```

Sous Linux

```powershell
sudo service datadog-agent start
```

4-Verification :

```powershell
sudo docker exec -it jenkins s6-svstat /var/run/s6/services/agent/
```

Projet présenté par [HAMZAOUI Oualid](mailto:MohammedOualid.HAMZAOUI@supinfo.com) et [BEN HAKIM Ilyass](mailto:309742@supinfo.com)
