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

## Qualité de code

- Les méthodes dans les controlleurs et dans les services doivent être nommées de la même façon.
<details>
<summary>Exemple</summary>

`products.controller.ts`

```ts
public getByUUID(uuid: string) {
  service.getByUUID(uuid);
}
```

`products.service.ts`

```ts
public getByUUID(uuid: string) {
  //logic here
}
```
</details>
- Le nommage des méthodes doit permettre de comprendre ce qu'elles font.
<details>
<summary>Exemple</summary>

`products.controller.ts`

```ts
public getByUUID(uuid: string) {
  //...
}
```

Ici, en lisant le nom "getByUUID" on sait qu'on récupère un **Produit** (Car la méthode se situe dans le controlleur **Product**) et on sait sur quel critère se base la récupération du Produit (Ici l'UUID).

</details>
- Les déclarations des méthodes doivent être dans un ordre précis et constant.
<details>
<summary>Exemple</summary>

`products.controller.ts`

```ts
public create(@Body() createProductDto: CreateProductDto) {}

public getByUUID(uuid: string) {}

public updateByUUID(uuid: string, @Body() updateProductDto: UpdateProductDto) {}

public deleteByUUID(uuid: string) {}
```

`products.service.ts`

```ts
public create(createProductDto: CreateProductDto) {}

public getByUUID(uuid: string) {}

public updateByUUID(uuid: string, updateProductDto: UpdateProductDto) {}

public deleteByUUID(uuid: string) {}
```

Dans l'ordre :

- Les routes `POST`.
- Les routes `GET`.
- Les routes `PUT/PATCH`.
- Les routes `DELETE`.

Les méthodes doivent être agencées de la même façon dans les controlleurs et les services, pour permettre de naviguer facilement dans le code.

</details>