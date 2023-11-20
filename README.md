# API interne pour une Médiathèque

Vous devez créer une API pour les employés d'une médiatèque, ces employés doivent référencés chaque livre sur le site de la médiathèque pour examiner les disponibilités des livres.

## Spécifications fonctionnelles

- Les employés doivent être authentifiés afin d'effectuer des opérations.
- Chaque livre doit avoir un nom et un autheur.
- Chaque livre peut être sujet à un emprunt de la part d'un client de la médiathèque.
- Chaque emprunt à un date de début et une date de fin.

## Spécifications techniques

- Les erreurs d'accession aux données via `Prisma` doivent être automatiquement gérées et renvoyées des réponses claires expliquant la raison de l'erreur sans encombrer les logs de l'API en plus, le code de status de la réponse doit être celui correspondant à l'erreur survenue. Vous devez coder ce système grâce à un intercepteur.