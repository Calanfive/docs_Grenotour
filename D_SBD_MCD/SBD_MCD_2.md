```mermaid
erDiagram
    filtre||--||itineraire :xxx
    filtre||--||type_de_sejour :xxx
    filtre||--||lieu_visiter :xxx
    filtre||--||evenement :xxx
    filtre||--||restaurant :xxx
    filtre||--||bar :xxx


    init}|--|{lieu :xxx
    itineraire}|--|{ init :xxx




    type_activite||--|| lieu :xxxx
    %% lieu||--||itineraire :xxx
    %% lieu||--||type_de_sejour :xxx
    %% lieu||--||lieu_visiter :xxx
    %% lieu||--||evenement :xxx
    %% lieu||--||restaurant :xxx
    %% lieu||--||bar :xxx

    itineraire_favoris}|--||utilisateur : xxxx
    itineraire|o--|{itineraire_favoris :xxxx
    utilisateur||--||pref :xxx
    utilisateur||--||itineraire : xxx

    filtre{
        INT filtre_id PK
        INT type_activite_id FK
        INT lieu_visiter_id FK
        INT evenement_id FK
        INT restaurant_id FK
        INT bar_id FK
    }
    type_de_sejour{
        INT type_activite_id PK
        VAR(255) romentique
        VAR(255) famille
        VAR(255) nature
        VAR(255) aventure
        VAR(255) art
    }
    lieu_visiter{
        INT lieu_visiter_id PK
        VAR(255) gratuit
        VAR(255) exterieur
        VAR(255) interieur
        VAR(255) beaux_point_vue
        VAR(255) art
    }
    evenement{
        INT evenement_id PK
        VAR(255) theatre
        VAR(255) musique
        VAR(255) fete
        VAR(255) dense
        VAR(255) nature
    }
    restaurant{
        INT restaurant_id PK
        VAR(255) gourmande
        VAR(255) local
        VAR(255) vege
        VAR(255) vegan
    }
    bar{
        INT bar_id PK
        VAR(255) biere
        VAR(255) vin
        VAR(255) pub
        VAR(255) cosy
        VAR(255) chil
    }


    init{
        INT itineraire_id FK
        INT pont_interet_id FK
    }
    type_activite{
        INT type_activite_id PK
        INT filtre_id FK
        VAR(255) bar
        VAR(255) restaurant
        VAR(255) loisir
        VAR(255) culture
    }

    utilisateur{
        INT utilisateur_id PK

        VAR(255) itineraire_id FK
        VAR(255) itineraire_favorie_id FK
        
        VAR(255) nom
        VAR(255) prenom 
        VAR(255) mail 
        VAR(255) MOT 
        INT telephone 
    }
    itineraire{
        INT itineraire_id PK

        INT nbr_pions 
        INT itineraire_nbr_voyageurs 
        INT itineraire_nbr_restaurants 
        INT itineraire_nbr_loisirs 
        INT itineraire_nbr_bars 
        INT itineraire_nbr_hotels 
    }

    itineraire_favoris{
        INT itineraire_favorie_id PK

        INT nbr_pions
        INT itineraire_nbr_voyageurs 
        INT itineraire_nbr_restaurants 
        INT itineraire_nbr_loisirs 
        INT itineraire_nbr_bars 
        INT itineraire_nbr_hotels 
    }
    lieu {
        INT pont_interet_id PK

        INT centre_activicter_id FK 
        INT type_activite_id FK
        
        INT nbr_visiteur 
        INT nbr_visiteur_mois 
        INT nbr_etoile 
        INT duree
        INT telephone 
        VAR(255) adress
        VAR(255) mail
    }

    pref{
        INT pref_id
        VAR(255) langue
    }
```

```dbdiagram
// Use DBML to define your database structure
// Docs: https://dbml.dbdiagram.io/docs
// les machin bidul truc qui permet de les reliers je ne me rappel plus du sens



table filtre{
  filtre_id PK
  type_activite_id FK
  lieu_visiter_id FK
  evenement_id FK
  restaurant_id FK
  bar_id FK
}
table type_de_sejour{
  type_activite_id PK
  romentique varchar(255)
  famille varchar(255)
  nature varchar(255)
  aventure varchar(255)
  art varchar(255)
}
table lieu_visiter{
  lieu_visiter_id PK
  gratuit varchar(255)
  exterieur varchar(255)
  interieur varchar(255)
  beaux_point_vue varchar(255)
  art varchar(255)
}
table evenement{
  evenement_id PK
  theatre varchar(255)
  musique varchar(255)
  fete varchar(255)
  dense varchar(255)
  nature varchar(255)
}
table restaurant{
  restaurant_id PK
  gourmande varchar(255)
  local varchar(255)
  vege varchar(255)
  vegan varchar(255)
}
table bar{
  bar_id PK
  biere varchar(255)
  vin varchar(255)
  pub varchar(255)
  cosy varchar(255)
  chil varchar(255)
}

Table utilisateur { // client
  utilisateur_id PK
  itineraire_id FK
  itineraire_favorie_id FK
  nom varchar(255)
  prenom varchar(255)
  mail varchar(255)
  MOT varchar(255)
  telephone int 
}

table init{
  itineraire_id FK
  pont_interet_id FK
}

table type_activite{
  type_activite_id PK
  filtre_id FK
  bar varchar(255)
  restaurant varchar(255)
  loisir varchar(255)
  culture varchar(255)
}

Table  lieu {
  lieu_id PK
  centre_activicter_id FK 
  type_activite_id FK
  nbr_visiteur int
  nbr_visiteur_mois int 
  nbr_etoile int
  duree int
  telephone int 
  adress varchar(255)
  mail varchar(255)
}

table pref{
  pref_id PK
  langue varchar(255)
}

Table itineraire { 
  itineraire_id PK

  itineraire_nbr_voyageurs int
  itineraire_nbr_restaurants int
  itineraire_nbr_loisirs int
  itineraire_nbr_bars int
  itineraire_nbr_hotels int
}

table itineraire_favorie {
  itineraire_favorie_id PK

  itineraire_nbr_voyageurs int
  itineraire_nbr_restaurants int
  itineraire_nbr_loisirs int
  itineraire_nbr_bars int
  itineraire_nbr_hotels int

}

```