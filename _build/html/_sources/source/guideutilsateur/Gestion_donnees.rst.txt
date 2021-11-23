===================
Gestion des données
===================
Le cluster HPC-MARWAN contient deux espaces disques /home et /data pour la gestion des fichiers. Un dossier personnel est mis à la disposition de l’utilisateur sur chacun des deux espaces :

  * Le dossier personnel sur l’espace /home (/home/$USER) , limité à ``2G`` par utilisateur.
  * Le dossier personnel sur l’espace /data (/data/$USER) , limité à ``2T`` par utilisateur.

Il est recommandé d’utiliser l’espace /home pour les fichiers scripts de slurm , bash scripts et codes sources. les fichiers de grandes tailles ( input ou output ) doivent être placé dans le dossier personnel sur l’espace /data .
**Essayer de nettoyer régulièrement** les dossiers /data/$USER et /home/$USER en supprimant les fichiers et dossiers non utiles et en déplaçant les données pertinentes vers un stockage personnel.

Gestion du quota disque sur /home
***********************************

Pour avoir plus d’information sur le quota, exécuter la commande :

.. code-block:: bash

    $quota

    Disk quotas for user:
     +--------------+---------+---------+----------+-------+-------+-------+-------+-------+
     | Filesystem   | blocks  | quota   | limit    | grace | files | quota | limit | grace |
     +--------------+---------+---------+----------+-------+-------+-------+-------+-------+
     | master:/home | 1602908 | 2097152 | R3145728 | 0     | 15712 | 0     | 0     | 0     |
     +--------------+---------+---------+----------+-------+-------+-------+-------+-------+




Ou ``blocks`` est la taille de votre espace /home/$USER en kilobyte, quota est le ``quota`` de l’espace /home/$USER définit par le système, ``limit`` est la taille maximum de /home/$USER qu’il ne peut
 jamais dépasser, ``grace`` est le compteur déclenché si ``blocks`` est égale ou supérieur à 2G

L’utilisateur ne peut pas dépasser la limite de 3G et aura immédiatement une erreur ``Disk quota exceeded``

Au moment où l’utilisateur dépasse 2G sur son espace /home/$USER 2G, un compteur de ``14 jours`` se déclenche et décrémente chaque jour. Il s’agit d’un délai donné à l’utilisateur afin de lui permettre de nettoyer son espace /home. A la fin de cette période, si la taille de /home/$USER est toujours supérieure à 2G, le système déclenchera une erreur de dépassement de quota disque ``Disk quota exceeded``

Commandes Utiles :
******************

Pour vérifier le contenu des dossiers :

.. code-block:: bash

    $ls -al /data/$USER
    $ls -al /home/$USER

Pour vérifier la taille des dossiers, utiliser la commande :

.. code-block:: bash

    $du -sh /data/$USER
    $du -sh /home/$USER

Pour vérifier la taille des sous dossiers :

.. code-block:: bash

    $du -h /data/$USER --max-depth 1
    $du -h /home/$USER --max-depth 1
