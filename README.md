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
![plot](./Screenshot1.png)

7. et 8. Voici le code des taches, avec task notification et queue.
![plot](./Screenshot2.png)

12. Il faut créer un sémaphore binaire et prendre le sémaphore dans les taches avant d'utiliser le printf. On donne le sémaphore quand on a finit d'utiliser le printf.

## 2 On joue avec le Shell

2. Que se passe-t-il si l’on ne respecte pas les priorités décrites précédemment ?
L'appel d'une fonction FreeRTOS déclenche un hardfault.

3. et 4. Voici la fonction LED et spam:
![plot](./Screenshot3.png)

## 3 Debug, gestion d’erreur et statistiques
### 3.1 Gestion du tas

1. Quel est le nom de la zone réservée à l’allocation dynamique ?
C'est la zone HEAP.

2. Est-ce géré par FreeRTOS ou la HAL ?
C'est géré par le FreeRTOS car on le retrouve dans la fonction pvPortMalloc qui est géré par le FreeRTOS.

4. Notez la mémoire RAM et Flash utilisée.
Voici notre mémoire à cet instant:
![plot](./Screenshot4.png)

6. Notez la nouvelle utilisation mémoire.
![plot](./Screenshot4.png)

7. Dans CubeMX, augmentez la taille du tas (TOTAL_HEAP_SIZE). Générez le code, compilez et testez.

8. Notez la nouvelle utilisation mémoire. Expliquez les trois relevés.
![plot](./Screenshot5.png)

Pour les 2 premiers relevés avant/après les taches bidons, on constate les meme relevés.
Cela représente pas l'utilisation imadiate, mais ce que FreeRTOS reserve dans la mémoire.
Après avoir augmenté la taille de FreeRTOS, on voit bien un plus gros pourcentage d'utilisation.

### 3.2 Gestion des piles

3. Écrivez la fonction vApplicationStackOverflowHook. (Rappel : C’est une
fonction appelée automatiquement par FreeRTOS, vous n’avez pas à l’appeler
vous-même).
![plot](./Screenshot6.png)

5. Il existe d’autres hooks. Expliquez l’intérêt de chacun d’entre eux.
IDLE_HOOK : Quand on rentre dans la tache IDLE
TICK_HOOK : Quand il y a un Tick d'OS
MALOK_FAILE_HOOK : Quand Maloc échoue
DEMON_TASK_STARTUP_HOOK : lance une fonction au démarrage

### 3.3 Statistiques dans l’IDE

4. Lancez le programme puis mettez-le en pause pour voir les statistiques.
![plot](./Screenshot7.png)

7. Affichez les sémaphores et les queues.
Il n'y en a pas car on n'en utilise pas dans le projet.

## 4 Écriture d’un driver
### 4.1 Interfacer l’ADXL345
