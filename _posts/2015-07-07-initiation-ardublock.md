---
title: Introduction Ardublock
layout: post
date: 2015-07-07
tags: [arduino, algo]
category: notes
---

![pres]({{ site.baseurl }}/images/ardublock/pres.png)
Ardublock est un plugin pour l'interface de programmation d'Arduino.
Grâce à Ardublock, on peut programmer Arduino sous forme graphique, le
plugin se charge de générer le code correpondant.


## Installation

L'installation est détaillée sur le site [ardublock](http://blog.ardublock.com/engetting-started-ardublockzhardublock/)

Pour résumer, on télécharge un paquet java et on l'enregistre dans le répertoire
où se trouvent les `sketchbook`. Dans ce répertoire, on devra créer l'arborescence
`tools/ArduBlockTool/tool/` puour déposer le .jar au bout.

Par exemple pour un utilisateur nommé `abu`,

- Sous Mac, /Users/abu/Documents/Arduino/tools/ArduBlockTool/tool/ardublock-all.jar
- Sous Linux, /home/abu/sketchbook/tools/ArduBlockTool/tool/ardublock-all.jar
- Sous Windows, C:\Users\abu\Documents\Arduino\tools\ArduBlockTool\tool\ardublock-all.jar

Une fois cela fait, un nouvel outil apparaît.

![pres]({{ site.baseurl }}/images/ardublock/launch.png)


## Premier programme : blink

Le principe de programmation Ardublock est le même aue celui de Scratch :
le code se construit par assemblage de briques de couleur.

Commençons par écrire un premier programme qui va faire clignoter la LED qui se
trouve à côté de la broche 13

l'algorithme est le suivant :

1. Allumer la LED
2. patienter 500 millisecondes
3. Éteindre la LED
4. patienter 500 millisecondes
5. Reprendre à l'étape 1

Voici la traduction sous formne de blocs Ardublock


![gif]({{ site.baseurl }}/images/ardublock/led13.png)

Après avoir cliqué sur «Transférer», le résultat est là

![gif]({{ site.baseurl }}/images/ardublock/led13.gif)

## Second programme : Aide au stationnement

Dans cette partie, on va construire un detecteur de distance qui alerte
le conducteur d'une voiture s'il s'approche trop près d'un obstacle lorsqu'il
recule.

Le câblage est simple : il suffit s'alimenter le module HC-SR04 entre VCC et GND
puis raccorder aux broches de l'arduino les pattes Trig et Echo qui vont
respectivement envoyer et recevoir le signal ultrasonique.
Voir l'[article sur HC-SR04](http://npoulain.fr/mesureDeDistanceHC-SR04/) pour
des détails techniques.

![gif]({{ site.baseurl }}/images/ardublock/sonar01-fritz.png)

Avant tout, verifions le fonctionnement du détecteur de distance en construisant
le programme suivant dans Ardublock.

![gif]({{ site.baseurl }}/images/ardublock/sonar01.png)

On branche le cable USB sur Arduino puis «Transférer».

Pour verifier que les choses fonctionnent, on ouvre le moniteur série

![gif]({{ site.baseurl }}/images/ardublock/moniteurSerie.png)

En approchant et en éloignant la main devant le détecteur, on verifie qu'il est
bien capable de détecter les obstacles.

![gif]({{ site.baseurl }}/images/ardublock/moniteurSerie2.png)

On peut maintenant améliorer l'algorithme comme suit

1. On recupère la mseure de la distance avec l'obstacle
2. Si la distance n'est pas inférieure à 40cm, on ne fait rien
3. Si la distance est inférieure à 40cm, alors on fait clignoter une diode ou
   sonner un buzzer avec un fréquence d'autant plus élevée que l'obstacle est 
   proche
4. on patiente un dixième de seconde et on recommence à l'étape 1





