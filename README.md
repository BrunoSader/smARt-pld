1. - ## Manuel utilisateur

     1. Télécharger le fichier .apk sur le téléphone portable
     2. Lancer l'application
     3. Scanner le QR code correspondant à l'objet
     4. Pointer la caméra du téléphone vers la première étape de l'assemblage
     5. Mettre la pièce suivante à l'endroit indiqué sur l'application
     6. Pointer de nouveau la caméra sur l'assemblage
     7. Suivre les étapes jusqu'à la fin de l'assemblage
     8. Possibilité de recommencer la construction avec d'autres codes QR.

     *** Le lien du projet unity : https://developer.cloud.unity3d.com/collab/orgs/300381/projects/3ff49d0a-9db5-420a-9041-e952f859e371/assets/ (afin d'y acceder il faut creer un compte et demander a un membre de l'hexanome h4244 de vous ajouter a l'organisation)
     
     *** Le lien du fichier .apk est disponible à l'adresse suivante: https://drive.google.com/open?id=1ABIXG0YCO3pK15jb3Tx4VmTs33VPpceu

     ## Construire l'application avec des modèles propres

     1. Sur le site de Vuforia, dans Target Manager, rajouter tous les QR dans une base de données nommée “smARt” sous forme d’Image. Une fois la base des données des QR faite, importer la dans Unity. Attention les QR doivent être nommés d'après une nomenclature spécifique : **“QRCode”+ObjName**.

        > Par exemple, le QR Code à utiliser pour démarrer l'assemblage de la construction "Avion" est "QRCodeAvion".

     2. Utiliser Vuforia Model Target Generator. Chaque étape doit suivre la nomenclature suivante : ObjName+”Step”+stepNum. Une étape correspond à l'assemblage partiel jusqu'à cette étape : AvionStep1 = Avion partie 1; AvionStep2 = Avion partie 1+2; AvionStep3 = Avion partie 1+2+3. Une fois chaque étape créée, créer une base de données du nom : **ObjName+”Training”** et l'entraîner sur les étapes créées. Importer la base de données dans Unity en cliquant dessus avec le projet Unity ouvert.

     3. Dans Unity, créer une scène par assemblage d'après la nomenclature : ObjName+”_scene-1”. Dans cette scène, importer smARtARCamera et smARtUI (à trouver dans les scènes Examples). Dans smARtARCamera, remplacer la Preview Animation par l’animation de votre objet final.

     4. Les objets 3d à importer sont de deux types : Obj et Build. La différence est dans le nom des objets.

        - Obj : Les objets de nom obj sont les objets à ajouter à une étape donnée. L’objet à ajouter à l'étape n est donc **ObjName+”Obj”+stepnum**. 

          > Par exemple, l'objet à ajouter à l'étape 3 de la construction "Avion" doit s'appeler "AvionObj3".

        - Build: Objets utilisés pour l’occlusion à l'étape n, c’est donc l’objet actuel de l'étape n : **ObjName+”Build”+stepnum**. 

          > Par exemple, l'objet nécessaire à l'occlusion corresponant à l'étape 2 de la construction "Avion" doit s'appeler "AvionBuild2".

     ## Tester dans le viewfinder Unity

     1. Une fois le projet complet, vous pouvez tester chaque scène individuellement en cliquant sur le button "play" en haut.
     2. La scène "scene-0" se charge de scanner les codes QR importés.
     3. Chaque scène correspondant à un assemblage s'occupe de reconnaître la totalité des étapes de l'assemblage.

     ## Build l'application pour la tester sur android

     1. Une fois le projet complet, aller dans File->Build Settings : en haut sélectionner la "scene-0" (ayant le 0 qui lui est associé à droite dans la fenêtre) et les scènes qui correspondent aux assemblages à tester.
     2. Tester l'application :
        - Pour tester directement avec un portable android depuis Unity: brancher le portable à l'ordinateur avec un cable USB et activer "USB debugging mode" sur le portable. Aller dans File->Build and run. Utiliser l'application en mode normal sur téléphone.
        - Pour tester depuis le téléphone en tant qu'application en dehors d'Unity: aller dans File->Build Settings->Build. Sélectionner l'emplacement souhaité sur le disque. Télécharger l'application sur votre portable par le moyen souhaité. Installer le .apk sur votre portable. Lancer l'application mobile.
        
        NB : le dossier Assets est le dossier qui contient les scripts et les scenes de notre projet. Sur ce git, par contre, il n'est pas complet, car il manque les objets 3d et les modeles targets (trop lourd pour le git).
