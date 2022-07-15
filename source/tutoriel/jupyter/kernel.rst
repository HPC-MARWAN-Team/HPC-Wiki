
Création de kernel 
*******************

Vous pouvez créer une template pour définir l'environnement d'execution de votre job  via la menu suivant : 

.. image:: /source/figures/portal-jupyter/2-tools.png

.. note:: 
    TODO Definition du  ``kernel``   .....

HPC-MARWAN propose deux template de kernel  :

+-----------------------+------------------------------------------------------------------+
| Template              | Description                                                      | 
+=======================+==================================================================+
| Python 3.7 via Slurm  | utilise  la version  python et les modules installés par défaut  | 
+-----------------------+------------------------------------------------------------------+
| Conda via Slurm       | utilise l'environnement Conda préparé par l'utilisateur          |          
+-----------------------+------------------------------------------------------------------+


Pour plus de détail , voir la section [Kernel templates de HPC-MARWAN](<#kernel-templates-de-hpc-marwan> "Kernel templates de HPC-MARWAN")
 

Pour créer un nouveau kernel  , choisir la template à utiliser et cliquer sur le bouton  ``+ ``

.. image:: /source/figures/portal-jupyter/new_kernel.jpg 

Un popup s'ouvre avec plusieurs options à remplir selon le besoin de l'utilisateur , tels que :  

* Nombre de  Tasks  ( pour les job MPI)  

* list des modules à charger 

.. image:: /source/figures/portal-jupyter/module_load.jpg 

* Partition  pour l'allocation de ressources 

.. image:: /source/figures/portal-jupyter/partition.jpg 

* L'utilisation des cartes GPU nécessite en plus de choisir 
    
   * Le modèle de cartes GPU  ( Tesla P100 ou Volta S100 )
       
.. image:: /source/figures/portal-jupyter/gpu_cards.jpg 


   * Une des partitions spécifique au GPU  : ``gpu-testq`` ou ``gpu-prodq`` selon la durée estimées ( 1 heure ou  7 jours respectivement ) 


   * Account ``gpu_users`` si l'utulisateur est autorisé à réserver les cartes GPU 
    
.. image:: /source/figures/portal-jupyter/account.png


Utilisation  du kernel 
**********************

Pour exploiter le kernel , il suffit de l'assosier à votre notebook  :

.. image:: /source/figures/portal-jupyter/select_kernel.jpg 

Attendre l'initialisation du kernel (INITIALIZING) 

.. image:: /source/figures/portal-jupyter/kernel_init.jpg

une fois le kernel  pret (IDLE) 

.. image:: /source/figures/portal-jupyter/kernel_idle.jpg

vous pouver lancer interactivement  les cellules du notebook : 

.. image:: /source/figures/portal-jupyter/notebook.jpg

un kernel initialisé correspond à une allocation de ressource via SLURM que vous pouvez visualiser avec la commande **squeue** au niveau de la session ssh vers la machine de login : 

.. code-block:: bash
            [b.rahim@login02 ~]$ squeue -u $USER
             JOBID PARTITION     NAME     USER ST       TIME  NODES NODELIST(REASON)
            144585      defq jupyter- b.rahim  R      25:53      1 node22

a la fin de votre simulation , vous pouvez arreter le kernel via l interface 

.. image:: /source/figures/portal-jupyter/shutdown.jpg

et s'assurer que l'allocation a bien été annulée  avec la commande **squeue** 

