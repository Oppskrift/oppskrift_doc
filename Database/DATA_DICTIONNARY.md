# Oppskrift data dictionnary
Topic discussed in [related issue](https://github.com/Oppskrift/oppskrift_api/issues/5)

## Recipe

Property | Type | Description | Exemples | Comments | 
------------ | ------------- | ------------- | ------------- | ------------- |
name | String | Explicit | `Avocado toast` | ✔️ |
author | String | Explicit | `Martin` | ✔️ |
description | String | Explicit | `Some dummy description...` | ✔️ |
image | String | Explicit | `dummyUrl` | Could it be an array of images ? |
cookTime | Duration in ISO format | Explicit | `PT40M` | ✔️ |
recipeCategory | String | Explicit | `dessert` | Could a recipe have several categories ? |
recipeCuisine | String | type of cuisine (French, Mexican, …) | `Japanese` | Could a recipe have several cuisines ? |
recipeIngredient | Array | List of ingredients | `['salt', 'pepper', 'cucumber']` | schema.org says it's a single ingredient but it's a list of ingredients |
recipeInstructions | Array | Explicit | `['wash salad', 'cut salad']` | ✔️ |
recipeYield | Number | quantity produced (number of servings, number of people) | `6` | Does it needs a related variable unit ? |
suitableForDiet | ??? | Explicit | --- | Need an example |
estimatedCost | Number | Explicit | --- | Not sure it is needed because mainly relative to regions/countries, if we keep, what about currency ? |
prepTime | Number | Explicit | `3600` | Need to select a unit |
**Properties from Recipe** | ??? | Specific properties related to a Recipe | --- | --- |

JSON example of a recipe
```json
{
    "name": "Tourte aux cerises",
    "recipeCategory": "dessert",
    "image": "https://assets.afcdn.com/recipe/20171113/74823_w1024h768c1cx2597cy1731cxt0cyt0cxb5195cyb3463.jpg",
    "createdAt": "2004-04-28T08:56:00+02:00",
    "prepTime": "PT40M",
    "cookTime": "PT30M",
    "totalTime": "PT70M", // Virtual ?
    "recipeYield": 6,
    // @todo discuss data type here
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
    // @todo discuss data type here
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
