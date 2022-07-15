Exemple avec GPU 
********************
L'utilisation des cartes GPU nécessite de spécifier : 
    
* Le modèle de cartes GPU  ( Tesla P100 ou Volta S100 ) ;

* Une des partitions spécifique au GPU  : ``gpu-testq`` ou ``gpu-prodq`` selon la durée estimées ( 1 heure ou  7 jours respectivement )  ;

* Account ``gpu_users`` si l'utulisateur est autorisé à réserver les cartes GPU ;
    
ci dessous un exemple de création de kernel pour GPU 

.. image:: /source/figures/portal-jupyter/kernel_gpu.jpg

et son exploitation sur un exemple de notebook affichant le nom du noeud  et le type de carte GPU

.. image:: /source/figures/portal-jupyter/notebook_gpu.jpg


