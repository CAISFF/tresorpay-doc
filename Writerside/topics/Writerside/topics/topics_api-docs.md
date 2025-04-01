# Vue d'ensemble des API

<!-- This document provides an introduction into your API. -->

## Introduction

La plateforme « TresorPay » est conçue pour permettre la collecte de toutes les natures de recettes de l’État, via des canaux digitaux. 
Cette plateforme numérique vise à fournir à l’ensemble des services de l’État et aux citoyens une solution unique de paiement. 
Ses caractéristiques principales incluent :
-	Centralisation des moyens de paiements : Intégration des moyens de paiement digitaux (mobile money, cartes bancaires, virement bancaire, etc.),
-	Variantes de la plateforme : Variante Web, mobile, USSD et TPE,
-	Traçabilité : Suivi en temps réel des recettes par nature et par structure,
-	Sécurité : Système de contrôle robuste pour minimiser les risques de fraude.

« TresorPay » comprend :
-	un module permettant aux citoyens de payer leurs impôts, taxes, droits et redevances en ligne sans se déplacer dans un service ;
-	un module permettant aux comptables du Trésor et ceux des collectivités :
     -	d’émettre des avis de recette et d’encaisser les paiements relatifs aux avis de recettes ;  
     -	de suivre en temps réels l’ensembles des paiements.
-	Un module de reporting permettant de faire la comptabilité des recettes par nature.

## Les fonctionnalités de API


Voici les principales fonctionnalités offertes par l'API TresorPay :
- <shortcut>Émettre un avis de recette </shortcut>: Cette fonctionnalité vous permet de créer un nouvel avis de recette pour un paiement,
- <shortcut>Vérifier l'état d'un avis de recette  </shortcut>: Vous pouvez consulter le statut actuel d'un avis de recette que vous avez émis,
- <shortcut>Annuler un avis de recette </shortcut>: Si nécessaire, vous pouvez annuler un avis de recette déjà émis,
 
## Authentification

L'API TresorPay utilise une méthode d'authentification basée sur les clés API.
Pour accéder aux ressources de l'API, vous devez inclure un token d'authentification dans l'en-tête de vos requêtes.
<a href="API-quickstart.md">Comment générer un token</a>
<code-block>
    Authorization: Bearer {votre_token}
</code-block>
Vous devez obtenir votre clé API via <a href="API-quickstart.md">Comment générer avoir un token TresorPay</a> pour l'utiliser dans vos requêtes.

## URL de base

L'URL de base pour toutes les requêtes API est la suivante :
- #### Production :
    Une fois que vous avez validé votre intégration dans l'environnement Sandbox, vous pouvez passer en mode Production pour traiter des paiements et générer des recettes gouvernementales en direct. 
    Les requêtes dans cet environnement génèrent des effets réels, et il est essentiel de bien tester toutes les fonctionnalités avant de passer à cette étape.
  <code-block>https://tresorpay.ml/api/public/v1</code-block>
- #### Sandbox (environnement de test) : 
  Cet environnement est conçu pour tester l'intégration et valider le fonctionnement de l'API dans un cadre sécurisé avant de passer en production. 
  Les requêtes effectuées dans cet environnement ne génèrent aucune transaction réelle et permettent d'identifier facilement les erreurs ou améliorations nécessaires.
  <code-block>https://recette.tresorpay.finances.ml/api/public/v1</code-block>


## Gestion des erreurs

En cas d'erreur, l'API retourne une réponse contenant des informations détaillées sur l'erreur rencontrée, ainsi qu'un code de statut HTTP approprié.

#### Exemple de réponse d'erreur :
<sample lang="JSON">
{
    "type": "https://www.jhipster.tech/problem/problem-with-message",
    "title": "La service client n'est pas dans cette structure",
    "status": 400,
    "instance": "/api/public/v1/payment/create-notice-recette",
    "message": "error.SERVICE_CLIENT_NOT_FOUND",
    "params": "appTransaction"
}
</sample>

#### Codes d'erreur courants :

- <shortcut>400 Bad Request</shortcut> : Paramètres manquants ou invalides dans la requête.
- <shortcut>401 Unauthorized</shortcut> : Clé API invalide ou manquante.
- <shortcut>404 Not Found</shortcut> : Ressource demandée introuvable.
- <shortcut>500 Internal Server Error</shortcut> : Erreur côté serveur.

## Versionnement

L'API TresorPay utilise un système de versionnement sémantique. Cela signifie que chaque version majeure de l'API peut introduire des
changements incompatibles avec les versions précédentes, tandis que les versions mineures ou les correctifs ajoutent des fonctionnalités sans casser la compatibilité.
#### Spécification de la version de l'API :
La version de l'API est incluse dans l'URL de la requête, comme suit :
<code-block>https://tresorpay.ml/api/public/v1/{point_de_terminaison}</code-block>
Lorsque de nouvelles versions sont publiées, la documentation sera mise à jour pour refléter les changements.
Nous vous recommandons de suivre les mises à jour et de migrer vers la dernière version stable dès que possible.


## Ressources supplémentaires
- <a href="https://tresorpay.ml">Plateforme officielle</a>
- <a href="https://portail.tresorpay.ml">Portail officiel</a>

