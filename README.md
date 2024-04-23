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
Dans ce screen on a mis la tache Take plus prioritaire que la tache give, ce qui took s'écrit avant token given.
https://github.com/Slaigosh/TP_FreeRTOS/blob/main/Screenshot1.png

7. et 8. Voici le code des taches, avec task notification et queue.
https://github.com/Slaigosh/TP_FreeRTOS/blob/main/Screenshot2.png

12. Il faut créer un sémaphore binaire et prendre le sémaphore dans les taches avant d'utiliser le printf. On donne le sémaphore quand on a finit d'utiliser le printf.

## 2 On joue avec le Shell
2. Que se passe-t-il si l’on ne respecte pas les priorités décrites précédemment ?
L'appel d'une fonction FreeRTOS déclenche un hardfault.

3. et 4. Voici la fonction LED et spam:
https://github.com/Slaigosh/TP_FreeRTOS/blob/main/Screenshot3.png

## 3 Debug, gestion d’erreur et statistiques


