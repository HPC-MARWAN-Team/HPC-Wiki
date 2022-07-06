Le Portail Jupyter HUB 
====================================

En plus de la soumission de job via Slurm avec les commandes bash , le service HPC-MARWAN fournit a  mis en place  portail jupyterhub  :  https://hpc-jupyter.marwan.ma:8000/ pour faciliter l'execution  des Jupyter Notebooks sur les noeuds de calcul du  cluster . 


Ouvir la session 
*****************
Se connecter avec le nom d'utlisateur et le mot de passe de votre compte : 


.. image:: /source/figures/portal-jupyter/0-login.png


Explorateur de fichier 
***********************
le portail fournit un explorateur de fichiers qui vous permet la gestion de vos fichiers ( inputs , scripts , notebooks ,...) via le navigateur  .

.. image:: /source/figures/portal-jupyter/1-explorer.png


Kernel templates  
*****************
TODO Definition du  kernel   .....
vous pouvez créer une template pour définir l'environnement d'execution de votre job  via la menu suivant : 

.. image:: /source/figures/portal-jupyter/2-tools.png

Python via Slurm 
-----------------
l'environnement par défaut installée sur HPC-MARWAN correspond à python 3.7  et propose des modules IA/DataScience  avec intégration des GPU (CUDA)
- ml-pythondeps-py37-cuda11.2-gcc8
- nccl2-cuda11.2-gcc8
- opencv4-py37-cuda11.2-gcc8
- pytorch-extra-py37-cuda11.2-gcc8
- pytorch-py37-cuda11.2-gcc8
- tensorflow2-extra-py37-cuda11.2-gcc8
- tensorflow2-py37-cuda11.2-gcc8

Conda via Slurm 
-----------------
Afin d exploiter votre propore environnement python crée par Anaconda 

il faut ajouter le package `cm-jupyter-eg-kernel-wlm` a votre environnement pour l'integrer au gestionnaire de tache SLURM : 
    .. code-block:: bash
         $module load  Anaconda3/2021.11
         $conda activate my_env
         $pip install cm-jupyter-eg-kernel-wlm==2.0.0

puis créer une template en spécifiant le nom de l'environnement à utiliser  . 





