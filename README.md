# Windows-Event-Log  

## Configuration du Windows Server  
  
Pour cette quête j'ai utilisé une VM Windows Server 2022, j'ai mis une interface Réseau NAT avec un réseau préconfiguré en 192.168.100.0/24.  
J'ai mis le serveur en IP fixe, en 192.168.100.50 et j'ai ensuite installé mle rôle DNS dessus (via le Sever Manager).  
J'ai aussi configuré des enregistrements pour le DNS en reprenant la quête Windows DNS qu'on avait fait il y a quelques semaines.  
Ensuite j'ai connecté une autre VM Windows 10 sur le même réseau pour pouvoir faire des requêtes DNS depuis celle-ci.  

## Préparation des enregistrements de Logs dans Event Viewer  

Ensuite j'ai ouvert Event Viewer depuis le serveur et j'ai préparé l'enregistrement demandé dans le Challenge de la quête :  
  
### Configuration de ta vue personnalisée :
  **Niveaux à surveiller**  
    Critique (1)  
    Erreur (2)  
    Avertissement (3)  
    Information (4) - Pour les démarrages/arrêts  
  **Sources d'événements à inclure**  
    DNS-Server-Service: Pour les opérations du serveur DNS  
    DNS Client Events: Pour les événements côté client  
 
<P ALIGN=CENTER><IMG SRC="https://github.com/julien-Nmd/Windows-Event-Log/blob/main/Capture%20d%E2%80%99%C3%A9cran%20du%202025-01-02%2021-43-04.png" Width=800></P>  

  **Événements critiques (ID principaux)**  
    2: Démarrage du serveur DNS  
    4: Arrêt du serveur DNS  
    409: Erreur de résolution de nom  
    501-502: Échec de chargement de zone  
    6001-6002: Problèmes de réplication DNS  

  

<P ALIGN=CENTER><IMG SRC="https://github.com/julien-Nmd/Windows-Event-Log/blob/main/Capture%20d%E2%80%99%C3%A9cran%20du%202025-01-02%2021-46-03.png" Width=800></P>  

Ensuite j'ai enregistré cette "vue presonnalisée" en "Custom View" et je suis allé dans la partie **Custom View** dans la partie de droite de Event Viewer.  
Là, j'ai cliqué sur **Save All Events in Custom View As...** j'ai enregistré au format XML un fichier que j'ai nommé **DNS-Event-Log.xml**.  
Bon je vous avoue que là je ne suis plus tout à fait sûr de moi et j'en appelle à vos commentaires pour voir si j'ai compris ou pas mais je suis pas sûr que le fichier en question soit bien "lisible". En tout cas pas de Github directement mais plutot d'un navigateur internet. En tout Cas le fichier en question est dans mon dépot GitHub.  
D'avance merci pour votre correction. 

