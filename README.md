# Rapport Partie 1 de "Comment Implémenter Déployer Tester Consommer un Web service SOAP WSDL avec JAXWS" par Monsieur Mohamed Youssfi

## Introduction
La vidéo présente un projet de développement d'un service web basé sur SOAP (Simple Object Access Protocol) . Le projet est structuré autour d'une application bancaire simple, qui expose des opérations telles que la conversion de devises et la gestion de comptes bancaires. L'objectif principal est de créer un service web SOAP utilisant Java et de tester ce service à l'aide de SoapUI , une outil populaire pour tester les services web.
  - Lien : https://www.youtube.com/watch?v=WZi3s2bZNAE

## Structure du projet :
### 1. Arborescence du Projet
Le projet est organisé dans un répertoire standard Maven :
  - src/main/java : Contient le code source.
    * ws : Package contenant les classes liées au service web.
      * BanqueService.java : Classe principale définissant les méthodes du service web.
      * Compte.java : Classe représentant un compte bancaire.
      * ServerJWS.java : Classe principale servant à démarrer le serveur SOAP.
  - src/main/resources : Contient les ressources nécessaires au projet.
  - target : Répertoire généré automatiquement par Maven après la compilation et la construction du projet.
  - pom.xml : Fichier de configuration Maven pour gérer les dépendances et les configurations du projet.
### 2. Fichiers Principaux
  - ServerJWS.java : Cette classe sert à démarrer le serveur SOAP. Elle utilise la bibliothèque jakarta.xml.ws.Endpoint pour publier le service web sur un endpoint spécifique (http://0.0.0.0:9090/).
      * Endpoint.publish(url, new BanqueService()) : Publie le service web BanqueService sur l'URL spécifiée.
      * System.out.println("Server started on " + url) : Affiche un message indiquant que le serveur est démarré.
  - BanqueService.java : Cette classe définit les méthodes du service web. Elle est annotée avec @WebService, ce qui indique qu'elle expose des opérations via SOAP.
      * conversion(double mt) : Méthode permettant de convertir un montant en euros en dirhams marocains (multiplié par 11).
      * getCompte(int code) : Méthode retournant un objet Compte correspondant au code fourni.
      * listComptes() : Méthode retournant une liste de comptes générés aléatoirement.
  - Compte.java : Cette classe représente un compte bancaire. Elle contient des attributs tels que le code du compte, le solde et la date de création.
      * Constructeurs et Getters/Setters : Permettent de manipuler les propriétés du compte.
        
  ## Étapes de Développement
  ### 1. Création du Service Web :
  - La classe BanqueService est annotée avec @WebService pour indiquer qu'elle expose des opérations via SOAP.
  - Les méthodes sont annotées avec @WebMethod pour les rendre accessibles depuis le client SOAP.
  - Les paramètres des méthodes sont annotés avec @WebParam pour fournir des noms significatifs aux paramètres lors de l'exécution du service.
  ### 2. Publication du Serveur SOAP :
  - La classe ServerJWS utilise Endpoint.publish() pour publier le service web sur l'URL http://0.0.0.0:9090/.
  - Une fois le serveur démarré, il est possible d'accéder au fichier WSDL via http://localhost:9090/BanqueWS?wsdl.
  ### 3. Test du Service avec SoapUI :
  - Après avoir démarré le serveur, SoapUI est utilisé pour tester les opérations du service web.
  - Les tests incluent :
    * Appel de la méthode conversion pour vérifier la conversion de devises.
    * Appel de la méthode getCompte pour récupérer un compte spécifique.
    * Appel de la méthode listComptes pour obtenir une liste de comptes.


## Résultats :
### Essai :
![image](https://github.com/user-attachments/assets/8382151a-5673-4aa9-b9d0-335f0818f590)
![image](https://github.com/user-attachments/assets/7b02e42f-44ba-4b7a-b678-833507d0c4d5)
![image](https://github.com/user-attachments/assets/eb1214d4-b37b-4ec2-a23b-b5bad0e4ca37)
![image](https://github.com/user-attachments/assets/f493fa76-ffe4-46a4-a5fd-d64cb72aacad)

### SoapUI:
![image](https://github.com/user-attachments/assets/50e1932c-69bc-47a4-be55-9bded1a3ee19)
![image](https://github.com/user-attachments/assets/c60f1c06-0c63-4890-898f-e3acacc65e3b)


## Conclusion
La vidéo présente un projet complet de développement d'un service web SOAP en Java. Le projet comprend :
  - Une classe ServerJWS pour démarrer le serveur SOAP.
  - Une classe BanqueService exposant des opérations bancaires via SOAP.
  - Une classe Compte modélisant un compte bancaire.
  - Des tests effectués avec SoapUI pour valider le fonctionnement des opérations du service web.
Ce projet illustre clairement les étapes nécessaires pour créer et tester un service web SOAP, en mettant l'accent sur la simplicité et la praticité.

