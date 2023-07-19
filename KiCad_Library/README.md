# KiCad Setup
*Instructions fait en fonction de Kicad 5.1.6*  
[Wiki](https://wiki.eclipseets.ca/en/ELE/DesignPCB/KiCad/KiCad_Setup)

# Installation
1. Pour commencer, faite l'installation du logiciel [KiCad](https://kicad-pcb.org/download/).  
2. Cloner le repo [KiCad_Library](https://github.com/EclipseETS/KiCad_Library) sur votre ordinateur à un endroit permanent.
3. Cloner le repo [Template_Hardware](https://github.com/EclipseETS/Template_Hardware) sur votre ordinateur à un endroit permanent.
4. Une fois l'installation de KiCad compétée, démarrer le logiciel.
5. Aller dans *fichier -> Ouvrir un projet*, aller dans le dossier du repo *Template_Hardware/Project_Template* et double cliquer sur *Projet_Template.pro*.

## Configuration des chemins d'accès
1. Dans la fenêtre principale de KiCad, dans préférence, ouvrir *Configurer les Chemins* 
2. Changer KICAD_SYMBOL_DIR  pour *[Votre PATH]/KiCad_Library/Library*.  
**KICAD_SYMBOL_DIR est le path pour les symboles**
3. Changer KISYS3DMOD pour *[Votre PATH]/KiCad_Library/3D_Model*  
**KISYS3DMOD est le path pour les modèles 3D.** 
4. Changer KISYSMOD pour *[Votre PATH]/KiCad_Library/Footprint*  
**KISYSMOD est le path pour les footprints**

## Library Tables
KiCad utilise des tables pour savoir quelles sont les libraries utilisées et leur emplacement. On dois donc ajouter nos libraries de pièces dans la configuration locale de KiCad.

### Table des symboles
1. Ouvrir l'éditeur de symboles
2. Ouvrir le menu préférence en haut
3. Sélectionner ```Configurer les libraries de symboles``` (```Manage Symbol Library```)
4. Cliquer sur l'icone de dossier pour ajouter des librairies à la table  
![kicad_symbole_ajout_lib.jpg](/kicad_symbole_ajout_lib.jpg)
5. Selectionner toutes les lib du dossier ```Library``` et cliquer ```ouvrir```  
![kicad_symbole_ajout_lib_ouvrir.jpg](/kicad_symbole_ajout_lib_ouvrir.jpg)
6. Fermer la fenetre en cliquant sur ```OK```
7. Fermer l'Éditeur de symboles


### Table des Footprint  
1. Ouvrir l'éditeur de Footprint
2. Ouvrir le menu préférence en haut
3. Sélectionner ```Configurer les libraries d'empreintes``` (```Manage Footprint Library```)
4. Cliquer sur l'icone de dossier pour ajouter des librairies à la table  
![kicad_symbole_ajout_lib.jpg](/kicad_symbole_ajout_lib.jpg)
5. Selectionner toutes les ```.pretty``` du dossier ```Footprint``` et cliquer sur ```ok``` 
![kicad_footprint_ajout_lib_ouvrir.jpg](/kicad_footprint_ajout_lib_ouvrir.jpg)
6. Fermer la fenetre en cliquant sur ```OK```
7. Fermer l'Éditeur d'empreinte

# Nouveau Projet
1. Demander à un admin de créer un nouveau repo à partir du repo [Template_Hardware](https://github.com/EclipseETS/Template_Hardware).
2. Cloner le nouveau repo sur votre ordinateur.
3. Remplacer les noms des fichiers dans **Project_Template** avec le nom de votre projet **SAUF Project_Template.kicad_wks** .
4. Renommer le dossier **Project_Template** avec la version (Ex.V1,V2 ...) **La hiérarchie de projet doit ressembler à E10/V1/**.
5. Commit et Push les changements au projet. **Les projets HW travaillent directement dans la branche master**

# Nouvelle Piece
Tous les composants doivent être uniques dans l'éditeur de schéma pour que l'on puisse générer les BOMs. Les Footprints et les modèles 3D eux ne sont pas uniques. 
**Toutes les pièces doivent avoir un modèle 3D et un footprint assigné.**
**Les modèles 3D doivent avoir un modèle de format STEP**

La librairie est faite pour que la création de pièce soit rapide et efficace. Les informations que vous avez de besoin devraient toutes se retrouver sur Digikey.

### Composantes

* Pour une composante dont le symbole ou une composante similaire est déjà créé

1. Ouvrir l'éditeur de symboles;
2. Dupliquer la composante similaire;
3. Modifier les informations de la pièces.

* Pour une composante créé a partir de zéro  

1. Ouvrir l'éditeur de symboles;
2. Sélectionner la librairie correspondante;
3. Cliquer sur 'Create new symbol';

* Remplir les informations nécessaire
1. Dans **Edit component properties**, dans l'onglet **Description** :  
*Description* : Copiez la description de Digikey.  
*Keywords* : Series, Type de pièce, etc. Cette information sert pour l'outil de recherche.  
*Documentation File Name* : Copiez le lien de la datasheet.
2. Dans **Add and remove field and edit field properties** (le T), remplir les champs :  
*Reference* : Lettre représentant la famille ou type de composant. Exemple, pour une résistance : R.  
(Voir : https://en.wikipedia.org/wiki/Reference_designator)  
*Value* : Nom du composant. Devrait déjà être rempli.  
*Footprint* : Assignation du footprint. Utilisez **Assign Footprint**.  
*Datasheet* : Lien vers la datasheet.  
*Supplier* : Nom du fournisseur, EX: Digikey, Mouser, etc.  
*Supplier Part Number* : Numéro de composant provenant du fournisseur.  
*Manufacturer* : Copier l'information du fournisseur.  
*Manufacturer Part Number* : Copier l'information du fournisseur.  
*Description* : Copier l'information du fournisseur.  
*Champs propre au type de composant* : Mettre les champs avec l'information nécessaire propre au type de composant. Exemple, pour une résistance, seulement mettre : Valeur de résistance, puissance, tolérance.

### Footprint
1. Ouvrir l'éditeur de footprint;
2. Sélectionner la **bonne librairie** dans **Select active library** (Premier icône en haut à gauche);
3. Créé un nouveau footprint avec **New Footprint**
4. Sauvegarder avec un nom **Significatif**. Utilisez le nom standard si le footprint est commun ex: **SOIC-8**. Si le footprint n'est pas commun, utilisez le nom de la **série** de la pièce ou dans le pire des cas son **Manufacturer Part Number**.

