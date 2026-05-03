# TP6 - Détection et suivi du mouvement dans une séquence d'images

Bonjour, ce dépôt contient mon travail pour le TP6 du cours de Vision Artificielle.
L'objectif était de détecter et suivre le mouvement d'une cellule dans une séquence d'images en utilisant Python et OpenCV.

---

## Ce que j'ai fait dans ce TP

J'ai implémenté un pipeline complet qui part des images brutes jusqu'au calcul de la trajectoire et de la vitesse de l'objet en mouvement. Voici les étapes que j'ai suivies :

1. Charger et afficher les images de la séquence
2. Calculer la différence absolue entre deux images successives
3. Appliquer un seuil pour obtenir un masque binaire
4. Nettoyer le masque avec des opérations morphologiques
5. Détecter l'objet en mouvement par contours
6. Calculer le centre de l'objet (centroïde)
7. Tracker l'objet sur toute la séquence
8. Tracer la trajectoire
9. Calculer la vitesse et les déplacements
10. Interpréter les résultats dans un contexte biomédical

---

## Les outils utilisés

- Python 3.14
- OpenCV 4.13
- NumPy
- Matplotlib

Pour installer les bibliothèques nécessaires :

```
pip install opencv-python numpy matplotlib
```

---

## Comment lancer le code

```
python TP6_detection_suivi_mouvement.py
```

Le script génère automatiquement une séquence de 15 images simulant une cellule qui se déplace, puis applique tout le pipeline dessus. Les captures d'écran sont sauvegardées dans le même répertoire.

---

## Résultats que j'ai obtenus

- Nombre d'images traitées : 15
- Positions détectées : 14 sur 14
- Vitesse moyenne : 14.40 pixels par frame
- Type de trajectoire : diagonale régulière

Le mouvement était assez régulier dans ma simulation, ce qui se voit dans les distances successives qui restent proches les unes des autres (écart-type de 0.54 seulement).

---

## Ce que j'ai appris

**Pourquoi le seuil est important ?**
Si le seuil est trop bas, on détecte du bruit comme si c'était du mouvement. Si il est trop élevé, on rate des vraies zones de mouvement. Après avoir testé 10, 20, 30 et 40, j'ai choisi 25 comme meilleur compromis.

**Différence entre détection et tracking ?**
La détection c'est juste dire "il y a un objet ici". Le tracking c'est suivre cet objet dans le temps et savoir que c'est le même objet d'une image à l'autre.

**Le mouvement détecté est-il toujours vrai ?**
Non. Des changements de lumière ou du bruit du capteur peuvent être détectés comme du mouvement alors que rien n'a bougé. C'est une vraie limite de cette méthode.

---

## Limites de la méthode

Cette méthode est simple mais elle a ses limites :
- Elle ne fonctionne que si le fond est complètement fixe
- Elle est sensible aux variations de lumière
- Elle ne peut pas gérer plusieurs objets en même temps
- Si l'objet s'arrête, on le perd complètement

---

## Application en biomédical

Ce type de suivi peut servir à analyser la migration de cellules cancéreuses, à mesurer la vitesse de cicatrisation dans un wound healing assay, ou encore à suivre des nanoparticules médicamenteuses dans un flux sanguin.

---

## Informations

- **Filière :** GBM2
- **Matière :** Vision Artificielle – Semestre 2
- **Enseignante :** Dr. Imene OUALI
- **Institut :** Institut National des Technologies et des Sciences du Kef
- **Université :** Université de Jendouba
- **Année :** 2025-2026
