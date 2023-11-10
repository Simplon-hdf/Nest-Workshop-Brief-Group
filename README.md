# API interne pour une Médiathèque

Vous devez créer une API pour les employés d'une médiatèques, ces employés doivent référencés chaque livre sur le site de la médiathèque pour examiner les disponibilités des livres.

## Spécifications non fonctionnelles

- Les employés doivent être authentifiés afin d'effectuer des opérations.
- Chaque livre doit avoir un nom et un autheur.
- Chaque livre peut être sujet à un emprun de la part d'un client de la médiathèque.
- Chaque emprun à un date de début et une date de fin.

## Spécifications fonctionnelles

- Les réponses de l'API doivent être normalisées au format suivant :
  - `message` : Ce champ contient un message expliquant quelle opération selon quels critères s'est exécutée correctement (e.g: Book for 'book_uuid' uuid has been found).
  - `data` : Ce champ contient les données de l'opération.
  - `statusCode` : Ce champ contient le code de status de la requête (Un code HTTP)
- Les erreurs d'accession aux données via `Prisma` doivent être automatiquement gérées et renvoyées des réponses claires expliquant la raison de l'erreur sans encombrer les logs de l'API. Vous devez coder ce système grâce à un intercepteur.