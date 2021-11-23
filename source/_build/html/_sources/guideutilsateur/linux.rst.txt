Accès à l’HPC via Linux
=============================

Via le Terminal :
*****************

Commande ssh et commande scp ou installer un client (Filezilla) pour le transfert des fichiers

.. code-block:: bash
    
    $ssh -X @hpc-login.marwan.ma ( remplacer par votre login )

Transfert de fichier :
*********************

.. code-block:: bash

     $scp @hpc-login.marwan.ma:/home// $scp @hpc-login.marwan.ma:/home//

Transfert de dossier :
**********************

.. code-block:: bash

    (ajouter l’option -r) $scp -r @hpc-login.marwan.ma:/home// $scp -r @hpc-login.marwan.ma:/home//

Ou utiliser un client SCP graphique( exemple Filezilla )Commande d’installation pour Ubunto :

.. code-block:: bash

    $sudo apt install filezilla

    .. image:: /figures/img_guideutilisateur/fiz.jpg

 
