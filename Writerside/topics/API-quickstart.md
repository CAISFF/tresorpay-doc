# Démarrage avec l'API TresorPay

Dans cette section, vous trouverez un guide étape par étape pour commencer à utiliser l'API TresorPay rapidement.

## Prérequis
Avant de commencer à utiliser l'API, assurez-vous d'avoir

* <ui-path>Compte client</ui-path>

## Authentification

L'authentification à l'API TresorPay se fait via un mécanisme OAuth2. 
Vous devez disposez d'un **client_id** et **client_secret** qui sont fournies 
par les administrateurs de la plateforme. 
Ces informations sont nécessaires pour obtenir un token d'accès permettant d'interagir avec l'API.

Voici les étapes pour obtenir un **token d'accès** en utilisant le **client_id** et le **client_secret** fournis par les administrateurs de la plateforme :
#### Étapes pour obtenir un token d'accès avec  <shortcut>client_id</shortcut> et le <shortcut>client_secret</shortcut>


<deflist>
    <def title="Obtenir les informations">
       Obtenir les informations <shortcut>client_id</shortcut> et <shortcut>client_secret</shortcut>
    </def>
    <def title="Envoyer une requête pour obtenir un token d'accès">
        Une fois que vous avez les informations <shortcut>client_id</shortcut> et le <shortcut>client_secret</shortcut>,
        vous pouvez envoyer une requête <ui-path>POST</ui-path> à l'endpoint <sample>https://auth.finances.ml/realms/tresorpay/protocol/openid-connect/token</sample> pour obtenir un token d'accès.
    </def>
</deflist>

<tabs>
    <tab id="http-client" title="Curl">
        <code-block lang="bash">
            curl -X POST "https://auth.finances.ml/realms/tresorpay/protocol/openid-connect/token" \
             -H "Content-Type: application/x-www-form-urlencoded" \
             -d "client_scope=tresorpay" \
             -d "client_id={client_id}" \
             -d "client_secret={client_secret}"
        </code-block>
    </tab>
    <tab id="postman" title="Postman">
        <img src="postman_api.png" alt="Image API auth postman" width="2000"/>
    </tab>
</tabs>

## Conseils d'utilisation de l'API
Voici quelques bonnes pratiques pour utiliser l'API de manière efficace et sécurisée :

- <shortcut><ui-path>Protéger vos clés API</ui-path></shortcut> : Ne partagez jamais vos clés privées. Utilisez des variables d'environnement pour les stocker en toute sécurité.
- <shortcut><ui-path>Tester en Sandbox</ui-path></shortcut> : Utilisez l'environnement de test (Sandbox) pour tester vos intégrations avant de passer en mode production.
- <shortcut><ui-path>Vérifier les réponses</ui-path></shortcut> : Assurez-vous de vérifier chaque réponse de l'API pour détecter les erreurs et éviter des comportements indésirables.

## Prochaines étapes
Une fois que vous avez configuré et testé l'API, voici quelques actions à envisager :
- **Intégrer des fonctionnalités avancées** : Explorez les endpoints disponibles, tels que l'émission d'un avis de recette, le suivi de l'avis de recette ou l'annulation d'un avis de recette.
- **Passer en mode production** : Après des tests réussis en Sandbox (environnement de test), passez à l'environnement de production disponible via : <code-block>https://tresorpay.ml/api/public/v1</code>
