# ISD - SA2022 - TP1 

Fichier de réponses

Professeur: Carlos Peña
Assistant: Thibault Schowing

Étudiant: Calvin - Graf (en plus du nom de fichier svp)

-----------------------

#  Partie 1

-----------------------

## Exercice 1

(5 points)

1) Ecrivez un script qui génère une liste contenant un million de valeurs entières aléatoires entre 1 et 10 (y compris) et qui calcule le pourcentage de valeurs paires dans cette liste.

```
# Copiez votre code ici:

from random import *

lstNumber = [];
iNumMax = 1000000;
iNumEven = 0;
iNumOdd = 0;

while len(lstNumber) < iNumMax:
    lstNumber.append(randint(1, 10))
    if (lstNumber[-1] % 2) == 0: # Égal au reste de la division par 2
        iNumEven = iNumEven + 1

iNumEven = iNumEven / len(lstNumber) * 100
iNumOdd = 100 - iNumEven;
print("Total de nombre pairs :", end=" ") ; print(iNumEven, end="") ; print("%")
print("Total de nombre impairs :", end=" ") ; print(iNumOdd, end="") ; print("%")
print("Total de nombre :", end=" ") ; print(len(lstNumber))
    

```


**Points obtenus: /5**
**Remarques:**


## Exercice 2

(10 points)

2.1) Décrivez avec vos mots et l'aide de la documentation les trois methodes décrites ci-dessus, leur différences et les fonctions utilisées. 

Réponse: 

La première méthode consiste faire la racine carré des deux liste concaténée. On ajoute chaque nombres impairs (le 2 signifie qu'on utilise un nombre sur deux, 1, 3, etc.) à la liste puis on y rajoute tous les nombres pairs.

La seconde méthode fait la racine carrée pour chaque nombres compris entre 1 et 21 (non-compris) en vérifiant pour chacun s'il est supérieur ou égal à 10 et impair ou s'il est inférieur à 10 et pair.

La troisième méthode fait la racine carré de tous les nombres impairs, puis fait celle des nombres pairs et additionne le tout. Il n'y a en revanche pas de liste cette fois-ci.

2.2) A partir de la liste "objets" données ci-dessous, créez une liste contenant uniquement les mots de la première liste qui contiennent la lettre "z" ou "Z".

```
# Copiez votre code ici:

objets = ["Canicule",
          "Zoo",
          "Prix béton 1981",
          "Pancréas",
          "Zebre",
          "Jazz",
          "Yverdon-les-Bains"]

lstObjectWithZ = [];

[lstObjectWithZ.append(obj) for obj in objets if ("z" in obj) or ("Z" in obj)]
for obj in lstObjectWithZ:
    print(obj)
    

""" Alternative :
    if "z" in obj or "Z" in obj:
        lstObjectWithZ.append(obj) """

```

**Points obtenus: /5**
**Remarques:**

-----------------------

#  Partie 2

-----------------------

(5 points)


1) Pourquoi utiliser NumPy ?

Réponse: Numpy offre la possibilité d'utiliser des tableaux contenant des nombres et permet d'user de formules mathématiques. Sa vitesse de calcul est optimisé comparé à Python.


2) Comment s'appelle (n.b. "de quel type est") l'objet "array" dans NumPy et que signifie son nom ?

Réponse: "ndarray" Le "nd" signifie qu'il s'agit d'un tableaux à plusieurs dimensions (N-Dimensions), c'est-à-dire qu'un tableau peut contenir lui-même d'autres tableaux.


3) Pourquoi utiliser NumPy est-il plus rapide qu'utiliser les listes ?

Réponse: Car les tableaux sont contenus dans un espace continue de la mémoire ce qui les rend plus rapidemment accessibles. On appelle ce comportement "localité de référence".


4) A quelle question le code "# Question 4" ci-dessous répond-il ?

Réponse: Il répond à la première partie de la question 2. Il affiche le type du tableau.


5) Affichez la somme des deux derniers éléments du tableau

```
# Copiez votre code ici:

import numpy as np 
arr = np.array([1, 2, 3, 4, 5])
print(arr[-1] + arr[-2])

```


**Points obtenus: /5**
**Remarques:**


-----------------------

#  Partie 3

-----------------------

(5 points)

1) Pourquoi utiliser Pandas ?

Réponse: Panda permet d'analyser les mégadonnées. Il consomme plus de mémoire que Numpy mais offre de meilleurs performances lorsque l'on utilise 500k lignes ou plus. Contrairement à Numpy, il permet d'utiliser des objets de type différents et non uniquement des nombres.

2) Que peut faire pandas (d'après le tuto w3schools) ?

Réponse: Panda permet de faire des opérations semblables à Excel (valeur max/min, moyenne, etc.) et permet de nettoyer les données en supprimant des valeurs eronnées/vide/NULL.

3) Que fait l'exemple "Question 3" ci-dessous ?

Réponse: On ajoute des tableaux conteant des données à notre ensemble de données, puis on les affiche. Chaque ensemble à son propre en-tête et est lié aux autres.

4) Compléter la cellule "Question 4" pour afficher les lignes demandées. Utiliser l'attribut *loc* comme décrit dans le tutoriel. Que remarquez vous concernant l'utilisation de simples crochets ([...]) ou doubles crochets ([[x,y]]) pour extraire _une_ colonne du dataframe ? En utilisant la fonction type(), donnez le type de données retournées avec les simples crochets ([...]) ou doubles crochets ([[x,y]]).

Réponse: Lorsque l'on utilise les crochets simple, un utilise le type "Series" qui se transforme en "DataFrame" lorsque l'on ajoute une deuxième valeur, alors qu'avec les doubles crochets, on utilisera toujours le type "DataFrame".

Simple crochet : Series
Double crochet : DataFrame

5) Complétez le code comme demandé dans la cellule "Question 5 - exercice". Extrait du tutoriel Pandas de w3school.

```
# Copiez votre code ici:

import pandas as pd

df = pd.read_csv("https://www.w3schools.com/python/pandas/dirtydata.csv.txt")

df_clean = pd.read_csv("https://www.w3schools.com/python/pandas/dirtydata.csv.txt") 

print(df)


# 2) La ligne 26 contient une date au mauvais format. Pour cela nous allons convertir la colonne "Date".
#    Attention a bien faire cette opération sur df_clean et non sur df (modifiez par rapport au tutoriel). 
#    En cas de Warnings, vous pouvez l'ignorer.

df_clean['Date'] = pd.to_datetime(df_clean['Date'])


# 3) La valeur à la ligne 7 vous semble suspecte. Vous pouvez choisir de la remplacer par une valeur qui a plus de sense (45) 
#    ou vous pouvez simplement supprimer la ligne. Basez-vous toujours sur le tutoriel pour réaliser cette tâche. 

df_clean.loc[7, 'Duration'] = 45

# Enfin on affiche notre dataframe propre et ses infos. Décommentez les "print" pour afficher le dataframe df_clean et ses infos

print("\n\n===================== Dataframe ====================\n\n")
print(df_clean)
print("\n\n===================== Infos ====================\n\n")
print(df_clean.info()) 

```

**Points obtenus: /5**
**Remarques:**

-------------
  Partie 4
-------------

(2 points)

1) Pourquoi utiliser Matplotlib ?

Réponse: Matplotlib permet la création de différentes figures graphiques configurables au maximum tel que des histogrammes, des camembert, etc. De la taille des marqueurs à la couleur des lignes ou encore la gestion de la transparence, tout est modifiable.


2) Allez regarder la gallerie des exemples de Matplotlib et regardez rapidement les 5 premières sections (jusqu'à la section "Pie and polar charts compris"). Choisissez 2 types de graphiques (Ou prenez les plus importants: Barchart, Boxplot et Scatterplot) et écrivez une courte description pour chaqu'un d'eux.

Réponse: 

Barchart permet la comparaison de deux éléments en affichant leurs données côte à côte.

Scatterplot permet de faire une relation entres plusieurs variables afin de mieux déterminer leurs impacts entre elles-mêmes.

**Points obtenus: /5**
**Remarques:**







