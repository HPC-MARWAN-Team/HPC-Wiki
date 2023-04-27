Accès à l’HPC via Linux
=============================

Via le Terminal 
*****************

Ouvrir un terminal de votre machine  et taper la commande ssh : 

.. code-block:: bash
    
    $ssh -X username@hpc-login.marwan.ma ( remplacer username par votre login )

Transfert de fichiers 
*********************

Ouvrir un terminal de votre machine et taper la commande scp 

-Pour transferer un fichier locale vers l'espace /home du cluster : 

.. code-block:: bash

    $scp local_file username@hpc-login.marwan.ma:/home/username/remote_file

-Pour transferer un fichier du cluser vers la machine utilisateur  : 

.. code-block:: bash

     $scp username@hpc-login.marwan.ma:/home/username/remote_file   local_file


-Pour transferer un dossier , il suffit d'ajouter l’option -r
 
.. code-block:: bash

  $scp -r username@hpc-login.marwan.ma:/home/username/remote_folder local_folder
  $scp -r local_folder username@hpc-login.marwan.ma:/home/username/remote_folder


Client SCP  
***********

Vous pouvez aussi utiliser le  client SCP de votre choix  . Voici la commande d’installation de Filezilla pour Ubuntu :

.. code-block:: bash

    $sudo apt install filezilla
    
.. image:: /source/figures/img_guideutilisateur/fiz.jpg
  :width: 600
 
