# TP_FreeRTOS

## 0 Reprise en main
1. Où se situe le fichier main.c ?
  Il se trouve dans /Core/src.

2. À quoi servent les commentaires indiquant BEGIN et END (appelons ça des
balises) ?
On doit écrire notre code entre ces balises sinon la génération de code suprime notre code.

3. Quels sont les paramètres à passer à HAL_Delay et HAL_GPIO_WritePin ?
Dans HAL_delay on passe le nombre de tick à attendre. Dans HAL_GPIO_WritePin en passe un port, un pin, et la valeur qu'on veut écrire.

4. Dans quel fichier les ports d’entrée/sorties sont-ils définis ?
Dans le fichier main.h

## 1 FreeRTOS, tâches et sémaphores
1.  En quoi le paramètre TOTAL_HEAP_SIZE a-t-il de l’importance ?
C'est la consommation HEAP total de l'OS. Si on met pas une taille assez grande, on peut avoir une corruption de mémoire.

2. Quel est le rôle de la macro portTICK_PERIOD_MS ?
Le role de la macro, est de transformé un nombre de ms en nombre de tick. Si l'horloge de l'OS est de 1KHz: 1ms = 1tick.

6. Changez les priorités. Expliquez les changements dans l’affichage.

## 2 On joue avec le Shell
1.3. Expliquer les mécanismes qui mènent à l’exécution de la fonction.

1.4. Quel est le problème ?

1.5. Proposer une solution

2. Que se passe-t-il si l’on ne respecte pas les priorités décrites précédemment ?

