Le Portail Jupyter HUB 
====================================

En plus de la soumission de job via Slurm avec les commandes bash , le service HPC-MARWAN fournit a  mis en place  portail jupyterhub  :  https://hpc-jupyter.marwan.ma:8000/ pour faciliter l'execution  des Jupyter Notebooks sur les noeuds de calcul du  cluster . 


Ouvir une session 
*****************
Se connecter avec le nom d'utlisateur et le mot de passe de votre compte : 

.. image:: /source/figures/portal-jupyter/0-login.png


Explorateur de fichier 
***********************
le portail fournit un explorateur de fichiers qui vous permet la gestion de vos fichiers ( inputs , scripts , notebooks ,...) via le navigateur  .

.. image:: /source/figures/portal-jupyter/1-explorer.png


Création de kernel 
*******************

Vous pouvez créer une template pour définir l'environnement d'execution de votre job  via la menu suivant : 

.. image:: /source/figures/portal-jupyter/2-tools.png

.. note:: 
    TODO Definition du  ``kernel``   .....

HPC-MARWAN propose deux template de kernel  :

- Python 3.7 via Slurm (utilise  la version  python et les modules installés : [python-3-7-via-slurm] (#python-3-7-via-slurm) 
- Conda via Slurm  (utilise l'environnement Conda préparé par l'utilisateur) :    [conda-via-slurm] (#conda-via-slurm)

Pour créer un nouveau kernel  , choisir la template ç utuliser et cliquer sur le bouton  ``+ ``

.. image:: /source/figures/portal-jupyter/new_kernel.jpg 

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

Kernel templates de HPC-MARWAN 
*******************************
HPC-MARWAN propose deux type de kernel : 

    
Python 3.7 via Slurm 
----------------------
Cette template permet d'exploiter l'environnement par défaut installé sur HPC-MARWAN correspond à python 3.7  et propose des modules IA/DataScience  avec intégration des GPU (CUDA) : 

- ml-pythondeps-py37-cuda11.2-gcc8
- nccl2-cuda11.2-gcc8
- opencv4-py37-cuda11.2-gcc8
- pytorch-extra-py37-cuda11.2-gcc8
- pytorch-py37-cuda11.2-gcc8
- tensorflow2-extra-py37-cuda11.2-gcc8
- tensorflow2-py37-cuda11.2-gcc8

pour ce faire , 

Conda via Slurm 
-----------------
Cette template permet d'exploiter votre propore environnement python crée par Anaconda 

il faut ajouter le package `cm-jupyter-eg-kernel-wlm` a votre environnement pour l'integrer au gestionnaire de tache SLURM : 

.. code-block:: bash
         $module load  Anaconda3/2021.11
         $conda activate my_env
         $pip install cm-jupyter-eg-kernel-wlm==2.0.0

puis créer une template  en spécifiant le nom de l'environnement à utiliser  :  

.. image:: /source/figures/portal-jupyter/conda_env.jpg




