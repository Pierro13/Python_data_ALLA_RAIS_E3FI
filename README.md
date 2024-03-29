# Python dashboard

Autheurs : Pierre ALLA - Ahmed RAIS

Classe : E3 FI groupe 3

Date : 31/12/2022

---

### User Guide

Ce dashboard est réalisé à partir de deux data set de la SNCF sur les trains en France.

Pour le visualiser, il faut d'abord que vous ayez installé les bonnes libraries et que vous téléchargiez les datasets grâce au fichier python : `getdata.py`

Ce fichier permet de télécharger la dernière version ou de mettre à jour les deux fichiers de données : `coords.geojson` et `data.csv`.

Pour avoir les bonnes libraries executez la commande : ``pip install -r requirements.txt``

Puis pour démarrer le dashboard, il faut exécuter le fichier python avec la commande : `python main.py`

Enfin il faudra ouvrir un navigateur web et aller à l'adresse : `http://127.0.0.1:8050/` (ou celle spécifiée dans la console)

---

### Rapport d'analyse

Grâce à ce dashboard nous pouvons indentifier le principal facteur de retard : la fréquentation d'une deux deux gares de liaison. En effet, plus une gare est fréquentée, plus la possibilité d'une liaison soit réalisée avec retard est élevée.

Par exemple la gare "Paris Gare de Lyon" est la gare la plus fréquentée avec 1474 départs de liaison. Elle a 30% de liaisons réalisées avec du retard.

En revanche, certaines petites gares avec très peu de liaisons ont des poucentages élevés. A titre d'exemple, la gare SAINT ETIENNE CHATEAUCREUX a 92% des liaisons réalisées avec retard. Cela s'explique par le faible nombre de liaisons (59) : il suffit que plusieurs de ces trains partant ou arrivant à SAINT ETIENNE CHATEAUCREUX soient en retard pour que le poucentage soit élevé.

---

### Developper Guide

Le code est structuré en deux sections.

La première permettant l'installation des datasets nécessaires et la seconde section qui s'occupe de la création du Dashboard est composé du `main.py` et du `map_gares.py`.

La création du dashboard et l'affichage des graphes se font en deux étapes, la première est celle du traitement des données récupérées depuis les fichiers csv et la deuxième est celle de l'affichage des graphes grâce à l'utilisation de balises html.

Dans la partie de récupération des données et le traitement de celles-ci, chaque graphe est traité et construit séparément. C'est à dire que l'on récupère les données, on les traite, on réalise ensuite la création du graphique et sa mise en forme puis on répète les mêmes étapes pour le graphe suivant. Cela permet d'imiter plus facilement la structure à adopter pour la création du graphique et permet aussi tout simplement d'ajouter un nouveau graphique dans le code juste après ceux déjà créés.

Juste après, dans la partie d'affichage des graphes, il faut voir la disposition comme un code html. En l'occurrence ici la structure est la même qu'en html sauf que les balises sont remplacées par des fonctions issue du framework dash. Une première partie du code html contient l'entête de la page avec des informations sur le dashboard et une description générale.

Dans la suite du code la décomposition se fait dans le même principe que dans la partie de création du dashboard. C'est à dire que l'on fait l'affichage un par un des graphiques.  Pour chaque graphique en général on possède une balise div avec du texte expliquant le graphique et une balise Graph avec la définition de l'id du graphique. On peut donc, après avoir ajouté nos traitements dans la partie de récupération des données, ajouter les balises html nécessaires à l'affichage de notre graphique.

Une partie supplémentaire est également disponible : elle est appellé le callback. C'est une méthode qui permet de manière synchronisée avec le site web de changer l'affichage de notre graphique. Elle permet donc de reéffectuer des traitements de données à chaque intervention depuis le dahsboard. En l'occurrence dans notre dashboard, un slider est visible à côté d'un des graphiques et permet de moduler l'affichage que l'on souhaite du graphique en fonction de la variable.
