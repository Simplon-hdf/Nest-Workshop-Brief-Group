# Brief en groupe pour le Workshop Nest

Ce repository est dédié au Workshop Nest pour la promo ".Net Roubaix P4", il fait suite à [ce repo](https://github.com/benjGam/E-Commerce-API-NW/tree/main).

## Contraintes pour la méthodologie de travail

Vous devez travailler en groupe sur un des projets présentés ci-dessous. Pour ce faire, vous devez travailler en collaboration par groupe de 3. Vous devez utiliser Git pour collaborer ainsi que le workflow Gitflow. Vous travaillez sur un repository commun (une seule origine pour tous les membres).

## Les projets disponibles

- API d'e-commerce [Voir le projet](./e-commerce/README.md)
- API interne pour une Médiathèque [Voir le projet](./mediatheque/README.md)
- API d'enregistrement d'informations de serveur Discord (Bonus) [Voir le projet](./discord-bot/README.md)

## Qualité de code

- Les méthodes dans les contrôleurs et dans les services doivent être nommées de la même façon.
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

Les méthodes doivent être agencées de la même façon dans les contrôleurs et les services, pour permettre de naviguer facilement dans le code.

</details>

## Spécifications techniques globales

- Les réponses d'API doivent être normalisées.
<details>
<summary>Exemple</summary>

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
</details>

- Les APIs doivent être documentées avec `Swagger`.