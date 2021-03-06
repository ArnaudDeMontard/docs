---
id: propertiesBackgroundAndBorder
title: Fond et bordure
---

---
## Couleur de fond alternée

Permet de définir une couleur d'arrière-plan différente pour les lignes / colonnes impaires dans une list box. By default, *Automatic* is selected: the column uses the alternate background color set at the list box level.

#### Grammaire JSON

| Nom           | Type de données | Valeurs possibles                          |
| ------------- | --------------- | ------------------------------------------ |
| alternateFill | string          | une valeur css; "transparent"; "automatic" |

#### Objets pris en charge
[List Box](listbox_overview.md#overview) - [Colonne List Box](listbox_overview.md#list-box-columns)



---
## Background Color / Fill Color

Defines the background color of an object.

In the case of a list box, by default *Automatic* is selected: the column uses the background color set at the list box level.

#### Grammaire JSON


| Nom          | Type de données | Valeurs possibles                          |
| ------------ | --------------- | ------------------------------------------ |
| border-style | string          | une valeur css; "transparent"; "automatic" |

#### Objets pris en charge

[Liste Hiérarchique](list_overview.md) - [List Box](listbox_overview.md) - [Colonne List Box](listbox_overview.md#list-box-columns) - [Pied List Box](listbox_overview.md#list-box-footers) - [Ovale](shapes_overview.md#oval) - [Rectangle](shapes_overview.md#rectangle) - [Zone de texte](text.md)

#### Voir également
[Transparent](#transparent)


---
## Expression couleur de fond

`Selection and collection type list boxes`

An expression or a variable (array variables cannot be used) to apply a custom background color to each row of the list box. The expression or variable will be evaluated for each row displayed and must return a RGB color value. For more information, refer to the description of the `OBJECT SET RGB COLORS` command in the *4D Language Reference manual*.

You can also set this property using the `LISTBOX SET PROPERTY` command with `lk background color expression` constant.
> With collection or entity selection type list boxes, this property can also be set using a [Meta Info Expression](properties_Text.md#meta-info-expression).

#### Grammaire JSON

| Nom           | Type de données | Valeurs possibles                         |
| ------------- | --------------- | ----------------------------------------- |
| rowFillSource | string          | An expression returning a RGB color value |

#### Objets pris en charge
[List Box](listbox_overview.md#overview) - [Colonne List Box](listbox_overview.md#list-box-columns)






---
## Style de la bordure

Permet de définir un style standard pour la bordure de l'objet.

#### Grammaire JSON

| Nom         | Type de données | Valeurs possibles                                                 |
| ----------- | --------------- | ----------------------------------------------------------------- |
| borderStyle | Texte           | "system", "none", "solid", "dotted", "raised", "sunken", "double" |

#### Objets pris en charge

[Zone 4D View Pro](viewProArea_overview.md) - [Zone 4D Write Pro](writeProArea_overview.md) - [Boutons](button_overview.md) - [Grille de boutons](buttonGrid_overview.md) - [Case à cocher](list_overview.md#overview) - [Zone de saisie](input_overview.md) - [List Box](listbox_overview.md#overview) - [Bouton image](pictureButton_overview.md) - [Pop up menu image](picturePopupMenu_overview.md) - [Zone de plug-in](pluginArea_overview.md#overview) - [Indicateur de progression](progressIndicator.md) - [Règle](ruler.md) - [Spinner](spinner.md) - [Stepper](stepper.md) - [Sous-formulaire](subform_overview.md#overview) - [Onglet](text.md) - [Zone Web](webArea_overview.md#overview)



---
## Dotted Line Type

Describes dotted line type as a sequence of black and white points.

#### Grammaire JSON

| Nom             | Type de données        | Valeurs possibles                                                           |
| --------------- | ---------------------- | --------------------------------------------------------------------------- |
| strokeDashArray | number array or string | Ex : "6 1" ou \[6,1\] pour une séquence de points noirs et un point blanc |

#### Objets pris en charge

[Rectangle](shapes_overview.md#rectangle) - [Ovale](shapes_overview.md#oval) - [Ligne](shapes_overview.md#line)




---
## Masquer lignes vides finales

Controls the display of extra blank rows added at the bottom of a list box object. By default, 4D adds such extra rows to fill the empty area:

![](assets/en/FormObjects/property_hideExtraBlankRows1.png)

You can remove these empty rows by selecting this option. The bottom of the list box object is then left blank:

![](assets/en/FormObjects/property_hideExtraBlankRows2.png)

#### Grammaire JSON

| Nom                | Type de données | Valeurs possibles |
| ------------------ | --------------- | ----------------- |
| hideExtraBlankRows | boolean         | true, false       |

#### Objets pris en charge

[List Box](listbox_overview.md#overview)




---
## Line Color

Designates the color of the object's lines. The color can be specified by:

* a color name - like "red"
* a HEX value - like "#ff0000"
* an RGB value - like "rgb(255,0,0)"

You can also set this property using the [**OBJECT SET RGB COLORS**](https://doc.4d.com/4Dv18/4D/18/OBJECT-SET-RGB-COLORS.301-4505456.en.html) command.

#### Grammaire JSON

| Nom    | Type de données | Valeurs possibles                         |
| ------ | --------------- | ----------------------------------------- |
| stroke | string          | any css value, "transparent", "automatic" |

> This property is also available for text based objects, in which case it designates both the font color and the object's lines, see [Font color](properties_Text.md#font-color).

#### Objets pris en charge

[Ligne](shapes_overview.md#line) - [Ovale](shapes_overview.md#oval) - [Rectangle](shapes_overview.md#rectangle)



---
## Line Width

Designates the thickness of a line.

#### Grammaire JSON

| Nom         | Type de données | Valeurs possibles                                                                       |
| ----------- | --------------- | --------------------------------------------------------------------------------------- |
| strokeWidth | number          | 0 pour la plus petite largeur dans un formulaire imprimé, ou toute valeur d'entier < 20 |

#### Objets pris en charge

[Ligne](shapes_overview.md#line) - [Ovale](shapes_overview.md#oval) - [Rectangle](shapes_overview.md#rectangle)







---
## Tableau couleurs de fond

`List box de type tableau`

The name of an array to apply a custom background color to each row of the list box or column.

The name of a Longint array must be entered. Each element of this array corresponds to a row of the list box (if applied to the list box) or to a cell of the column (if applied to a column), so the array must be the same size as the array associated with the column. You can use the constants of the [SET RGB COLORS](https://doc.4d.com/4Dv17R6/4D/17-R6/SET-RGB-COLORS.302-4310385.en.html) theme. If you want the cell to inherit the background color defined at the higher level, pass the value -255 to the corresponding array element.

For example, given a list box where the rows have an alternating gray/light gray color, defined in the properties of the list box. A background color array has also been set for the list box in order to switch the color of rows where at least one value is negative to light orange:

```4d
 <>_BgndColors{$i}:=0x00FFD0B0 // orange
 <>_BgndColors{$i}:=-255 // default value
```
![](assets/en/FormObjects/listbox_styles1.png)

Next you want to color the cells with negative values in dark orange. To do this, you set a background color array for each column, for example <>_BgndColor_1, <>_BgndColor_2 and <>_BgndColor_3. The values of these arrays have priority over the ones set in the list box properties as well as those of the general background color array:

```4d
 <>_BgndColorsCol_3{2}:=0x00FF8000 // dark orange
 <>_BgndColorsCol_2{5}:=0x00FF8000
 <>_BgndColorsCol_1{9}:=0x00FF8000
 <>_BgndColorsCol_1{16}:=0x00FF8000
```
![](assets/en/FormObjects/listbox_styles2.png)

You can get the same result using the `LISTBOX SET ROW FONT STYLE` and `LISTBOX SET ROW COLOR` commands. They have the advantage of letting you skip having to predefine style/color arrays for the columns: instead they are created dynamically by the commands.


#### Grammaire JSON

| Nom           | Type de données | Valeurs possibles            |
| ------------- | --------------- | ---------------------------- |
| rowFillSource | string          | The name of a longint array. |

#### Objets pris en charge
[List Box](listbox_overview.md) - [List Box Column](listbox_overview.md#list-box-columns)





---
## Transparent

Sets the list box background to "Transparent". When set, any [alternate background color](#alternate-background-color) or [background color](#background-color-fill-color) defined for the column is ignored.

#### Grammaire JSON

| Nom          | Type de données | Valeurs possibles |
| ------------ | --------------- | ----------------- |
| border-style | Texte           | "transparent"     |

#### Objets pris en charge
[List Box](listbox_overview.md#overview)

#### Voir également
[Background Color / Fill Color](#background-color-fill-color)