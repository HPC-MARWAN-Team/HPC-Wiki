===================
Gestion des données
===================
Systèmes de fichiers 
***********************************

Le cluster HPC-MARWAN contient 3 espaces disques /home , /data et /scratch pour la gestion des fichiers. Un dossier personnel est mis à la disposition de l’utilisateur sur chacun des  espaces :

  * Le dossier personnel sur l’espace /home (/home/$USER) , limité à ``100G`` par utilisateur.
  * Le dossier personnel sur l’espace /data (/data/$USER) , limité à ``500G`` par utilisateur.
  * Le dossier personnel sur l’espace /scratch (/scratch/users/$USER) , limité à ``500G`` par utilisateur.


Il est recommandé d’utiliser l’espace /home pour les fichiers scripts de slurm , bash scripts et codes sources. les fichiers de grandes tailles ( input ou output ) doivent être placé dans le dossier personnel sur l’espace /data , /scratch .

**Essayer de nettoyer régulièrement** les dossiers /data/$USER , /home/$USER et /scratch/users/$USER en supprimant les fichiers et dossiers non utiles et en déplaçant les données pertinentes vers un stockage personnel.

Gestion du quota disque sur /home
***********************************

Pour avoir plus d’information sur le quota, exécuter la commande :

.. code-block:: bash

    $quota -s -f /home

.. image:: /source/figures/image_data/quotahome.png

Ou ``blocks`` est la taille de votre espace /home/$USER en Megabyte, quota est le ``quota`` de l’espace /home/$USER définit par le système, ``limit`` est la taille maximum de /home/$USER qu’il ne peut  jamais dépasser, ``grace`` est le compteur déclenché si ``blocks`` est égale ou supérieur à 100G

L’utilisateur ne peut pas dépasser la limite de 150G et aura immédiatement une erreur ``Disk quota exceeded``

Au moment où l’utilisateur dépasse 100G sur son espace /home/$USER , un compteur de ``14 jours`` se déclenche et décrémente chaque jour. Il s’agit d’un délai donné à l’utilisateur afin de lui permettre de nettoyer son espace /home. A la fin de cette période, si la taille de /home/$USER est toujours supérieure à 100G, le système déclenchera une erreur de dépassement de quota disque ``Disk quota exceeded``

le process qui precede s'applique aussi sur l'epace /data et /scratch

.. code-block:: bash

   $quota -s -f /data

.. image:: /source/figures/image_data/quotadata.png


Pour plus d'informations sur votre espace de stockage beegfs (/scratch), tapez la commande suivante:

.. code-block:: bash
  
    $srun -p defq -C beegfs beegfs-ctl --getquota --uid $UID

.. image:: /source/figures/image_data/quotadatainteractif.png

Commandes Utiles 
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
