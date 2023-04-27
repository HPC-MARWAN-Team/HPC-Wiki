Accès à l’HPC via Linux
=============================

Via le Terminal 
*****************

.. code-block:: bash
    
    $ssh -X username@hpc-login.marwan.ma ( remplacer username par votre login )

Transfert de fichier 
*********************

.. code-block:: bash

     $scp username@hpc-login.marwan.ma:/home/username/remote_file   local_file 
     $scp local_file username@hpc-login.marwan.ma:/home/username/remote_file
     
Transfert de dossier 
**********************
  ajouter l’option -r
.. code-block:: bash

  $scp -r username@hpc-login.marwan.ma:/home/username/remote_folder local_folder
  $scp -r local_folder username@hpc-login.marwan.ma:/home/username/remote_folder

Client SCP 
***********

Exemple Filezilla , voici la commande d’installation pour Ubuntu :

.. code-block:: bash

    $sudo apt install filezilla
    
.. image:: /source/figures/img_guideutilisateur/fiz.jpg
  :width: 600
 
