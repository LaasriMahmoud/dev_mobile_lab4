# 🧩 Lab 4 - Manipulation Dynamique des Fragments

## 📋 Présentation du Projet
Ce laboratoire illustre la puissance et la flexibilité des **Fragments** dans le développement Android. L'application développée met en œuvre une activité principale qui gère dynamiquement l'affichage de deux fragments distincts, permettant de naviguer de l'un à l'autre sans avoir à changer d'activité.

---

## 🎯 Objectifs Pédagogiques
- Comprendre et manipuler la classe `Fragment` et son cycle de vie propre.
- Utiliser le `FragmentManager` et la classe `FragmentTransaction` pour instancier, remplacer et ajouter des fragments dynamiquement.
- Manipuler la pile de retour (`addToBackStack()`) pour permettre une navigation intuitive avec le bouton "Retour" d'Android.
- Gérer l'état de l'interface (comme une `SeekBar`) et persister les données lors de la rotation de l'écran avec `onSaveInstanceState()`.
- Lier des actions spécifiques dans les vues des fragments.

---

## 🛠️ Architecture du Code

### 1. MainActivity (Le Contrôleur Principal)
L'activité principale sert d'hôte. Son layout (`activity_main.xml`) comporte une barre de boutons en haut et un `FrameLayout` vide qui fait office de conteneur.
- La méthode `replaceFragment()` orchestre la transition. Elle utilise `getSupportFragmentManager().beginTransaction().replace(...)`.
- `addToBackStack(null)` est invoqué pour mémoriser la transition, ce qui autorise le retour au fragment précédent sans détruire l'activité.

### 2. FragmentOne (Premier Fragment)
- Layout simple avec un texte et un bouton.
- Dans `onViewCreated()`, un écouteur est lié au bouton pour modifier dynamiquement le contenu du `TextView`.
- Des méthodes de debug (`onResume`, `onPause`) peuvent être observées dans le Logcat.

### 3. FragmentTwo (Second Fragment avec État)
- Gère une `SeekBar` (barre de progression) et met à jour un `TextView` en direct avec `setOnSeekBarChangeListener`.
- Implémente `onSaveInstanceState()` pour persister la valeur de progression. Si l'écran pivote, l'activité et le fragment sont recréés, mais l'état restauré dans `onViewCreated(..., Bundle savedInstanceState)` permet de conserver la donnée.

---

## 🚀 Utilisation de l'Application
1. Au lancement, le **Fragment 1** est affiché par défaut.
2. Cliquez sur le bouton "Fragment 2" pour basculer dynamiquement vers la seconde interface.
3. Déplacez le curseur de la barre de progression (SeekBar) : la valeur change en direct.
4. Appuyez sur le bouton "Retour" de l'appareil pour annuler la transaction et revenir au **Fragment 1**.

---
**Développé par :** Laasri Mahmoud  
**Cadre :** Programmation Mobile : Android avec Java