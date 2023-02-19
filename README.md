## Optimisation des performances de l'API Java | Spring Boot
Dans ce repo, nous allons voir quelques astuces générales pour optimiser les performances de l'API en Java - Spring Boot.

*Notez que je suis toujours dans le processus d'apprentissage - probablement sans fin :)-*

De nombreux facteurs peuvent affecter les performances de l'API, qui peuvent être résumés comme suit.
- Requête lente de la base de données
- Logique métier complexe
- Code peu performant
- Ressources insuffisantes

### Astuces d'optimisation
---
- Convertir les API appelées séquentiellement en appels parallèles
- Éviter les grosses transactions `@Transactional(rollbackFor=Exception.class)` sur la classe
- Séparer les opérations **non transactionnelles** et les opérations **transactionnelles** dans le code métier
- On peut utiliser la transaction programmatique de spring `TransactionTemplate`
- **Ajouter l'index approprié** : nous devons ajouter les index appropriés à vos tables de base de données quand la quantité de données dans une seule table continue d'augmenter et que les performances des requêtes de la base de données se détériorent.
- **Renvoyer moins de données** : Si nous interrogeons une grande quantité de données qualifiées, nous n'avons pas besoin de renvoyer toutes les données. Nous pouvons fournir des données de manière incrémentielle sous forme de pagination. De cette manière, nous avons besoin de moins de données à transmettre via le réseau, de moins de temps pour coder et décoder les données et d'une réponse API plus rapide.
- **Utiliser le cache** : La mise en cache est une solution spatio-temporelle. Les données fréquemment consultées par certains utilisateurs sont directement mises en cache en mémoire. Étant donné que la vitesse de lecture de la mémoire est beaucoup plus rapide que celle des E/S disque, nous pouvons également utiliser une mise en cache appropriée pour améliorer les performances de l'API. Simplement, nous pouvons utiliser Java HashMap, ConcurrentHashMap ou un cache local tel que la caféine ou un middleware de cache distribué tel que Memcached et Redis.

*Bon apprentissage...*