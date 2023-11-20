# API d'e-commerce

Vous devez créer une API d'e-commerce pour permettre à des utilisateurs de commander des articles.

## Spécifications fonctionnelles

### Clients

- Les Clients doivent être composés des champs :
  - UUID (De type VARCHAR de longueur 36)
  - Un pseudo (De type VARCHAR de longueur 20)
  - Un nom d'utilisateur (De type VARCHAR de longueur 30)
  - Un mot de passe (De type VARCHAR de longeur 72)
  - Une date de création (De type DATE)
- Les Clients doivent être authentifié afin d'effectuer des commandes sur les produits.

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
  - `statusCode` : Ce champ contient le code de status de la requête (Un code HTTP)

### Exemple

Pour normaliser vos réponses, faites comme suit :

```ts
public maLogicPourRécupererUnProduit(uuid: string) {
  //Logic de récupération
  return {
    message: `Product for '${uuid}' has been getted.`
    data: ,//Les données du produit
    statusCode: HTTPStatus.OK,
  }
}
```

Ou d'une autre façon qui renverrait un résultat similaire.

## Qualité de code

Les méthodes dans les controlleurs et dans les services doivent être nommées de la même façon.
<details>
<summary>Exemple</summary>

`controller.ts`

```ts
public getByUUID(uuid: string) {
  service.getProductByUUID(uuid);
}
```

`service.ts`

```ts
public getByUUID(uuid: string) {
  //logic here
}
```
</details>