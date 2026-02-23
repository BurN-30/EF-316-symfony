# Partie 1 

## Question 1 - Architecture Symfony

1. Request : Le navigateur envoie une requête HTTP (GET/POST)
2. Contrôleur frontal : Point d'entrée unique (`index.php`) qui intercepte la requête.
3. Routing : Le routeur analyse la méthode du contrôleur et trouve la route correspondante.
4. Controller : Symfony exécute la péthode du contrôleur liée à cette route.
5. Repository & Doctrine : Si nécessaire, le controleur utilise un Repository pour interroger la BDD via l'ORM Doctrine.
6. Vue (Twig) : Le controleur transmet la data au moteur de template Twig pour génerer le HTML.
7. Response : Le controleur renvoie une réponse au navigateur contenant le HTML et un code HTTP (200 ok ou 404 Not Found)

## Question 2 - Cache HTTP Symfony

Symfony s'appuie sur les standards HTTP selon 2 stratégies : 

- Expiration (cach-control, max-age) : la page est stockée temporairement. Le client la réutlise sans interroger le serveur tant qu'elle est valide.
- Validation (ETag, last-modified) : le client demande au seveur si la ressource a changé. Sinon, le serveur renvoie un code `304 not modified` vide, évitant un nouveau télechargement.

Avantages : Temps de réponse quasiment instantané, économie massive de ressources serveur (CPU,RAM), réduction de bande passante et suppressiosn des requetes inutiles en BDD.
