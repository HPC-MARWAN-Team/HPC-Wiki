====================================
Guide d'installation des applications
====================================

L’équipe HPC-MARWAN prend en charge l’installation d’une pile logicielle assez étendue d’outils et d’applications les plus couramment utilisés par la communauté scientifique marocaine. Cependant, il est recommandé aux utilisateurs d'installer eux-mêmes les applications spécifiques dont dépend leur travail. 

La liste des applications installées sur HPC-MARWAN sont disponibles sur `le site web HPC-MARWAN <https://hpc.marwan.ma/index.php/fr/>`_ , ou en utilisant la commande « module avail ». Pour plus d’information, voir le guide d’utilisateur `lien <https://hpc-wiki.readthedocs.io/fr/latest/source/guideutilsateur/installation_application.html>`_.

Indépendamment de la méthode d’installation, le répertoire d’application doit être placer dans l’espace utilisateur /home/$USER.
Si l’installations ne peut être effectuée que par l’équipe HPC-MARWAN. Vous pouvez envoyer une demande d’installation d’application à l’équipe par mail à hpc@marwan.ma
Ceci est un d’installation des applications dans votre répertoire personnel. Si vous avez besoin d'aide, veuillez envoyer vos erreurs via `lien <https://hpc-wiki.readthedocs.io/fr/latest/source/guideutilsateur/Gestion_donnees.html>`_.

Condition d’installation
*********************************

* Vérifiez si l’application est déjà disponible dans le cluster HPC-MARWAN en utilisant les commandes  "module spider" ou "module avail".
* Les binaires, bibliothèques et fichiers d'inclusion du système sont situés dans /usr/bin/, /usr/lib/ , /usr/lib64 et /usr/include.
* Si l’application a des dépendances d'installation - telles que des bibliothèques, des interfaces ou des modules - vérifiez d'abord si elles sont déjà fournies sur le cluster avant de les installer vous-même. Assurez-vous d'avoir d'abord chargé (module load) le compilateur, le langage interprété ou l'application concernés avant d'examiner la liste des logiciels fournis, car cette liste est ajustée dynamiquement en fonction de votre environnement actuel.
* L’application ne peut pas être installé directement via les RPMs/YUM. elle doit être téléchargée sous forme de fichier compressé, par exemple tar.gz.
* Red Hat Entreprise Linux 8 est notre système d'exploitation par défaut.

Préparations d’installation 
*********************************
Dossier d’installation
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
La partie la plus importante de l'installation d’une application est d'identifier où vous devez l'installer et comment vous devez modifier le script d'installation pour pointer vers le bon emplacement. Nous recommandons la structure de répertoire suivante, que vous devez créer au niveau supérieur de votre répertoire personnel :

.. code-block:: bash

    local
        |-- apps
        |-- modfiles
        |-- share

        

* local/apps - Rassemble tous les fichiers liés à vos installations locales dans un seul répertoire, pour éviter d'encombrer votre répertoire personnel. Les applications seront installées dans ce répertoire avec le format "nom d'application/version". Cela vous permet de gérer facilement plusieurs versions d'une installation logicielle particulière si nécessaire.
* local/share - Stocke les installateurs - généralement les répertoires sources - de vos applications. Stocke également les archives compressées ("tarballs") de vos installateurs ; utile si vous voulez réinstaller plus tard en utilisant différentes options de construction.
* local/modfiles – le dossier standard pour stocker les fichiers de modules, qui vous permettront d'ajouter ou de supprimer dynamiquement des applications installées localement dans votre environnement.

Vous pouvez créer cette structure avec une seule commande :

.. code-block:: bash

    $  mkdir -p /home/$USER/local/apps /home/$USER/local/modfiles/home/$USER/local/share


Allocation de ressource
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Ne lancer pas l’installation de l’application directement sur des nœuds de connexion (login), car ceci peut avoir un impact sur les sessions et la connectivité de tous les autres membres du cluster. Réserver un nœud de calcul, en exécutant la commande suivante :

.. code-block:: bash

    $ salloc -N 1 -n 1 -p defq bash
    $ ssh nodealocated

Certains paquets permettent la compilation en parallèle. Pour compiler en parallèle, vous aurez besoin de plus de tâches. Choisissez une valeur différente pour l'indicateur -n. Il s'agira du nombre de threads que vous pourrez spécifier à la compilation. 

Téléchargement de l’application
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Maintenant que vous avez créé votre structure de répertoire, vous pouvez installer votre application. Pour les besoins de la démonstration.
Tout d'abord, localisez le fichier d'installation dans le site web qui correspond à l'environnement et à la plate-forme de votre serveur. Les fichiers d'installation sont généralement au format de compression tar.gz, tar.bz2. 
Téléchargez le fichier d'installation dans votre répertoire personnel $HOME/local/share :

.. code-block:: bash

    $ cd $HOME/local/share

Depuis le web :

.. code-block:: bash

    $ wget <url>
(Cliquez avec le bouton droit de la souris sur le lien du fichier et sélectionnez "copier l'adresse du lien" pour l'url).

Depuis GitHub : comme un service d'hébergement basé sur le web, clonez le dépôt ou vous pouvez télécharger le format .zip en cliquant sur le lien ZIP :

.. code-block:: bash

    $ git clone <url>

(Remarque : s'il n'y a pas d'option wget ou git pour télécharger et que vous téléchargez le fichier manuellement sur votre PC, transférez-le au HPC en suivant la procédure suivante : 

.. code-block:: bash

    $ scp -r /fromyourlocal/folder-name   $USER@hpc-login.marwan.ma:/home/$USER/local/share/

Installation d’application
*********************************

From source code
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Maintenant que vous avez créé votre structure de répertoire, et téléchargée le code source de l’application, vous pouvez installer votre application.

Tout d'abord, vous devez décompresser l'archive afin d'avoir accès au code source et aux autres fichiers : 

.. code-block:: bash

    $ tar xzvf software-name-0.1.tar.gz

Ensuite, nous allons aller dans le répertoire source.

.. code-block:: bash

    $ cd  software-name-0.1

Vous pouvez trouver les fichiers README, Notes ou INSTALL avec d'autres fichiers de configuration. Ces fichiers peuvent vous guider dans votre processus d'installation. Si vous trouvez CMakeLists.txt, alors vous devez l'installer en utilisant l'utilitaire cmake. Si vous trouvez le fichier configure, alors vous allez suivre le process « Configure-Make-MakeInstall ». 

Configure-Make-MakeInstall
------------------------------

Dans ce cas, nous utiliserons l'option --prefix de l'outil configure pour spécifier l'emplacement d'installation.

.. code-block:: bash

    $./configure --prefix=/home/$USER/local/apps/software-name/version
    $ make
    $ make install
    $ make clean

configure est généralement un script shell complexe qui rassemble des informations sur le système et prépare le processus de compilation.
Avec l'option --prefix vous pouvez spécifier un répertoire d'installation de base, où make install installera les fichiers dans des sous-répertoires comme bin, lib, include, etc.
L'utilitaire make est celui qui effectue la compilation et l'édition de liens. Si, par exemple, certaines bibliothèques supplémentaires manquent sur le système ou ne sont pas trouvées à l'endroit prévu, la commande se terminera immédiatement.

CMake install
--------------------------------
Cmake est le système de construction multiplateforme. Le processus de construction est décrit dans un simple fichier texte CMakeLists.txt via des commandes spéciales de CMake. Lorsqu'il est invoqué, CMake analyse ces fichiers texte et génère une chaîne de compilation native pour la plate-forme et le compilateur souhaités. Il fournit des options permettant à l'utilisateur de personnaliser le processus de construction.
Pour modifier les variables CMake, utilisez l'option -D après la commande cmake. Pour changer l'emplacement du répertoire d'installation du répertoire par défaut /usr/local au répertoire personnel, utilisez "DCMAKE_INSTALL_PREFIX=/home/$USER/local/apps/software-name/version".
Créez un répertoire de build et accédez-y. Les résultats du compilateur sont stockés ici, ce qui inclut les fichiers objets ainsi que l'exécutable final et les bibliothèques.

.. code-block:: bash

    $mkdir /home/$USER/local/sahre/software-name-0.1/build;cd build

Exécutez la commande cmake avec les options appropriées.

.. code-block:: bash

    $cmake .. -DCMAKE_INSTALL_PREFIX=/home/$USER/local/apps/software-name/version

(Si vous devez assigner plusieurs bibliothèques, vous pouvez le faire avec -D<X_LIBRARIES>='-L <path-to-library> -l<lib1> -l<lib2>')

Makefile est créé dans le répertoire source une fois la configuration terminée. Maintenant, vous pouvez lancer la commande make :

.. code-block:: bash

    $make

Pour installer les binaires et les bibliothèques à l'emplacement préfixé par configure pour le logiciel installé, utilisez la commande make install.

.. code-block:: bash

    $make install



Votre application devrait maintenant être complètement installée. Cependant, avant de pouvoir l'utiliser, vous devrez ajouter les répertoires de l'installation à votre chemin. Pour ce faire, vous devrez créer un module.

Precompiled Binaries
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Dans ce cas, Il vous suffit de décompresser ou de dé-tarer le fichier d'installation en déterminant le chemin dans le module file.

 .. code-block:: bash

    $tar xzvf software-name-0.1.tar.gz -C /home/$USER/local/apps/software-name/version
    $unzip software-name-0.1.zip  -d /home/$USER/local/apps/software-name/version

Il y a des cas où le répertoire bin peut ne pas avoir la permission d'exécuter. Dans ce cas, exécutez la commande suivante :

.. code-block:: bash

    $chmod -R 755 <path-to-bin>/bin


Easybuild 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

EasyBuild est un logiciel de build et d'installation d’application visant spécifiquement les systèmes HPC, avec un accent sur l'automatisation du build, la reproductibilité et la résolution automatique des dépendances. Il est entièrement compatible avec le système de modules Lmod, et chaque installation d'EB génère automatiquement un fichier module correspondant qui vous permet de charger le logiciel dans votre environnement.
EasyBuild est le moyen le plus simple et le plus rapide pour installer une application par vous-même. Toutes les installations sont effectuées au niveau de l'utilisateur, vous n'avez donc pas besoin des droits d'administrateur (root). Les applications sont installés dans votre répertoire personnel sous $EASYBUILD_PREFIX.

.. code-block:: bash

    $mkdir -p /home/$USER/local/Easybuild 
    $Export $ EASYBUILD_PREFIX=/home/$USER/local/Easybuild

Les logiciels installée sont placés sous ${EASYBUILD_PREFIX}/software/
Le chemin d'installation des modules ${EASYBUILD_PREFIX}/modules/all

Afin d’installer une application en utilisant Easybuild, Les étapes suivantes sont nécessaires :

* Charger les modules
* Trouver la spécification du package 
* Déterminer la chaine d’outil souhaitée
* Lancer l'installation EasyBuild en utilisant eb-install-all ou eb-install-generic

Charger les modules
----------------------

En premier lieu, vous devez charger le module EasyBuild. Assurez-vous que vous avez un environnement propre sans aucun autre module chargé :

.. code-block:: bash

    $module purge
    $module load EasyBuild

.. Attention::/!\ IMPORTANT:
Rappelons que vous devez être sur un nœud de calcul pour poursuivre vos installation.

Chercher le package
-------------------------

EasyBuild dispose d'un large référentiel d’application disponibles en différentes versions. Les applications disponibles peuvent être recherchés en utilisant la commande suivante :

.. code-block:: bash

    $eb -S software-name

Easybuild génère la liste des référentiels. Dans cette liste, vous devez sélectionner la version correspondante à la version de la chaîne d'outils cible, exemple «softwarename3.8-GCCcore-9.3.0-Java-1.8.eb» .

Choisir le package
-------------------------

Pour installer une application avec EasyBuild, la première chose à faire est de choisir une chaîne d'outils de compilation supportée par EasyBuild. Cette chaine d’outils spécifie les dépendances associées, qui sont chargées avec l’application. Ces dépendances peuvent avoir d'autres dépendances.

Les chaînes d'outils de compilation sont essentiellement un ensemble de compilateurs avec un ensemble de bibliothèques qui fournissent un support supplémentaire qui est généralement requis pour construire des logiciels. Cela consiste généralement en une bibliothèque MPI (communication inter-processus sur un réseau), BLAS/LAPACK (routines d'algèbre linéaire) et FFT (Transformations de Fourier rapides).

La chaîne de dépendances est appelée toolchain. Par exemple :

* GCC consiste en GCCcore et binutils
* gompi consiste en GCC et OpenMPI
* foss est basé sur le compilateur GCC et sur des bibliothèques open-source (OpenMPI, OpenBLAS, FFTW, ScaLAPACK etc.).
* intel est basé sur le compilateur Intel et sur des bibliothèques Intel (Intel MPI, Intel Math Kernel Library, etc.).


Pour lister les toolchains connues d'EasyBuild, utilisez l'option de ligne de commande --list-toolchains (disponible depuis EasyBuild v1.1). Cela donnera quelque chose comme ci-dessous :

.. code-block:: bash

    $ eb --list-toolchains
    List of known toolchains (toolchainname: module[,module...]):
            ClangGCC: Clang, GCC
            GCC: GCC
            cgmpich: ClangGCC, MPICH
            cgmpolf: BLACS, ClangGCC, FFTW, MPICH, OpenBLAS, ScaLAPACK
            cgmvapich2: ClangGCC, MVAPICH2
            cgmvolf: BLACS, ClangGCC, FFTW, MVAPICH2, OpenBLAS, ScaLAPACK
            cgompi: ClangGCC, OpenMPI
            cgoolf: BLACS, ClangGCC, FFTW, OpenBLAS, OpenMPI, ScaLAPACK
            dummy:
            gcccuda: CUDA, GCC
            gimkl: GCC, imkl, impi
            gmacml: ACML, BLACS, FFTW, GCC, MVAPICH2, ScaLAPACK
            gmpich2: GCC, MPICH2
            gmpolf: BLACS, FFTW, GCC, MPICH2, OpenBLAS, ScaLAPACK
            gmvapich2: GCC, MVAPICH2
            gmvolf: BLACS, FFTW, GCC, MVAPICH2, OpenBLAS, ScaLAPACK
            goalf: ATLAS, BLACS, FFTW, GCC, OpenMPI, ScaLAPACK
            gompi: GCC, OpenMPI
            goolf: BLACS, FFTW, GCC, OpenBLAS, OpenMPI, ScaLAPACK
            goolfc: BLACS, CUDA, FFTW, GCC, OpenBLAS, OpenMPI, ScaLAPACK
            gqacml: ACML, BLACS, FFTW, GCC, QLogicMPI, ScaLAPACK
            iccifort: icc, ifort
            ictce: icc, ifort, imkl, impi
            iiqmpi: QLogicMPI, icc, ifort
            iomkl: OpenMPI, icc, ifort, imkl
            iqacml: ACML, BLACS, FFTW, QLogicMPI, ScaLAPACK, icc, ifort
            ismkl: MPICH2, icc, ifort, imkl
    

Installation 
-----------------

Après avoir sélectionné le package d'installation et toolchain cible, le processus d'installation peut être soumis. Les packages y sont installés et les fichiers de modules créés. La syntaxe générale est la suivante :

.. code-block:: bash

    $ eb_install_{all,generic} [options] [easybuild options] <software-name-toolchain>.eb

Example d’installation de Geant4:

.. code-block:: bash

    $ export tmp_dir=/home/$USER/_Easybuild/tmp
    $ export source_path=/home/$USER/local/share
    $eb Geant4-10.5-foss-2018b.eb -r --tmpdir=$tmp_dir --ignore-checksums --sourcepath=$source_path

Dans cet exemple on lance l’installation de l’application Geant4 version 10.5 dont le toolchain est « foss-2018b ». L’option -r (--robot) active la résolution des dépendances, en installant automatiquement toutes les dépendances.  L’option --sourcepath permet de déterminer le dossier dans lequel Easybuild télécharge les archives et procède à l’installation, par contre l’option --tmpdir definit le dossier temporaire de chargement des archives.
Pour plus de détails merci de consulter le site officiel de easybuild : https://docs.easybuild.io/en/latest/Configuration.html

Une fois terminé, un message comme celui-ci s’affiche :
.. code-block:: bash

    == Build succeeded for 1 out of 1
    == Temporary log file(s) /tmp/eb-BoOCuj/easybuild-CuSy5M.log* have been removed.
    == Temporary directory /tmp/eb-BoOCuj has been removed.

vous devriez être en mesure d'utiliser l’application, en chargeant simplement le module du package installé :

.. code-block:: bash

    $ module use /home/$USER/local/Easybuild/all
    $ module load  software-name

Création de module
*********************************

Après avoir installé l’application dans votre répertoire comme expliqué ci-dessus, et avant de l'utiliser, un fichier module utilisateur doit être créé.
Un fichier module décrit l'emplacement et la configuration de l'environnement pour l'application ciblée, par exemple en définissant les variables PATH, LD_LIBRARY_PATH et autres. Le système Lmod actuel recherche ces fichiers modules dans les sous-répertoires de tous les répertoires enregistrés dans $MODULEPATH. 
Supposons que nous avons installé l’application software-name avec la version « X.Y». Le répertoire de module serait alors :
.. code-block:: bash
/home/$USER/local/modfiles/software-name/toolchaine/X.Y  
Nommez le fichier de module comme le numéro de version (X.Y) de votre logiciel installé, puis placez le fichier de module dans un répertoire portant le nom du logiciel. 
La manière la plus simple d'écrire votre fichier de module est d'utiliser l'exemple ci-dessous comme modèle.

.. code-block:: bash

    #%Module -*- tcl -*-
    ###
    ### dot modulefile
    ###
    proc ModulesHelp { } {
      puts stderr "\tAdds software-name to your environment variables,"
      }
      module-whatis "adds software-name to your environment variables"    
     set                       version                     $version
     set                       root                          /home/$USER/local/apps/software-name
     prepend-path     PATH                        $root/bin
     prepend-path     LD_LIBRARY_PATH   $root/lib64
     prepend-path     LIBRARY_PATH         $root/lib64
     prepend-path     CPATH                      $root/include


Afin d’utiliser ce module, vous devez indiquer à lmod où le chercher. Vous pouvez le faire en lançant la commande module use :

.. code-block:: bash

    $ module use /home/$USER/local/modfiles
    $ module load software-name/toolchaine/version

NOTE : le module use et le module load "software_name" doivent être entrés dans la ligne de commande chaque fois que vous entrez dans une nouvelle session sur le système, aussi à déclarer au niveau du script Slurm pour lancer un job utilisant une de vos applications installées en local.
