L'application NetLogo
============================

Vu le fait que l’application NetLogo fonctionne en mode graphique, on vous demande de lancer l’application dans un nœud de calcul libre, et non pas au niveau de la machine login(login-hpc.marwan.ma), en exécutant les étapes suivantes :
 
  .. image:: /figures/app-netlogo/NetLogo_etape_de_lancement.png

#. location de ressource: allocation de nœud de calcul libre pour une durée de 2 heure par défaut, vous pouvez la changer en spécifiant la partition avec l’option « -p » (pour plus de détails sur les partitions voir le lien `https://slurm.schedmd.com/salloc.html <https://slurm.schedmd.com/salloc.html>`_ ) :

    .. code-block:: bash
        $salloc -n1
        $squeue --job 79860 :JOBID donnée par la commande précédente.
        

    se connecter en mode ssh au noeud libre donnée par la commande précédente :

    .. code-block:: bash

        $ssh -X node16

#. une fois connecté au nœud , charger les modules nécessaires pour le lancement de l’application NetLogo :

    .. code-block:: bash

        $module load NetLogo/6.1.1

#. Lancement de l’application NetLogo :

    .. code-block:: bash

        $NetLogo
 
 .. image:: /figures/app-netlogo/NetLogo_interface_2.png

.. warning:: 
    N’oubliez pas de libérer les ressources réservés (nœud de calcul) à la fin du calcul :

    .. code-block:: bash
        
        $cancel 79860