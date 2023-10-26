
# Approfondissez vos compétences avec Appium et WebdriverIO

Pour aller encore plus loin dans votre apprentissage d'Appium en association avec WebdriverIO, voici une liste de sujets que vous devriez explorer :

## Gestion de la Configuration

### Configuration simple d'un linter.

Pour commencer, vous devez installer [ESLint](https://eslint.org/):

```bash
npm  i  eslint  --save-dev
```

Ensuite, exécutez le configurateur ESLint :

```bash
➜  appium-wdio-advanced-config  git:(main) ✗  npm  init  @eslint/config
✔  How  would  you  like  to  use  ESLint?  ·  problems
✔  What  type  of  modules  does  your  project  use?  ·  commonjs
✔  Which  framework  does  your  project  use?  ·  none
✔  Does  your  project  use  TypeScript?  ·  No  /  Yes
✔  Where  does  your  code  run?  ·  browser
✔  What  format  do  you  want  your  config  file  to  be  in?  ·  JavaScript
The  config  that  you've selected requires the following dependencies:
@typescript-eslint/eslint-plugin@latest @typescript-eslint/parser@latest
✔ Would you like to install them now? · No / Yes
✔ Which package manager do you want to use? · npm
```
Ensuite, installez `eslint-plugin-wdio` :

```bash
npm  install  eslint-plugin-wdio  --save-dev
```

**Note :** Si vous avez installé ESLint de manière globale (en utilisant le drapeau `-g`), vous devrez également installer `eslint-plugin-wdio` de manière globale.

### Configuration Recommandée

Ce plugin propose une configuration recommandée qui encourage de bonnes pratiques. Pour utiliser les configurations recommandées d'ESLint et de `eslint-plugin-wdio`, ajoutez ce qui suit à votre fichier de configuration `.eslintrc` :

```js
{
    "plugins": [
        'wdio',
        '@typescript-eslint'
    ],
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
## Récupérer les applications natives Android et iOS
- Pour effectuer des tests sur des applications natives, récupérez les fichiers d'application mobile pour Android et iOS à partir de ce [lien](https://github.com/webdriverio/native-demo-app/releases).
- Créez un dossier `apps` à la racine de votre projet et placez les fichiers à l'intérieur.

## Récupération des tests associés à ces applications

Pour exécuter rapidement une série de tests, j'ai récupéré des tests par défaut associés aux fichiers APK et applications dans ce [dépôt](https://github.com/webdriverio/appium-boilerplate/tree/main/tests).

## Gestion des Configurations de Lancement des Tests

Pour une gestion plus efficace des fichiers de configuration, créez un dossier `config` à la racine de votre projet. 

Créez ou récupérez les fichiers de configuration suivants, avec les explications ci-dessous :
-  `wdio.shared.conf.ts`: c'est le fichier de configuration principal de WebdriverIO avec seulement quelques options configurées, comme la `baseUrl` qui sera utilisée pour tous les tests.
-  `wdio.shared.local.appium.conf.ts`: c'est le fichier de configuration qui permet de démarrer automatiquement le serveur Appium au lancement des tests avec des options prédéfinies.
-  `wdio.android.app.conf.ts`: c'est le fichier de configuration pour exécuter les tests d'applications natives sur Android.
-  `wdio.ios.app.conf.ts`: c'est le fichier de configuration pour exécuter les tests d'applications natives sur iOS.
-  `wdio.android.browser.conf.ts`: c'est le fichier de configuration pour exécuter les tests dans Chrome sur Android.
-  `wdio.ios.browser.conf.ts`: c'est le fichier de configuration pour exécuter les tests dans Safari sur iOS.
- Mettez à jour le fichier de configuration TypeScript `tsconfig.json` pour qu'il inclue les nouveaux fichiers de configuration :

```json
"include": [
    "./config/**/*.ts",
    "./tests/**/*.ts"
]
```

## Scripts de Lancement

Étant donné qu'il y a des tests par type de dispositif (Android et iOS) et par type d'application (navigateur et application native), nous allons créer des scripts de lancement pour chacun. Pour ce faire, ajoutez les scripts suivants dans le fichier package.json :

```bash
"scripts":  {
    "android.app":  "wdio config/wdio.android.app.conf.ts",
    "android.browser":  "wdio config/wdio.android.browser.conf.ts",
    "ios.app":  "wdio config/wdio.ios.app.conf.ts",
    "ios.browser":  "wdio config/wdio.ios.browser.conf.ts"
},
```

Ainsi, vous pourrez lancer chaque série de tests avec les commandes suivantes (à condition d'avoir démarré les simulateurs Android et iOS avant les tests) :

```bash
npm  run  android.app
npm  run  android.browser
npm  run  ios.app
npm  run  ios.browser
```

## Rapports de Tests

Pour générer un rapport HTML, vous devrez installer des dépendances supplémentaires telles que [Allure Reporter](https://www.npmjs.com/package/@wdio/allure-reporter).

### Installation du reporter

```bash
npm  install  @wdio/allure-reporter  --save-dev
```

### Configuration du reporter

Pour que le rapport soit global, modifiez le fichier `wdio.shared.conf.ts` comme suit :

```bash
reporters: [
    'spec',
    ['allure', {
        outputDir: 'allure-results',
        disableWebdriverStepsReporting: true,
        disableWebdriverScreenshotsReporting: true
    }]
]
```

### Génération du rapport

Pour générer et ouvrir le rapport HTML après la fin de l'exécution des tests, utilisez la commande suivante :

```bash
npm  run  reports
```

Vous pouvez ajouter d'autres configurations pour des intégrations avec des outils tiers (Slack, Teams, etc.).

## Fonctionnalités d'Appium

- [ ] Approfondir la connaissance des capacités d'Appium.

## Recherche d'Éléments

- [ ] Apprendre à rechercher efficacement des éléments.
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
- [ ] Contrôler l'orientation du dispositif.
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