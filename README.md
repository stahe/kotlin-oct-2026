# Apprentissage du langage Kotlin 2.4

📖 **Lire le tutoriel : [https://stahe.github.io/kotlin-oct-2026/](https://stahe.github.io/kotlin-oct-2026/)**

Ce cours apprend le langage [Kotlin](https://kotlinlang.org/) 2.4 **par l'exemple** : plus de deux cents programmes (337 fichiers Kotlin), commentés ligne par ligne, dont les résultats d'exécution sont reproduits. Il part des bases du langage et va jusqu'aux coroutines, à l'accès aux bases de données avec JDBC et Hibernate, à la programmation réseau et aux services web avec Spring Boot.

C'est le portage en Kotlin du cours [Apprentissage du langage Java 25](https://stahe.github.io/java-oct-2026/) (octobre 2026), lui-même portage du cours [C# 14](https://stahe.github.io/csharp-oct-2026/), réécriture d'un cours C# de 2008 : même plan, mêmes exemples, même fil rouge, mais écrits dans le Kotlin d'aujourd'hui. Tous les programmes compilent **sans erreur ni avertissement** avec Kotlin 2.4.20 (avertissements traités comme des erreurs) et ont été exécutés sur le JDK 25 ; les résultats reproduits dans le cours sont ceux de ces exécutions.

| Cours Java 25 (2026) | Cours Kotlin 2.4 (2026) |
|---|---|
| Java 25 (LTS), JDK 25 | Kotlin 2.4.20, JDK 25 |
| fichiers source compacts (`java Prog.java`) | fonctions `main` de haut niveau, `kotlinc`, triangle vert d'IntelliJ IDEA |
| projets Maven (`pom.xml`) | projets Gradle en Kotlin DSL (`build.gradle.kts`), wrapper Gradle 9.8 |
| `null`, classes enveloppes et `Optional` | sûreté vis-à-vis de `null` dans le système de types (`?.`, `?:`, `!!`) |
| accesseurs, records, pas de surcharge des opérateurs | propriétés, classes de données, surcharge des opérateurs, fonctions d'extension |
| exceptions contrôlées, `try` avec ressources | exceptions toutes non contrôlées, `use` |
| API Stream | opérations sur les collections, séquences |
| interfaces fonctionnelles, lambdas | types fonctionnels, lambdas, fonctions `inline`, propriétés déléguées |
| `CompletableFuture`, threads virtuels | **coroutines** : `suspend`, `launch` / `async`, concurrence structurée, `Flow`, `Channel` |
| JUnit 6, Spring Framework 7 | JUnit 6 et `kotlin.test`, Spring Framework 7 (plugin `kotlin-spring`) |
| Jackson 3 | Jackson 3 avec les classes de données |
| JDBC, MySQL Connector/J, HikariCP | les mêmes, avec les idiomes de Kotlin |
| Hibernate 7 | Hibernate 7 avec les plugins `kotlin-jpa` (no-arg) et all-open |
| `HttpClient`, `Socket` / `ServerSocket` | les mêmes classes, en Kotlin |
| Spring Boot 4 | Spring Boot 4 en Kotlin |

## Le plan du cours

| Chapitre | Contenu |
|---|---|
| Installation | JDK 25, IntelliJ IDEA / VS Code, le compilateur `kotlinc`, Gradle (wrapper, Kotlin DSL), projets multi-modules |
| Les bases du langage | types, `val` / `var`, inférence, gabarits de chaînes, chaînes brutes, sûreté vis-à-vis de `null`, conversions, tableaux, opérateurs, `when`, intervalles et boucles, exceptions, `use`, énumérations, paramètres par défaut et nommés, fonctions locales, `Pair` et déstructuration |
| Classes, interfaces, classes de données | constructeurs primaires, propriétés, `object` et `companion object`, héritage, classes scellées, surcharge des opérateurs, indexeurs, classes de valeur, fonctions d'extension, interfaces, classes abstraites, génériques et variance, paquetages, classes de données, transtypage intelligent |
| Classes Kotlin d'usage courant | chaînes, tableaux, collections en lecture seule et modifiables, opérations fonctionnelles, **séquences**, fichiers texte et binaires, JSON avec Jackson 3, expressions régulières (`Regex`) |
| Architectures en couches | couches [dao] / [metier] / [ui], construction Gradle multi-projets, tests unitaires **JUnit 6** et `kotlin.test`, **injection de dépendances** avec Spring |
| Types fonctionnels, lambdas et événements | types fonctionnels, lambdas, références de fonctions, `fun interface`, fermetures, composition, fonctions `inline`, écouteurs, propriétés déléguées observables |
| Les threads d'exécution | `thread { }`, **threads virtuels**, `synchronized`, `@Volatile`, `ReentrantLock`, `Condition`, atomiques, sémaphores, collections concurrentes, `ExecutorService`, fork/join, `ThreadLocal`, `ScopedValue` |
| La programmation asynchrone | **coroutines** : fonctions `suspend`, `runBlocking`, `launch`, `async` / `await`, dispatchers, concurrence structurée, exceptions, annulation et délais, `Flow`, `Channel`, `CompletableDeferred`, parallélisme limité, coroutines et threads virtuels |
| L'accès aux bases de données avec JDBC | MySQL, MySQL Connector/J, `DataSource` et HikariCP, requêtes paramétrées et injection SQL, transactions, lots, JDBC avec threads virtuels et coroutines |
| **Hibernate** | entités Kotlin, `SessionFactory` / `Session`, CRUD, HQL et API Criteria, relations, migrations, concurrence optimiste, SQL natif, Spring ORM et `@Transactional` |
| Programmation Internet | TCP/IP, IPv6, clients et serveurs TCP (un thread virtuel par client), HTTP, `HttpClient`, SMTP avec Jakarta Mail |
| Services web | REST / JSON avec **Spring Boot 4** en Kotlin, clients console Kotlin, client web JavaScript, client Node.js |

## Le fil rouge : un calcul d'impôt en 9 versions

Tout le cours construit, version après version, une application de **calcul de l'impôt sur le revenu** :

- **version 1** : un programme unique ; **version 2** : des classes et des interfaces ; **version 3** : les données lues dans un fichier texte ou JSON ;
- **versions 4 et 5** : une architecture en couches, en sous-projets Gradle, testée avec JUnit et intégrée par injection de dépendances avec Spring ;
- **versions 6 et 7** : les données dans une base MySQL, lues avec JDBC puis avec Hibernate ;
- **version 8** : un serveur TCP de calcul de l'impôt et son client ;
- **version 9** : un service web REST Spring Boot, son client console et son client web.

## Technologies

Kotlin 2.4.20 · JDK 25 · Gradle 9.8 (Kotlin DSL) · IntelliJ IDEA · kotlinx.coroutines 1.11 · JUnit 6 · Spring Framework 7 · Jackson 3 · MySQL 8 · MySQL Connector/J 9 · HikariCP · Hibernate ORM 7.4 · Jakarta Persistence 3.2 · Spring Boot 4.1 · Laragon

## Prérequis

- Avoir déjà programmé dans un langage quelconque.
- Un [JDK 25](https://adoptium.net) (Eclipse Temurin ou autre distribution) et [IntelliJ IDEA](https://www.jetbrains.com/idea/) (Kotlin y est intégré). Gradle n'a pas à être installé : chaque dossier de chapitre contient son wrapper (`gradlew`). Si le JDK 25 n'est pas installé, Gradle le télécharge lui-même (plugin `foojay-resolver-convention`). [Laragon](https://laragon.org) pour MySQL (chapitres sur les bases de données). Les instructions d'installation sont données dans le cours.

## Auteur

Ce cours et ses codes ont été rédigés par **Claude**, l'IA d'[Anthropic](https://www.anthropic.com) (octobre 2026), à la demande de Serge Tahé, à partir de son cours Java 25.

Réviseur : [Serge Tahé](https://stahe.github.io)
