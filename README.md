# API d'e-commerce

Vous devez créer une API pour permettre à des utilisateurs de poster des articles à la vente, d'acheter des articles et de supprimer leurs articles de la vente.

## Spécifications fonctionnelles

- Les utilisateurs doivent être authentifié afin de consulter la liste des produits.
- Les produits doivent être composés des champs :
  - UUID (De type VARCHAR de longueur 36)
  - Un nom (De type VARCHAR de longueur 20)
  - Une description (De type LONGTEXT de longueur 500)
  - Un prix unitaire (De type FLOAT)
  - Une quantité (De type INT >= 1)
  - Une date d'ajout (De type DATE)
  - Une date de mise à jour (De type DATE)

## Spécifications techniques

- Les réponses de l'API doivent être normalisées au format suivant :
  - `message` : Ce champ contient un message expliquant quelle opération selon quels critères s'est exécutée correctement (e.g: User for 'user_uuid' uuid has been found).
  - `data` : Ce champ contient les données de l'opération.
  - `statusCode` : Ce champ contient le code de status de la requête (Un code HTTP)