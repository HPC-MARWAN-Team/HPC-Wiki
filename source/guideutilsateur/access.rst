Accès à l’HPC via Windows
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

Accès à l’HPC via Linux
=============================

Via le Terminal 
*****************

Commande ssh et commande scp ou installer un client (Filezilla) pour le transfert des fichiers

.. code-block:: bash
    
    $ssh -X @hpc-login.marwan.ma ( remplacer par votre login )

Transfert de fichier 
*********************

.. code-block:: bash

     $scp @hpc-login.marwan.ma:/home// $scp @hpc-login.marwan.ma:/home//

Transfert de dossier 
**********************

.. code-block:: bash

    (ajouter l’option -r) $scp -r @hpc-login.marwan.ma:/home// $scp -r @hpc-login.marwan.ma:/home//

Ou utiliser un client SCP graphique( exemple Filezilla )Commande d’installation pour Ubunto :

.. code-block:: bash

    $sudo apt install filezilla
    
.. image:: /source/figures/img_guideutilisateur/fiz.jpg
  :width: 600
 
