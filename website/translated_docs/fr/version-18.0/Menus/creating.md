---
id: version-18.0-creating
title: Créer des menus et des barres de menus
original_id: creating
---

Les barres de menus peuvent être définies :

- dans l'éditeur de menus de la fenêtre de Boîte à outils 4D. Dans ce cas, les menus et barres de menus sont stockés dans la structure de l'application.
- dynamiquement, à l'aide des commandes du langage depuis le thème "Menus". Dans ce cas, les menus et barres de menus ne sont pas stockés, ils existent uniquement dans la mémoire.

Vous pouvez combiner les deux fonctionnalités et utiliser les menus créés dans la structure comme templates pour définir des menus dans la mémoire.


## Barre de menu par défaut

Une application personnalisée doit contenir au moins une barre de menu avec un menu. Par défaut, lorsque vous créez une nouvelle base, 4D crée automatiquement une barre de menu par défaut (Barre n°1) pour que l’utilisateur puisse accéder au mode Application. La barre de menus par défaut (Barre n°1) comporte des menus standard et une commande de retour au mode Développement.

Ce mécanisme permet à l’utilisateur d’accéder au mode Application dès la création de la base. Menu Bar #1 is called automatically when the **Test Application** command is chosen in the **Run** menu.

La barre de menus par défaut contient trois menus : Fichier, Edition et Mode.

- **File**: only includes the **Quit** command. The *Quit* standard action is associated with the command, which causes the application to quit.
- **Edit**: standard and completely modifiable. Les fonctions d’édition du type copier, coller, etc. sont définies via des actions standard.
- **Mode**: contains, by default, the **Return to Design mode** command, which is used to exit the Application mode.
> Menu items appear *in italics* because they consist of references and not hard-coded text. Pour plus d’informations sur ce point, reportez-vous à la section [Utiliser des références dans les titres de menus](properties.md#title).

Vous pouvez modifier cette barre de menus comme vous le souhaitez ou créer des barres de menus supplémentaires.


## Créer des menus

### A l'aide de l'éditeur de menus

1. Sélectionnez la ligne de menu que vous souhaitez créer et cliquez sur le bouton d'ajout ![](assets/en/Menus/PlussNew.png) sous la zone de liste des barres de menu. OR Choose **Create a new menu bar** or **Create a new menu** from the context menu of the list or the options menu below the list. Si vous avez créé une barre de menu, une nouvelle barre de menus apparaît dans la liste, contenant les menus par défaut (Fichier et Edition).
2. (Facultatif) Effectuez un double-clic sur le nom du menu/de la barre de menus afin de le rendre éditable et saisissez un nom personnalisé. OU Saisissez le nom personnalisé dans la zone “Titre”. Les noms des barres de menu doivent être uniques. Ils peuvent comporter jusqu’à 31 caractères. You can enter the name as "hard coded" or enter a reference (see [information about the Title property](properties.md#title)).

### A l'aide du langage 4D
Use the `Create menu` command to create a new menu bar or menu reference (*MenuRef*) in memory.

When menus are handled by means of *MenuRef* references, there is no difference per se between a menu and a menu bar. Dans les deux cas, il s'agit d'une liste d'éléments. Seul leur utilisation diffère. Dans le cas d'une barre de menus, chaque élément correspond à un menu lui-même composé d'éléments.

`Créer un menu` permet de créer des menus vides (à remplir à l'aide de l'option `APPEND MENU ITEM` ou `INSERT MENU ITEM`) ou des menus créés à partir de menus conçus dans l'éditeur de menus.

## Ajouter des lignes
Pour chacun des menus, vous devez ajouter les commandes qui apparaissent lorsque le menu est déroulé. Vous pouvez insérer des lignes qui seront associées à des méthodes ou à des actions standard, ou rattacher d’autres menus (sous-menus).

### A l'aide de l'éditeur de menus
Pour ajouter une ligne de menu :

1. Dans la liste des menus source, sélectionnez le menu auquel vous souhaitez ajouter une commande. Si le menu contient déjà des commandes, elles seront affichées dans la liste centrale. Si vous souhaitez insérer la nouvelle commande, sélectionnez celle que vous souhaitez voir apparaître ci-dessus. Il est toujours possible de réorganiser le menu ultérieurement par glisser-déposer.
2. Choose **Add an item to menu “MenuName”** in the options menu of the editor or from the context menu (right click in the central list). OU Cliquez sur le bouton Ajouter ![](assets/en/Menus/PlussNew.png) situé sous la liste centrale. 4D ajoute une nouvelle ligne avec le nom par défaut “Ligne X”, où X représente le nombre de lignes déjà créées.
3. Double-cliquez sur le nom de la commande pour passer en mode édition et saisissez un nom personnalisé. OU Saisissez le nom personnalisé dans la zone “Titre”. Il peut comporter jusqu’à 31 caractères. Vous pouvez saisir le nom comme "en dur" ou saisir une référence (voir ci-dessous).


### A l'aide du langage 4D

Utilisez `INSERT MENU ITEM` ou `APPEND MENU ITEM` pour insérer ou ajouter des lignes de menu dans les références de menu existantes.


## Supprimer des menus et des lignes de menus

### A l'aide de l'éditeur de menus
Vous pouvez supprimer une barre de menus, un menu ou une ligne de menu à tout moment. A noter qu’il n’existe qu’une seule référence d’un menu ou barre de menus. Lorsqu’un menu est rattaché à différentes barres ou différents menus, toute modification ou suppression effectuée dans ce menu est immédiatement reportée dans toutes les instances de ce menu. Supprimer un menu supprimera uniquement une référence. Lorsque vous supprimez la dernière référence d'un menu, 4D affiche une alerte.

Pour supprimer une barre de menus, un menu ou une ligne de menu, vous disposez de deux possibilités :

- Sélectionner l’élément à supprimer et de cliquer sur le bouton de suppression ![](assets/en/Menus/MinussNew.png) situé sous la liste.
- or, use the appropriate **Delete...**  command from the context menu or the options menu of the editor.

> Il est impossible de supprimer Menu Bar #1.


### A l'aide du langage 4D

Utilisez la commandes `SUPPRIMER LIGNE DE MENU` pour supprimer une ligne de la barre de menus. Utilisez la commande `EFFACER MENU` pour ne pas charger le menu de la mémoire.


## Rattacher des menus

Une fois que vous avez créé un menu, vous pouvez le rattacher à une ou plusieurs barres de menus ou à un ou plusieurs autres menus (sous-menus).

Les sous-menus permettent de regrouper des fonctions thématiques à l’intérieur d’un même menu. Les sous-menus et leurs lignes peuvent disposer des mêmes attributs que les menus (actions, méthodes, raccourcis, icônes, etc.). Les lignes du sous-menu conservent leurs caractéristiques et leurs propriétés, le fonctionnement du sous-menu est identique à celui d’un menu standard.

Vous pouvez créer des sous-menus de sous-menus sur une profondeur virtuellement illimitée. A noter toutefois que pour des raisons d’ergonomie d’interface, il n’est généralement pas conseillé de dépasser deux niveaux de sous-menus.

A l'exécution, si un menu rattaché est modifié par programmation, toute autre élément du menu reflétera ces modifications.


### A l'aide de l'éditeur de menus

Un menu peut être attaché à une barre de menus ou à un autre menu.

- To attach a menu to a menu bar: right-click on the menu bar and select **Attach a menu to the menu bar "bar name" >**, then choose the menu to be attached to the menu bar: ![](assets/en/Menus/attach.png) You can also select a menu bar then click on the options button found below the list.
- To attach a menu to another menu: select the menu in the left-hand area, then right-click on the menu item and select **Attach a sub-menu to the item "item name">**, then choose the menu you want to use as sub-menu: ![](assets/en/Menus/attach2.png) You can also select a menu item then click on the options button found below the list. Le menu que vous êtes en train de rattacher deviendra un sous-menu. Le titre de la ligne est maintenu (le nom initial du sous-menu est ignoré), mais il peut être modifié.

#### Détacher des menus

Vous pouvez à tout moment détacher un menu d’une barre ou un sous-menu d’un menu. Le menu détaché n’est alors plus disponible dans la barre ou le sous-menu, mais reste présent dans la liste des menus.

To detach a menu, right-click with the right button on the menu or sub-menu that you want to detach in the central list, then choose the **Detach the menu(...)** or **Detach the sub-menu(...)**

### A l'aide du langage 4D

Since there is no difference between menus and menu bars in the 4D language, attaching menus or sub-menus is done in the same manner: use the *subMenu* parameter of the `APPEND MENU ITEM` command to attach a menu to a menu bar or an menu.  