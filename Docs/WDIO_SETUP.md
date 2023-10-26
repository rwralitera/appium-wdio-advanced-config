
# Approfondissez vos compétences avec Appium WebdriverIO

Pour aller plus loin dans votre apprentissage d'Appium avec WebdriverIO, voici une liste de sujets à explorer :

## Gestion des configuration

### Configurer un linter de manière optimale.

# Installation

Pour commencer, vous devez installer [ESLint](https://eslint.org/):

```bash
npm i eslint --save-dev
```
Lancer le wizard de configuration d'eslint:

```bash
➜  appium-wdio-advanced-config git:(main) ✗ npm init @eslint/config
✔ How would you like to use ESLint? · problems
✔ What type of modules does your project use? · commonjs
✔ Which framework does your project use? · none
✔ Does your project use TypeScript? · No / Yes
✔ Where does your code run? · browser
✔ What format do you want your config file to be in? · JavaScript
The config that you've selected requires the following dependencies:
@typescript-eslint/eslint-plugin@latest @typescript-eslint/parser@latest
✔ Would you like to install them now? · No / Yes
✔ Which package manager do you want to use? · npm
```

Ensuite, installez `eslint-plugin-wdio`:

```bash
npm install eslint-plugin-wdio --save-dev
```

**Note :** Si vous avez installé ESLint de manière globale (en utilisant le drapeau `-g`), vous devrez également installer `eslint-plugin-wdio` de manière globale.

## Recommandé

Ce plugin propose une configuration recommandée qui impose de bonnes pratiques.

Pour bénéficier des configurations recommandées d'ESLint et de `eslint-plugin-wdio`, rajouter dans le fichier de configuration `.eslintrc` :

```json
{
    "plugins": [
        'wdio',
        '@typescript-eslint'],
    "extends": [
        'eslint:recommended',
        'plugin:@typescript-eslint/recommended',
        'plugin:wdio/recommended'
    ],
    "rules": {
        'semi': ['error', 'always'],
        'indent': [2, 4],

        'no-multiple-empty-lines': [2, { 'max': 1, 'maxEOF': 1 }],
        'array-bracket-spacing': ['error', 'never'],
        'brace-style': ['error', '1tbs', { allowSingleLine: true }],
        'camelcase': ['error', { properties: 'never' }],
        'comma-spacing': ['error', { before: false, after: true }],
        'no-lonely-if': 'error',
        'no-else-return': 'error',
        'no-tabs': 'error',
        'no-trailing-spaces': ['error', {
            'skipBlankLines': false,
            'ignoreComments': false,
        }],
        'quotes': ['error', 'single', { avoidEscape: true }],
        'unicode-bom': ['error', 'never'],
        'object-curly-spacing': ['error', 'always'],
        'keyword-spacing': ['error'],
        'require-atomic-updates': 0,
        'no-unexpected-multiline': 0,
    },
}
```
## Applications natives Android et iOS
- Pour pouvoir faire quelques tests d'applications natives, récupérer les fichiers des applications mobiles pour Android et pour iOS sur ce [lien](https://github.com/webdriverio/native-demo-app/releases)
- Créer un dossier `apps` à la racine de votre projet et coller les fichiers à l'intérrieur

## Gestion des configurations de lancement des tests
- Pour gérer plus efficacement les fichiers de configuration, créez un dossier `config` à la racine de votre projet.
- Créez ou récupérez les fichiers de configurations dont voici les explications: 
    - `wdio.shared.conf.ts`: c'est le fichier de configuration principal de webdriverio avec seulement quelques options qui sont configurés, comme par exemple la `baseUrl` qui sera utilisé pour tous les tests
    - `wdio.shared.local.appium.conf.ts`: c'est le fichier de configuration qui va permettre de démarrer automatisauement le serveur appium au lancement des tests avec les options prédéfinis
    - `wdio.android.app.conf.ts`: c'est le fichier de configuration pour lancer les tests app natives sur android
    - `wdio.ios.app.conf.ts`: c'est le fichier de configuration pour lancer les tests app natives sur iOS
    - `wdio.android.browser.conf.ts`: c'est le fichier de configuration pour lancer les tests chrome sur android
    - `wdio.ios.browser.conf.ts`: c'est le fichier de configuration pour lancer les tests safari sur iOS
- Mettez à jour le fichier de configuration typescript `tsconfig.json`pour qu'il prenne en compte les nouveaux fichiers de configuration:

```json
"include": [
    "./config/**/*.ts"
]
```

## Récupérer les tests
Pour pouvoir lancer rapidement une execution, j'ai récupéré des tests par défaut associés aux fichiers apk et app dans ce [repository](https://github.com/webdriverio/appium-boilerplate/tree/main/tests)

## Scripts de Lancement
Etant donné qu'il y a des tests par device (andoid et ios) et aussi des tests par types d'application (browser et app native), on va créer des scripts de lancement pour chacun. Pour cela, dans le fichier package.json, on va rajouter les scripts:

```bash
"scripts": {
    "android.app": "wdio config/wdio.android.app.conf.ts",
    "android.browser": "wdio config/wdio.android.browser.conf.ts",
    "ios.app": "wdio config/wdio.ios.app.conf.ts",
    "ios.browser": "wdio config/wdio.ios.browser.conf.ts"
  },
```

De ce fait, on va pouvoir lancer chacun des tests avec les commandes (à condition d'avoir lancer les simulateurs android et ios avant les tests):

```bash
    npm run android.app
    npm run android.browser
    npm run ios.app
    npm run ios.browser
  },
```

## Rapports de Tests
- [ ] Configurer des rapports de tests.
    - [ ] Intégration avec des outils tiers (Slack, Teams, etc)
    - [ ] Rapports au format HTML.

## Fonctionnalités d'Appium
- [ ] Approfondir la connaissance des capabilities d'Appium.

## Recherche d'Éléments
- [ ] Apprendre à rechercher les éléments efficacement.
    - [ ] Par ID.
    - [ ] Par identifiant d'accessibilité.
    - [ ] Utilisation de XPath.

## Interactions avec les Éléments
- [ ] Maîtriser les interactions avec les éléments.
    - [ ] Effacer un champ.
    - [ ] Remplir un champ.
    - [ ] Cliquer sur un élément.

## Vérifications
- [ ] Apprendre à effectuer des vérifications.
    - [ ] Utilisation de Chai.

## Gestion des Sessions
- [ ] Gérer les sessions de test.
    - [ ] Contrôler l'orientation du device.
    - [ ] Effectuer un retour en arrière.
    - [ ] Capturer des captures d'écran.

## Gestion des Timeouts
- [ ] Apprendre à gérer les timeouts.
    - [ ] Timeouts implicites.
    - [ ] Timeouts explicites.

## Manipulation des Attributs
- [ ] Savoir manipuler les attributs des éléments.
    - [ ] Récupérer du texte.
    - [ ] Récupérer un attribut.

## Gestion des États
- [ ] Comprendre la gestion des états des éléments.
    - [ ] Vérifier si un élément est sélectionné.
    - [ ] Vérifier si un élément est activé.
    - [ ] Vérifier si un élément est affiché.

## Écriture de Tests Efficaces
- [ ] Maîtriser les bonnes pratiques pour écrire des tests efficaces.
    - [ ] Utilisation de Page Objects.
    - [ ] Utilisation de Hooks.
    - [ ] Gestion des données de test.

## Actions Avancées
- [ ] Explorer des actions avancées.
    - [ ] Faire défiler l'écran vers le haut.
    - [ ] Faire défiler l'écran vers le bas.
    - [ ] Faire défiler l'écran vers la droite.
    - [ ] Faire défiler l'écran vers la gauche.
    - [ ] Manipulation de carrousels.
    - [ ] Gestion des alertes.
    - [ ] Utilisation de Picker.

## Gestion des Contextes
- [ ] Apprendre à gérer les contextes.
    - [ ] Travailler en mode Webview.
    - [ ] Travailler en mode Natif.

## Intégration dans la CI
- [ ] Savoir intégrer vos tests dans un environnement d'Intégration Continue (CI).

