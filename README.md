# Conception-Integree-et-Optimisation-d-un-Culbuteur-de-Distribution-CAO-Calcul-sur-CATIA-V5
FR : Conception intégrée et optimisation topologique d'un culbuteur de distribution automobile sous CATIA V5 (Analyse cinématique, statique graphique, Hertz, et Éléments Finis). EN : Integrated CAD design and structural optimization of a rocker arm mechanism using CATIA V5 (Kinematics, graphical statics, Hertz contact theory, and FEA).

# Conception Intégrée et Optimisation d'un Culbuteur de Distribution (CAO / Calcul)

## 📌 Présentation du Projet
Ce dépôt contient les fichiers de conception et le compte-rendu d'un projet dédié à la **conception formelle, au dimensionnement et à l'optimisation topologique (allègement de masse)** d'un culbuteur pour un mécanisme de distribution à came automobile. 

L'ensemble de l'étude a été réalisé de manière intégrée sous l'environnement **CATIA V5**, en combinant des approches géométriques, analytiques et numériques. L'objectif principal était de concevoir une pièce respectant une loi de levée de soupape stricte tout en minimisant sa masse sous une contrainte de Von Mises maximale admissible de **$\sigma_{max} = 100 \text{ MPa}$**.

---

## 🛠️ Démarche d'Ingénierie & Méthodologie

Le projet suit un cycle complet de conception intégrée divisé en 4 grandes étapes :

### 1. Définition de l'Épure Cinématique
* **Modélisation de la loi de levée :** Établissement d'une loi de levée de soupape de $6\text{ mm}$ de course maximale (comprenant les zones de repos constant, de montée et de descente).
* **Sketcher & Solveur géométrique :** Utilisation du solveur de contraintes de CATIA pour créer une épure 2D, reliant les contraintes cinématiques (tangence came/galet, entraxes) afin d'en extraire le profil géométrique de la came.
* **Génération de la Came :** Interpolation par Spline polynomiale par morceaux à l'aide du module *Wireframe and Surface Design* à partir des coordonnées de points relevées.

### 2. Maquette Numérique & Simulation Cinématique (`DMU Kinematics`)
* Assemblage des composants du mécanisme (culasse, came, soupape, ensemble-culbuteur, poussoir).
* Résolution des liaisons cinématiques (liaison pivot, glissière, courbe glissante, point sur courbe) pour piloter le mécanisme à une vitesse de **$1000 \text{ tr/min}$** ($1 \text{ tour en } 0{,}06\text{ s}$).
* Analyse de la sensibilité de la discrétisation en évaluant l'influence du nombre de pas ($20$, $100$, $200$) sur la précision des courbes de position, de vitesse et d'accélération de la soupape.

### 3. Résolution Statique Graphique & Dimensionnement Fonctionnel
* **Résolution graphique 2D :** Création d'une esquisse statique à la levée critique maximum ($9{,}5\text{ mm}$) pour déterminer graphiquement et par fermeture vectorielle (torseur des moments en $O$) les efforts aux contacts ($\vec{F_s}$, $\vec{F_g}$, $\vec{F_c}$).
* **Théorie de Hertz (Contact Galet-Came) :** Dimensionnement de la largeur du galet ($L_g = 8{,}6\text{ mm}$) via un fichier de calcul pour garantir une pression effective inférieure à la limite de $850\text{ MPa}$ ($P_{\text{max}} = 848{,}8\text{ MPa}$).
* **Sélection de Palier Lisse (Permaglide P20) :** Choix technologique sur catalogue ($D_i = 10\text{ mm}$, $B = 15\text{ mm}$) basé sur le produit $P \cdot V$ et un critère de durée de vie minimale de $2000\text{ h}$.

### 4. Analyse de Structure par Éléments Finis (`FEA`) & Optimisation de Masse
* **Maillage :** Utilisation d'éléments paraboliques de taille $2\text{ mm}$ dans le module *Generative Structural Analysis*.
* **Conditions aux limites :** Encastrement virtuel sur l'axe du culbuteur et application des forces distribuées calculées lors de l'étude statique.
* **Processus itératif d'optimisation :** * Première ébauche robuste mais lourde ($\sigma_{max} = 78{,}9\text{ MPa}$).
  * Modification des géométries d'extrusion pour lisser les concentrations de contraintes sur les arêtes vives (abaissement à $50{,}7\text{ MPa}$).
  * Évidements itératifs de matière (trous) dans les zones de faible contrainte.

---

## 📈 Résultats Finaux
* **Respect du Cahier des Charges :** La contrainte maximale finale de Von Mises obtenue est de **$74 \text{ MPa}$**, ce qui valide la tenue mécanique vis-à-vis du seuil maximal imposé de $100 \text{ MPa}$.
* **Gain de Masse :** L'optimisation géométrique des évidements a permis de réduire la masse de la pièce tout en garantissant une excellente diffusion des contraintes structurelles.

---

## 📁 Structure du Repository
* 📂 `Documents/` : Le compte-rendu final de l'étude au format PDF (`CR CAO.pdf`).
