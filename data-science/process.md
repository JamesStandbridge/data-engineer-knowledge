Récupération
Nettoyage
Exploration
Modélisation
Évaluation et interprétation
Mise en production




- modélisation : 
    Apprentissage supervisé 
        Associer un dataset avec des données annotées (image de chien -> label : "chien")
        Objectif : le modèle classifie les prochaines images de chien sans annotation sans se tromper

        son reçoit des données d'exemple annotées : (x1,y1),(x2,y2),(x3,y3),... et on espère prédire la ortie sur de nouvelles observations : x∗→y∗ .

    Apprentissage non supervisé
        Dataset sans annotation : les similarités sont retrouvées par le modèle et regroupent
        les données partageant une ou plusieurs caractéristiques communes.

        on reçoit uniquement des observations brutes de variables aléatoires :  x1,x2,x3,x4,... et on espère découvrir la relation avec des variables latentes structurelles :  xi→yi.

    Apprentissage semi supervisé : mélange des deux (données en partie annotées)

    Apprentissage renforcé : cycle d'expérience / récompense (analogie de la dopamine).

    -----------------------------------------------------

- Type de sortie :
        - Classification (valeur discrète, catégorisation)
        - Régression (valeur continue)


    -----------------------------------------------------
    
- Nettoyage dataset :
        Déterminer les outliers (valeurs abberentes) 


    -----------------------------------------------------

Données = Modèle sous-jacent + bruit indépendant
Fonction loss : En apprentissage supervisé, la notion principale est celle de perte d’information (loss en anglais) due à l'approximation dont je viens de parler. Elle détermine à quel point notre modélisation du phénomène, qui est une approximation de la réalité, perd de l’information par rapport à la réalité observée à travers les données d’exemple.

