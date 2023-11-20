# API d'enregistrement d'informations de serveur Discord

Vous devez créer une API pour permettre à des Bots Discord d'enregister les informations d'un Serveur Discord, dans le but d'utiliser ces informations ultérieurement.

## Spécifications fonctionnelles

- Les réponses de l'API doivent être normalisées au format suivant de façon automatique[¹](#explain) :
  - `message` : Ce champ contient un message expliquant quelle opération selon quels critères s'est exécutée correctement (e.g: Guild for 'guild_uuid' uuid has been found).
  - `data` : Ce champ contient les données de l'opération.
  - `statusCode` : Ce champ contient le code de status de la requête (Un code HTTP)
- Les erreurs d'accession aux données via `Prisma` doivent être automatiquement gérées et renvoyées des réponses claires expliquant la raison de l'erreur sans encombrer les logs de l'API en plus, le code de status de la réponse doit être celui qui correspond à l'erreur survenue. Vous devez coder ce système grâce à un intercepteur.

### Annexes

<a id="explain"></a>¹ : Pour ce faire vous devez utiliser un intercepteur et coder un système qui crée un message cohérent en fonction du contexte et qui normalise automatiquement la réponse.

### Glossaire

- `Guild` : Le terme Guild signifie `Serveur Discord`.