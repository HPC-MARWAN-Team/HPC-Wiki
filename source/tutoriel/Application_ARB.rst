L'application ARB
=====================

Vu le fait que l’application ARB fonctionne en mode graphique, on vous demande de lancer l’application dans un nœud de calcul libre, et non pas au niveau de la machine login login-hpc.marwan.ma, en exécutant les étapes suivantes :

.. image:: /source/figures/application-arb/etape_de_lancement_de_arb.png
   :width: 800
 

Allocation de ressource:  allocation de nœud de calcul libre pour une durée de 2 heure par défaut, vous pouvez la changer en spécifiant la partition avec l’option « -p »  (pour plus de détails sur les partitions voir le lien `https://slurm.schedmd.com/salloc.html <https://slurm.schedmd.com/salloc.htmlL>`_) :

.. code-block:: bash

    $salloc -n1

    $squeue --job 65467 :JOBID donnée par la commande précédente.
 
se connecter en mode ssh au noeud réservé au job donnée par la commande précédente.

.. code-block:: bash

    $ssh -X node07

une fois connecté au nœud , charger les modules nécessaires pour le lancement de l’application ARB :

.. code-block:: bash

    $module load xerces-c/gcc/64/3.2.2

    $module load ARB/gcc/18314

Puis lancer l’application:

.. code-block:: bash

    $arb


.. image:: /source/figures/application-arb/ARB_interface.png
   :width: 800


.. warning::
    N’oubliez pas de libérer les ressources réservés (nœud de calcul) à la fin du calcul :

.. code-block:: bash

         $cancel 65467
