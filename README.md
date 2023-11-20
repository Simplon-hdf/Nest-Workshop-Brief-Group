# API d'e-commerce

Vous devez créer une API d'e-commerce pour permettre à des utilisateurs de commander des articles.

## Spécifications fonctionnelles

### Utilisateurs

- Les Utilsateurs doivent être composés des champs :
  - UUID (De type VARCHAR de longueur 36)
  - Un pseudo (De type VARCHAR de longueur 20)
  - Un nom d'utilisateur (De type VARCHAR de longueur 30)
  - Un mot de passe (De type VARCHAR de longeur 72)
  - Une date de création (De type DATE)
- Les Utilisateurs doivent être authentifiés afin d'effectuer des commandes sur les produits.

### Produits

- Les produits doivent être composés des champs :
  - UUID (De type VARCHAR de longueur 36)
  - Un nom (De type VARCHAR de longueur 20)
  - Une description (De type LONGTEXT de longueur 500)
  - Un prix unitaire (De type FLOAT)
  - Une quantité (De type INT >= 1)
  - Une date d'ajout (De type DATE)
  - Une date de mise à jour (De type DATE)

### Commandes

- Les commandes doivent être composées des champs :
  - Un numéro (De type INT en auto-increment)
  - L'UUID d'un Client
  - L'UUID d'un Produit
  - Une quantité de produit (De type INT >= 1)
  - Un prix total (TTC)
  - Une date de création (De type DATE)
  - Une date d'expedition (De type DATE)

## Spécifications techniques

- Les réponses de l'API doivent être normalisées au format suivant :
  - `message` : Ce champ contient un message expliquant quelle opération selon quels critères s'est exécutée correctement (e.g: User for 'user_uuid' uuid has been found).
  - `data` : Ce champ contient les données de l'opération.
  - `statusCode` : Ce champ contient le code de status de la requête (Le code HTTP correspondant)
- L'API doit être documentée avec `Swagger`.

### Exemple

Pour normaliser vos réponses, faites comme suit :

```ts
public logicToGetProduct(uuid: string) {
  //Logic
  return {
    message: `Product for '${uuid}' has been getted.`
    data: ,//Product datas
    statusCode: HTTPStatus.OK,
  }
}
```

Ou d'une autre façon qui renverrait un résultat similaire.