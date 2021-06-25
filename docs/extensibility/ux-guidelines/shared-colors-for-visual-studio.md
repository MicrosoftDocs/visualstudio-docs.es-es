---
title: Colores compartidos para Visual Studio | Microsoft Docs
description: Obtenga información sobre cómo usar elementos Visual Studio shell y temas comunes para diseñar su propia interfaz de usuario personalizada que sea coherente con el Visual Studio personalizado.
ms.date: 04/26/2017
ms.topic: reference
ms.assetid: 8d11b9a0-6175-4f2e-8e7f-79daee1bfd41
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 262f90fb8d03a9404cdbba8b942e90f6fe6fd3aa
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903975"
---
# <a name="shared-colors-for-visual-studio"></a>Colores compartidos para Visual Studio
Al diseñar una interfaz de usuario que usa elementos de shell de Visual Studio comunes, o quiere que el elemento de interfaz sea coherente con características similares, use los nombres de token existentes en los archivos de definición de paquete para elegir y asignar colores. Esto garantiza que la interfaz de usuario mantenga la coherencia con el entorno general de Visual Studio y que se actualice automáticamente cuando se agreguen o actualicen temas.

En este artículo se describen los elementos de interfaz de usuario comunes y los nombres de token que estos usan y a los que se puede hacer referencia al crear una interfaz de usuario similar. Para obtener información específica sobre cómo tener acceso a estos tokens de color, vea [The VSColor Service](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).

Asegúrese de usar correctamente los nombres de token:

- **Usar nombres de token basados en función, no en el color en sí.** Los colores comunes compartidos están asociados a elementos específicos de la interfaz y solo están destinados para características iguales o similares. Por ejemplo, no vuelva a usar el color de un cuadro combinado presionado para una animación de progreso de giro solo porque le gusta el color. Las funciones del cuadro combinado y la animación son diferentes y, si cambia el color asociado al cuadro combinado, es posible que ya no sea un color adecuado para el elemento de animación. Un uso coherente del color ayuda a orientar a los usuarios y evitar confusiones.

- **Usar colores de fondo y de texto en la combinación correcta.** Los colores de fondo destinados para usarse con texto tendrán un color de texto asociado. No use colores de texto que no sean los que se especifican para el fondo. Si no hay un color de texto asociado, no use ese color de fondo para ninguna superficie en la que espera mostrar texto. Otras combinaciones de texto y colores de fondo podrían dar lugar a una interfaz ilegible.

- **Usar colores de control adecuados para su ubicación.** En ciertos estados, algunos Visual Studio controles no tienen colores de borde y fondo independientes. En su lugar, toman los colores de las superficies que están detrás de ellos. Procure usar siempre los nombres de token que sean adecuados para la ubicación donde coloca el control.

> [!IMPORTANT]
> No use tokens encontrados en las categorías "Página de inicio" o "Cider".

## <a name="common-shared-controls"></a>Controles comunes compartidos

Cuando se usa una barra Visual Studio comandos estándar en la característica, tendrá acceso a los controles de shell con estilo. No debe volver a crear plantillas de estos controles comunes. Sin embargo, si necesita crear una barra de comandos personalizada, también podría ser necesario crear controles personalizados. En ese caso, asegúrese de usar los nombres de token correctos para cada uno de los siguientes controles de modo que la interfaz de usuario sea coherente con el resto de Visual Studio.

### <a name="button-controls"></a>Controles de botón

![Límite de control de botón](../../extensibility/ux-guidelines/media/0303-155_buttoncontrolredline.png "0303-155_ButtonControlRedline")

| Uso... | No use ... |
| --- | --- |
| ... para los botones del documento que desea integrar con temas Visual Studio (claro, oscuro, azul o un tema de contraste alto sistema). | ... para los botones que se mostrarán en un fondo personalizado que no forma parte de un Visual Studio tema. |

**Botón: estado estándar**

![Botón Estándar](../../extensibility/ux-guidelines/media/03.03.Button.Standard.png "03.03.Button.Standard")<br />Botón Estándar

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Botón | `CommonControls.Button` |
| Borde de botón | `CommonControls.ButtonBorder` |

**Botón: estado predeterminado**

![Botón Predeterminado](../../extensibility/ux-guidelines/media/03.03.Button.Default.png "03.03.Button.Default")<br />Botón Predeterminado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Botón | `CommonControls.ButtonDefault` |
| Borde de botón | `CommonControls.ButtonBorderDefault` |

**Botón: estado deshabilitado**

![Botón Deshabilitado](../../extensibility/ux-guidelines/media/03.03.Button.Disabled.png "03.03.Button.Disabled")<br />Botón Deshabilitado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Botón | `CommonControls.ButtonDisabled` |
| Borde de botón | `CommonControls.ButtonBorderDisabled` |

**Botón: estado del mouse**

![Botón al mantener el mouse](../../extensibility/ux-guidelines/media/03.03.Button.hover.png "03.03.Button.hover")<br />Botón al mantener el mouse

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Botón | `CommonControls.ButtonHover` |
| Borde de botón | `CommonControls.ButtonBorderHover` |

**Botón: estado presionado**

![Botón presionado](../../extensibility/ux-guidelines/media/03.03.Button.Pressed.png "03.03.Button.Pressed")<br />Botón presionado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Botón | `CommonControls.ButtonPressed` |
| Borde de botón | `CommonControls.ButtonBorderPressed` |

**Botón: estado centrado**

![Botón enfocado](../../extensibility/ux-guidelines/media/03.03.Button.Focused.png "03.03.Button.Focused")<br />Botón enfocado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Botón | `CommonControls.ButtonFocused` |
| Borde de botón | `CommonControls.ButtonBorderFocused` |

### <a name="check-box-controls"></a>Controles de casilla
![Casilla (línea roja)](../../extensibility/ux-guidelines/media/0303-161_checkboxredline.png "0303-161_CheckboxRedline")<br />Casilla (línea roja)

| Uso... | No use ... |
| --- | --- |
| ... para los controles de casilla incluidos en el documento. | ... para cualquier interfaz de usuario que no sea un control de casilla. |

**Casilla: estado predeterminado**

![casilla](../../extensibility/ux-guidelines/media/0303-162_checkbox.png "0303-162_Checkbox")<br />Casilla predeterminada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `CommonControls.CheckBoxBackground` |
| Borde | `CommonControls.CheckBoxBorder` |
| Texto | `CommonControls.CheckBoxText` |
| Glifo | `CommonControls.CheckBoxGlyph` |

**Casilla: estado deshabilitado**

![Casilla Deshabilitada](../../extensibility/ux-guidelines/media/0303-163_checkboxdisabled.png "0303-163_CheckboxDisabled")<br />Casilla Deshabilitada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `CommonControls.CheckBoxBackgroundDisabled` |
| Borde | `CommonControls.CheckBoxBorderDisabled` |
| Texto | `CommonControls.CheckBoxTextDisabled` |
| Glifo | `CommonControls.CheckBoxGlyphDisabled` |

**Casilla: estado del mouse**

 ![Casilla de verificación al mantener el mouse](../../extensibility/ux-guidelines/media/0303-164_checkboxhover.png "0303-164_CheckboxHover")<br />Casilla de verificación al mantener el mouse

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `CommonControls.CheckBoxBackgroundHover` |
| Borde | `CommonControls.CheckBoxBorderHover` |
| Texto | `CommonControls.CheckBoxTextHover` |
| Glifo | `CommonControls.CheckBoxGlyphHover` |

**Casilla: estado presionado**

![Casilla presionada](../../extensibility/ux-guidelines/media/0303-165_checkboxpressed.png "0303-165_CheckboxPressed")<br />Casilla presionada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `CommonControls.CheckBoxBackgroundPressed` |
| Borde | `CommonControls.CheckBoxBorderPressed` |
| Texto | `CommonControls.CheckBoxTextPressed` |
| Glifo | `CommonControls.CheckBoxGlyphPressed` |

**Casilla: estado centrado**

![Casilla centrada](../../extensibility/ux-guidelines/media/0303-166_checkboxfocused.png "0303-166_CheckboxFocused")<br />Casilla centrada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `CommonControls.CheckBoxBackgroundFocused` |
| Borde | `CommonControls.CheckBoxBorderFocused` |
| Texto | `CommonControls.CheckBoxTextFocused` |
| Glifo | `CommonControls.CheckBoxGlyphFocused` |

### <a name="drop-downs-and-combo-boxes"></a>Menús desplegables y cuadros combinados
![Cuadro desplegable o combinado (línea roja)](../../extensibility/ux-guidelines/media/0303-167_dropdowncomboboxredline.png "0303-167_DropDownComboBoxRedline")<br />Cuadro desplegable o combinado (línea roja)

| Uso... | No use ... |
| --- | --- |
| ... para los menús desplegables y cuadros combinados del documento. | ... para cualquier interfaz de usuario que no sea un cuadro desplegable o combinado. |
| | ... para los menús [desplegables de la barra de comandos](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown) o los cuadros [combinados](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox). |

**Menús desplegables y cuadros combinados: estado predeterminado**

![Cuadro combinado o desplegable predeterminado](../../extensibility/ux-guidelines/media/0303-168_dropdowncombobox.png "0303-168_DropDownComboBox")<br />Cuadro combinado o desplegable predeterminado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `CommonControls.ComboBoxBackground` |
| Borde | `CommonControls.ComboBoxBorder` |
| Texto | `CommonControls.ComboBoxText` |
| Separador | `CommonControls.ComboBoxSeparator` |
| Glifo | `CommonControls.ComboBoxGlyph` |
| Fondo de glifo | `CommonControls.ComboBoxGlyphBackground` |

**Menús desplegables y cuadros combinados: estado deshabilitado**

![Cuadro desplegable o combinado deshabilitado](../../extensibility/ux-guidelines/media/0303-169_dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")<br />Cuadro desplegable o combinado deshabilitado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `CommonControls.ComboBoxBackgroundDisabled` |
| Borde | `CommonControls.ComboBoxBorderDisabled` |
| Texto | `CommonControls.ComboBoxTextDisabled` |
| Separador | `CommonControls.ComboBoxSeparatorDisabled` |
| Glifo | `CommonControls.ComboBoxGlyphDisabled` |
| Fondo de glifo | `CommonControls.ComboBoxGlyphBackgroundDisabled` |

**Menús desplegables y cuadros combinados: estado del mouse**

![Desplegable o cuadro combinado al mantener el mouse](../../extensibility/ux-guidelines/media/0303-170_dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")<br />Desplegable o cuadro combinado al mantener el mouse

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `CommonControls.ComboBoxBackgroundHover` |
| Borde | `CommonControls.ComboBoxBorderHover` |
| Texto | `CommonControls.ComboBoxTextHover` |
| Separador | `CommonControls.ComboBoxSeparatorHover` |
| Glifo | `CommonControls.ComboBoxGlyphHover` |
| Fondo de glifo | `CommonControls.ComboBoxGlyphBackgroundHover` |

**Menús desplegables y cuadros combinados: estado presionado**

![Cuadro combinado o desplegable presionado](../../extensibility/ux-guidelines/media/0303-171_dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")<br />Cuadro combinado o desplegable presionado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `CommonControls.ComboBoxBackgroundPressed` |
| Borde | `CommonControls.ComboBoxBorderPressed` |
| Texto | `CommonControls.ComboBoxTextPressed` |
| Separador | `CommonControls.ComboBoxSeparatorPressed` |
| Glifo | `CommonControls.ComboBoxGlyphPressed` |
| Fondo de glifo | `CommonControls.ComboBoxGlyphBackgroundPressed` |

**Vista de elementos de lista de listas desplegables y cuadros combinados: estado presionado**

 ![Vista de elemento de lista presionada de cuadro desplegable o combinado](../../extensibility/ux-guidelines/media/0303-174_dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")<br />Vista de elemento de lista presionada de cuadro desplegable o combinado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `CommonControls.ComboBoxListBackground`<br />`CommonControls.ComboBoxListBackgroundHover`<br />`CommonControls.ComboBoxListItemBackgroundPressed`<br />`CommonControls.ComboBoxListItemBackgroundFocused` |
| Borde | `CommonControls.ComboBoxListBorder`<br />`CommonControls.ComboBoxListBorderHover`<br />`CommonControls.ComboBoxListBorderPressed`<br />`CommonControls.ComboBoxListBorderFocused` |
| Texto del elemento | `CommonControls.ComboBoxListItemText`<br /> `CommonControls.ComboBoxListItemTextHover`<br />`CommonControls.ComboBoxListItemTextPressed`<br />`CommonControls.ComboBoxListItemTextFocused` |
| Sombra de fondo | `CommonControls.ComboBoxListBackgroundShadow` |

**Menús desplegables y cuadros combinados: estado centrado**

![Cuadro desplegable o combinado con foco](../../extensibility/ux-guidelines/media/0303-172_dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")<br />Cuadro desplegable o combinado con foco

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `CommonControls.ComboBoxBackgroundFocused` |
| Borde | `CommonControls.ComboBoxBorderFocused` |
| Texto | `CommonControls.ComboBoxTextFocused` |
| Separador | `CommonControls.ComboBoxSeparatorFocused` |
| Glifo | `CommonControls.ComboBoxGlyphFocused` |
| Fondo de glifo | `CommonControls.ComboBoxGlyphBackgroundFocused` |

**Menús desplegables y cuadros combinados: selección de entrada de texto**

![Selección de entrada de texto de lista desplegable o cuadro combinado](../../extensibility/ux-guidelines/media/0303-173_dropdowncomboboxtextinput.png "0303-173_DropDownComboBoxTextInput")<br />Selección de entrada de texto de lista desplegable o cuadro combinado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Resaltar | `CommonControls.ComboBoxTextInputSelection` |

### <a name="tabular-data-grid-controls"></a>Controles de datos tabulares (cuadrícula)
Los controles de datos tabulares, también conocidos como controles de cuadrícula, son controles comunes de Visual Studio que se pueden usar para presentar grandes cantidades de datos en varias columnas. Los controles estándar de datos tabulares están en varias ubicaciones de Visual Studio: la ventana de herramientas Lista de errores, los informes de IntelliTrace y la vista de montón de memoria, entre otros. Use siempre los controles de datos tabulares estándar que se proporcionan. En raras ocasiones, podría no tener acceso a los controles estándar de datos tabulares. En estos casos, use los siguientes nombres de token para asegurarse de que la interfaz de usuario sea coherente con otros controles de datos tabulares de Visual Studio.

![Control tabular de datos o cuadrícula (línea roja)](../../extensibility/ux-guidelines/media/0303-197_tabulardatagridcontrolredline.png "0303-197_TabularDataGridControlRedline")<br />Control tabular de datos o cuadrícula (línea roja)

| Uso... | No use ... |
| --- | --- |
| ... para controles tabulares o de cuadrícula. | ... para cualquier interfaz de usuario que no sea un control tabular o de cuadrícula. |

#### <a name="column-headers"></a>Encabezados de columna
Los encabezados de columna constan de un fondo, un borde, el texto del título y un glifo opcional que suele usarse cuando se ordena una cuadrícula por esa columna.

**Encabezado de columna: estado predeterminado**

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Header.Default` |
| Primer plano (texto) | `Environment.CommandBarTextActive` |
| Primer plano (glifo) | `Header.Glyph` |
| Borde | `Header.SeparatorLine` |

**Encabezado de columna: estado del mouse**

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Header.MouseOver` |
| Primer plano (texto) | `Environment.CommandBarTextHover` |
| Primer plano (glifo) | `Header.MouseOverGlyph` |
| Borde | `Header.SeparatorLine` |

**Encabezado de columna: estado presionado**

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `CommonControls.CheckBoxBackgroundPressed` |
| Primer plano (texto) | `CommonControls.CheckBoxBorderPressed` |
| Primer plano (glifo) | `CommonControls.CheckBoxTextPressed` |
| Borde | `CommonControls.CheckBoxGlyphPressed` |

#### <a name="list-view-items"></a>Elementos de vista lista
 Los elementos de vista de lista constan de un fondo y el contenido. El contenido puede ser texto, un icono o ambos.

**Elementos de vista de lista: estado predeterminado**

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | Transparente |
| Primer plano (texto) | `Environment.CommandBarTextActive` |
| Borde | Ninguno |

**Elementos de vista de lista: estado activo**

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `TreeView.SelectedItemActive` |
| Primer plano (texto) | `TreeView.SelectedItemActiveText` |
| Borde | Ninguno |

**Elementos de vista de lista: estado inactivo**

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `TreeView.SelectedItemInactive` |
| Primer plano (texto) | `TreeView.SelectedItemInactiveText` |
| Borde | Ninguno |

### <a name="ui-text"></a>Texto de la interfaz de usuario

#### <a name="instructional-text"></a>Texto informativo
El texto informativo proporciona una explicación principal destacada de lo que se debe hacer en un cuadro de diálogo o una página de documento.

![Texto de instrucciones predeterminado](../../extensibility/ux-guidelines/media/0303_InstructionalText.png "0303_InstructionalText.png")<br />Texto de instrucciones predeterminado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Primer plano (texto) | `Environment.ControlText` |

#### <a name="secondary-instructional-text"></a>Texto informativo secundario
En las páginas de documentos con una gran cantidad de texto y controles, algún texto informativo usa un valor de color diferente. Esto ayuda a transmitir qué información es más importante y a reducir la densidad general de los elementos de la interfaz de usuario. (Consulte también la sección siguiente sobre el texto de la sugerencia).

![Texto informativo secundario](../../extensibility/ux-guidelines/media/0303_SecondaryInstructionalText.png "0303_SecondaryInstructionalText.png")<br />Texto informativo secundario

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Primer plano (texto) | `Environment.ControlEditHintText` |

#### <a name="hint-text"></a>Texto de sugerencia
El texto de la sugerencia aparece en un control vacío, debajo de un control o en una superficie de documento vacía para mostrar al usuario qué hacer a continuación. Puede usar texto de sugerencia con fondos de Ventana o Control.

**Texto de sugerencia predeterminado**

![Texto de sugerencia predeterminado](../../extensibility/ux-guidelines/media/0303_HintText.png "0303_HintText.png")<br />Texto de sugerencia predeterminado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Primer plano (texto) | `Environment.ControlEditHintText` |

**Texto de sugerencia requerido**

![Texto de sugerencia requerido](../../extensibility/ux-guidelines/media/0303_RequiredHintText.png "0303_RequiredHintText.png")<br />Texto de sugerencia requerido

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Primer plano (texto) | `Environment.ControlRequiredHintText` |
| Información previa | `Environment.ControlRequiredBackground` |

**Texto del control de cuadro de búsqueda**

> Consulte [Cuadros de búsqueda](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_SearchBoxes) para ver otros tokens de color relacionados con el control De búsqueda.

![Texto del control cuadro de búsqueda](../../extensibility/ux-guidelines/media/0303_SearchBoxControl.png "0303_SearchBoxControl.png")<br />Texto del control cuadro de búsqueda

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Primer plano (texto) | `SearchControl.UnfocusedWatermarkText` |

### <a name="hyperlink"></a>Hyperlink
El hipervínculo es un control que no tiene un par de primer plano y fondo. En todos los casos, use el color de hipervínculo de primer plano, que aparecerá correctamente en fondos oscuros, grises y blanco. Si no usa el token de color para el control de hipervínculo, verá el color predeterminado del sistema para "pressed", que parpadeará en rojo. Esa es la señal de que el control no usa el token de color de entorno correcto.

![Hipervínculo (línea roja)](../../extensibility/ux-guidelines/media/0303-133_hyperlinkredline.png "0303-133_HyperlinkRedline")<br />Hipervínculo (línea roja)

| Uso... | No use ... |
| --- | --- |
| ... cuando necesite crear un hipervínculo personalizado. | ... para cualquier cosa que no sea un hipervínculo. |

**Hipervínculo: estado predeterminado**

![Hipervínculo predeterminado](../../extensibility/ux-guidelines/media/0303-134_hyperlink.png "0303-134_Hyperlink")<br />Hipervínculo predeterminado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Primer plano (texto) | `Environment.PanelHyperlink` |

**Hipervínculo: estado del mouse**

![Hipervínculo al mantener el mouse](../../extensibility/ux-guidelines/media/0303-135_hyperlinkhover.png "0303-135_HyperlinkHover")<br />Hipervínculo al mantener el mouse

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Primer plano (texto) | `Environment.PanelHyperlinkHover` |

**Hipervínculo: estado presionado**

![Hipervínculo presionado](../../extensibility/ux-guidelines/media/0303-136_hyperlinkpressed.png "0303-136_HyperlinkPressed")<br />Hipervínculo presionado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Primer plano (texto) | `Environment.PanelHyperlinkPressed` |

**Hipervínculo: estado deshabilitado**

![Hipervínculo deshabilitado](../../extensibility/ux-guidelines/media/0303-137_hyperlinkdisabled.png "0303-137_HyperlinkDisabled")<br />Hipervínculo deshabilitado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Primer plano (texto) | `Environment.PanelHyperlinkDisabled` |

### <a name="infobars"></a>Barras de información
Las barras de información se usan para proporcionar más información sobre un determinado contexto y siempre se muestran en la parte superior de una ventana de documento o una ventana de herramientas.

![Barra de información (línea roja)](../../extensibility/ux-guidelines/media/0303-138_infobarredline.png "0303-138_InfobarRedline")<br />Barra de información (línea roja)

| Uso... | No use ... |
| --- | --- |
| ... al crear barras de información personalizadas. | ... para elementos de interfaz de usuario que no son similares a una barra de información. |

**Barra de información: estado predeterminado**

![Barra de información predeterminada](../../extensibility/ux-guidelines/media/0303-139_infobar.png "0303-139_Infobar")<br />Barra de información predeterminada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `InfoBar.InfoBarBackground` |
| Primer plano (texto) | `InfoBar.InfoBar` |
| Borde | `InfoBar.InfoBarBorder` |

**Botón Cerrar de la barra de información ( &times; ): estado predeterminado**

![Botón Cerrar de la barra de información predeterminada ( &times; )](../../extensibility/ux-guidelines/media/0303_InfobarCloseDefault.png "0303_InfobarCloseDefault.png")<br />Botón Cerrar de la barra de información predeterminada ( &times; )

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `InfoBar.CloseButton` |
| Borde | `InfoBar.CloseButtonBorder` |
| Glifo | `InfoBar.CloseButtonGlyph` |

**Botón Cerrar de la barra de información ( &times; ): estado del mouse**

![Botón Cerrar de la barra de información ( &times; ) al mantener el puntero](../../extensibility/ux-guidelines/media/0303_InfobarCloseHover.png "0303_InfobarCloseHover.png")<br />Botón Cerrar de la barra de información ( &times; ) al mantener el puntero

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `InfoBar.CloseButtonHover` |
| Borde | `InfoBar.CloseButtonHoverBorder` |
| Glifo | `InfoBar.CloseButtonHoverGlyph` |

**Botón Cerrar de la barra de información ( &times; ): estado presionado**

![Botón Cerrar de la barra de información presionada ( &times; )](../../extensibility/ux-guidelines/media/0303_InfobarClosePressed.png "0303_InfobarClosePressed.png")<br />Botón Cerrar de la barra de información presionada ( &times; )

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `InfoBar.CloseButtonDown` |
| Borde | `InfoBar.CloseButtonDownBorder` |
| Glifo | `InfoBar.CloseButtonDownGlyph` |

**Botón hipervínculo de la barra de información: estado predeterminado**

![Botón hipervínculo de la barra de información predeterminada](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonDefault.png "0303_InfobarHyperlinkButtonDefault.png")<br />Botón hipervínculo de la barra de información predeterminada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Primer plano (texto) | `InfoBar.Hyperlink` |

**Botón de hipervínculo de la barra de información: estado del mouse**

![Botón de hipervínculo de la barra de información al mantener el puntero](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonHover.png "0303_InfobarHyperlinkButtonHover.png")<br />Botón de hipervínculo de la barra de información al mantener el puntero

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Primer plano (texto) | `Infobar.HyperlinkMouseOver`<br />(Con subrayado) |

**Botón hipervínculo de la barra de información: estado presionado**

![Botón de hipervínculo de la barra de información presionado](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonPressed.png "0303_InfobarHyperlinkButtonPressed.png")<br />Botón de hipervínculo de la barra de información presionado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Primer plano (texto) | `Infobar.HyperlinkMouseDown`<br />(Con subrayado) |

**Hipervínculo en línea de la barra de información (dentro de una frase): estado predeterminado**

![Botón de hipervínculo de la barra de información insertable predeterminada](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonDefault.png "0303_InfobarHyperlinkButtonDefault.png")<br />Botón de hipervínculo de la barra de información insertable predeterminada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Primer plano (texto) | `InfoBar.Hyperlink` |

**Hipervínculo en línea de la barra de información (dentro de una oración): estado del mouse**

![Botón de hipervínculo en línea de la barra de información al mantener el puntero](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkInlineHover.png "0303_InfobarHyperlinkInlineHover.png")<br />Botón de hipervínculo en línea de la barra de información al mantener el puntero

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Primer plano (texto) | `Infobar.HyperlinkMouseOver`<br />(Con subrayado) |

**Hipervínculo en línea de la barra de información (dentro de una frase): estado presionado**

![Botón de hipervínculo en línea de la barra de información presionada](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkInlinePressed.png "0303_InfobarHyperlinkInlinePressed.png")<br />Botón de hipervínculo en línea de la barra de información presionada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Primer plano (texto) | `Infobar.HyperlinkMouseDown`<br />(Con subrayado) |

**Botón barra de información: estado predeterminado**

![Botón de la barra de información predeterminada](../../extensibility/ux-guidelines/media/0303_InfobarButtonDefault.png "0303_InfobarButtonDefault.png")<br />Botón de la barra de información predeterminada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `InfoBar.Button` |
| Primer plano (texto) | `InfoBar.Button` |
| Borde | `InfoBar.ButtonBorder` |

**Botón de la barra de información: estado del mouse**

![Botón de la barra de información al mantener el puntero](../../extensibility/ux-guidelines/media/0303_InfobarButtonHover.png "0303_InfobarButtonHover.png")<br />Botón de la barra de información al mantener el puntero

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `InfoBar.ButtonMouseOver` |
| Primer plano (texto) | `InfoBar.ButtonMouseOver` |
| Borde | `InfoBar.ButtonMouseOverBorder` |

**Botón barra de información: estado presionado**

![Botón de barra de información presionado](../../extensibility/ux-guidelines/media/0303_InfobarButtonPressed.png "0303_InfobarButtonPressed.png")<br />Botón de barra de información presionado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `InfoBar.ButtonMouseDown` |
| Primer plano (texto) | `InfoBar.ButtonMouseDown` |
| Borde | `InfoBar.ButtonMouseDownBorder` |

**Botón de la barra de información: estado deshabilitado**

![Botón barra de información deshabilitada](../../extensibility/ux-guidelines/media/0303_InfobarButtonDisabled.png "0303_InfobarButtonDisabled.png")<br />Botón barra de información deshabilitada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `InfoBar.ButtonDisabled` |
| Primer plano (texto) | `InfoBar.ButtonDisabled` |
| Borde | `InfoBar.ButtonDisabledBorder` |

**Botón barra de información: estado centrado**

![Botón de la barra de información centrada](../../extensibility/ux-guidelines/media/0303_InfobarButtonFocus.png "0303_InfobarButtonFocus.png")<br />Botón de la barra de información centrada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `InfoBar.ButtonFocus` |
| Primer plano (texto) | `InfoBar.ButtonFocus` |
| Borde | `InfoBar.ButtonFocusBorder` |

### <a name="scroll-bars"></a>Barras de desplazamiento
El entorno de Visual Studio estilo de las barras de desplazamiento y no tendrá que tener un formato. Sin embargo, puede decidir que quiere aprovechar los colores usados en las barras de desplazamiento para que la interfaz de usuario siempre parezca coherente con esta parte del Visual Studio usuario.

![Barra de desplazamiento (línea roja)](../../extensibility/ux-guidelines/media/0303-140_scrollbarredline.png "0303-140_ScrollbarRedline")<br />Barra de desplazamiento (línea roja)

| Uso... | No use ... |
| --- | --- |
| ... al crear la interfaz de usuario que desea que coincida con Visual Studio de desplazamiento. | ... para cualquier cosa que no quiera que coincida siempre con la interfaz de usuario de la barra de desplazamiento. |

**Barra de desplazamiento: estado predeterminado**

![Barra de desplazamiento predeterminada](../../extensibility/ux-guidelines/media/0303-141_scrollbar.png "0303-141_Scrollbar")<br />Barra de desplazamiento predeterminada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Barra de desplazamiento | `Environment.ScrollBarBackground` |
| Primer plano (control) | `Environment.ScrollBarThumbBackground` |

**Barra de desplazamiento: estado del mouse**

![Barra de desplazamiento al mantener el mouse](../../extensibility/ux-guidelines/media/0303-143_scrollbarhover.png "0303-143_ScrollbarHover")<br />Barra de desplazamiento al mantener el mouse

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Barra de desplazamiento | `Environment.ScrollBarBackground` |
| Primer plano (control) | `Environment.ScrollBarThumbMouseOverBackground` |

*Barra de desplazamiento: estado presionado**

![Barra de desplazamiento presionada](../../extensibility/ux-guidelines/media/0303-145_scrollbarpressed.png "0303-145_ScrollbarPressed")<br />Barra de desplazamiento presionada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Barra de desplazamiento | `Environment.ScrollBarBackground` |
| Primer plano (control) | `Environment.ScrollBarThumbPressedBackground` |

**Flecha de la barra de desplazamiento: estado predeterminado**

![Flecha de barra de desplazamiento predeterminada](../../extensibility/ux-guidelines/media/0303-142_scrollbararrow.png "0303-142_ScrollbarArrow")<br />Flecha de barra de desplazamiento predeterminada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.ScrollBarArrowBackground`<br />(Se establece en el mismo color que la barra de desplazamiento). |
| Primer plano (glifo) | `Environment.ScrollBarArrowGlyph` |

**Flecha de la barra de desplazamiento: estado del mouse**

![Flecha de barra de desplazamiento al mantener el mouse](../../extensibility/ux-guidelines/media/0303-144_scrollbararrowhover.png "0303-144_ScrollbarArrowHover")<br />Flecha de barra de desplazamiento al mantener el mouse

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.ScrollBarArrowMouseOverBackground`<br />(Se establece en el mismo color que la barra de desplazamiento). |
| Primer plano (glifo) | `Environment.ScrollBarArrowGlyphMouseOver` |

**Flecha de la barra de desplazamiento: estado presionado**

![Flecha de la barra de desplazamiento presionada](../../extensibility/ux-guidelines/media/0303-146_scrollbararrowpressed.png "0303-146_ScrollbarArrowPressed")<br />Flecha de la barra de desplazamiento presionada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.ScrollBarArrowPressedBackground`<br />(Se establece en el mismo color que la barra de desplazamiento). |
| Primer plano (glifo) | `Environment.ScrollBarArrowGlyphPressed` |

### <a name="search-boxes"></a><a name="BKMK_SearchBoxes"></a>Cuadros de búsqueda
Siempre que sea posible, use el control de búsqueda común proporcionado por el entorno de Visual Studio. Los colores del cuadro de búsqueda se encuentran en la categoría "SearchControl" del archivo **ShellColors.pkgdef** , que contiene los nombres de token para el campo de entrada, el botón de acción, el botón desplegable y el menú desplegable.

Un cuadro de búsqueda puede tener uno de varios estados, algunos de los cuales son mutuamente excluyentes:

- "Con foco" o "sin foco" se refiere a si el cursor está en el cuadro de texto.

- "Activo" o "inactivo" se refiere a si el usuario ha especificado una consulta de búsqueda en el cuadro de texto.

- "Desplazar el puntero" significa que el usuario ha colocado el puntero sobre el cuadro de búsqueda con el mouse (este estado invalida todos los demás estados).

- "Deshabilitado" significa que la función de búsqueda se ha desactivado para el contexto actual.

![Cuadro de búsqueda (línea roja)](../../extensibility/ux-guidelines/media/0303-110_searchboxredline.png "0303-110_SearchBoxRedline")<br />Cuadro de búsqueda (línea roja)

| Uso... | No use ... |
| --- | --- |
| ... al diseñar un cuadro de búsqueda personalizado. | ... para cualquier cosa que no sea un cuadro de búsqueda. |
| | ... para todo lo que no quiera que coincida siempre con la interfaz de usuario del cuadro de búsqueda. |

**Campo de entrada de búsqueda centrado**

![Campo de entrada de búsqueda centrado](../../extensibility/ux-guidelines/media/0303-111_searchinputfieldfocused.png "0303-111_SearchInputFieldFocused")<br />Campo de entrada de búsqueda centrado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `SearchControl.FocusedBackground` |
| Primer plano (texto) | `SearchControl.FocusedBackground` |
| Borde | `SearchControl.FocusedBorder` |
| Separador | `SearchControl.FocusedDropDownSeparator` |

**Campo de entrada de búsqueda activo y sin foco**

![Campo de entrada de búsqueda no enfocado](../../extensibility/ux-guidelines/media/0303-114_searchinputfieldunfocused.png "0303-114_SearchInputFieldUnfocused")<br />Campo de entrada de búsqueda activo y sin foco

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `SearchControl.SearchActiveBackground` |
| Primer plano (texto) | `SearchControl.SearchActiveBackground` |
| Borde | `SearchControl.UnfocusedBorder` |
| Separador | `SearchControl.DropDownSeparator` |

**Campo de entrada de búsqueda inactivo y sin foco**

![Campo de entrada de búsqueda inactivo y sin foco](../../extensibility/ux-guidelines/media/0303-114-1_searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br />Campo de entrada de búsqueda inactivo y sin foco

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `SearchControl.Unfocused` |
| Primer plano (texto) | `SearchControl.Unfocused` |
| Borde | `SearchControl.UnfocusedBorder` |
| Separador | `SearchControl.DropDownSeparator` |

**Campo de entrada de búsqueda resaltado (solo texto)**

![Campo de entrada de búsqueda resaltado](../../extensibility/ux-guidelines/media/0303-120_searchinputfieldhighlight.png "0303-120_SearchInputFieldHighlight")<br />Campo de entrada de búsqueda resaltado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `SearchControl.Selection` |
| Primer plano (texto) | `SearchControl.FocusedBackground` |
| Borde | Ninguno |
| Separador | `SearchControl.FocusedDropDownSeparator` |

**Campo de entrada de búsqueda deshabilitado**

![Campo de entrada de búsqueda deshabilitado](../../extensibility/ux-guidelines/media/0303-121_searchinputfielddisabled.png "0303-121_SearchInputFieldDisabled")<br />Campo de entrada de búsqueda deshabilitado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `SearchControl.Disabled` |
| Primer plano (texto) | `SearchControl.Disabled` |
| Borde | `SearchControl.DisabledBorder` |
| Separador | `SearchControl.DropDownSeparator` |

**Botón de acción de búsqueda centrada**

![Botón de acción de búsqueda enfocado](../../extensibility/ux-guidelines/media/0303-112_searchactionbuttonfocused.png "0303-112_SearchActionButtonFocused")<br />Botón de acción de búsqueda centrada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | Ninguno |
| Primer plano (glifo de búsqueda) | `SearchControl.SearchGlyph` |
| Primer plano (glifo de detención) | `SearchControl.StopGlyph` |
| Primer plano (glifo de borrado) | `SearchControl.ClearGlyph` |
| Borde | N/D |

**Botón de acción de búsqueda sin foco**

![Botón de acción de búsqueda sin foco](../../extensibility/ux-guidelines/media/0303-115_searchactionbuttonunfocused.png "0303-115_SearchActionButtonUnfocused")<br />Botón de acción de búsqueda sin foco

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | N/D |
| Primer plano (glifo de búsqueda) | `SearchControl.SearchGlyph` |
| Primer plano (glifo de detención) | `SearchControl.StopGlyph` |
| Primer plano (glifo de borrado) | `SearchControl.ClearGlyph` |
| Borde | N/D |

**Botón de acción de búsqueda presionado**

![Botón de acción de búsqueda presionado](../../extensibility/ux-guidelines/media/0303-116-1_searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")<br />Botón de acción de búsqueda presionado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `SearchControl.ActionButtonMouseDown` |
| Primer plano (glifo) | `SearchControl.ActionButtonMouseDownGlyph` |
| Borde | `SearchControl.ActionButtonMouseDownBorder` |

**Botón de acción de búsqueda deshabilitada**

![Botón de acción de búsqueda deshabilitado](../../extensibility/ux-guidelines/media/0303-122_searchactionbuttondisabled.png "0303-122_SearchActionButtonDisabled")<br />Botón de acción de búsqueda deshabilitada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | Ninguno |
| Primer plano (glifo) | `SearchControl.ActionButtonDisabledGlyph` |
| Borde | Ninguno |

**Botón desplegable de búsqueda centrada**

![Botón desplegable de búsqueda centrada](../../extensibility/ux-guidelines/media/0303-113_searchdropdownbuttonfocused.png "0303-113_SearchDropdownButtonFocused")<br />Botón desplegable de búsqueda centrada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `SearchControl.FocusedDropDownButton` |
| Primer plano (glifo) | `SearchControl.FocusedDropDownButtonGlyph` |
| Borde | `SearchControl.FocusedDropDownButtonBorder` |

**Botón desplegable Desenfoque de búsqueda**

![Botón desplegable Desenfoque de búsqueda](../../extensibility/ux-guidelines/media/0303-116_searchdropdownbuttonunfocused.png "0303-116_SearchDropdownButtonUnfocused")<br />Botón desplegable Desenfoque de búsqueda

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `SearchControl.UnfocusedDropDownButton` |
| Primer plano (glifo) | `SearchControl.UnfocusedDropDownButtonGlyph` |
| Borde | `SearchControl.UnfocusedDropDownButtonBorder` |

**Botón desplegable De búsqueda presionada**

![Botón desplegable De búsqueda presionada](../../extensibility/ux-guidelines/media/0303-116-2_searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")<br />Botón desplegable De búsqueda presionada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `SearchControl.MouseDownDropDownButton` |
| Primer plano (glifo) | `SearchControl.MouseDownDropDownButtonGlyph` |
| Borde | `SearchControl.MouseDownDropDownButtonBorder` |

**Botón desplegable De búsqueda deshabilitada**

![Botón desplegable De búsqueda deshabilitada](../../extensibility/ux-guidelines/media/0303-123_searchdropdownbuttondisabled.png "0303-123_SearchDropdownButtonDisabled")<br />Botón desplegable De búsqueda deshabilitada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | Ninguno |
| Primer plano (glifo) | `SearchControl.DisabledDownButtonGlyph` |
| Borde | Ninguno |

#### <a name="search-drop-down-lists"></a>Listas desplegables de búsqueda
El menú desplegable del cuadro de búsqueda puede ser ligeramente más complejo que otros menús desplegables de Visual Studio. Las secciones "búsquedas sugeridas" y "opciones de búsqueda" pueden aparecer solas o juntas en el menú, y cada una se colore por separado. Además, estas secciones están separadas por una línea cuando aparecen juntas y un borde rodea todo el menú desplegable.

![Lista desplegable de búsqueda (línea roja)](../../extensibility/ux-guidelines/media/0303-124_searchdropdownredline.png "0303-124_SearchDropdownRedline")<br />Lista desplegable de búsqueda (línea roja)

| Uso... | No use ... |
| --- | --- |
| ... al crear una lista desplegable de búsqueda personalizada. | ... para listas desplegables que aparecen en otros contextos. |
| ... los nombres de token correctos para los componentes de lista correctos. | ... en cualquier combinación de fondo y primer plano que no sea la especificada. |

**Buscar elementos de lista desplegable**

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Borde | `SearchControl.PopupBorder` |
| Separador | `SearchControl.PopupSectionHeaderSeparator` |
| Shadow | `Environment.DropShadowBackground` |

**Búsquedas sugeridas: estado predeterminado**

![Búsquedas sugeridas predeterminadas](../../extensibility/ux-guidelines/media/0303-125_searchsuggested.png "0303-125_SearchSuggested")<br />Búsquedas sugeridas predeterminadas

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `SearchControl.PopupItemsListBackgroundGradientBegin`<br />(Los delimitadores de degradado para este token no se usan en la interfaz de usuario con formato). |
| Primer plano (texto) | `SearchControl.PopupItemText` |

**Búsquedas sugeridas: estado del mouse**

![Búsquedas sugeridas al mantener el puntero](../../extensibility/ux-guidelines/media/0303-128_searchsuggestedhover.png "0303-128_SearchSuggestedHover")<br />Búsquedas sugeridas al mantener el puntero

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br />(Los delimitadores de degradado para este token no se usan en la interfaz de usuario con formato). |
| Primer plano (texto) | `SearchControl.PopupMouseOverItemText` |
| Borde | `SearchControl.PopupControlMouseOverBorder` |

**Opciones de búsqueda: estado predeterminado**

![Casilla de verificación de búsqueda](../../extensibility/ux-guidelines/media/0303-126_searchcheckbox.png "0303-126_SearchCheckbox")<br />Opciones de búsqueda predeterminadas (casilla)

![Opciones de búsqueda](../../extensibility/ux-guidelines/media/0303-127_searchoptions.png "0303-127_SearchOptions")<br />Opciones de búsqueda predeterminadas (vínculo)

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `SearchControl.PopupSectionBackgroundGradientBegin`<br />(Los delimitadores de degradado para este token no se usan en la interfaz de usuario con formato). |
| Primer plano (texto de casilla) | `SearchControl.PopupCheckboxText` |
| Primer plano (texto de vínculo) | `SearchControl.PopupButtonText` |
| Fondo de encabezado | `SearchControl.PopupSectionHeaderGradientBegin`<br />(Los delimitadores de degradado para este token no se usan en la interfaz de usuario con formato). |
| Primer plano (texto de encabezado) | `SearchControl.PopupSectionHeaderText` |

**Opciones de búsqueda: estado del mouse**

![Opciones de búsqueda (casilla) al mantener el puntero](../../extensibility/ux-guidelines/media/0303-129_searchcheckboxhover.png "0303-129_SearchCheckboxHover")<br />Opciones de búsqueda (casilla) al mantener el puntero

![Opciones de búsqueda (vínculo) al mantener el puntero](../../extensibility/ux-guidelines/media/0303-130_searchoptionshover.png "0303-130_SearchOptionsHover")<br />Opciones de búsqueda (vínculo) al mantener el puntero

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br />(Los delimitadores de degradado para este token no se usan en la interfaz de usuario con el mismo formato). |
| Primer plano (texto de casilla) | `SearchControl.PopupCheckboxMouseDownText` |
| Primer plano (texto de vínculo) | `SearchControl.PopupButtonMouseDownText` |
| Borde | `SearchControl.PopupControlMouseOverBorder` |

**Opciones de búsqueda: estado presionado**

![Opciones de búsqueda presionadas (casilla)](../../extensibility/ux-guidelines/media/0303-131_searchsuggestedpressed.png "0303-131_SearchSuggestedPressed")<br />Opciones de búsqueda presionadas (casilla)

![Opciones de búsqueda presionadas (vínculo)](../../extensibility/ux-guidelines/media/0303-132_searchoptionspressed.png "0303-132_SearchOptionsPressed")<br />Opciones de búsqueda presionadas (vínculo)

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo de casilla | `SearchControl.PopupControlMouseDownBackgroundGradientBegin`<br />`SearchControl.PopupControlMouseDownBackgroundGradientEnd`<br />(Los delimitadores de degradado para este token no se usan en la interfaz de usuario con el mismo formato). |
| Primer plano (texto de casilla) | `SearchControl.PopupCheckboxMouseDownText` |
| Fondo de vínculo | `SearchControl.PopupButtonMouseDownBackgroundGradientBegin`<br />(Los delimitadores de degradado para este token no se usan en la interfaz de usuario con el mismo formato). |
| Primer plano (texto de vínculo) | `SearchControl.PopupButtonMouseDownText` |

### <a name="tree-views"></a><a name="BKMK_TreeView"></a> Vistas de árbol
Varias ventanas de herramientas, incluidas Explorador de soluciones, Explorador de servidores y Vista de clases, implementan un esquema organizativo jerárquico cuyos colores se controlan mediante nombres de color en la `TreeView` categoría. Todos los elementos de una vista de árbol tienen colores de fondo y de texto. Los elementos que tienen elementos secundarios anidados también tienen glifos que indican si el elemento está expandido o contraído.

![Vista de árbol (línea roja)](../../extensibility/ux-guidelines/media/0303-147_treeviewredline.png "0303-147_TreeViewRedline")<br />Vista de árbol (línea roja)

| Uso... | No use ... |
| --- | --- |
| ... en cualquier lugar en el que necesite implementar una vista jerárquica de la organización. | ... para cualquier cosa que no sea similar a una vista de árbol. |
| | ... en cualquier combinación de fondo/primer plano que no sea la especificada. |

**Elemento de vista de árbol: estado predeterminado**

![Elemento de vista de árbol predeterminado](../../extensibility/ux-guidelines/media/0303-148_treeview.png "0303-148_TreeView")<br />Elemento de vista de árbol predeterminado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `TreeView.Background` |
| Primer plano (texto) | `TreeView.Background` |
| Primer plano (glifo) | `TreeView.Glyph` |
| Borde | Ninguno |

**Elemento de vista de árbol: estado del mouse**

![Elemento de vista de árbol al mantener el puntero](../../extensibility/ux-guidelines/media/0303-149_treeviewhover.png "0303-149_TreeViewHover")<br />Elemento de vista de árbol al mantener el puntero

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `TreeView.Background` |
| Primer plano (texto) | `TreeView.Background` |
| Primer plano (glifo) | `TreeView.GlyphMouseOver` |
| Borde | Ninguno |

**Elemento de vista de árbol: arrastrar sobre el estado**

![Elemento de vista de árbol al arrastrar](../../extensibility/ux-guidelines/media/0303-150_treeviewdragover.png "0303-150_TreeViewDragOver")<br />Elemento de vista de árbol al arrastrar

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `TreeView.DragOverItem` |
| Primer plano (texto) | `TreeView.DragOverItem` |
| Primer plano (glifo) | `TreeView.DragOverItemGlyph` |
| Borde | Ninguno |

**Elemento de vista de árbol: estado seleccionado y centrado**

![Elemento de vista de árbol seleccionado y centrado](../../extensibility/ux-guidelines/media/0303-151_treeviewfocused.png "0303-151_TreeViewFocused")<br />Elemento de vista de árbol seleccionado y centrado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `TreeView.SelectedItemActive` |
| Primer plano (texto) | `TreeView.SelectedItemActive` |
| Primer plano (glifo) | `TreeView.SelectedItemActiveGlyph` |
| Borde | `TreeView.FocusVisualBorder` |

**Elemento de vista de árbol: estado seleccionado y sin foco**

![Elemento de vista de árbol seleccionado y sin foco](../../extensibility/ux-guidelines/media/0303-152_treeviewunfocused.png "0303-152_TreeViewUnfocused")<br />Elemento de vista de árbol seleccionado y sin foco

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `TreeView.SelectedItemInactive` |
| Primer plano (texto) | `TreeView.SelectedItemInactive` |
| Primer plano (glifo) | `TreeView.SelectedItemInactiveGlyph` |
| Borde | Ninguno |

**Elemento de vista de árbol: estado con el mouse, seleccionado y centrado**

![Elemento de vista de árbol seleccionado y centrado al mantener el puntero](../../extensibility/ux-guidelines/media/0303-153_treeviewfocusedhover.png "0303-153_TreeViewFocusedHover")<br />Elemento de vista de árbol seleccionado y centrado al mantener el puntero

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `TreeView.SelectedItemActive` |
| Primer plano (texto) | `TreeView.SelectedItemActive` |
| Primer plano (glifo) | `TreeView.SelectedItemActiveGlyphMouseOver` |
| Borde | `TreeView.FocusVisualBorder` |

**Elemento de vista de árbol: estado desenfoque, seleccionado y desenfoque**

![Elemento de vista de árbol seleccionado y sin foco al mantener el puntero](../../extensibility/ux-guidelines/media/0303-154_treeviewunfocusedhover.png "0303-154_TreeViewUnfocusedHover")<br />Elemento de vista de árbol seleccionado y sin foco al mantener el puntero

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `TreeView.SelectedItemInactive` |
| Primer plano (texto) | `TreeView.SelectedItemInactive` |
| Primer plano (glifo) | `TreeView.SelectedItemActiveGlyphMouseOver` |
| Borde | Ninguno |

## <a name="shell-appearance"></a>Apariencia de Shell

### <a name="background"></a>Información previa
El fondo del entorno consta de dos niveles. El nivel inferior es un color sólido que cubre todo el IDE. El nivel superior se encuentra debajo del área de comandos y entre los canales de ocultación automática de la ventana de herramientas en los extremos izquierdo y derecho del IDE. Las capas de fondo superior e inferior se establecen en el mismo color en los temas Claro y Oscuro.

![Visual Studio fondo del shell (línea roja)](../../extensibility/ux-guidelines/media/0303-187_shellbackgroundredline.png "0303-187_ShellBackgroundRedline")<br />Visual Studio fondo del shell (línea roja)

| Uso... | No use ... |
| --- | --- |
| ... para los lugares en los que desea buscar coincidencias con el fondo del Visual Studio de trabajo. | ... como relleno para los lugares que no son superficies de fondo. |
| | ... como fondo en el que colocar elementos en primer plano. |

**Apariencia del shell de capa inferior**

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.EnvironmentBackground` |

**Aspecto del shell de capa superior**

> Los delimitadores de degradado se establecen en el mismo valor de color en los temas claro y oscuro de Visual Studio 2013.

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.EnvironmentBackgroundGradientBegin`<br />`Environment.EnvironmentBackgroundGradientEnd`<br />`Environment.EnvironmentBackgroundGradientMiddle1`<br />`Environment.EnvironmentBackgroundGradientMiddle2` |

### <a name="command-shelf"></a>Área de comandos
Para los fondos del área de comandos se usan dos conjuntos de nombres de token: un conjunto para la ubicación donde se coloca la barra de menús y uno para la ubicación donde se colocan las barras de comandos. Un grupo individual de la barra de comandos tiene sus propios valores de color de fondo, que se describen con más detalle en la sección "Barra de comandos". El texto de la barra de menús y la barra de comandos se describe en las secciones de barra de menús y barra de comandos, respectivamente.

![Visual Studio de comandos (línea roja)](../../extensibility/ux-guidelines/media/0303-188_commandshelfredline.png "0303-188_CommandShelfRedline")<br />Visual Studio de comandos (línea roja)

| Uso... | No use ... |
| --- | --- |
| ... para áreas donde se coloquen menús o barras de herramientas. | ... para áreas que no son similares a una plataforma de comandos. |
|... con la combinación correcta de nombre de token en segundo plano y primer plano. | |

**Barra de menús de la plataforma de comandos**

> Los delimitadores de degradado se establecen en el mismo valor de color en los temas claro y oscuro de Visual Studio 2013.

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.CommandShelfHighlightGradientBegin`<br /><br />`Environment.CommandShelfHighlightGradientMiddle`<br />`Environment.CommandShelfHighlightGradientEnd` |

**Barra de comandos de la plataforma de comandos**

> Los delimitadores de degradado se establecen en el mismo valor de color en los temas claro y oscuro de Visual Studio 2013.

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.CommandShelfBackgroundGradientBegin`<br />`Environment.CommandShelfBackgroundGradientMiddle`<br />`Environment.CommandShelfBackgroundGradientEnd` |

## <a name="manifest-designer"></a>Diseñador de manifiestos
El Diseñador de manifiestos se creó para que resulte más fácil editar el archivo de manifiesto en los proyectos de Windows 8 y Windows Phone 8. Aunque no hay ningún marco compartido disponible para su consumo, es conveniente que haga coincidir el diseño y los colores de las pestañas de navegación u orientación con la estructura general. Para obtener más información sobre el diseño, vea [Layout for Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).

![Diseñador de manifiestos (línea roja)](../../extensibility/ux-guidelines/media/0303-175_manifestdesignerredline.png "0303-175_ManifestDesignerRedline")<br />Diseñador de manifiestos (línea roja)

| Uso... | No use ... |
| --- | --- |
| ... para diseñadores que son similares al Diseñador de manifiestos. | ... si tiene más de seis pestañas. |
| ... en lugar de usar controles de tabulación comunes en la parte superior de un editor dentro del documento. | ... para cualquier interfaz de usuario que no esté estructurada como el Diseñador de manifiestos. |

**Pestaña Diseñador de manifiestos seleccionada: estado predeterminado**

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `ManifestDesigner.TabActive` |
| Borde | Ninguno |

**Panel de descripción seleccionado del Diseñador de manifiestos: estado predeterminado**

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `ManifestDesigner.DescriptionPane` |

**Página de contenido seleccionada del Diseñador de manifiestos: estado predeterminado**

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `ManifestDesigner.Background` |
| Texto del asistente del cuadro de diálogo | `ManifestDesigner.WatermarkText`<br />(Este nombre de token no coincide con su función). |

**Pestaña Diseñador de manifiestos: estado no seleccionado**

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `ManifestDesigner.Tab.Inactive` |

**Pestaña Diseñador de manifiestos: estado del mouse**

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `ManifestDesigner.Tab.Mouseover` |

## <a name="command-structures"></a>Estructuras de comandos

### <a name="menus"></a><a name="BKMK_CommandMenus"></a> Menús
Los menús pueden producirse en varios lugares dentro de Visual Studio: la barra de menús principal, incrustada en ventanas de documentos o herramientas, o al hacer clic con el botón derecho en varias ubicaciones del IDE. Las implementaciones de menús asociados con otros elementos de la interfaz de usuario se describen en la sección del elemento respectivo. Se debe usar siempre la implementación de menús estándar proporcionada por el entorno de Visual Studio. Sin embargo, en algunas ocasiones podría no tener acceso a los menús estándar de Visual Studio. En estos casos, use los siguientes nombres de token para asegurarse de que la interfaz de usuario sea coherente con otros menús de Visual Studio.

![Visual Studio menú (línea roja)](../../extensibility/ux-guidelines/media/0303-000_menuredline.png "0303-000_MenuRedline")<br />Visual Studio menú (línea roja)

| Uso... | No use ... |
| --- | --- |
| ... cuando necesite crear un menú personalizado.| ... el color de fondo por sí solo. Use siempre la combinación de primer plano y fondo tal como se especifica. |
| ... cuando tiene un nuevo componente de interfaz de usuario que desea que coincida con los Visual Studio menús.| |

#### <a name="menu-titles"></a>Títulos de menú
Los títulos de menú constan de un fondo, un borde y el texto del título, así como un glifo opcional, que suele usarse cuando el menú se encuentra en una barra de comandos.

![Título del menú (línea roja)](../../extensibility/ux-guidelines/media/0303-001_menutitleredline.png "0303-001_MenuTitleRedline")<br />Título del menú (línea roja)

| Uso... | No use ... |
| --- | --- |
| ... siempre que cree un título de menú personalizado. | ... para cualquier cosa que no quiera que coincida siempre con el título del menú. |
| | ... en cualquier combinación de fondo/primer plano que no sea la especificada. |

**Título del menú: estado predeterminado**

![Título del menú predeterminado](../../extensibility/ux-guidelines/media/0303-002_menutitledefault.png "0303-002_MenuTitleDefault")<br />Título del menú predeterminado

![Título del menú predeterminado con glifo](../../extensibility/ux-guidelines/media/0303-003_menutitlewithglyphdefault.png "0303-003_MenuTitleWithGlyphDefault")<br />Título del menú predeterminado con glifo

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | Ninguno |
| Primer plano (texto) | `Environment.CommandBarTextActive` |
| Primer plano (glifo) | `Environment.CommandBarMenuGlyph` |
| Borde | Ninguno |

**Título del menú: estado del mouse**

![Título de menú al mantener el mouse](../../extensibility/ux-guidelines/media/0303-004_menutitlehover.png "0303-004_MenuTitleHover")<br />Título de menú al mantener el mouse

![Título de menú con glifo al mantener el mouse](../../extensibility/ux-guidelines/media/0303-005_menutitlewithglyphhover.png "0303-005_MenuTitleWithGlyphHover")<br />Título de menú con glifo al mantener el mouse

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Los delimitadores de degradado para este token no se usan en la interfaz de usuario con el mismo formato). |
| Primer plano (texto) | `Environment.CommandBarTextHover` |
| Primer plano (glifo) | `Environment.CommandBarMenuMouseOverGlyph` |
| Borde | `Environment.CommandBarBorder` |

**Título del menú: estado presionado**

![Título del menú presionado](../../extensibility/ux-guidelines/media/0303-006_menutitlepressed.png "0303-006_MenuTitlePressed")<br />Título del menú presionado

![Título del menú presionado con glifo](../../extensibility/ux-guidelines/media/0303-007_menutitlewithglyphpressed.png "0303-007_MenuTitleWithGlyphPressed")<br />Título del menú presionado con glifo

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.CommandBarMenuBackgroundGradientBegin`<br/>(Los delimitadores de degradado para este token no se usan en la interfaz de usuario con el mismo formato). |
| Primer plano (texto) | `Environment.CommandBarTextActive` |
| Primer plano (glifo) | `Environment.CommandBarMenuMouseDownGlyph` |
| Borde | `Environment.CommandBarMenuBorder`<br />(Solo los lados izquierdo, superior y derecho). |

**Título del menú: estado deshabilitado**

![Título del menú Deshabilitado con glifo](../../extensibility/ux-guidelines/media/0303-008_menutitlewithglyphdisabled.png "0303-008_MenuTitleWithGlyphDisabled")<br />Título del menú Deshabilitado con glifo

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | Ninguno |
| Primer plano (texto) | `Environment.CommandBarTextInactive` |
| Primer plano (glifo) | `Environment.CommandBarTextInactive` |
| Borde | Ninguno |

#### <a name="menu-items"></a>Elementos de menú
Un elemento de menú individual se compone del texto del menú y un icono opcional, una casilla o un glifo de submenú. Su color de fondo y de texto cambian al mantener el puntero. Este token de color es un par de primer plano y fondo.

![Revisión de elementos de menú](../../extensibility/ux-guidelines/media/0303-009_menuitemredline.png "0303-009_MenuItemRedline")

| Uso... | No use ... |
|---|---|
| ... para cualquier lista desplegable que se inicia desde una barra de menús o una barra de comandos. | ... para cualquier lista desplegable en otro contexto. |
| | ... en cualquier combinación de fondo/primer plano que no sea la especificada. |

**Elementos de menú: estado predeterminado**

![Elementos de menú predeterminados](../../extensibility/ux-guidelines/media/0303-010_menudefault.png "0303-010_MenuDefault")<br />Elementos de menú predeterminados

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.CommandBarMenuBackgroundGradientBegin`<br />(Los delimitadores de degradado para este token no se usan en la interfaz de usuario con el mismo formato). |
| Primer plano (texto) | `Environment.CommandBarTextActive` |
| Primer plano (glifo de submenú) | `Environment.CommandBarMenuSubmenuGlyph` |
| Borde | `Environment.CommandBarMenuBorder` |
| Fondo de canal de iconos | `Environment.CommandBarMenuIconBackground` |
| Separador | `Environment.CommandBarMenuSeparator` |
| Shadow | `Environment.DropShadowBackground` |

**Elementos de menú: estados activados y seleccionados**

![Menú activado](../../extensibility/ux-guidelines/media/0303-011_menuchecked.png "0303-011_MenuChecked")<br />Elemento de menú activado

![Menú seleccionado](../../extensibility/ux-guidelines/media/0303-012_menuselected.png "0303-012_MenuSelected")<br />Elemento de menú seleccionado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Marca de verificación | `Environment.CommandBarCheckBox` |
| Fondo de marca de verificación | `Environment.CommandBarSelectedIcon` |
| Fondo de icono | `Environment.CommandBarSelected` |
| Borde de icono | `Environment.CommandBarSelectedBorder` |

**Elementos de menú: estado del mouse**

![Menú al mantener el mouse](../../extensibility/ux-guidelines/media/0303-013_menuhover.png "0303-013_MenuHover")<br />Elemento de menú al mantener el puntero

![Menú activado al mantener el mouse](../../extensibility/ux-guidelines/media/0303-014_menuhoverchecked.png "0303-014_MenuHoverChecked")<br />Elemento de menú activado al mantener el puntero

![Menú seleccionado al mantener el mouse](../../extensibility/ux-guidelines/media/0303-015_menuhoverselected.png "0303-015_MenuHoverSelected")<br />Elemento de menú seleccionado al mantener el puntero

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.CommandBarMenuItemMouseOver` |
| Primer plano (texto) | `Environment.CommandBarMenuItemMouseOverText` |
| Primer plano (glifo de submenú) | `Environment.CommandBarMenuMouseOverSubmenuGlyph` |
| Marca de verificación | `Environment.CommandBarCheckBoxMouseOver` |
| Fondo de marca de verificación | `Environment.CommandBarHoverOverSelectedIcon` |
| Fondo de icono | `Environment.CommandBarHoverOverSelected` |
| Borde de icono | `Environment.CommandBarHoverOverSelectedIconBorder` |

**Elementos de menú: estado deshabilitado**

![Menú deshabilitado](../../extensibility/ux-guidelines/media/0303-016_menudisabled.png "0303-016_MenuDisabled")<br />Elemento de menú Deshabilitado

![Menú deshabilitado activado](../../extensibility/ux-guidelines/media/0303-017_menudisabledchecked.png "0303-017_MenuDisabledChecked")<br />Elemento de menú deshabilitado con marca de verificación

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Primer plano (texto) | `Environment.CommandBarTextInactive` |
| Primer plano (glifo de submenú) | `Environment.CommandBarMenuSubmenuGlyph` |
| Marca de verificación | `Environment.CommandBarCheckBoxDisabled` |
| Fondo de marca de verificación | `Environment.CommandBarSelectedIconDisabled` |

### <a name="command-bars"></a>Barras de comandos
Una barra de comandos puede aparecer en varios lugares dentro del IDE de Visual Studio, especialmente en la plataforma de comandos e incrustada en ventanas de herramientas o documentos.

En general, use siempre la implementación de menús estándar proporcionada por el entorno de Visual Studio. El uso del mecanismo estándar, garantiza que todos los detalles visuales se mostrarán correctamente y que los elementos interactivos se comportarán de forma coherente con otros controles de barra de comandos de Visual Studio. Sin embargo, si necesita crear su propia barra de comandos, asegúrese de diseñarla correctamente mediante los siguientes nombres de token.

![Límite de barra de comandos](../../extensibility/ux-guidelines/media/0303-018_commandbarredline.png "0303-018_CommandBarRedline")<br />Barra de comandos (línea roja)

![Límite de botón de desbordamiento](../../extensibility/ux-guidelines/media/0303-019_overflowbuttonredline.png "0303-019_OverflowButtonRedline")<br />Botón De desbordamiento (línea roja)

| Uso... | No use ... |
| --- | --- |
| ... en los lugares donde necesita una barra de comandos incrustada, pero no puede usar el estándar Visual Studio implementación de la barra de comandos. | ... para elementos de interfaz de usuario que no son similares a una barra de comandos. |
| | ... para los componentes de la barra de comandos distintos de los para los que se especifican nombres de token. |

#### <a name="command-bar-groups"></a>Grupos de barras de comandos
Un grupo de la barra de comandos se compone de un conjunto relacionado de controles de barra de comandos y puede incluir cualquier número de botones, botones de expansión, menús desplegables, cuadros combinados o menús. Los colores de dichos controles se regulan mediante nombres de token independientes y se describen individualmente en esta guía. Se usa una línea divisoria para dividir un grupo de la barra de comandos en subgrupos relacionados.

![Límite de grupo de la barra de comandos](../../extensibility/ux-guidelines/media/0303-020_commandbargroupredline.png "0303-020_CommandBarGroupRedline")<br />Grupo de la barra de comandos (línea roja)

| Uso... | No use ... |
| --- | --- |
| ... en los lugares donde necesita una barra de comandos incrustada, pero no puede usar el estándar Visual Studio implementación de la barra de comandos. | ... para elementos de interfaz de usuario que no son similares a una barra de comandos. |
| | ... para los componentes de la barra de comandos distintos de los para los que se especifican nombres de token. |

**Grupo de la barra de comandos: estado predeterminado**

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.CommandBarGradientBegin`<br />(Los delimitadores de degradado para este token no se usan en la interfaz de usuario con el mismo formato). |
| Borde | `Environment.CommandBarToolBarBorder` |
| Controlador de arrastre | `Environment.CommandBarDragHandle` |
| Separador | `Environment.CommandBarToolBarSeparator`<br />`Environment.CommandBarToolBarSeparatorHighlight` |

#### <a name="command-icons"></a>Iconos de comando
![Límite de icono de comando](../../extensibility/ux-guidelines/media/0303-021_commandiconredline1.png "0303-021_CommandIconRedline1")<br />Icono de comando (línea roja)

![Icono de comando con línea roja de texto](../../extensibility/ux-guidelines/media/0303-022_commandiconredline2.png "0303-022_CommandIconRedline2")<br />Icono de comando con texto (línea roja)

| Uso... | No use ... |
| --- | --- |
| ... para los botones que se colocarán en una barra de comandos. | ... para los controles que tienen sus propios nombres de token. |
| | ... en cualquier combinación de fondo/primer plano que no sea la especificada. |

**Icono de comando: estado predeterminado**

![Icono de comando predeterminado](../../extensibility/ux-guidelines/media/0303-023_commandicondefault.png "0303-023_CommandIconDefault")<br />Icono de comando predeterminado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | N/D (se hereda del fondo de la barra de comandos) |
| Primer plano (texto) | `Environment.CommandBarTextActive` |
| Borde | N/D |

**Icono de comando: estado predeterminado, seleccionado**

![Icono de comando predeterminado seleccionado](../../extensibility/ux-guidelines/media/0303-024_commandicondefaultselected.png "0303-024_CommandIconDefaultSelected")<br />Icono de comando predeterminado seleccionado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.CommandBarSelected` |
| Primer plano (texto) | `Environment.CommandBarTextSelected` |
| Borde | `Environment.CommandBarSelectedBorder` |

**Icono de comando: mantener el puntero o los estados de foco**

![Icono de comando al mantener el puntero o el foco](../../extensibility/ux-guidelines/media/0303-025_commandiconhover.png "0303-025_CommandIconHover")<br />Icono de comando al mantener el puntero o el foco

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Los delimitadores de degradado para este token no se usan en la interfaz de usuario con el mismo formato). |
| Primer plano (texto) | `Environment.CommandBarTextHover` |
| Borde | `Environment.CommandBarBorder` |

**Icono de comando: mantener el puntero o los estados de foco seleccionados**

![Icono de comando seleccionado al mantener el puntero o el foco](../../extensibility/ux-guidelines/media/0303-026_commandiconhoverselected.png "0303-026_CommandIconHoverSelected")<br />Icono de comando seleccionado al mantener el puntero o el foco

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.CommandBarHoverOverSelected` |
| Primer plano (texto) | `Environment.CommandBarTextHoverOverSelected` |
| Borde | `Environment.CommandBarHoverOverSelectedIconBorder` |

 **Icono de comando: estado presionado**

![Icono de comando presionado](../../extensibility/ux-guidelines/media/0303-027_commandiconpressed.png "0303-027_CommandIconPressed")<br />Icono de comando presionado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.CommandBarMouseDownBackgroundBegin`<br />(Los delimitadores de degradado para este token no se usan en la interfaz de usuario con el mismo formato). |
| Primer plano (texto) | `Environment.CommandBarTextMouseDown` |
| Borde | `Environment.CommandBarBorder` |

**Icono de comando: estado deshabilitado**

![Icono de comando deshabilitado](../../extensibility/ux-guidelines/media/0303-028_commandicondisabled.png "0303-028_CommandIconDisabled")<br />Icono de comando deshabilitado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | N/D (se hereda del fondo de la barra de comandos) |
| Primer plano (texto) | `Environment.CommandBarTextInactive` |
| Borde | N/D |

#### <a name="command-bar-combo-boxes"></a><a name="BKMK_CommandComboBox"></a> Cuadros combinados de la barra de comandos

> [!IMPORTANT]
> Los cuadros combinados son similares a las listas desplegables, pero incluyen un área de texto editable. Si la lista desplegable no incluye una región de texto modificable, use los tokens de color para los [menús desplegables de la barra de comandos.](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown)

![Línea roja del cuadro combinado de la barra de comandos](../../extensibility/ux-guidelines/media/0303-029_comboboxredline.png "0303-029_ComboBoxRedline")<br />Cuadro combinado de la barra de comandos (línea roja)

| Uso... | No use ... |
| --- | --- |
| ... al crear cuadros combinados personalizados. | ... para cualquier cosa que no quiera que siempre coincida con la interfaz de usuario de la barra de comandos. |
| ... al crear un control de barra de comandos similar a un cuadro combinado. | ... cuando tiene acceso a un cuadro combinado con estilo. |

**Campo de entrada del cuadro combinado de la barra de comandos: estado predeterminado**

![Campo de entrada del cuadro combinado de la barra de comandos](../../extensibility/ux-guidelines/media/0303-030_comboboxinputfield.png "0303-030_ComboBoxInputField")<br />Campo de entrada del cuadro combinado de la barra de comandos

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.ComboBoxBackground` |
| Primer plano (texto) | `Environment.ComboBoxText` |
| Borde | `Environment.ComboBoxBorder` |
| Separador | Sin separador |

**Botón desplegable de la barra de comandos: estado predeterminado**

![Botón desplegable cuadro&#45;desplegable](../../extensibility/ux-guidelines/media/0303-031_comboboxdropdownbutton.png "0303-031_ComboBoxDropdownButton")<br />Botón desplegable de la barra de comandos

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | N/D (se hereda del fondo de la barra de comandos) |
| Primer plano (glifo) | `Environment.ComboBoxGlyph` |

**Lista desplegable de la barra de comandos: estado predeterminado**

![Lista desplegable de la barra de comandos](../../extensibility/ux-guidelines/media/0303-032_comboboxdropdownlist.png "0303-032_ComboBoxDropdownList")<br />Lista desplegable de la barra de comandos

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.ComboBoxPopupBackgroundBegin`<br />(Los delimitadores de degradado para este token no se usan en la interfaz de usuario con el mismo formato). |
| Primer plano (texto) | `Environment.ComboBoxItemText` |
| Borde | `Environment.ComboBoxPopupBorder` |

**Campo de entrada del cuadro combinado de la barra de comandos: estado del mouse**

![Campo de entrada del cuadro combinado de la barra de comandos al mantener el puntero](../../extensibility/ux-guidelines/media/0303-033_comboboxinputfieldhover.png "0303-033_ComboBoxInputFieldHover")<br />Campo de entrada del cuadro combinado de la barra de comandos al mantener el puntero

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.ComboBoxMouseOverBackgroundBegin`<br />(Los delimitadores de degradado para este token no se usan en la interfaz de usuario con el mismo formato). |
| Primer plano (texto) | `Environment.ComboBoxMouseOverText` |
| Borde | `Environment.ComboBoxMouseOverBorder` |
| Separador | `Environment.ComboBoxMouseOverSeparator` |

 **Botón desplegable de la barra de comandos: estado del mouse**

![Botón desplegable del cuadro combinado de la barra de comandos al mantener el puntero](../../extensibility/ux-guidelines/media/0303-034_comboboxdropdownbuttonhover.png "0303-034_ComboBoxDropdownButtonHover")<br />Botón desplegable de la barra de comandos al mantener el puntero

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.ComboBoxButtonMouseOverBackground` |
| Primer plano (glifo) | `Environment.ComboBoxMouseOverGlyph` |

**Lista desplegable de la barra de comandos: estado del mouse**

 ![Lista desplegable del cuadro combinado de la barra de comandos al mantener el puntero](../../extensibility/ux-guidelines/media/0303-035_comboboxdropdownlisthover.png "0303-035_ComboBoxDropdownListHover")<br />Lista desplegable de la barra de comandos al mantener el puntero

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo (elemento de menú) | `Environment.ComboBoxItemMouseOverBackground` |
| Primer plano (texto) | `Environment.ComboBoxItemMouseOverText` |
| Borde (elemento de menú) | `Environment.ComboBoxItemMouseOverBorder` |

 **Campo de entrada del cuadro combinado de la barra de comandos: estado enfocado**

![Campo de entrada del cuadro combinado de la barra de comandos centrada](../../extensibility/ux-guidelines/media/0303-036_comboboxinputfieldfocused.png "0303-036_ComboBoxInputFieldFocused")<br />Campo de entrada del cuadro combinado de la barra de comandos centrada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.ComboBoxFocusedBackground` |
| Primer plano (texto) | `Environment.ComboBoxFocusedText` |
| Borde | `Environment.ComboBoxFocusedBorder` |
| Separador | `Environment.ComboBoxFocusedButtonSeparator` |

**Botón desplegable de la barra de comandos: estado centrado**

![Botón desplegable de la barra de comandos centrada](../../extensibility/ux-guidelines/media/0303-037_comboboxdropdownbuttonfocused.png "0303-037_ComboBoxDropdownButtonFocused")<br />Botón desplegable de la barra de comandos centrada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.ComboBoxFocusedButtonBackground` |
| Primer plano (glifo) | `Environment.ComboBoxFocusedGlyph` |

 **Campo de entrada del cuadro combinado de la barra de comandos: estado presionado**

![Campo de entrada del cuadro combinado de la barra de comandos presionado](../../extensibility/ux-guidelines/media/0303-038_comboboxinputfieldpressed.png "0303-038_ComboBoxInputFieldPressed")<br />Campo de entrada del cuadro combinado de la barra de comandos presionado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.ComboBoxMouseDownBackground` |
| Primer plano (texto) | `Environment.ComboBoxMouseDownText` |
| Borde | `Environment.ComboBoxMouseDownBorder` |
| Separador | `Environment.ComboBoxMouseDownSeparator` |

**Botón desplegable de la barra de comandos: estado presionado**

![Botón desplegable del cuadro combinado de la barra de comandos presionado](../../extensibility/ux-guidelines/media/0303-039_comboboxdropdownbuttonpressed.png "0303-039_ComboBoxDropdownButtonPressed")<br />Botón desplegable de la barra de comandos presionado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.ComboBoxButtonMouseDownBackground` |
| Primer plano (glifo) | `Environment.ComboBoxMouseDownGlyph` |

**Campo de entrada del cuadro combinado de la barra de comandos: estado deshabilitado**

![Campo de entrada del cuadro combinado de la barra de comandos deshabilitado](../../extensibility/ux-guidelines/media/0303-041_comboboxinputfielddisabled.png "0303-041_ComboBoxInputFieldDisabled")<br />Campo de entrada del cuadro combinado de la barra de comandos deshabilitado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.ComboBoxDisabledBackground` |
| Primer plano (texto) | `Environment.ComboBoxDisabledText` |
| Borde | `Environment.ComboBoxDisabledBorder` |
| Separador | Sin separador |

**Botón desplegable de la barra de comandos: estado deshabilitado**

![Botón desplegable de cuadro combinado de la barra de comandos deshabilitado](../../extensibility/ux-guidelines/media/0303-040_comboboxdropdownbuttondisabled.png "0303-040_ComboBoxDropdownButtonDisabled")<br />Botón desplegable Barra de comandos deshabilitado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | Ninguno |
| Primer plano (glifo) | `Environment.ComboBoxDisabledGlyph` |

#### <a name="command-bar-drop-downs"></a><a name="BKMK_CommandDropDown"></a> Menús desplegables de la barra de comandos

> [!IMPORTANT]
> Las listas desplegables son similares a los cuadros combinados, pero carecen de áreas de texto editable. Si la lista desplegable incluye una región de texto editable, use los tokens de color para los cuadros [combinados de la barra de comandos](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox).

![Lista desplegable de la barra de comandos (línea roja)](../../extensibility/ux-guidelines/media/0303-042_dropdownredline.png "0303-042_DropdownRedline")<br />Lista desplegable de la barra de comandos (línea roja)

| Uso... | No use ... |
| --- | --- |
| ... al crear controles de lista desplegable personalizados. | ... para cualquier cosa que no sea similar a una lista desplegable. |
| | ... para cuadros combinados o botones de división. |

**Campo de selección desplegable de la barra de comandos: estado predeterminado**

![Campo de selección desplegable de la barra de comandos predeterminado](../../extensibility/ux-guidelines/media/0303-043_dropdownselectionfield.png "0303-043_DropdownSelectionField")<br />Campo de selección desplegable de la barra de comandos predeterminado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.DropDownBackground` |
| Primer plano (texto) | `DropDownText` |
| Borde | `DropDownBorder` |
| Separador | Sin separador |

**Botón desplegable de la barra de comandos: estado predeterminado**

![Botón desplegable de la barra de comandos predeterminado](../../extensibility/ux-guidelines/media/0303-044_dropdownbutton.png "0303-044_DropdownButton")<br />Botón desplegable de la barra de comandos predeterminado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | Ninguno |
| Primer plano (glifo) | `Environment.DropDownGlyph` |

**Lista desplegable de la barra de comandos: estado predeterminado**

![Lista desplegable de la barra de comandos predeterminada](../../extensibility/ux-guidelines/media/0303-045_dropdownlist.png "0303-045_DropdownList")<br />Lista desplegable de la barra de comandos predeterminada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.DropDownPopupBackgroundBegin`<br />(Los delimitadores de degradado para este token no se usan en la interfaz de usuario con el mismo formato). |
| Primer plano (texto) | `Environment.ComboBoxItemText` |
| Borde | `Environment.DropDownPopupBorder` |
| Shadow | `Environment.DropShadowBackground` |

**Campo de selección desplegable de la barra de comandos: estado del mouse**

![Campo de selección desplegable de la barra de comandos al mantener el puntero](../../extensibility/ux-guidelines/media/0303-046_dropdownselectionfieldhover.png "0303-046_DropdownSelectionFieldHover")<br />Campo de selección desplegable de la barra de comandos al mantener el puntero

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.DropDownMouseOverBackgroundBegin`<br />(Los delimitadores de degradado para este token no se usan en la interfaz de usuario con el mismo formato). |
| Primer plano (texto) | `Environment.DropDownMouseOverText` |
| Borde | `Environment.DropDownMouseOverBorder` |
| Separador | `Environment.DropDownButtonMouseOverSeparator` |

**Botón desplegable de la barra de comandos: estado del mouse**

![Botón desplegable de la barra de comandos al mantener el puntero](../../extensibility/ux-guidelines/media/0303-047_dropdownbuttonhover.png "0303-047_DropdownButtonHover")<br />Botón desplegable de la barra de comandos al mantener el puntero

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.DropDownButtonMouseOverBackground` |
| Primer plano (glifo) | `Environment.DropDownMouseOverGlyph` |

**Lista desplegable de la barra de comandos: estado del mouse**

![Lista desplegable de la barra de comandos al mantener el puntero](../../extensibility/ux-guidelines/media/0303-048_dropdownlisthover.png "0303-048_DropdownListHover")<br />Lista desplegable de la barra de comandos al mantener el puntero

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo (elemento de menú) | `Environment.ComboBoxItemMouseOverBackground` |
| Primer plano (texto) | `Environment.ComboBoxItemMouseOverText` |
| Borde (elemento de menú) | `Environment.ComboBoxItemMouseOverBorder` |

 **Campo de selección desplegable de la barra de comandos: estado presionado**

![Campo de selección&#45;desplegable presionado](../../extensibility/ux-guidelines/media/0303-049_dropdownselectionfieldpressed.png "0303-049_DropdownSelectionFieldPressed")<br />Campo de selección desplegable de la barra de comandos presionado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.DropDownMouseDownBackground` |
| Primer plano (texto) | `Environment.DropDownMouseDownText` |
| Borde | `Environment.DropDownMouseDownBorder` |
| Separador | `Environment.DropDownButtonMouseDownSeparator` |

**Botón desplegable de la barra de comandos: estado presionado**

![Botón desplegable de la barra de comandos presionado](../../extensibility/ux-guidelines/media/0303-050_dropdownbuttonpressed.png "0303-050_DropdownButtonPressed")<br />Botón desplegable de la barra de comandos presionado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.DropDownButtonMouseDownBackground` |
| Primer plano (glifo) | `Environment.DropDownMouseDownGlyph` |

**Campo de selección desplegable de la barra de comandos: estado deshabilitado**

![Campo de selección desplegable de la barra de comandos deshabilitado](../../extensibility/ux-guidelines/media/0303-051_dropdownselectionfielddisabled.png "0303-051_DropdownSelectionFieldDisabled")<br />Campo de selección desplegable de la barra de comandos deshabilitado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.DropDownDisabledBackground` |
| Primer plano (texto) | `Environment.DropDownDisabledText` |
| Borde | `Environment.DropDownDisabledBorder` |
| Separador | Sin separador |

**Botón desplegable de la barra de comandos: estado deshabilitado**

![Botón desplegable barra de comandos deshabilitado](../../extensibility/ux-guidelines/media/0303-052_dropdownbuttondisabled.png "0303-052_DropdownButtonDisabled")<br />Botón desplegable barra de comandos deshabilitado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | N/D |
| Primer plano (glifo) | `Environment.DropDownDisabledGlyph` |

#### <a name="command-bar-split-buttons"></a>Botones de división de la barra de comandos
Los botones de expansión comparten muchos nombres de token con otros controles de barra de comandos como, por ejemplo, botones, menús y texto de la barra de comandos. Todos los nombres de token de acciones y botones desplegables necesarios se repiten aquí para su comodidad. Las listas desplegables de botones de división son implementaciones de [menús de la barra de comandos.](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus)

![Límite de botón de expansión](../../extensibility/ux-guidelines/media/0303-053_splitbuttonredline.png "0303-053_SplitButtonRedline")<br />Botón de división de la barra de comandos (línea roja)

| Uso... | No use ... |
| --- | --- |
| ... al crear un botón de división personalizado. | ... para otros tipos de botones. |
| | ... en cualquier combinación de fondo y primer plano que no sea la especificada. |

**Botón de división de la barra de comandos: estado predeterminado**

![Botón de división de la barra de comandos predeterminado](../../extensibility/ux-guidelines/media/0303-054_splitbutton.png "0303-054_SplitButton")<br />Botón de división de la barra de comandos predeterminado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | Ninguno |
| Primer plano (texto) | `Environment.CommandBarTextActive` |
| Primer plano (glifo) | `Environment.CommandBarSplitButtonGlyph` |
| Borde | N/D |
| Separador | N/D |

**Botón de división de la barra de comandos: estado del mouse**

![Botón de división de la barra de comandos al mantener el puntero](../../extensibility/ux-guidelines/media/0303-055_splitbuttonhover.png "0303-055_SplitButtonHover")<br />Botón de división de la barra de comandos al mantener el puntero

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Los delimitadores de degradado para este token no se usan en la interfaz de usuario con formato). |
| Primer plano (texto) | `Environment.CommandBarTextHover` |
| Primer plano (glifo) | `Environment.CommandBarSplitButtonMouseOverGlyph` |
| Borde | `Environment.CommandBarBorder` |
| Separador | `Environment.CommandBarSplitButtonSeparator` |

**Botón de división de la barra de comandos: estado presionado**

![Botón de división de la barra de comandos presionado](../../extensibility/ux-guidelines/media/0303-056_splitbuttonpressed.png "0303-056_SplitButtonPressed")<br />Botón de división de la barra de comandos presionado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.CommandBarMouseDownBackgroundBegin`<br />(Los delimitadores de degradado para este token no se usan en la interfaz de usuario con formato). |
| Primer plano (texto) | `Environment.CommandBarTextMouseDown` |
| Primer plano (glifo) | `Environment.CommandBarSplitButtonMouseDownGlyph` |
| Borde | `Environment.CommandBarBorder` |
| Separador | N/D |

**Botón de división de la barra de comandos: estado deshabilitado**

![Botón de división de la barra de comandos deshabilitado](../../extensibility/ux-guidelines/media/0303-057_splitbuttondisabled.png "0303-057_SplitButtonDisabled")<br />Botón de división de la barra de comandos deshabilitado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | N/D |
| Primer plano (texto) | `Environment.ComboBoxItemTextInactive` |
| Primer plano (glifo) | `Environment.CommandBarTextInactive` |
| Borde | N/D |
| Separador | N/D |

#### <a name="command-bar-more-options-and-overflow-buttons"></a>Botones "Más opciones" y "Desbordamiento" de la barra de comandos
El botón "Más opciones" se usa cuando un grupo de la barra de comandos se puede personalizar al agregar o quitar botones relacionados de barra de comandos. El botón "Desbordamiento" aparece cuando una barra de comandos se trunca debido a la falta de espacio horizontal y, al hacer clic en él, muestra un menú que contiene los botones de la barra de comandos que no pueden mostrarse. Los colores para estos dos botones están controlados por el mismo conjunto de nombres de token.

![Botón "Más opciones" de la barra de comandos (línea roja)](../../extensibility/ux-guidelines/media/0303-058_moreoptionsredline.png "0303-058_MoreOptionsRedline")<br />Botón "Más opciones" de la barra de comandos (línea roja)

| Uso... | No use ... |
| --- | --- |
| ... para los botones "Más opciones" o "Desbordamiento" personalizados. | ... para los botones que no tienen una funcionalidad similar a un botón "Más opciones" o "Desbordamiento". |

**Botones "Más opciones" y "Desbordamiento" de la barra de comandos: estado predeterminado**

![Botón "Más opciones" de la barra de comandos predeterminada](../../extensibility/ux-guidelines/media/0303-059_moreoptions.png "0303-059_MoreOptions")<br />Botón "Más opciones" de la barra de comandos predeterminada

![Botón "Overflow" de la barra de comandos predeterminada](../../extensibility/ux-guidelines/media/0303-060_overflow.png "0303-060_Overflow")<br />Botón "Overflow" de la barra de comandos predeterminada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.CommandBarOptionsBackground` |
| Primer plano (glifo) | `Environment.CommandBarOptionsGlyph` |

**Botones "Más opciones" y "Desbordamiento" de la barra de comandos: estado del mouse**

![Botón "Más opciones" de la barra de comandos al mantener el puntero](../../extensibility/ux-guidelines/media/0303-061_moreoptionshover.png "0303-061_MoreOptionsHover")<br />Botón "Más opciones" de la barra de comandos al mantener el puntero

![Botón "Overflow" de la barra de comandos al mantener el puntero](../../extensibility/ux-guidelines/media/0303-062_overflowoptions.png "0303-062_OverflowOptions")<br />Botón "Overflow" de la barra de comandos al mantener el puntero

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.CommandBarOptionsMouseOverBackgroundBegin`<br />(Los delimitadores de degradado para este token no se usan en la interfaz de usuario con el mismo formato). |
| Primer plano (glifo) | `Environment.CommandBarOptionsMouseDownGlyph` |

**Botones "Más opciones" y "Desbordamiento" de la barra de comandos: estado presionado**

![Botón "Más opciones" de la barra de comandos presionada](../../extensibility/ux-guidelines/media/0303-063_moreoptionspressed.png "0303-063_MoreOptionsPressed")<br />Botón "Más opciones" de la barra de comandos presionada

![Desbordamiento presionado](../../extensibility/ux-guidelines/media/0303-064_overflowpressed.png "0303-064_OverflowPressed")<br />Botón "Desbordamiento" de la barra de comandos presionada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.CommandBarOptionsMouseDownBackgroundBegin`<br />(Los delimitadores de degradado para este token no se usan en la interfaz de usuario con el mismo formato). |
| Primer plano (glifo) | `Environment.CommandBarOptionsMouseDownGlyph` |

## <a name="document-windows"></a>Ventanas de documento
No es necesario replicar las ventanas de documentos, ya que las proporciona el Visual Studio de documentos. Sin embargo, quizá prefiera aprovechar los colores que se usan en las ventanas de documento para que la interfaz de usuario se muestre siempre coherente con esta parte del entorno de Visual Studio.

Al usar tokens de color de ventana de documento, tenga cuidado de usarlos solo para elementos similares y siempre en pares. Si no lo hace, es posible que obtenga resultados inesperados en la interfaz de usuario.

### <a name="document-window-frames"></a>Marcos de ventana del documento
Las ventanas de documento pueden estar acopladas en el IDE o flotantes como una ventana independiente. Cuando una ventana de documento está flotante fuera del IDE, todavía se encuentra en un área de documento y tiene colores de fondo, borde, texto y tabulación que son los mismos que cuando forma parte del IDE. Sin embargo, el documento se encuentra dentro de un marco que tiene su propio fondo, borde y colores de texto. Cuando las ventanas de herramientas se acoplan en el cuadro del documento, heredan el comportamiento y el color de los nombres de token de ventana de documento para sus pestañas.

![Ventana de documento acoplado (línea roja)](../../extensibility/ux-guidelines/media/0303-065_dockeddocumentwindowredline.png "0303-065_DockedDocumentWindowRedline")<br />Ventana de documento acoplado (línea roja)

![Ventana de documento flotante (línea roja)](../../extensibility/ux-guidelines/media/0303-066_floatingdocumentwindowredline.png "0303-066_FloatingDocumentWindowRedline")<br />Ventana de documento flotante (línea roja)

| Uso... | No use ... |
| --- | --- |
| ... en cualquier lugar en el que cree la interfaz de usuario que desee que coincida con la ventana del documento. | ...  para cualquier interfaz de usuario que no quiera cambiar automáticamente si el shell tiene una actualización de tema. |

**Ventana de documento acoplada o flotante: estado predeterminado**

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | Depende del tipo de documento |
| Primer plano (texto) | Depende del tipo de documento |
| Borde | `Environment.ToolWindowBorder` |

**Marco de ventana de documento flotante centrado: estado predeterminado**

![Marco de ventana de documento flotante con foco predeterminado](../../extensibility/ux-guidelines/media/0303-067_framefocused.png "0303-067_FrameFocused")<br />Marco de ventana de documento flotante con foco predeterminado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.ToolWindowFloatingFrame` |
| Primer plano (texto) | `Environment.ToolWindowFloatingFrame` |
| Primer plano (glifo) | `Environment.RaftedWindowButtonActiveGlyph` |
| Borde | `Environment.MainWindowActiveDefaultBorder` |
| Borde (glifo) | `Environment.RaftedWindowButtonActiveBorder`<br />(Se establece en transparente) |

**Marco de ventana de documento flotante sin foco: estado predeterminado**

![Marco de ventana de documento flotante y sin foco predeterminado](../../extensibility/ux-guidelines/media/0303-068_frameunfocused.png "0303-068_FrameUnfocused")<br />Marco de ventana de documento flotante y sin foco predeterminado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.ToolWindowFloatingFrameInactive` |
| Primer plano (texto) | `Environment.ToolWindowFloatingFrameInactive` |
| Primer plano (glifo) | `Environment.RaftedWindowButtonInactiveGlyph` |
| Borde | `Environment.MainWindowInactiveBorder` |
| Borde (glifo) | `Environment.RaftedWindowButtonInactiveBorder`<br />(Se establece en transparente) |

**Marco de ventana de documento flotante centrado: estado del mouse**

![Marco de ventana de documento flotante centrado al mantener el puntero](../../extensibility/ux-guidelines/media/0303-069_framefocusedhover.png "0303-069_FrameFocusedHover")<br />Marco de ventana de documento flotante centrado al mantener el puntero

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo (glifo) | `Environment.RaftedWindowButtonHoverActive` |
| Primer plano (glifo) | `Environment.RaftedWindowButtonHoverActiveGlyph` |
| Borde (glifo) | `Environment.RaftedWindowButtonHoverActiveBorder` |

**Marco de ventana de documento flotante sin foco: estado del mouse**

![Marco de ventana de documento flotante sin foco al mantener el puntero](../../extensibility/ux-guidelines/media/0303-070_frameunfocusedhover.png "0303-070_FrameUnfocusedHover")<br />Marco de ventana de documento flotante sin foco al mantener el puntero

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo (glifo) | `EnvironmentRaftedWindowButtonHoverInactive` |
| Primer plano (glifo) | `Environment.RaftedWindowButtonHoverInactiveGlyph` |
| Borde (glifo) | `Environment.RaftedWindowButtonHoverInactiveBorder` |

**Marco de ventana de documento flotante centrado: estado presionado**

![Marco de ventana de documento flotante centrado al presionar](../../extensibility/ux-guidelines/media/0303-071_framefocusedpressed.png "0303-071_FrameFocusedPressed")<br />Marco de ventana de documento flotante centrado al presionar

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo (glifo) | `Environment.RaftedWindowButtonDown` |
| Primer plano (glifo) | `Environment.RaftedWindowButtonDownGlyph` |
| Borde (glifo) | `Environment.RaftedWindowButtonDownBorder` |

### <a name="document-tabs"></a>Pestañas de documentos
Las pestañas de documentos se colocan en el canal de pestañas para indicar los documentos que están abiertos actualmente, así como el documento actual activo o seleccionado. Las ventanas de herramientas también se pueden acoplar en el canal de pestañas de documentos si el usuario las coloca allí. En este caso, usan los mismos colores de pestaña que las ventanas de documento. Si va a crear interfaz de usuario que desea que siempre coincida con los colores de las ventanas de documento (lo que incluye las actualizaciones de temas o si se instalan nuevos temas), entonces haga referencia a estos tokens de color.

![Pestañas del documento (línea roja)](../../extensibility/ux-guidelines/media/0303-072_documenttabredline.png "0303-072_DocumentTabRedline")<br />Pestañas del documento (línea roja)

| Uso... | No use ... |
| --- | --- |
| ... en cualquier lugar en el que cree una interfaz de usuario que desee que coincida con las pestañas del documento y que elija automáticamente actualizaciones de temas o nuevos colores de tema. | ... para cualquier interfaz de usuario que no quiera cambiar automáticamente cuando el shell tiene una actualización de tema. |

#### <a name="open-document-tabs"></a>Pestañas de documentos abiertos
Cada documento abierto tiene una pestaña en el canal de pestañas de documentos que muestra su nombre. Los documentos pueden estar seleccionados o abiertos en segundo plano y sus pestañas reflejan los siguientes estados:

- La pestaña seleccionada representa el documento que se muestra actualmente en el cuadro de documento. Una pestaña seleccionada tiene un borde de documento que se extiende por todo el borde superior del cuadro de documento.

- Las pestañas en segundo plano son las pestañas de documento que no son la pestaña seleccionada actualmente. Una vez hecho clic, se convierten en la pestaña seleccionada y adquieren todos los colores de fondo, borde y texto de esos nombres de token.

![Abrir la pestaña documento (línea roja)](../../extensibility/ux-guidelines/media/0303-073_opendocumenttabredline.png "0303-073_OpenDocumentTabRedline")<br />Abrir la pestaña documento (línea roja)

| Uso... | No use ... |
| --- | --- |
| ... al crear pestañas de documento personalizadas. | ... para las pestañas provisionales (versión preliminar). |
| | ... para cualquier interfaz de usuario que no quiera cambiar automáticamente si el shell tiene una actualización de tema. |

**Pestaña De documento seleccionado y centrado**

![Pestaña De documento seleccionado y centrado](../../extensibility/ux-guidelines/media/0303-074_selectedtabfocused.png "0303-074_SelectedTabFocused")<br />Pestaña De documento seleccionado y centrado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.FileTabSelectedGradientTop`<br />(Los delimitadores de degradado para este token no se usan en la interfaz de usuario con el mismo formato). |
| Primer plano (texto) | `Environment.FileTabSelectedText` |
| Borde | `Environment.FileTabSelectedBorder`<br />(Se establece en el mismo color que el fondo). |
| Borde de documento | `Environment.FileTabDocumentBorderBackground` |

**Pestaña Documento seleccionado sin foco**

![Pestaña Documento seleccionado sin foco](../../extensibility/ux-guidelines/media/0303-075_selectedtabunfocused.png "0303-075_SelectedTabUnfocused")<br />Pestaña Documento seleccionado sin foco

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.FileTabInactiveGradientTop`<br />(Los delimitadores de degradado para este token no se usan en la interfaz de usuario con el mismo formato). |
| Primer plano (texto) | `Environment.FileTabInactiveText` |
| Borde | `Environment.FileTabInactiveBorder`<br />(Se establece en el mismo color que el fondo). |
| Borde de documento | `Environment.FileTabInactiveDocumentBorderBackground` |

**Pestaña Documento en segundo plano: estado predeterminado**

![Pestaña Documento en segundo plano predeterminado](../../extensibility/ux-guidelines/media/0303-076_backgroundtab.png "0303-076_BackgroundTab")<br />Pestaña Documento en segundo plano predeterminado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.FileTabBackground` |
| Primer plano (texto) | `Environment.FileTabText` |
| Borde | `Environment.FileTabBorder`<br />(Se establece en el mismo color que el fondo). |

**Pestaña Documento en segundo plano: estado del mouse**

![Pestaña Documento en segundo plano al mantener el puntero](../../extensibility/ux-guidelines/media/0303-077_backgroundtabhover.png "0303-077_BackgroundTabHover")<br />Pestaña Documento en segundo plano al mantener el puntero

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.FileTabHotGradientTop`<br />(Los delimitadores de degradado para este token no se usan en la interfaz de usuario con el mismo formato). |
| Primer plano (texto) | `Environment.FileTabHotText` |
| Borde | `Environment.FileTabHotBorder`<br />(Se establece en el mismo color que el fondo). |

#### <a name="preview-tab"></a>Pestaña de vista previa
También se denomina pestaña "provisional". La pestaña vista previa aparece en el lado derecho del canal de pestañas del documento cuando el usuario hace clic en un elemento en la Explorador de soluciones herramientas. Funciona como una vista previa del documento y también proporciona al usuario la posibilidad de mantener el documento abierto en la parte izquierda del canal de pestañas de documentos. Solo se puede abrir una pestaña de vista previa a la vez. Las pestañas de vista previa tienen tanto el estado seleccionado como en segundo plano al igual que las pestañas abiertas y, además, pueden estar con y sin foco en su estado activo.

![Pestaña Vista previa (línea roja)](../../extensibility/ux-guidelines/media/0303-078_previewtabredline.png "0303-078_PreviewTabRedline")<br />Pestaña Vista previa (línea roja)

| Uso... | No use ... |
| --- | --- |
| ... en cualquier lugar en el que cree una vista previa provisional y desee que algún elemento coincida con el color de la pestaña de vista previa actual. | ... para cualquier tipo de documento o pestaña que no sea provisional (versión preliminar). |
| | ... para cualquier interfaz de usuario que no quiera cambiar automáticamente si el shell tiene una actualización de tema. |

**Pestaña vista previa seleccionada y centrada**

![Pestaña vista previa seleccionada y centrada](../../extensibility/ux-guidelines/media/0303-079_previewtabfocused.png "0303-079_PreviewTabFocused")<br />Pestaña vista previa seleccionada y centrada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.FileTabProvisionalSelectedActive` |
| Primer plano (texto) | `Environment.FileTabProvisionalSelectedActiveForeground` |
| Borde | `Environment.FileTabProvisionalSelectedActiveBorder`<br />(Se establece en el mismo color que el fondo). |
| Borde de documento | `Environment.FileTabProvisionalSelectedActiveBorder` |

**Pestaña vista previa seleccionada sin foco**

![Pestaña vista previa seleccionada sin foco](../../extensibility/ux-guidelines/media/0303-080_previewtabunfocused.png "0303-080_PreviewTabUnfocused")<br />Pestaña vista previa seleccionada sin foco

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.FileTabProvisionalSelectedInactive` |
| Primer plano (texto) | `Environment.FileTabProvisionalSelectedInactiveForeground` |
| Borde | `Environment.FileTabProvisionalSelectedInactiveBorder` |
| Borde de documento | `Environment.FileTabProvisionalSelectedInactiveBorder` |

**Pestaña Vista previa en segundo plano: estado predeterminado**

![Pestaña vista previa en segundo plano predeterminada](../../extensibility/ux-guidelines/media/0303-081_previewbackgroundtab.png "0303-081_PreviewBackgroundTab")<br />Pestaña vista previa en segundo plano predeterminada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.FileTabProvisionalInactive` |
| Primer plano (texto) | `Environment.FileTabProvisionalInactiveForeground` |
| Borde | `Environment.FileTabProvisionalInactiveBorder`<br />(Se establece en el mismo color que el fondo). |

**Pestaña vista previa en segundo plano: estado del mouse**

![Pestaña vista previa en segundo plano al mantener el puntero](../../extensibility/ux-guidelines/media/0303-082_previewbackgroundtabhover.png "0303-082_PreviewBackgroundTabHover")<br />Pestaña vista previa en segundo plano al mantener el puntero

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.FileTabProvisionalHover` |
| Primer plano (texto) | `Environment.FileTabProvisionalHoverForeground` |
| Borde | `Environment.FileTabProvisionalHoverBorder`<br />(Se establece en el mismo color que el fondo). |

#### <a name="document-overflow-button"></a>Botón de desbordamiento de documento
El botón de desbordamiento de documento se muestra si hay uno o varios documentos abiertos, independientemente de si hay espacio vertical en la configuración actual para que quepan todas las pestañas de documentos. El menú desplegable de desbordamiento de [](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus) documentos, que se controla mediante los colores del menú de la barra de comandos, muestra una lista de todos los documentos abiertos, visibles y ocultos, y el glifo de desbordamiento cambia en función de si todos los documentos abiertos se muestran en el canal de pestañas.

![Botón de desbordamiento del documento (línea roja)](../../extensibility/ux-guidelines/media/0303-083_overflowredline.png "0303-083_OverflowRedline")<br />Botón de desbordamiento del documento (línea roja)

| Uso... | No use ... |
| --- | --- |
| ... al crear un botón de desbordamiento de documento personalizado. | ... para la interfaz de usuario que no es similar a un botón de desbordamiento. |
| | ... para los botones de desbordamiento de la barra de comandos. |

**Botón de desbordamiento del documento: estado predeterminado**

![Botón de desbordamiento de documento predeterminado](../../extensibility/ux-guidelines/media/0303-084_overflow.png "0303-084_Overflow")<br />Botón de desbordamiento de documento predeterminado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.DocWellOverflowButtonBackground` |
| Primer plano (glifo) | `Environment.DocWellOverflowButtonGlyph` |
| Borde | N/D |

**Botón de desbordamiento del documento: estado del mouse**

![Botón de desbordamiento de documento al mantener el puntero](../../extensibility/ux-guidelines/media/0303-085_overflowhover.png "0303-085_OverflowHover")<br />Botón de desbordamiento de documento al mantener el puntero

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.DocWellOverflowButtonMouseOverBackground` |
| Primer plano (glifo) | `Environment.DocWellOverflowButtonMouseOverGlyph` |
| Borde | `Environment.DocWellOverflowButtonMouseOverBorder` |

**Botón de desbordamiento del documento: estado presionado**

![Botón de desbordamiento del documento al presionar](../../extensibility/ux-guidelines/media/0303-086_overflowpressed.png "0303-086_OverflowPressed")<br />Botón de desbordamiento del documento al presionar

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.DocWellOverflowButtonMouseDownBackground` |
| Primer plano (glifo) | `Environment.DocWellOverflowButtonMouseDownGlyph` |
| Borde | `Environment.DocWellOverflowButtonMouseDownBorder` |

### <a name="tagging"></a>Etiquetado
Visual Studio admite el etiquetado, lo que permite al usuario declarar palabras clave de búsqueda con fines de seguimiento. Por ejemplo, los desarrolladores y los administradores de proyectos pueden usar Team Foundation Server (TFS) para etiquetar elementos de trabajo. Las tablas siguientes proporcionan nombres de colores para la etiqueta en sí y el glifo del "icono de cerrar" que aparecen en los estados Al desplazar el puntero y Seleccionado.

![Etiquetado en Visual Studio (línea roja)](../../extensibility/ux-guidelines/media/0303-176_taggingredline.png "0303-176_TaggingRedline")<br />Etiquetado en Visual Studio (línea roja)

| Uso... | No use ... |
| --- | --- |
| ... para la interfaz de usuario que admite el etiquetado. | ... para cualquier otro tipo de interfaz de usuario. |

#### <a name="tags"></a>Etiquetas

**Etiqueta: estado predeterminado**

![Etiqueta predeterminada](../../extensibility/ux-guidelines/media/0303-177_tag.png "0303-177_Tag")<br />Etiqueta predeterminada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Tag.Background` |
| Primer plano (texto) | `Tag.Background` |

**Etiqueta: estado del mouse**

![Etiqueta al mantener el mouse](../../extensibility/ux-guidelines/media/0303-178_taghover.png "0303-178_TagHover")<br />Etiqueta al mantener el mouse

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Tag.HoverBackground` |
| Primer plano (texto) | `Tag.HoverBackgroundText` |

**Etiqueta: estado presionado**

![Etiqueta presionada](../../extensibility/ux-guidelines/media/0303-179_tagpressed.png "0303-179_TagPressed")<br />Etiqueta presionada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Tag.PressedBackground` |
| Primer plano (texto) | `Tag.PressedBackgroundText` |

**Etiqueta: estado seleccionado**

![Etiqueta seleccionada](../../extensibility/ux-guidelines/media/0303-180_tagselected.png "0303-180_TagSelected")<br />Etiqueta seleccionada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Tag.SelectedBackground` |
| Primer plano (texto) | `Tag.SelectedBackgroundText` |

#### <a name="close-times-tag-glyph"></a>Glifo de etiqueta Close ( &times; )

**Glifo de etiqueta Close ( &times; ) : estado predeterminado**

![Glifo de etiqueta Close ( &times; ) predeterminado](../../extensibility/ux-guidelines/media/0303-181_tagglyph.png "0303-181_TagGlyph")<br />Glifo de etiqueta Close ( &times; ) predeterminado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | N/D |
| Primer plano (glifo) | `Tag.TagHoverGlyph` |

**Glifo de etiqueta Close ( &times; ): hover state**

![Cierre &times; () el glifo de etiqueta al mantener el puntero](../../extensibility/ux-guidelines/media/0303-182_tagglyphhover.png "0303-182_TagGlyphHover")<br />Cierre &times; () el glifo de etiqueta al mantener el puntero

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Tag.TagHoverGlyphHoverBackground` |
| Primer plano (glifo) | `Tag.TagHoverGlyphHover` |
| Borde | `Tag.TagHoverGlyphHoverBorder` |

**Cierre ( &times; ) glifo de etiqueta: estado presionado**

![Glifo de etiqueta Pressed Close ( &times; )](../../extensibility/ux-guidelines/media/0303-183_tagglyphpressed.png "0303-183_TagGlyphPressed")<br />Glifo de etiqueta Pressed Close ( &times; )

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Tag.TagHoverGlyphPressedBackground` |
| Primer plano (glifo) | `Tag.TagHoverGlyphPressed` |
| Borde | `Tag.TagHoverGlyphPressedBorder` |

**Etiqueta seleccionada con glifo Cerrar ( &times; ): estado predeterminado**

![Etiqueta seleccionada predeterminada con glifo Cerrar ( &times; )](../../extensibility/ux-guidelines/media/0303-184_tagselected.png "0303-184_TagSelected")<br />Etiqueta seleccionada predeterminada con glifo Cerrar ( &times; )

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | N/D |
| Primer plano (glifo) | `Tag.TagSelectedGlyph` |

**Etiqueta seleccionada con el glifo Cerrar ( &times; ): estado del mouse**

![Etiqueta seleccionada con el glifo Cerrar ( &times; ) al mantener el puntero](../../extensibility/ux-guidelines/media/0303-185_tagselectedhover.png "0303-185_TagSelectedHover")<br />Etiqueta seleccionada con el glifo Cerrar ( &times; ) al mantener el puntero

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Tag.TagSelectedGlyphHoverBackground` |
| Primer plano (glifo) | `Tag.TagSelectedGlyphHover` |
| Borde | `Tag.TagSelectedGlyphHoverBorder` |

**Etiqueta seleccionada con glifo Cerrar ( &times; ): estado presionado**

![Etiqueta seleccionada y presionada con glifo Cerrar ( &times; )](../../extensibility/ux-guidelines/media/0303-186_tagselectedpressed.png "0303-186_TagSelectedPressed")<br />Etiqueta seleccionada y presionada con glifo Cerrar ( &times; )

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Tag.TagSelectedGlyphPressedBackground` |
| Primer plano (glifo) | `Tag.TagSelectedGlyphPressed` |
| Borde | `Tag.TagSelectedGlyphPressedBorder` |

## <a name="tool-windows"></a>Ventanas de herramientas
No es necesario replicar las ventanas de herramientas, ya que las proporciona el Visual Studio trabajo. Sin embargo, quizá prefiera aprovechar los colores que se usan en las ventanas de herramientas para que la interfaz de usuario se muestre siempre coherente con esta parte del entorno de Visual Studio.

![Ventana de herramientas (línea roja)](../../extensibility/ux-guidelines/media/0303-087_toolwindowredline.png "0303-087_ToolWindowRedline")<br />Ventana de herramientas (línea roja)

| Uso... | No use ... |
| --- | --- |
| ... en cualquier lugar en el que cree la interfaz de usuario que desee que coincida con las ventanas de herramientas. | ... para cualquier interfaz de usuario que no quiera cambiar automáticamente si el shell tiene una actualización de tema. |

### <a name="tool-window-frame"></a>Marco de ventana de herramientas
Las ventanas de herramientas de Visual Studio se usan para diversas tareas y pueden estar en uno de varios estados diferentes. Si una ventana de herramientas está abierta, se puede asignar a cualquiera de los cuatro lados del área del documento. Estas ventanas también pueden flotar fuera del IDE, lo que permite reubicarlas en cualquier lugar dentro de la pantalla del usuario. Las ventanas flotantes siempre se colocan arriba del IDE. Por último, las ventanas de herramientas se pueden acoplar como ventanas de documento y aparecen como una pestaña en el cuadro de documento. Las ventanas de herramientas que se han acoplado como ventanas de documento se colorean en parte mediante los nombres de token de ventana de documento.

![Marco de ventana de herramientas (línea roja)](../../extensibility/ux-guidelines/media/0303-088_toolwindowframeredline.png "0303-088_ToolWindowFrameRedline")<br />Marco de ventana de herramientas (línea roja)

| Uso... | No use ... |
| --- | --- |
| ...  en cualquier lugar en el que cree la interfaz de usuario que desee que coincida con las ventanas de herramientas. | ... para cualquier interfaz de usuario que no quiera cambiar automáticamente si el shell tiene una actualización de tema. |

**Ventana de herramientas acopladas**

![Ventana de herramientas acopladas](../../extensibility/ux-guidelines/media/0303-089_toolwindowdocked.png "0303-089_ToolWindowDocked")<br />Ventana de herramientas acopladas

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.ToolWindowBackground` |
| Borde | `Environment.ToolWindowBorder` |

**Ventana de herramientas flotante y centrada**

![Ventana de herramientas flotante y centrada](../../extensibility/ux-guidelines/media/0303-090_toolwindowfocused.png "0303-090_ToolWindowFocused")<br />Ventana de herramientas flotante y centrada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.ToolWindowBackground` |
| Borde | `Environment.MainWindowActiveDefaultBorder` |

**Ventana de herramientas flotantes sin foco**

![Ventana de herramientas flotantes sin foco](../../extensibility/ux-guidelines/media/0303-091_toolwindowunfocused.png "0303-091_ToolWindowUnfocused")<br />Ventana de herramientas flotantes sin foco

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.ToolWindowBackground` |
| Borde | `Environment.MainWindowInactiveBorder` |

### <a name="toolbox-like-windows"></a>Ventanas de tipo Cuadro de herramientas
El cuadro de herramientas es una de las ventanas de herramientas comunes que se usan con más frecuencia en Visual Studio. Básicamente, es un control de árbol con un tema especial y aplicación de estilos.

![Ventana de tipo cuadro de herramientas (línea roja)](../../extensibility/ux-guidelines/media/0303-189_toolboxredline.png "0303-189_ToolboxRedline")<br />Ventana de tipo cuadro de herramientas (línea roja)

| Uso... | No use ... |
| --- | --- |
| ... al diseñar una ventana de herramientas que desea que sea coherente siempre con el cuadro de herramientas del shell. | ... para cualquier cosa que no sea similar a la interfaz de usuario del cuadro de herramientas, o si no está seguro de si la interfaz de usuario tendrá problemas si cambian los colores del cuadro de herramientas del shell. |

**Nodos del cuadro de herramientas: estado predeterminado**

![Nodo primario del cuadro de herramientas predeterminado](../../extensibility/ux-guidelines/media/0303-190_toolboxparentnode.png "0303-190_ToolboxParentNode")<br />Nodo primario del cuadro de herramientas predeterminado

![Nodo secundario del cuadro de herramientas predeterminado](../../extensibility/ux-guidelines/media/0303-191_toolboxchildnode.png "0303-191_ToolboxChildNode")<br />Nodo secundario del cuadro de herramientas predeterminado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.ToolboxContent`<br />(Encabezados) |
| Información previa | `Environment.ToolWindowBackground`<br />(Elementos individuales o ventana completa si no hay controles disponibles) |
| Borde | Ninguno |
| Primer plano (glifo) | `Environment.ToolboxContent` |
| Primer plano (texto) | `Environment.ToolboxContent` |

**Nodos secundarios del cuadro de herramientas: estado del mouse**

![Nodo secundario de cuadro de herramientas al mantener el mouse](../../extensibility/ux-guidelines/media/0303-192_toolboxchildnodehover.png "0303-192_ToolboxChildNodeHover")<br />Nodo secundario de cuadro de herramientas al mantener el mouse

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.ToolboxContentMouseOver`<br />(Solo elementos individuales) |
| Borde | Ninguno |
| Primer plano (texto) | `Environment.ToolboxContentMouseOver`<br />(Solo elementos individuales) |

**Nodos seleccionados del cuadro de herramientas: estado enfocado**

![Nodo primario del cuadro de herramientas seleccionado y centrado](../../extensibility/ux-guidelines/media/0303-193_toolboxparentnodefocused.png "0303-193_ToolboxParentNodeFocused")<br />Nodo primario del cuadro de herramientas seleccionado y centrado

![Nodo secundario del cuadro de herramientas seleccionado y centrado](../../extensibility/ux-guidelines/media/0303-194_toolboxchildnodefocused.png "0303-194_ToolboxChildNodeFocused")<br />Nodo secundario del cuadro de herramientas seleccionado y centrado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `TreeView.SelectedItemActive`<br />De categoría [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Borde | `TreeView.FocusVisualBorder`<br />De categoría [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Primer plano (glifo) | `TreeView.SelectedItemActive`<br />De categoría [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Primer plano (texto) | `TreeView.SelectedItemActive`<br />De categoría [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |

**Nodos del cuadro de herramientas seleccionados: estado sin foco**

![Nodo primario del cuadro de herramientas seleccionado y sin foco](../../extensibility/ux-guidelines/media/0303-195_toolboxparentnodeunfocused.png "0303-195_ToolboxParentNodeUnfocused")<br />Nodo primario del cuadro de herramientas seleccionado y sin foco

![Nodo secundario del cuadro de herramientas seleccionado y sin foco](../../extensibility/ux-guidelines/media/0303-196_toolboxchildnodeunfocused.png "0303-196_ToolboxChildNodeUnfocused")<br />Nodo secundario del cuadro de herramientas seleccionado y sin foco

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `TreeView.SelectedItemInactive`<br />De categoría [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Borde | Ninguno |
| Primer plano (glifo) | `TreeView.SelectedItemInactive`<br />De categoría [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Primer plano (texto) | `TreeView.SelectedItemInactive`<br />De categoría [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |

### <a name="tool-window-title-bar"></a>Barra de título de la ventana de herramientas
El borde de la barra de título no es un borde verdadero, es una línea gruesa en la parte superior de la barra de título. No tiene un nombre de token para su estado sin foco.

![Barra de título de la ventana de herramientas (línea roja)](../../extensibility/ux-guidelines/media/0303-092_toolwindowtitlebarredline.png "0303-092_ToolWindowTitleBarRedline")<br />Barra de título de la ventana de herramientas (línea roja)

| Uso... | No use ... |
| --- | --- |
| ... en cualquier lugar en el que cree la interfaz de usuario que desee que coincida con las ventanas de herramientas. | ... para cualquier interfaz de usuario que no quiera cambiar automáticamente si el shell tiene una actualización de tema. |

**Barra de título con foco**

![Barra de título con foco](../../extensibility/ux-guidelines/media/0303-093_titlebarfocused.png "0303-093_TitleBarFocused")<br />Barra de título con foco

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.TitleBarActiveGradientBegin`<br />(Los delimitadores de degradado para este token no se usan en la interfaz de usuario con formato). |
| Primer plano (texto) | `Environment.TitleBarActiveText` |
| Borde | `Environment.TitleBarActiveBorder`<br />(Se establece en el mismo color que el fondo). |
| Controlador de arrastre | `Environment.TitleBarDragHandleActive` |

**Barra de título sin foco**

![Barra de título no enfocada](../../extensibility/ux-guidelines/media/0303-094_titlebarunfocused.png "0303-094_TitleBarUnfocused")<br />Barra de título sin foco

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.TitleBarInactiveGradientBegin`<br />(Los delimitadores de degradado para este token no se usan en la interfaz de usuario con formato). |
| Primer plano (texto) | `Environment.TitleBarInactiveText` |
| Borde | N/D |
| Controlador de arrastre | `Environment.TitleBarDragHandle` |

#### <a name="tool-window-title-bar-buttons"></a>Botones de la barra de título de la ventana de herramientas
![Botón de la barra de título (línea roja)](../../extensibility/ux-guidelines/media/0303-095_titlebarbuttonredline.png "0303-095_TitleBarButtonRedline")<br />Botón de la barra de título (línea roja)

| Uso... | No use ... |
| --- | --- |
| ... para los botones que aparecen en la interfaz de usuario que usa tokens de color de las barras de título de la ventana de herramientas. | ... para los botones que aparecen en otras ubicaciones. |
| | ... en cualquier combinación de fondo/primer plano que no sea la especificada. |

**Botones de barra de título centrados: estado predeterminado**

![Botones predeterminados de la barra de título centrada](../../extensibility/ux-guidelines/media/0303-096_titlebarbuttonfocused.png "0303-096_TitleBarButtonFocused")<br />Botones predeterminados de la barra de título centrada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | N/D |
| Primer plano (glifo) | `Environment.ToolWindowButtonActiveGlyph` |
| Borde | N/D |

**Botones de barra de título sin foco: estado predeterminado**

![Botones predeterminados de la barra de título sin foco](../../extensibility/ux-guidelines/media/0303-097_titlebarbuttonunfocused.png "0303-097_TitleBarButtonUnfocused")<br />Botones predeterminados de la barra de título sin foco

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | N/D |
| Primer plano (glifo) | `Environment.ToolWindowButtonInactiveGlyph` |
| Borde | N/D |

**Botones de barra de título centrados: estado del mouse**

![Botones de barra de título centrados al mantener el puntero](../../extensibility/ux-guidelines/media/0303-098_titlebarbuttonfocusedhover.png "0303-098_TitleBarButtonFocusedHover")<br />Botones de barra de título centrados al mantener el puntero

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.ToolWindowButtonHoverActive` |
| Primer plano (glifo) | `Environment.ToolWindowButtonHoverActiveGlyph` |
| Borde | `Environment.ToolWindowButtonHoverActiveBorder` |

**Botones de barra de título sin foco: estado del mouse**

![Botones de la barra de título sin foco al mantener el puntero](../../extensibility/ux-guidelines/media/0303-099_titlebarbuttonunfocusedhover.png "0303-099_TitleBarButtonUnfocusedHover")<br />Botones de la barra de título sin foco al mantener el puntero

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.ToolWindowButtonHoverInactive` |
| Primer plano (glifo) | `Environment.ToolWindowButtonHoverInactiveGlyph` |
| Borde | `Environment.ToolWindowButtonHoverInactiveBorder` |

**Botones de barra de título centrados: estado presionado**

![Botones de barra de título centrados al presionar](../../extensibility/ux-guidelines/media/0303-100_titlebarbuttonfocusedpressed.png "0303-100_TitleBarButtonFocusedPressed")<br />Botones de barra de título centrados al presionar

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.ToolWindowButtonDown` |
| Primer plano (glifo) | `Environment.ToolWindowButtonDownActiveGlyph` |
| Borde | `Environment.ToolWindowButtonDownBorder` |

**Botones de barra de título sin foco: estado presionado**

![Botones de barra de título sin foco al presionar](../../extensibility/ux-guidelines/media/0303-101_titlebarbuttonunfocusedpressed.png "0303-101_TitleBarButtonUnfocusedPressed")<br />Botones de barra de título sin foco al presionar

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.ToolWindowButtonDown` |
| Primer plano (glifo) | `Environment.ToolWindowButtonDownInactiveGlyph` |
| Borde | `Environment.ToolWindowButtonDownBorder` |

### <a name="tool-window-tabs"></a>Pestañas de ventana de herramientas
![Pestaña Ventana de herramientas (línea roja)](../../extensibility/ux-guidelines/media/0303-102_toolwindowtabredline.png "0303-102_ToolWindowTabRedline")<br />Pestaña Ventana de herramientas (línea roja)

| Uso... | No use ... |
| --- | --- |
| ... en cualquier lugar en el que cree la interfaz de usuario que desee que coincida con las ventanas de herramientas. | ... para cualquier interfaz de usuario que no quiera cambiar automáticamente si el shell tiene una actualización de tema. |

**Pestaña de ventana de herramienta seleccionada, con foco**

![Pestaña de ventana de herramienta seleccionada, con foco](../../extensibility/ux-guidelines/media/0303-103_toolwindowtabfocused.png "0303-103_ToolWindowTabFocused")<br />Pestaña de ventana de herramienta seleccionada, con foco

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.ToolWindowTabSelectedTab` |
| Primer plano (texto) | `Environment.ToolWindowTabSelectedActiveText` |
| Borde | `Environment.ToolWindowTabSelectedBorder`<br />(Se establece en el mismo color que el fondo). |

**Pestaña de ventana de herramienta seleccionada, sin foco**

![Pestaña de ventana de herramienta seleccionada, sin foco](../../extensibility/ux-guidelines/media/0303-104_toolwindowtabunfocused.png "0303-104_ToolWindowTabUnfocused")<br />Pestaña de ventana de herramienta seleccionada, sin foco

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.ToolWindowTabSelectedTab` |
| Primer plano (texto) | `Environment.ToolWindowTabSelectedText` |
| Borde | `Environment.ToolWindowTabSelectedBorder`<br />(Se establece en el mismo color que el fondo). |

**Pestaña ventana de herramientas en segundo plano: estado predeterminado**

![Pestaña de la ventana de herramientas en segundo plano predeterminada](../../extensibility/ux-guidelines/media/0303-105_toolwindowbackgroundtab.png "0303-105_ToolWindowBackgroundTab")<br />Pestaña de la ventana de herramientas en segundo plano predeterminada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.ToolWindowTabGradientBegin`<br />`Environment.ToolWindowTabGradientEnd`<br />(Los delimitadores de degradado se establecen en el mismo valor de color Visual Studio 2013). |
| Primer plano (texto) | `Environment.ToolWindowTabText` |
| Borde | `Environment.ToolWindowTabBorder` |

**Pestaña de la ventana de herramientas en segundo plano: estado del mouse**

![Pestaña de ventana de herramientas en segundo plano al mantener el puntero](../../extensibility/ux-guidelines/media/0303-106_toolwindowbackgroundtabhover.png "0303-106_ToolWindowBackgroundTabHover")<br />Pestaña de ventana de herramientas en segundo plano al mantener el puntero

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.ToolWindowTabMouseOverBackgroundBegin`<br />`Environment.ToolWindowTabMouseOverBackgroundEnd`<br />(Los delimitadores de degradado se establecen en el mismo valor de color Visual Studio 2013). |
| Primer plano (texto) | `Environment.ToolWindowTabMouseOverText` |
| Borde | `Environment.ToolWindowTabMouseOverBorder`<br />(Se establece en el mismo color que el fondo). |

### <a name="auto-hide-tabs"></a>Pestaña de ocultación automática

![Ocultar automáticamente las pestañas (línea roja)](../../extensibility/ux-guidelines/media/0303-107_autohideredline.png "0303-107_AutoHideRedline") Ocultar automáticamente las pestañas (línea roja)

| Uso... | No use ... |
| --- | --- |
| ... en cualquier lugar en el que cree la interfaz de usuario que desee que coincida con las pestañas de la ventana de herramientas ocultas automáticamente. | ... para cualquier interfaz de usuario que no quiera cambiar automáticamente si el shell tiene una actualización de tema. |

**Ocultar automáticamente las pestañas: estado predeterminado**

![Pestaña de ocultación automática predeterminada](../../extensibility/ux-guidelines/media/0303-108_autohidetab.png "0303-108_AutoHideTab")<br />Pestaña de ocultación automática predeterminada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.AutoHideTabBackgroundBegin`<br />(Los delimitadores de degradado para este token no se usan en la interfaz de usuario con formato). |
| Primer plano (texto) | `Environment.AutoHideTabText` |
| Borde | `Environment.AutoHideTabBorder` |

**Ocultar automáticamente las pestañas: estado del mouse**

![Pestaña de ocultación automática al mantener el puntero](../../extensibility/ux-guidelines/media/0303-109_autohidetabhover.png "0303-109_AutoHideTabHover")<br />Pestaña de ocultación automática al mantener el puntero

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.AutoHideTabMouseOverBackgroundBegin`<br />(Los delimitadores de degradado para este token no se usan en la interfaz de usuario con formato). |
| Primer plano (texto) | `Environment.AutoHideTabMouseOverText` |
| Borde | `Environment.AutoHideTabMouseOverBorder` |
