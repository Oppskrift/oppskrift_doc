# Oppskrift data dictionnary
Topic discussed in [related issue](https://github.com/Oppskrift/oppskrift_api/issues/5)

## Recipe

Property | Type | Description | Examples | Is calculated (not persisted) | Comments |
------------ | ------------- | ------------- | ------------- | ------------- | ----- |
name | `String` | Explicit | `Avocado toast` | |  |
author | `String` | Explicit | `Martin` |  |  |
description | `String` | Explicit | `Some dummy description...` |  | Optional |
image | `String or Array<String>` | Explicit | `dummyUrl` |  | Single url or array of urls, Optional |
cookTime | Duration in `ISO` format | Explicit | `PT40M` | Optional |
prepTime | Duration in `ISO` format | Explicit | `3600` |  |  |
waitTime | Duration in `ISO` format | Explicit | `3600` |  | Optional |
totalTime | Duration in `ISO` format | Explicit | `3600` | ✔️ | =cookTime+prepTime+waitTime | 
recipeCategory | `String or Array<String>` | Explicit | `dessert` |  |  |
recipeCuisine | `String` | type of cuisine (French, Mexican, …) | `Japanese` |  | Optional |
recipeIngredient | `Array<String or Object>` | List of ingredients | `['salt', 'pepper', ' 1 cucumber', '200ml milk']` | Is it raw ingredient or is it computed one with qty and unit ? |
recipeInstructions | `Array<String>` | Explicit | `['wash salad', 'cut salad']` |  |  |
recipeYield | `String` | quantity produced (number of servings, number of people) | `1 loaf`, `300g of salad`, `12 servings` or `4 personnes` |  |  |
suitableForDiet | `Array<String>` | Explicit | `['vegan', 'gluten free']` |  | Optional |
url | `String` | Explicit | `http://dummy-url` | ✔️ | Only for JSON-LD |
tools | `Array<String>` | Cooking tool to perform recipe | `['oven', 'mixer']` |  | Optional |
dateCreated | `Date` | Explicit | --- |  |  |
dateModified | `Date` | Explicit | --- |  |  |
datePublished | `Date` | Explicit | --- |  |  |
discussionUrl | `String` | Explicit | `http://dummy-url` | ✔️ |
isFamilyFriendly | `Boolean` | Is the content of the recipe limited to an adult audience (false) or is it ok for a family audience (true) | `false` |  |  |
isPartOf | `String or Array<String>` | This recipe is part of an other recipe | `spaghetti bolognese` |  |  |
isBasedOn | Link to another inspired Recipe, useful to fork Recipes I guess
inLanguage | language in `IETF BCP 47` Standard | Explicit | `fr-fr` |  |
comment | `Array<String>` | Comments, typically from users. |  |  |  |
commentCount | `Integer` | Number of comments |  | ✔️ |  |
creativeWorkStatus | Draft, Published, Deleted |  | ✔️ | The values here are arbitrary regarding our own cycles of publications |

JSON example of a recipe

```json
{
    "name": "Tourte aux cerises",
    "recipeCategory": "dessert",
    "image": "https://assets.afcdn.com/recipe/20171113/74823_w1024h768c1cx2597cy1731cxt0cyt0cxb5195cyb3463.jpg",
    "createdAt": "2004-04-28T08:56:00+02:00",
    "prepTime": "PT40M",
    "cookTime": "PT30M",
    "totalTime": "PT70M", // Virtual !
    "recipeYield": "6 servings",
    "recipeIngredient": [
        "300 g de farine",
        "200 g de beurre",
        "50 g de sucre semoule",
        "1 oeuf",
        "1 pinc\u00e9e de sel",
        "500 g de cerise",
        "150 g de sucre semoule",
        "2 cuill\u00e8res \u00e0 soupe de kirsch",
        "1 jaune d'oeuf pour dorer"
    ],
    "recipeInstructions": [
        {
            "@type": "HowToStep",
            "text": "Pr\u00e9parer la p\u00e2te la veille :"
        },
        {
            "@type": "HowToStep",
            "text": "Tamiser la farine puis la verser dans un saladier et creuser une fontaine. D\u00e9poser au centre les morceaux de beurre ramolli, l'oeuf entier, le sucre et le sel. Bien m\u00e9langer et p\u00e9trir du bout des doigts, puis rouler la p\u00e2te en boule et la laisser reposer 1 journ\u00e9e."
        },
        {
            "@type": "HowToStep",
            "text": "Le lendemain, \u00e9taler la p\u00e2te \u00e0 l'aide d'un rouleau sur un plan de travail propre et farin\u00e9."
        },
        {
            "@type": "HowToStep",
            "text": "Beurrer un moule \u00e0 tarte d'environ 23 cm de diam\u00e8tre puis y d\u00e9poser la moiti\u00e9 de la p\u00e2te et r\u00e9server l'autre moiti\u00e9."
        },
        {
            "@type": "HowToStep",
            "text": "Pr\u00e9chauffer votre four \u00e0 210\u00b0C (thermostat 7)."
        },
        {
            "@type": "HowToStep",
            "text": "Laver, \u00e9queuter et d\u00e9noyauter les cerises (on peut utiliser des cerises en bocaux). Les s\u00e9cher puis les disposer sur le fond de tarte. Saupoudrer les cerises de sucre, puis arroser de kirsch. Couvrir avec l'autre moiti\u00e9 de la p\u00e2te, bien souder les bords."
        },
        {
            "@type": "HowToStep",
            "text": "Badigeonner la tourte de jaune d'oeuf \u00e0 l'aide d'un pinceau pour faire dorer puis enfourner 30 min \u00e0 four chaud."
        },
        {
            "@type": "HowToStep",
            "text": "A d\u00e9guster plut\u00f4t ti\u00e8de."
        }
    ],
    "author": "Annick",
    "description": "farine, beurre, sucre semoule, oeuf, sel, cerise, sucre semoule, kirsch, jaune d'oeuf",
    "recipeCuisine": "French",
}
```

## Cookbook

General questions :

- Can a user have several cookbooks or is it one cookbook by user ?
- Do we rely on recipes' categories to sort the cookbook ?

Property | Type | Description | Examples | Is calculated (not persisted) | Comments |
------------ | ------------- | ------------- | ------------- | ------------- | ----- |
label | `String` | Explicit | `My dessert cookbook` | | |
owner | `String` | Explicit | `Martin Moreau` | | I don't know if we plan to have groups of users that can own a cookbook |
description | `String` | Explicit | `My dessert cookbook` | | Could also be named summary |
public | `Boolean` | Wether it is public or not | `true` | | Not sure about this |
recipes | ??? | Explicit | ??? | | Depending on chosen database, it is wether a key, a ref or an embedded document ? |
recipesCount | `Number` | Explicit | `127` | Should be | |

JSON example of a cookbook

```json
{
    "label": "Les recettes de ma grand-mere",
    "owner": "Martin Moreau",
    "description": "Toutes les recettes favorites de mamie Georgette, du lapin en giblotte au riz au lait",
    "public": false,
    "recipes": ["lapin en giblotte", "riz au lait"],
    "createdAt": "2004-04-28T08:56:00+02:00",
}
```

## User

General questions :

- Do we implement social features like followers, groups, likes, etc. I think so and you ?
- Thus group would be an other model

Property | Type | Description | Examples | Is calculated (not persisted) | Comments |
------------ | ------------- | ------------- | ------------- | ------------- | ----- |
email | `String` | Explicit | `foo@bar.com` | | |
name | `String` | Explicit | `serial_cooker33` | | Is it better not to store true identity... though we have email already ? |
password | `String` | Explicit | `sd$%12s4sdfPv45` | | Hashed password |
followers | `Array<String>` | Explicit | `['Martin Moreau']` | | Depending on chosen database, it is wether a key, a ref or an embedded document ? |
following | `Array<String>` | Explicit | `['Georgette Moreau']` | | Depending on chosen database, it is wether a key, a ref or an embedded document ? |
groups | `Array<String>` | Explicit | `['Les cuisiniers du coeur']` | | Depending on chosen database, it is wether a key, a ref or an embedded document ? |
cookbooks | `Array<String>` | One or several cookbooks | `['Les recettes de ma grand-mere']` | | Depending on chosen database, it is wether a key, a ref or an embedded document ? |

JSON example of a user

```json
{
    "email": "foo@bar.com",
    "name": "Patrick Moreau",
    "password": "sd$%12s4sdfPv45",
    "followers": ["Martin Moreau"],
    "following": ["Georgette Moreau"],
    "groups": ["Les cuisiniers du coeur"],
    "cookbooks": ["Les recettes de ma grand-mere"],
    "createdAt": "2004-04-28T08:56:00+02:00",
}
```
