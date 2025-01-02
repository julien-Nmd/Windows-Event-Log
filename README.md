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

