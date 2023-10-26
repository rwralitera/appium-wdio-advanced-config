
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

Pour activer cette configuration, rajouter dans le fichier de configuration `.eslintrc` :

```json
{
    "plugins": ["wdio"],
    "extends": [
        "eslint:recommended",
        "plugin:wdio/recommended"
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

Add some rules on the .eslintrc.cjs:


```json
{
        semi: ['error', 'always'],
        indent: [2, 4],

        'no-multiple-empty-lines': [ 2, { 'max': 1, 'maxEOF': 1 } ],
        'array-bracket-spacing': [ 'error', 'never' ],
        'brace-style': [ 'error', '1tbs', { allowSingleLine: true } ],
        camelcase: [ 'error', { properties: 'never' } ],
        'comma-spacing': [ 'error', { before: false, after: true } ],
        'no-lonely-if': 'error',
        'no-else-return': 'error',
        'no-tabs': 'error',
        'no-trailing-spaces': [ 'error', {
            skipBlankLines: false,
            ignoreComments: false,
        } ],
        quotes: [ 'error', 'single', { avoidEscape: true } ],
        'unicode-bom': [ 'error', 'never' ],
        'object-curly-spacing': [ 'error', 'always' ],
        'keyword-spacing': [ 'error' ],
        'require-atomic-updates': 0,
        'no-unexpected-multiline': 0,
    },
    ```

Cela vous permettra de bénéficier des configurations recommandées d'ESLint et de `eslint-plugin-wdio`.

- [ ] Gérer plus efficacement les fichiers de configuration.
    - [ ] Gestion des tests avec Saucelabs.
    - [ ] Gestion des tests avec BrowserStack.
    - [ ] Gestion des tests par device.
    - [ ] Gestion des tests par navigateur.

## Scripts de Lancement
- [ ] Maîtriser la gestion des scripts de lancement des tests.
    - [ ] Par type de test.
    - [ ] Par device.

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

