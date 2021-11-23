Questions Fréquemment Posées
====================================





Principe de fonctionnement de HPC
------------------------------------------------


En principe, l’utilisation du cluster de calcul haute performance se fait en ``mode batch`` .Ce qui signifie que le chercheur prépare ses fichiers inputs au préalable et lance le calcul via une commande ``sbatch``.

- Le calcul atterrit par la suite dans une file d’attente contenant d’autres calculs appartenant aux autres utilisateurs du HPC ``squeue`` et le gestionnaire des calculs (SLURM pour notre cas) a pour rôle d’affecter une ressource libre au premier calcul de la file d’attente.
 
 * Le calcul est géré par SLURM et le chercheur peut fermer la session . Il peut consulter de temps en temps l’état de calcul avec le commande ``squeue`` pour voir si son calcul a été lancé.

 * Une fois le calcul lancé, le chercheur consulte le dossier d’exécution et suit l’avancement via les fichiers logs et outputs.

 * Quand le calcul se termine, il disparait de la file d’attente et le chercheur peut récupérer les résultats sur son laptop.

 * Les commandes utiles pour le mode batch sont décrite dans la deuxième partie du tutoriel : Gestion des calculs.

- Le mode interactif avec interface graphique est aussi possible, mais présente des limitations.  S’il n’y a pas de ressources libre, le chercheur doit attendre devant son pc jusqu’à que la ressource lui soit affectée . 
Une fois il a la main et fait les manipulations nécessaires, il ne doit pas quitter la session jusqu’à la fin de l’exécution. 
Aussi la réservation de la ressource ne peut généralement pas dépasser quelques heures si le programme ne se termine pas avant, il sera arrété.

.. Note::
     Nous conseillons au chercheur d’utiliser le ``mode batch`` pour la partie lourde du travail,programme qui a besoin d’un temps de calcul important , 
     et laisser le mode interactif pour le ``post-processing`` par exemple la visualisation d’un fichier output.

	
	
Que dois-je faire pour être autorisé à utiliser le cluster HPC-MARWAN?
-----------------------------------------------------------------------------------


Afin d'accéder au Cluster HPC-MARWAN , il vous suffit de remplir ce formulaire , le signer et le retourner à l'équipe HPC-MARWAN par l'un des moyens suivants :
   
   • En vous rendant au CNRST , Angle Allal Al Fassi et Avenue des FAR, Hay Ryad, BP. 8027 10102 Rabat
   • Par Fax : (+212) 05 37.56.98.34
   • Par Mail :hpc@marwan.ma

Une fois la demande reçue ,l'équipe vous contactera dans les plus brefs délais pour la création du compte d'accès.



Ai-je besoin d'un programme spécial pour accéder au cluster HPC?
----------------------------------------------------------------------


Cela dépend du système d'exploitation que vous utilisez sur votre ordinateur privé et de la façon dont vous devez utiliser le système HPC. Vous avez besoin ``d'un client SSH`` pour pouvoir vous connecter au système.

Si vous souhaitez utiliser des programmes avec une interface utilisateur graphique, vous pouvez installer le logiciel ``Mobaxtream`` (disponible pour Windows). Les instructions sont disponibles sous le rubrique Guide utilisateur.



Combien d'espace disque puis-je utiliser? 
-----------------------------------------------------------------------

Chaque utilisateur de HPC-MARWAN dispose d'un répertoire personnel de ``2Go`` (/home/login). Vous pouvez déposer vos fichiers volumineux sur /data/login,dont la limite et 2 To.



Demander de l'aide
---------------------------------------

Le modèle de soutien du service HPC-MARWAN fournit une assistance personnelle individualisée pour répondre aux besoins uniques et complexes de chaque chercheur.

Si vous avez des questions ou si vous avez besoin d'aide pour utiliser le cluster, envoyez un e-mail à hpc@marwan.ma.



Formulaire reçue incomplet
----------------------------------------

Au cas de réception du formulaire incomplet,nous demandons à l’utilisateur de nous ré-envoyez le formulaire rempli et signé.



Problèmes d’accès à l’HPC
--------------------------------------------

La majorité des problèmes d’accès à l’HPC-MARWAN, sont dus:

   * Plusieurs tentative de connexion erronées.

   * Mot de passe erronée (erreur de frape/ ajout d’espace …).

   * Adresse IP public bloquée.

Pour cela on demande aux utilisateurs de nous envoyer une capture d’écran du message d’erreur, et de nous envoyer leur adresse IP public https://www.whatismyip.com.




Probléme de lancement d'un calcul
------------------------------------------------

En cas d’utilisation d’un éditeur de fichier sous Windows pour écrire le script Slurm run.sl ; le lancement de ce dernier run.sl sous linux, vous donnera l’erreur suivante :

.. code-block:: bash

  $ sbatch run.sl

  sbatch: error: Batch script contains DOS line breaks (\r\n)

  sbatch: error: instead of expected UNIX line breaks (\n).


Afin de résoudre se problème, on vous propose d’utiliser un éditeur de fichier (Notepad++) qui permet de spécifier linux comme format.

.. image:: /source/figures/mobaxterm.png



Combien de calculs je peux lancer ?
------------------------------------------------------


Le nombre de calculs qui peuvent être exécutés ``Etat Running`` simultanément pour chaque utilisateur est de ``10`` calculs. 
Le nombre de calcul pouvant être placés dans la queue ``Etat Pending`` est limité à ``20`` calculs.



