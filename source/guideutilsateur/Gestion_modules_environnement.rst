============================================
Gestion des modules d’environnement
============================================

Afin de répondre au mieux aux divers besoins de tous nos chercheurs, Les logiciels sur HPC-MARWAN sont principalement gérés par un système de modules ``lmod``. En chargeant et en commutant les modules, vous contrôlez les compilateurs, les bibliothèques et les logiciels disponibles.

Lorsque vous compilez ou exécutez des programmes sur HPC-MARWAN, vous devez configurer les modules appropriés, pour charger votre compilateur et toutes les bibliothèques requises (par exemple, les bibliothèques numériques, les bibliothèques de format 
d'entrée/sortie).

Afin de gérer ces logiciels, le cluster HPC-MARWAN utilise des ``fichiers de module``. 
Ces fichiers de module vous permettent de spécifier facilement quelles versions de quels paquets vous souhaitez utiliser.

Pour plus d'informations, consultez la documentation en ligne sur le système de module d’environnement : `https://lmod.readthedocs.io/en/latest/010_user.html <https://lmod.readthedocs.io/en/latest/010_user.html>`_

Liste de tous les modules chargés 
************************************

La commande ``module list`` affiche tous les noms des modules et de leurs versions qui sont actuellement chargés dans votre environnement :

.. image:: /source/figures/img_lmod/lmod1.png
     :width: 800

Trouver les modules disponibles 
*********************************

Pour lister les modules disponibles sur le système, on utilise la commande ``module avail`` :

.. image:: /source/figures/img_lmod/modules_disponibles.png
    :width: 800
    
Vous pouvez également lister tous les modules dont le nom contient une chaîne de caractères spécifique. Par exemple, pour trouver tous les fichiers de module Python, utilisez ``module avail python`` :

.. image:: /source/figures/img_lmod/modules_disponibles2.png
    :width: 800

.. Note:: 
Si un logiciel n'est pas disponible dans la liste des modules, n'hésitez pas à nous envoyer une demande d'installation du logiciel à  hpc@marwan.ma .

Charger et décharger les modules 
***********************************

Pour charger un module, on utiliser la commande ``module add`` ou ``module load`` . Par exemple, si vous avez trouvé et souhaitez charger la version 3.7.4 de Python, exécutez la commande :

.. code-block:: bash

  module load python/3.7.4
  module add python/3.7.4

Vous pouvez charger la version par défaut d’un module. Par exemple, pour charger la version par défaut du compilateur ``gcc`` :

.. image:: /source/figures/img_lmod/Charger_moduledefaut.png
     :width: 800

Vous pouvez également décharger / supprimer un module que vous avez déjà chargé, on utilisant les commande ``module unload``, ou ``module rm`` :

.. image:: /source/figures/img_lmod/decharger_modules.png
    :width: 800

Collections des modules 
**************************

Les utilisateurs peuvent créer des collections des modules, qui contiennent la liste des modules à charger chaque fois que vous vous connectez au cluster.

Cette méthode est particulièrement utile si vous avez deux ou plusieurs ensembles de modules qui peuvent entrer en conflit les uns avec les autres.

Pour créer une collection sauvegardée, il suffit de charger tous les modules souhaités, puis de taper ``module save`` afin d’enregistrer cet ensemble des modules comme votre ensemble par défaut.

Si vous souhaitez avoir plusieurs collections des modules, il suffit d’attribuer un nom à la collection en tapant ``module save environnement_name`` .

.. image:: /source/figures/img_lmod/Collections_modules.png
    :width: 800

Pour charger la collection par défaut ou spécifiée, tapez respectivement ``module restore`` , ``module restore environnement_name`` .

.. image:: /source/figures/img_lmod/charger_collectiondefaut.png
     :width: 800

Pour modifier une collection, restaurer la collection, effectuer les changements souhaités en chargeant et/ou en déchargeant des modules et à sauvegarder sous le même nom.

Un utilisateur peut lister les collections dont il dispose en tapant ``module savelist`` :

.. image:: /source/figures/img_lmod/modifier_collection.png
    :width: 800

 
 
