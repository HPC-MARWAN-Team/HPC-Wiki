Le Portail Jupyter HUB 
====================================

Ce tutoriel vous montre comment exploiter le portail Jupyter HUB  pour la somission de calcul dans le 
https://hpc-jupyter.marwan.ma:8000


Ouvir la session 
*****************
capture login 


.. image:: /source/figures/app-paraview/0-runserver.png


Explorateur de fichier 
***********************
explorer les fichiers


    mpirun -np 1 pvserver --force-offscreen-rendering

Allocation de ressource 
---------------------------


Sur la machine de connexion hpc-login.marwan.ma, utilisez la commande appropriée pour allouer un nœud de calcul libre (srun, salloc ). Vous devez utiliser les différents d'option pour spécifier les détails de la commande tels que le nombre de nœuds, les limites de temps, la partition des nœuds à utiliser. Par exemple:


Démarrer le(s) serveur(s)
---------------------------

Une fois que les nœuds sont réservés (dans les prise d’écran, le nœud réservé est : node4 ), vous serez connecté à une ligne de commande interactive sur le premier nœud du travail par lots. Charger le module paraview, et lancer le serveur pvserver souhaitées. Par exemple :

.. code-block:: bash
    module load ParaView

    mpirun -np 1 pvserver --force-offscreen-rendering

.. image:: /source/figures/app-paraview/0-runserver.png

Par defaut Paraview utilise le port 11111

Créer un tunnel SSH
---------------------

Afin de créer des tunnels SSH vers ou depuis votre système Windows, vous aurez besoin d'un logiciel supplémentaire. Nous vous recommandons d'utiliser Mobaxterm comme client SSH sur Windows. Les suivantes vous montrent comment vous pouvez créer un tunnel ssh entre votre machine, la machine hpc-login.marwan.ma et le nœud de calcul réservé auparavant (node4)


Création de Kernel Python via Slurm 
-------------------------------------

Une fois que vous avez un pvserver en cours d'exécution sur le cluster, vous pouvez vous connecter à partir de votre client de bureau. Ouvrez ParaView sur votre bureau (si vous ne l'avez pas déjà fait fonctionner). Ensuite, cliquez sur l'icône Connexion, ou sélectionnez Fichier -> Connexion dans les menus.


Création de Kernel Conda via Slurm 
-------------------------------------

Une fois que vous avez un pvserver en cours d'exécution sur le cluster, vous pouvez vous connecter à partir de votre client de bureau. Ouvrez ParaView sur votre bureau (si vous ne l'avez pas déjà fait fonctionner). Ensuite, cliquez sur l'icône Connexion, ou sélectionnez Fichier -> Connexion dans les menus.

