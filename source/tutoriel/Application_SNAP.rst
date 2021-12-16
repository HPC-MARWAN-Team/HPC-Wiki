L'application SNAP
=====================

Vu le fait que l’application SNAP fonctionne en mode graphique, on vous demande de lancer l’application dans un nœud de calcul libre, et non pas au niveau de la machine login login-hpc.marwan.ma, en exécutant les étapes suivantes :


.. code-block:: bash
    $salloc -N 1 -n 1 -p defq --constraint=opa bash
   
    $squeue -j 115113 :JOBID donnée par la commande précédente.
        
.. image:: /source/figures/application-snap/sallocsnap.png
   :width: 800
 

Allocation de ressource:  allocation de nœud de calcul libre pour une durée de 2 heure par défaut, vous pouvez la changer en spécifiant la partition avec l’option « -p » . vus que l'application SNAP est configuré pour utilisé jusqu'à 16 threads et 10G de memoire, vous pouvez spacifier le nombre de cpu, et la tail de memoire a alloué , en changant l'option «-n et ajoutant l'option «--mem» , (pour plus de détails sur les options de la commande salloc voir le lien `https://slurm.schedmd.com/salloc.html <https://slurm.schedmd.com/salloc.htmlL>`_) :
   
 
Se connecter en mode ssh au noeud réservé au job donnée par la commande précédente.

.. code-block:: bash

    $ssh -X node01

Une fois connecté au nœud , charger les modules nécessaires pour le lancement de l’application SNAP :

.. code-block:: bash

    $module load SNAP/8.0

Puis lancer l’application:

.. code-block:: bash

    $snap

.. image:: /source/figures/application-snap/snaplancer.png
   :width: 800
   
   
.. image:: /source/figures/application-snap/snapapp.png
  
.. warning::
    N’oubliez pas de libérer les ressources réservés (nœud de calcul) à la fin du calcul :

.. code-block:: bash

         $exit
         $cancel 115113
