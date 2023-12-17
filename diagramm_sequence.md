# 1 Séquence génération d'itinéraire

```mermaid
sequenceDiagram
    user->>+GrenoTour: demande la page filtre
    GrenoTour->>+user: envoie la page "filtre"
    user->>+GrenoTour: envoie ses parramètres 
    GrenoTour->>+GrenoTour: applique les filtres
    GrenoTour->>+BDD: envoie une requette
    BDD->>+GrenoTour: envoie les résultats trouvés
    GrenoTour->>+user: créer un itinéraire
    user->>+GrenoTour: itinéraire pas d'accord
    GrenoTour->>+BDD: envoie une requette
    BDD->>+GrenoTour: envoie les résultats trouvés
    GrenoTour->>+user: créer un deuxième itinéraire
```

# 2 Séquence inscription d'un nouvel utilisateur

```mermaid
sequenceDiagram
    GrenoTour->>+user: Ouverture du formulaire
    user->>+GrenoTour: Envoi du formulaire
    GrenoTour->>+GrenoTour: Adresse mail check
    alt Adresse mail déjà utilisé / non valide
        GrenoTour->>+user: Login ou mot de passe refusé 
    else Identifiants valides
        GrenoTour->>+BDD: Requête inscription
    BDD->>+GrenoTour: Validation inscription
    GrenoTour->>+user: Accusé de validation (mail)
    end
```

# 3 Séquence authentification
 
 ```mermaid
 sequenceDiagram
    User->>+GrenoTour: Demande d'authentification
    User->>+GrenoTour: Saisir mot de passe et login
    GrenoTour->>+GrenoTour: Adresse mail check
    alt Identifiants non reconnus
        GrenoTour->>+User: Login ou mot de passe refusé 
    else Identifiants corrects
        GrenoTour->>+ User: Connexion établie
        GrenoTour->>+GrenoTour: Chargement de la carte
    end
 ```

# 4 Séquence enregistrement (favoris) et partage d'un itinéraire