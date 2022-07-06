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
version par défaut de python + modules installées par défauts 
tensorflow ... 

Conda via Slurm 
-----------------
Afin d exploiter votre propore environnement python crée par Anaconda 

il faut ajouter le package a votre environnement 

puis créer une template en spécifiant le nom de l'environnement à utiliser 





