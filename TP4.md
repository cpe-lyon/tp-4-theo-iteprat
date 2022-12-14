## Théo ITEPRAT - 3ICS

# 1. Commandes de base

### 1 - 
Pour mettre à jour le système, on utilise d'abord la commande ```apt update``` puis ```apt upgrade```

### 2 - 
Pour créer un alias permanent, il faut se rendre dans le fichier ```~/.bashrc``` et y définir un nouvel alias ```alias maj='sudo apt update ; sudo apt upgrade'```. Il faut ensuite forcer le redémarrage de Ubuntu afin de rendre les modifications effectives à l'aide de la commande ```source ~/.bashrc```. L'alias est désormais mis en ligne.

### 3 - 
Pour obtenir les 5 derniers paquets  installés par la machine, on utilise la commande ```tail -5 /var/log/dpkg.log'

### 4 -
![image](https://user-images.githubusercontent.com/113093094/192952254-4b867a38-d01e-4e69-9673-a1df2584e4be.png)


### 5 - 
Pour compter les paquets installés, on peut utiliser ```dpkg --list | wc -l``` : on obtient un nombre de 611 paquets. On peut aussi compter les paquets en utilisant ```apt list --installed | wc -l```, on en compte 607. Cette différence s'explique par des lignes de texte ajoutées au début du fichier dpkg. 

### 6 - 
Pour déterminer combien de paquets sont disponibles en téléchargement sur les dépôts Ubuntu, on utilise la commande ```apt list | wc -l```. On voit qu'il y en a 68744 

### 7 -
glances est un outil de surveillance qui permet d'afficher l'état des principales ressources d'un système, de sa charge et du fonctionnement des applications.
tldr, quant à lui est une alternative à la commande ```man```. Il permet cependant de résumer l'essentiel de la page et non d'y afficher toutes les informations.
hollywood est un programme qui simule un centre de contrôle affichant des logs qui défilent. Ce paquet n'a pas de réelle utilité si ce n'est dans un but esthétique.
```
sudo apt update 
sudo apt install glances 
sudo apt install tldr
sudo apt install hollywood
```     

### 8 - 
Pour savoir quels paquets permet de jouer au sudoku, il convient d'exécuter la commande ```apt search sudoku```


## Exercice 2

Pour trouver le paquet installant la commande ls, il faut utiliser la commande ```dpkg -S ls```. Pour obtenir cette information en une seule commande ```dpkg -S $(which ls)```.

```bash
#!/bin/bash

if [ $# -ne 1 ]; then
    echo "Usage: $0 <command>"
    exit 1
fi

dpkg -S $(which $1)
```

## Exercice 3. 

```bash
dpkg -s $1 | grep Status | cut -d " " -f 4
```

## Exercice 4.

Pour lister les programmes livrés avec coreutils, il faut exécuter la commande ````apt-cache show coreutils | grep -E "Package:|Description:"````. Le programme ````.```` sert à vérifier si un fichier existe.

## Exercice 5.

Installer emacs et lynx : ```aptitude install emacs lynx```.



## Exercice 6.

Pour installer la version Oracle de Java, il faut utiliser la commande ```sudo add-apt-repository ppa:webupd8team/java``` puis ```sudo apt-get update``` et enfin  ```sudo apt-get install oracle-java8-installer```.

Pour vérifier qu'un nouveau fichier a été créé, on utilise  ```ls /etc/apt/sources.list.d```. Ce fichier contient les nouveaux dépôts de paquets.


