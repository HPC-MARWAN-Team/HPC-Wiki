Accès à l’HPC 
##############################################


Via linux
=============================

Via le Terminal 
*****************

Commande ssh et commande scp ou installer un client (Filezilla) pour le transfert des fichiers

.. code-block:: bash
    
    $ssh -X username@hpc-login.marwan.ma ( remplacer par votre login )

Transfert de fichier 
*********************

Pour transferer un fichier depuis le HPC vers  la machine de l'utilisateur  , utiliser la commande :

.. code-block:: bash

     $scp username@hpc-login.marwan.ma:/home/username/fichier.txt   /home/localuser/fichier.txt


Pour transferer un fichier depuis la machine de l'utilisateur vers le HPC  , utiliser la commande 

.. code-block:: bash
 
      $scp /home/localuser/fichier.txt username@hpc-login.marwan.ma:/home/username/fichier.txt 

Transfert de dossier 
**********************

 Pour transferer tout un dossier , ajouter l’option -r à la commandes scp : 
 
.. code-block:: bash
    
    $scp -r username@hpc-login.marwan.ma:/home/username/dossier   
    
    $scp -r /home/localuser/dossier username@hpc-login.marwan.ma:/home/username/dossier

Outil de transfert de fichiers  
*******************************
Vous pouvez  utiliser un client SFTP   tel que  Filezilla . 

Voici la Commande d’installation pour Ubuntu :

.. code-block:: bash

    $sudo apt install filezilla
    
.. image:: /source/figures/img_guideutilisateur/fiz.jpg
  :width: 600

Connecter l'espace de stockage distant via le gestionnaire de fichier
***********************************************************************
Dans la plupart des environnements de bureau modernes, le navigateur/gestionnaire de fichiers (Nautilus, Nemo, Thunar, Dolphin, etc.) devrait prendre en charge SFTP.

.. image:: /source/figures/img_guideutilisateur/nautilus.png

Il suffit de spécifier  protocole sftp dans la barre du nom du serveur **sftp://username@hpc-login.marwan.ma:/home/username**

Une fois connecté, vous aurez accès aux répertoires et fichiers du serveur distant. Vous pourrez alors naviguer dans ces fichiers et dossiers, copier et coller des fichiers et dossiers, ainsi qu'éditer les fichiers textes, tout comme vous le feriez avec les fichiers et dossiers locaux.

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

