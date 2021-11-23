L'application Jupyter notebook 
======================================

Pour accéder à Jupyter Notebook à partir de votre navigateur, vous devez passer par un tunnel ssh.
Voici les étapes principales à suivre :

• Creation d'un environnement Conda sur votre espace de travail. en poursuivant les étapes décrites dans le lien suivant:`https://github.com/HPC-MARWAN-Team/hpc_samples/tree/master/Anaconda <https://github.com/HPC-MARWAN-Team/hpc_samples/tree/master/Anaconda>`_  et installation de jupyter à l'aide de la commande ``conda install``
• Réservation d’un core d’un nœud de calcul libre via la commande :

.. code-block:: bash

    srun -N 1 -n 1 -p defq --pty bash -i
    
Vous pouvez ajouter d'autres argument pour demander une partition spécifique ou plus de cores, pour plus d’informations voir la documentation sur la commande ``srun –help`` . Par défaut cette commande vous donne accès ssh à un des nœuds de calcul où vous pouvez lancer Jupyter Notebook. L’option ``defq`` de cette commande vous permet d’accéder   à ce nœud durant 2h.

.. image:: /source/figures/app-jupyter-notebook/linux1.jpg

• Charger l’environnement Conda que vous avez crée dans l'étape precedente sur le nœud de calcul réservé auparavant (pour notre exemple de test c’est node11) . l’environnement Conda installé sur le cluster HPC-MARWAN est anaconda, voici les lignes de commandes a exécuter pour charger l’environnement anaconda et activer l’application jupyter :

.. code-block:: bash

    export CONDA_ENVS_PATH=/data/$USER/envs
    module load anaconda3
    source activate my_Env_Name

• Lancer Jupyter Notebook en précisant un numéro de port (40000 par exemple)


.. image:: /source/figures/app-jupyter-notebook/linux2.jpg
  
.. Note::
     Noter le token généré par Jupyter pour sécuriser l’accès

Sur Windows
*************
 a l’aide de l'application MobaXterm , créer le tunnel ssh :

.. image:: /source/figures/app-jupyter-notebook/4.png

Et le configurer pour permettre le forwarding entre

    - un port libre dans votre machine locale (exemple 8080)
    - la machine hpc-login.marwan.ma(port 22 )
    - et le nœud alloué (pour notre exemple : node11 , port 40000)

.. image:: /source/figures/app-jupyter-notebook/5.png


 Puis lancez le tunnel (bouton ‘Start’ ) et tapez le mot de passe de votre compte ssh sur la machine hpc-login.marwan.ma .
   

.. image:: /source/figures/app-jupyter-notebook/6.png


Sur Linux 
**********
Ouvrir un terminal et lancer la commande suivante:

.. code-block:: bash
          ssh username@hpc-login.marwan.ma -L8080:node11:40000 –N
    

.. image:: /source/figures/app-jupyter-notebook/6.png
 

Une fois le tunnel ssh démarré, vous pouvez vous connecter via le navigateur de votre machine local (de préférence Firefox ou Chrome) après avoir fourni le token généré (par exemple : db3648aa8efc526c89239523acda3a166ce17389fab97c94), voir la figure suivante :

.. image:: /source/figures/app-jupyter-notebook/7.png

Pour terminer l’allocation des ressources (node11 dans l’exemple), il suffit d’arrêter le notebook (ctrl –c) et de faire un exit du nœud réservé.
