Accès à l’HPC 
##############################################


Via linux
=============================

Via le Terminal 
*****************

Commande ssh et commande scp ou installer un client (Filezilla) pour le transfert des fichiers

.. code-block:: bash
    
    $ssh -X login@hpc-login.marwan.ma ( remplacer par votre login )

Transfert de fichier 
*********************
pour transferer un fichier depuis le HPC vers  la machine de l'utilisateur  , utiliser la commande 
.. code-block:: bash


     $scp <username>@hpc-login.marwan.ma:/home/<username>/fichier.txt   /home/<localuser>/fichier.txt
pour transferer un fichier depuis la machine de l'utilisateur vers le HPC  , utiliser la commande 

.. code-block:: bash
 
      $scp /home/<localuser>/fichier.txt <username>@hpc-login.marwan.ma:/home/<username>/fichier.txt 

Transfert de dossier 
**********************

.. code-block:: bash

  pour transferer tout un dossier , ajouter l’option -r à la commandes scp : 
    
    $scp -r <username>@hpc-login.marwan.ma:/home/<username>/<dossier>   
    
    $scp -r /home/<localuser>/<dossier> <username>@hpc-login.marwan.ma:/home/<username>/<dossier>

Ou utiliser un client SCP graphique( exemple Filezilla )

Commande d’installation pour Ubuntu :

.. code-block:: bash

    $sudo apt install filezilla
    
.. image:: /source/figures/img_guideutilisateur/fiz.jpg
  :width: 600


Via windows
=============================

Installer un client ssh ( Mobaxterm ou Putty ) et un client scp (Winscp, Filezilla, Mobaxterm) pour le transfert des fichiers

.. Hint:: 
    Paramètres de connexion: 
        * Username : username (remplacer <username> par votre login )
        * Remote host: hpc-login.marwan.ma
        * Port : 22
    
Acces ssh avec MobaXterm
**************************

.. image:: /source/figures/img_guideutilisateur/access_ssh.png
    :width: 500

.. image:: /source/figures/img_guideutilisateur/Mobaxterm.png
    :width: 500
    
Transfert de fichiers (scp) avec Mobaxterm 
************************************************

    - Transfert de fichiers/dossiers de la machine de l’utilisateur vers le dossier personnel sur HPC

.. image:: /source/figures/img_guideutilisateur/uploadfichier.png
      :width: 500

    - Transfert de fichiers/dossiers du dossier personnel sur HPC vers la machine de l’utilisateur

.. image:: /source/figures/img_guideutilisateur/downloadfichier.png
    :width: 500

    - Changement de dossier courant (taper /data/<username>pour accéder au dossier de données et effectuer les transferts)

.. image:: /source/figures/img_guideutilisateur/Changementdossier.png
    :width: 500

