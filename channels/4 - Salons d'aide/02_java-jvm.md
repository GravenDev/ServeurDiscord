# `#❔︱java︱jvm`
Le salon `#❔︱java︱jvm` est un salon vous permettant de poser vos questions sur le
langage Java et les langages de la JVM.

### Permissions :
![](https://img.shields.io/badge/Lecture-OUI-green?style=for-the-badge) <br/>
![](https://img.shields.io/badge/Ecriture-OUI-green?style=for-the-badge)

<br/>

# Liste des référents 
| Nom | ID|
|:---|:---|
| Clems#7696 | 240890972366569472 |
| RedsTom#4616 | 723471302123323434 |
| Il_totore#9133 | 403609872123428864 |
| enimaloc#5587 | 136200628509605888 |
| Tartur#5891 | 797145312438648832 |

# Message(s) Épinglé(s)

## Message 1 (par RedsTom#4616 [723471302123323434])

Comment ajouter vos dépendances gradle dans le jar final ?

> En utilisant Shadow Jar

Mais comment bien l'utiliser ?

1️⃣ **Étape 1 :** Ajouter Shadow Jar dans vos plugins gradle en ajoutant cette ligne dans votre block `plugins` :
```groovy
plugins {
    ... // (Autres plugins)
    id "com.github.johnrengelman.shadow" version "6.1.0"
}
```

2️⃣ **Étape 2 :** Configurez les dépendances qui vont être empaquetées dans le jar, ici, je choisis d'empaqueter les dépendances qui sont en `implementation`
```groovy
shadowJar {
    project.configurations.implementation.canBeResolved(true)
    configurations = [project.configurations.implementation]
}
```


Pour compiler une dépendance dans le jar, ajoutez-la avec `implementation` 
> Exemple : `implementation 'com.google.code.gson:gson:2.8.6'`

Pour qu'une dépendance soit utilisée à la compilation, mais n'aille pas dans le jar, ajoutez-la avec  `compileOnly`
> Exemple : `compileOnly 'com.destroystokyo.paper:paper-api:1.12-R0.1-SNAPSHOT'`

Maintenant, il vous suffit de lancer la tâche `shadowJar` et le tour est joué 😉


## Message 2 (par RedsTom#4616 [807926854915719209])

Si dans IDEA, le contrôle clavier shift + ctrl + O (pour réimporter les dépendances), ça ne fonctionne pas, suivez la procédure ci-jointe :

![image](https://cdn.discordapp.com/attachments/763849218359033856/766783360453312602/unknown.png)
