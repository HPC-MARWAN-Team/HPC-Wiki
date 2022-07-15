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

