---
title: Compartido colores para Visual Studio | Documentos de Microsoft
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: 8d11b9a0-6175-4f2e-8e7f-79daee1bfd41
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f31912d5528c38374aafd1212767bfb850a8b976
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56723583"
---
# <a name="shared-colors-for-visual-studio"></a>Colores compartidos para Visual Studio
Cuando diseña la interfaz de usuario que utiliza elementos comunes de shell de Visual Studio, o desea que el elemento de la interfaz para que sea coherente con características similares, utilice nombres de token existentes en archivos de definición de paquete para elegir y asignar colores. Esto garantiza que la interfaz de usuario mantenga la coherencia con el entorno general de Visual Studio y que se actualice automáticamente cuando se agreguen o actualicen temas.

En este artículo se describen los elementos de interfaz de usuario comunes y los nombres de token que estos usan y a los que se puede hacer referencia al crear una interfaz de usuario similar. Para obtener información específica sobre cómo tener acceso a estos tokens de color, vea [The VSColor Service](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).

Asegúrese de usar correctamente los nombres de token:

-   **Usar nombres de token en función de la función, no en el color en Sí.** Los colores comunes compartidos están asociados a elementos específicos de la interfaz y solo están destinados para características iguales o similares. Por ejemplo, no vuelva a usar el color de un cuadro combinado presionado para una animación de progreso de giro solo porque le gusta el color. Las funciones del cuadro combinado y de la animación son diferentes, y si el color asociado con los cambios de cuadro combinado, ya no es posible un color adecuado para el elemento de animación. Un uso coherente del color ayuda a orientar a los usuarios y evitar confusiones.

-   **Usar colores de fondo y texto en la combinación correcta.** Los colores de fondo destinados para usarse con texto tendrán un color de texto asociado. No use colores de texto que no sean los que se especifican para el fondo. Si no hay un color de texto asociado, no use ese color de fondo para cualquier superficie en la que tiene pensado mostrar texto. Otras combinaciones de colores de texto y en segundo plano pueden dar lugar a una interfaz ilegible.

-   **Usar colores de control que son adecuados para su ubicación.** En determinados Estados, algunos controles de Visual Studio no tienen borde independiente y los colores de fondo. En su lugar, toman los colores de las superficies que están detrás de ellos. Procure usar siempre los nombres de token que sean adecuados para la ubicación donde coloca el control.

> [!IMPORTANT]
> No use los tokens que se encuentran en las categorías "Página de inicio" o "Cider".

## <a name="common-shared-controls"></a>Controles comunes compartidos

Cuando se usa una barra de comandos estándar de Visual Studio en su característica, tendrá acceso a los controles de shell con estilo. No debería re-template estos controles comunes. Sin embargo, si necesita crear una barra de comandos personalizada, también podría ser necesario crear controles personalizados. En ese caso, asegúrese de usar los nombres de token correctos para cada uno de los siguientes controles de modo que la interfaz de usuario sea coherente con el resto de Visual Studio.

### <a name="button-controls"></a>Controles de botón

![Límite de control de botón](../../extensibility/ux-guidelines/media/0303-155_buttoncontrolredline.png "0303 155_ButtonControlRedline")

| Utilice... | No use … |
| --- | --- |
| … para los botones del cuadro de documento que desee integrar con temas de Visual Studio (claro, oscuro, azul o un tema de contraste alto del sistema). | … para los botones que se mostrarán con un fondo personalizado que no forma parte de un tema de Visual Studio. |

**Botón: estado estándar**

![Botón estándar](../../extensibility/ux-guidelines/media/03.03.Button.Standard.png "03.03.Button.Standard")<br />Botón estándar

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Botón | `CommonControls.Button` |
| Borde de botón | `CommonControls.ButtonBorder` |

**Botón: estado predeterminado**

![Botón predeterminado](../../extensibility/ux-guidelines/media/03.03.Button.Default.png "03.03.Button.Default")<br />Botón predeterminado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Botón | `CommonControls.ButtonDefault` |
| Borde de botón | `CommonControls.ButtonBorderDefault` |

**Botón: estado deshabilitado**

![Botón deshabilitado](../../extensibility/ux-guidelines/media/03.03.Button.Disabled.png "03.03.Button.Disabled")<br />Botón deshabilitado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Botón | `CommonControls.ButtonDisabled` |
| Borde de botón | `CommonControls.ButtonBorderDisabled` |

**Botón: estado de mantener el mouse**

![Botón de desplazamiento](../../extensibility/ux-guidelines/media/03.03.Button.hover.png "03.03.Button.hover")<br />Botón al mantener el mouse

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

**Botón: estado de foco**

![Botón enfocado](../../extensibility/ux-guidelines/media/03.03.Button.Focused.png "03.03.Button.Focused")<br />Botón enfocado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Botón | `CommonControls.ButtonFocused` |
| Borde de botón | `CommonControls.ButtonBorderFocused` |

### <a name="check-box-controls"></a>Controles de casilla
![Casilla de verificación (línea roja)](../../extensibility/ux-guidelines/media/0303-161_checkboxredline.png "0303 161_CheckboxRedline")<br />Casilla de verificación (límite)

| Utilice... | No use … |
| --- | --- |
| ... en los controles de casilla de verificación incluidos en el documento también. | … para cualquier interfaz de usuario que no es un control de casilla de verificación. |

**Casilla de verificación: estado predeterminado**

![Casilla de verificación](../../extensibility/ux-guidelines/media/0303-162_checkbox.png "0303 162_Checkbox")<br />Casilla de verificación de forma predeterminada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `CommonControls.CheckBoxBackground` |
| Borde | `CommonControls.CheckBoxBorder` |
| Texto | `CommonControls.CheckBoxText` |
| Glifo | `CommonControls.CheckBoxGlyph` |

**Casilla de verificación: estado deshabilitado**

![Casilla de verificación deshabilitada](../../extensibility/ux-guidelines/media/0303-163_checkboxdisabled.png "0303 163_CheckboxDisabled")<br />Casilla de verificación deshabilitada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `CommonControls.CheckBoxBackgroundDisabled` |
| Borde | `CommonControls.CheckBoxBorderDisabled` |
| Texto | `CommonControls.CheckBoxTextDisabled` |
| Glifo | `CommonControls.CheckBoxGlyphDisabled` |

**Casilla de verificación: mantenga el puntero de estado**

 ![Casilla de verificación al mantener el mouse](../../extensibility/ux-guidelines/media/0303-164_checkboxhover.png "0303 164_CheckboxHover")<br />Casilla de verificación al mantener el mouse

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `CommonControls.CheckBoxBackgroundHover` |
| Borde | `CommonControls.CheckBoxBorderHover` |
| Texto | `CommonControls.CheckBoxTextHover` |
| Glifo | `CommonControls.CheckBoxGlyphHover` |

**Casilla de verificación: estado presionado**

![Casilla de verificación presionada](../../extensibility/ux-guidelines/media/0303-165_checkboxpressed.png "0303 165_CheckboxPressed")<br />Casilla de verificación presionada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `CommonControls.CheckBoxBackgroundPressed` |
| Borde | `CommonControls.CheckBoxBorderPressed` |
| Texto | `CommonControls.CheckBoxTextPressed` |
| Glifo | `CommonControls.CheckBoxGlyphPressed` |

**Casilla de verificación: centra el estado**

![Casilla de verificación centrado](../../extensibility/ux-guidelines/media/0303-166_checkboxfocused.png "0303 166_CheckboxFocused")<br />Casilla de verificación con foco

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `CommonControls.CheckBoxBackgroundFocused` |
| Borde | `CommonControls.CheckBoxBorderFocused` |
| Texto | `CommonControls.CheckBoxTextFocused` |
| Glifo | `CommonControls.CheckBoxGlyphFocused` |

### <a name="drop-downs-and-combo-boxes"></a>Listas desplegables y combinado cuadros
![Drop-down/combo box (redline)](../../extensibility/ux-guidelines/media/0303-167_dropdowncomboboxredline.png "0303-167_DropDownComboBoxRedline")<br />Lista desplegable o cuadro combinado (límite)

| Utilice... | No use … |
| --- | --- |
| … para listas desplegables y combinado cuadros en el documento también. | … para cualquier interfaz de usuario que no es una lista desplegable o cuadro combinado. |
| | ... por la barra de comandos [listas desplegables](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown) o [cuadros combinados](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox). |

**Listas desplegables y combinado cuadros: estado predeterminado**

![Predeterminada lista desplegable o cuadro combinado](../../extensibility/ux-guidelines/media/0303-168_dropdowncombobox.png "0303 168_DropDownComboBox")<br />Predeterminada lista desplegable o cuadro combinado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `CommonControls.ComboBoxBackground` |
| Borde | `CommonControls.ComboBoxBorder` |
| Texto | `CommonControls.ComboBoxText` |
| Separador | `CommonControls.ComboBoxSeparator` |
| Glifo | `CommonControls.ComboBoxGlyph` |
| Fondo de glifo | `CommonControls.ComboBoxGlyphBackground` |

**Listas desplegables y combinado cuadros: estado deshabilitado**

![Deshabilitado lista desplegable o cuadro combinado](../../extensibility/ux-guidelines/media/0303-169_dropdowncomboboxdisabled.png "0303 169_DropDownComboBoxDisabled")<br />Deshabilitado lista desplegable o cuadro combinado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `CommonControls.ComboBoxBackgroundDisabled` |
| Borde | `CommonControls.ComboBoxBorderDisabled` |
| Texto | `CommonControls.ComboBoxTextDisabled` |
| Separador | `CommonControls.ComboBoxSeparatorDisabled` |
| Glifo | `CommonControls.ComboBoxGlyphDisabled` |
| Fondo de glifo | `CommonControls.ComboBoxGlyphBackgroundDisabled` |

**Listas desplegables y combinado cuadros: mantenga el puntero de estado**

![Lista desplegable o cuadro combinado al mantener el mouse](../../extensibility/ux-guidelines/media/0303-170_dropdowncomboboxhover.png "0303 170_DropDownComboBoxHover")<br />Desplegable o cuadro combinado al mantener el mouse

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `CommonControls.ComboBoxBackgroundHover` |
| Borde | `CommonControls.ComboBoxBorderHover` |
| Texto | `CommonControls.ComboBoxTextHover` |
| Separador | `CommonControls.ComboBoxSeparatorHover` |
| Glifo | `CommonControls.ComboBoxGlyphHover` |
| Fondo de glifo | `CommonControls.ComboBoxGlyphBackgroundHover` |

**Listas desplegables y combinado cuadros: estado presionado**

![Pressed drop-down/combo box](../../extensibility/ux-guidelines/media/0303-171_dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")<br />Presiona la lista desplegable o cuadro combinado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `CommonControls.ComboBoxBackgroundPressed` |
| Borde | `CommonControls.ComboBoxBorderPressed` |
| Texto | `CommonControls.ComboBoxTextPressed` |
| Separador | `CommonControls.ComboBoxSeparatorPressed` |
| Glifo | `CommonControls.ComboBoxGlyphPressed` |
| Fondo de glifo | `CommonControls.ComboBoxGlyphBackgroundPressed` |

**Vista de elemento de lista de cuadros de listas desplegables y combinado: estado presionado**

 ![Colocar-desplegable o cuadro combinado presionado de la vista de elemento de lista](../../extensibility/ux-guidelines/media/0303-174_dropdowncomboboxlistview.png "0303 174_DropDownComboBoxListView")<br />Colocar-desplegable o cuadro combinado presionado de la vista de elemento de lista

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `CommonControls.ComboBoxListBackground`<br />`CommonControls.ComboBoxListBackgroundHover`<br />`CommonControls.ComboBoxListItemBackgroundPressed`<br />`CommonControls.ComboBoxListItemBackgroundFocused` |
| Borde | `CommonControls.ComboBoxListBorder`<br />`CommonControls.ComboBoxListBorderHover`<br />`CommonControls.ComboBoxListBorderPressed`<br />`CommonControls.ComboBoxListBorderFocused` |
| Texto del elemento | `CommonControls.ComboBoxListItemText`<br /> `CommonControls.ComboBoxListItemTextHover`<br />`CommonControls.ComboBoxListItemTextPressed`<br />`CommonControls.ComboBoxListItemTextFocused` |
| Sombra de fondo | `CommonControls.ComboBoxListBackgroundShadow` |

**Listas desplegables y combinado cuadros: centra el estado**

![Lista de desplegable o cuadro combinado con el foco](../../extensibility/ux-guidelines/media/0303-172_dropdowncomboboxfocused.png "0303 172_DropDownComboBoxFocused")<br />Lista de desplegable o cuadro combinado con foco

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `CommonControls.ComboBoxBackgroundFocused` |
| Borde | `CommonControls.ComboBoxBorderFocused` |
| Texto | `CommonControls.ComboBoxTextFocused` |
| Separador | `CommonControls.ComboBoxSeparatorFocused` |
| Glifo | `CommonControls.ComboBoxGlyphFocused` |
| Fondo de glifo | `CommonControls.ComboBoxGlyphBackgroundFocused` |

**Listas desplegables y combinado cuadros: selección de entrada de texto**

![Drop-down/combo box text input selection](../../extensibility/ux-guidelines/media/0303-173_dropdowncomboboxtextinput.png "0303-173_DropDownComboBoxTextInput")<br />Selección de entrada de texto de la lista desplegable o cuadro combinado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Resaltar | `CommonControls.ComboBoxTextInputSelection` |

### <a name="tabular-data-grid-controls"></a>Controles de datos tabulares (cuadrícula)
Los controles de datos tabulares, también conocidos como controles de cuadrícula, son controles comunes de Visual Studio que se pueden usar para presentar grandes cantidades de datos en varias columnas. Los controles estándar de datos tabulares están en varias ubicaciones de Visual Studio: la ventana de herramientas Lista de errores, los informes de IntelliTrace y la vista de montón de memoria, entre otros. Use siempre los controles de datos tabulares estándar que se proporcionan. En raras ocasiones, podría no tener acceso a los controles estándar de datos tabulares. En estos casos, use los siguientes nombres de token para asegurarse de que la interfaz de usuario sea coherente con otros controles de datos tabulares de Visual Studio.

![Control de cuadrícula o datos tabulares (línea roja)](../../extensibility/ux-guidelines/media/0303-197_tabulardatagridcontrolredline.png "0303 197_TabularDataGridControlRedline")<br />Control de cuadrícula o datos tabulares (límite)

| Utilice... | No use … |
| --- | --- |
| ... por tabular o controles de cuadrícula. | … para cualquier interfaz de usuario que no es un control tabular o de cuadrícula. |

#### <a name="column-headers"></a>Encabezados de columna
Los encabezados de columna constan de un fondo, un borde, el texto del título y un glifo opcional que suele usarse cuando se ordena una cuadrícula por esa columna.

**Encabezado de columna: estado predeterminado**

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `Header.Default` |
| Primer plano (texto) | `Environment.CommandBarTextActive` |
| Primer plano (glifo) | `Header.Glyph` |
| Borde | `Header.SeparatorLine` |

**Encabezado de columna: mantenga el puntero de estado**

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `Header.MouseOver` |
| Primer plano (texto) | `Environment.CommandBarTextHover` |
| Primer plano (glifo) | `Header.MouseOverGlyph` |
| Borde | `Header.SeparatorLine` |

**Encabezado de columna: estado presionado**

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `CommonControls.CheckBoxBackgroundPressed` |
| Primer plano (texto) | `CommonControls.CheckBoxBorderPressed` |
| Primer plano (glifo) | `CommonControls.CheckBoxTextPressed` |
| Borde | `CommonControls.CheckBoxGlyphPressed` |

#### <a name="list-view-items"></a>Elementos de vista lista
 Los elementos de vista de lista constan de un fondo y el contenido. El contenido puede ser texto, un icono o ambos.

**Los elementos de vista de lista: estado predeterminado**

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | Transparente |
| Primer plano (texto) | `Environment.CommandBarTextActive` |
| Borde | Ninguna |

**Los elementos de vista de lista: estado activo**

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `TreeView.SelectedItemActive` |
| Primer plano (texto) | `TreeView.SelectedItemActiveText` |
| Borde | Ninguna |

**Los elementos de vista de lista: estado inactivo**

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `TreeView.SelectedItemInactive` |
| Primer plano (texto) | `TreeView.SelectedItemInactiveText` |
| Borde | Ninguna |

### <a name="ui-text"></a>Texto de la interfaz de usuario

#### <a name="instructional-text"></a>Texto informativo
Texto informativo ofrece una explicación principal destacada de qué hacer en una página del cuadro de diálogo o documento.

![Texto informativo predeterminado](../../extensibility/ux-guidelines/media/0303_InstructionalText.png "0303_InstructionalText.png")<br />Texto predeterminado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Primer plano (texto) | `Environment.ControlText` |

#### <a name="secondary-instructional-text"></a>Texto informativo secundaria
En las páginas del documento con una gran cantidad de texto y controles, texto informativo utiliza un valor de color diferente. Esto ayuda a transmitir información que es más importante y reducir la densidad de los elementos de interfaz de usuario. (Vea también la siguiente sección en el texto de sugerencia.)

![Texto informativo secundaria](../../extensibility/ux-guidelines/media/0303_SecondaryInstructionalText.png "0303_SecondaryInstructionalText.png")<br />Texto informativo secundaria

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Primer plano (texto) | `Environment.ControlEditHintText` |

#### <a name="hint-text"></a>Texto de sugerencia
Texto de sugerencia aparece en un control vacío, debajo de un control o en una superficie del documento vacío para mostrar al usuario qué hacer a continuación. Puede usar el texto de sugerencia con fondos de ventana o Control.

**Texto de sugerencia predeterminado**

![Texto de sugerencia predeterminado](../../extensibility/ux-guidelines/media/0303_HintText.png "0303_HintText.png")<br />Texto de sugerencia predeterminado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Primer plano (texto) | `Environment.ControlEditHintText` |

**Texto de sugerencia que requiere**

![El texto de sugerencia requerido](../../extensibility/ux-guidelines/media/0303_RequiredHintText.png "0303_RequiredHintText.png")<br />Texto de sugerencia que requiere

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Primer plano (texto) | `Environment.ControlRequiredHintText` |
| Fondo | `Environment.ControlRequiredBackground` |

**Texto del control de cuadro de búsqueda**

> Consulte [cuadros de búsqueda](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_SearchBoxes) para otros tokens de color relacionados con el control de búsqueda.

![Texto del control de cuadro de búsqueda](../../extensibility/ux-guidelines/media/0303_SearchBoxControl.png "0303_SearchBoxControl.png")<br />Texto del control de cuadro de búsqueda

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Primer plano (texto) | `SearchControl.UnfocusedWatermarkText` |

### <a name="hyperlink"></a>Hipervínculo
El hipervínculo es un control que no tiene un par de primer plano y fondo. En todos los casos, use el color de hipervínculo de primer plano, que se muestre adecuadamente en fondos oscuros, grises y blancos. Si no usa el token de color para el control de hipervínculo, verá el color predeterminado del sistema para "pressed", que parpadeará en rojo. Que es la señal de que el control no está usando el token de color correcto del entorno.

![Hyperlink (redline)](../../extensibility/ux-guidelines/media/0303-133_hyperlinkredline.png "0303-133_HyperlinkRedline")<br />Hipervínculo (límite)

| Utilice... | No use … |
| --- | --- |
| ... cuando necesite crear un hipervínculo personalizado. | ... por cualquier cosa que no es un hipervínculo. |

**Hipervínculo: estado predeterminado**

![Hipervínculo predeterminado](../../extensibility/ux-guidelines/media/0303-134_hyperlink.png "0303 134_Hyperlink")<br />Hipervínculo predeterminado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Primer plano (texto) | `Environment.PanelHyperlink` |

**Hipervínculo: estado de desplazamiento**

![Hipervínculo al mantener el mouse](../../extensibility/ux-guidelines/media/0303-135_hyperlinkhover.png "0303 135_HyperlinkHover")<br />Hipervínculo al mantener el mouse

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Primer plano (texto) | `Environment.PanelHyperlinkHover` |

**Hipervínculo: estado presionado**

![Pressed hyperlink](../../extensibility/ux-guidelines/media/0303-136_hyperlinkpressed.png "0303-136_HyperlinkPressed")<br />Hipervínculo presionado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Primer plano (texto) | `Environment.PanelHyperlinkPressed` |

**Hipervínculo: estado de deshabilitado**

![Hipervínculo deshabilitado](../../extensibility/ux-guidelines/media/0303-137_hyperlinkdisabled.png "0303 137_HyperlinkDisabled")<br />Hipervínculo deshabilitado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Primer plano (texto) | `Environment.PanelHyperlinkDisabled` |

### <a name="infobars"></a>Infobars
Las barras de información se usan para proporcionar más información sobre un determinado contexto y siempre se muestran en la parte superior de una ventana de documento o una ventana de herramientas.

![Infobar (redline)](../../extensibility/ux-guidelines/media/0303-138_infobarredline.png "0303-138_InfobarRedline")<br />Infobar (redline)

| Utilice... | No use … |
| --- | --- |
| ... al crear barras de información personalizadas. | … para elementos de interfaz de usuario que no son similares a una barra de información. |

**La barra de información: estado predeterminado**

![Predeterminado de la barra de información](../../extensibility/ux-guidelines/media/0303-139_infobar.png "0303 139_Infobar")<br />Barra de información de forma predeterminada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `InfoBar.InfoBarBackground` |
| Primer plano (texto) | `InfoBar.InfoBar` |
| Borde | `InfoBar.InfoBarBorder` |

**Cerrar barra de información (&times;) botón: estado predeterminado**

![Cerrar barra de información de predeterminado (&times;) botón](../../extensibility/ux-guidelines/media/0303_InfobarCloseDefault.png "0303_InfobarCloseDefault.png")<br />Cerrar barra de información de predeterminado (&times;) botón

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `InfoBar.CloseButton` |
| Borde | `InfoBar.CloseButtonBorder` |
| Glifo | `InfoBar.CloseButtonGlyph` |

**Cerrar barra de información (&times;) botón: mantenga el puntero de estado**

![Cerrar barra de información (&times;) botón al mantener el mouse](../../extensibility/ux-guidelines/media/0303_InfobarCloseHover.png "0303_InfobarCloseHover.png")<br />Cerrar barra de información (&times;) botón al mantener el mouse

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `InfoBar.CloseButtonHover` |
| Borde | `InfoBar.CloseButtonHoverBorder` |
| Glifo | `InfoBar.CloseButtonHoverGlyph` |

**Cerrar barra de información (&times;) botón: estado presionado**

![Presiona la barra de información de cierre (&times;) botón](../../extensibility/ux-guidelines/media/0303_InfobarClosePressed.png "0303_InfobarClosePressed.png")<br />Presiona la barra de información de cierre (&times;) botón

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `InfoBar.CloseButtonDown` |
| Borde | `InfoBar.CloseButtonDownBorder` |
| Glifo | `InfoBar.CloseButtonDownGlyph` |

**Botón de hipervínculo de la barra de información: estado predeterminado**

![Botón de hipervínculo de barra de información predeterminada](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonDefault.png "0303_InfobarHyperlinkButtonDefault.png")<br />Botón de la barra de información hipervínculo predeterminado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Primer plano (texto) | `InfoBar.Hyperlink` |

**Botón de hipervínculo de la barra de información: mantenga el puntero de estado**

![Botón de hipervínculo de la barra de información al mantener el mouse](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonHover.png "0303_InfobarHyperlinkButtonHover.png")<br />Botón de hipervínculo de la barra de información al mantener el mouse

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Primer plano (texto) | `Infobar.HyperlinkMouseOver`<br />(Con subrayado) |

**Botón de hipervínculo de la barra de información: estado presionado**

![Botón de hipervínculo de la barra de información presionado](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonPressed.png "0303_InfobarHyperlinkButtonPressed.png")<br />Botón de hipervínculo presionado de la barra de información

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Primer plano (texto) | `Infobar.HyperlinkMouseDown`<br />(Con subrayado) |

**Barra de información en línea hyperlink (dentro de una frase): estado predeterminado**

![Botón de hipervínculo de barra de información de forma predeterminada en línea](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonDefault.png "0303_InfobarHyperlinkButtonDefault.png")<br />Botón de hipervínculo de barra de información de forma predeterminada en línea

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Primer plano (texto) | `InfoBar.Hyperlink` |

**Barra de información en línea hyperlink (dentro de una frase): mantenga el puntero de estado**

![Botón de barra de información en línea hyperlink al mantener el mouse](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkInlineHover.png "0303_InfobarHyperlinkInlineHover.png")<br />Botón de barra de información en línea hyperlink al mantener el mouse

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Primer plano (texto) | `Infobar.HyperlinkMouseOver`<br />(Con subrayado) |

**Barra de información en línea hyperlink (dentro de una frase): estado presionado**

![Botón de hipervínculo presionado de la barra de información en línea](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkInlinePressed.png "0303_InfobarHyperlinkInlinePressed.png")<br />Presiona el botón de barra de información en línea hyperlink

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Primer plano (texto) | `Infobar.HyperlinkMouseDown`<br />(Con subrayado) |

**Botón de barra de información: estado predeterminado**

![Botón de barra de información predeterminado](../../extensibility/ux-guidelines/media/0303_InfobarButtonDefault.png "0303_InfobarButtonDefault.png")<br />Botón de barra de información de forma predeterminada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `InfoBar.Button` |
| Primer plano (texto) | `InfoBar.Button` |
| Borde | `InfoBar.ButtonBorder` |

**Botón de barra de información: mantenga el puntero de estado**

![Botón de barra de desplazamiento](../../extensibility/ux-guidelines/media/0303_InfobarButtonHover.png "0303_InfobarButtonHover.png")<br />Botón de barra de desplazamiento

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `InfoBar.ButtonMouseOver` |
| Primer plano (texto) | `InfoBar.ButtonMouseOver` |
| Borde | `InfoBar.ButtonMouseOverBorder` |

**Botón de barra de información: estado presionado**

![Botón de barra de información presionado](../../extensibility/ux-guidelines/media/0303_InfobarButtonPressed.png "0303_InfobarButtonPressed.png")<br />Botón presionado de la barra de información

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `InfoBar.ButtonMouseDown` |
| Primer plano (texto) | `InfoBar.ButtonMouseDown` |
| Borde | `InfoBar.ButtonMouseDownBorder` |

**Botón de barra de información: estado deshabilitado**

![Botón de barra de información deshabilitado](../../extensibility/ux-guidelines/media/0303_InfobarButtonDisabled.png "0303_InfobarButtonDisabled.png")<br />Botón de barra de información deshabilitado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `InfoBar.ButtonDisabled` |
| Primer plano (texto) | `InfoBar.ButtonDisabled` |
| Borde | `InfoBar.ButtonDisabledBorder` |

**Botón de barra de información: centra el estado**

![Botón de barra de información con foco](../../extensibility/ux-guidelines/media/0303_InfobarButtonFocus.png "0303_InfobarButtonFocus.png")<br />Botón de barra de información con foco

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `InfoBar.ButtonFocus` |
| Primer plano (texto) | `InfoBar.ButtonFocus` |
| Borde | `InfoBar.ButtonFocusBorder` |

### <a name="scroll-bars"></a>Barras de desplazamiento
Las barras de desplazamiento se aplica el estilo del entorno de Visual Studio y no necesitan ser temáticas. Sin embargo, puede decidir desea aprovechar los colores utilizados en las barras de desplazamiento para que la interfaz de usuario se muestre siempre coherente con esta parte del entorno de Visual Studio.

![Barra de desplazamiento (línea roja)](../../extensibility/ux-guidelines/media/0303-140_scrollbarredline.png "0303 140_ScrollbarRedline")<br />Barra de desplazamiento (límite)

| Utilice... | No use … |
| --- | --- |
| ... cuando se crea la interfaz de usuario que desea hacer coincidir las barras de desplazamiento de Visual Studio. | … para nada que no desea que siempre coincida con la interfaz de usuario de la barra de desplazamiento. |

**Barra de desplazamiento: estado predeterminado**

![Barra de desplazamiento predeterminado](../../extensibility/ux-guidelines/media/0303-141_scrollbar.png "0303 141_Scrollbar")<br />Barra de desplazamiento de forma predeterminada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Barra de desplazamiento | `Environment.ScrollBarBackground` |
| Primer plano (control) | `Environment.ScrollBarThumbBackground` |

**Barra de desplazamiento: mantenga el puntero de estado**

![Barra de desplazamiento al mantener el mouse](../../extensibility/ux-guidelines/media/0303-143_scrollbarhover.png "0303 143_ScrollbarHover")<br />Barra de desplazamiento al mantener el mouse

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Barra de desplazamiento | `Environment.ScrollBarBackground` |
| Primer plano (control) | `Environment.ScrollBarThumbMouseOverBackground` |

*Barra de desplazamiento: estado presionado**

![Barra de desplazamiento presionada](../../extensibility/ux-guidelines/media/0303-145_scrollbarpressed.png "0303 145_ScrollbarPressed")<br />Presiona la barra de desplazamiento

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Barra de desplazamiento | `Environment.ScrollBarBackground` |
| Primer plano (control) | `Environment.ScrollBarThumbPressedBackground` |

**Flecha de barra de desplazamiento: estado predeterminado**

![Flecha de barra de desplazamiento predeterminado](../../extensibility/ux-guidelines/media/0303-142_scrollbararrow.png "0303 142_ScrollbarArrow")<br />Flecha de barra de desplazamiento predeterminado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `Environment.ScrollBarArrowBackground`<br />(Establecer en el mismo color como la barra de desplazamiento). |
| Primer plano (glifo) | `Environment.ScrollBarArrowGlyph` |

**Flecha de barra de desplazamiento: mantenga el puntero de estado**

![Flecha de desplazamiento de la barra de desplazamiento](../../extensibility/ux-guidelines/media/0303-144_scrollbararrowhover.png "0303 144_ScrollbarArrowHover")<br />Flecha de barra de desplazamiento al mantener el mouse

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `Environment.ScrollBarArrowMouseOverBackground`<br />(Establecer en el mismo color como la barra de desplazamiento). |
| Primer plano (glifo) | `Environment.ScrollBarArrowGlyphMouseOver` |

**Flecha de barra de desplazamiento: estado presionado**

![Flecha de la barra de desplazamiento presionada](../../extensibility/ux-guidelines/media/0303-146_scrollbararrowpressed.png "0303 146_ScrollbarArrowPressed")<br />Presiona la flecha de la barra de desplazamiento

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `Environment.ScrollBarArrowPressedBackground`<br />(Establecer en el mismo color como la barra de desplazamiento). |
| Primer plano (glifo) | `Environment.ScrollBarArrowGlyphPressed` |

### <a name="BKMK_SearchBoxes"></a>Cuadros de búsqueda
Siempre que sea posible, use el control de búsqueda común proporcionado por el entorno de Visual Studio. Los colores del cuadro de búsqueda se encuentran en la categoría "SearchControl" del archivo **ShellColors.pkgdef** , que contiene los nombres de token para el campo de entrada, el botón de acción, el botón desplegable y el menú desplegable.

Un cuadro de búsqueda puede tener uno de varios estados, algunos de los cuales son mutuamente excluyentes:

-   "Con foco" o "sin foco" se refiere a si el cursor está en el cuadro de texto.

-   "Activo" o "inactivo" se refiere a si el usuario ha especificado una consulta de búsqueda en el cuadro de texto.

-   "Desplazar el puntero" significa que el usuario ha colocado el puntero sobre el cuadro de búsqueda con el mouse (este estado invalida todos los demás estados).

-   "Deshabilitado" significa que la función de búsqueda se ha desactivado para el contexto actual.

![Search box (redline)](../../extensibility/ux-guidelines/media/0303-110_searchboxredline.png "0303-110_SearchBoxRedline")<br />Cuadro de búsqueda (límite)

| Utilice... | No use … |
| --- | --- |
| ... cuando diseña un cuadro de búsqueda personalizada. | ... por cualquier cosa que no es un cuadro de búsqueda. |
| | ... cualquier cosa que no desea que siempre coincida con la búsqueda de cuadro de la interfaz de usuario. |

**Centra el campo de entrada de búsqueda**

![Campo de entrada de búsqueda centrada en](../../extensibility/ux-guidelines/media/0303-111_searchinputfieldfocused.png "0303 111_SearchInputFieldFocused")<br />Centra el campo de entrada de búsqueda

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `SearchControl.FocusedBackground` |
| Primer plano (texto) | `SearchControl.FocusedBackground` |
| Borde | `SearchControl.FocusedBorder` |
| Separador | `SearchControl.FocusedDropDownSeparator` |

**Campo de entrada de búsqueda no enfocado activo**

![Campo de entrada de búsqueda no enfocado](../../extensibility/ux-guidelines/media/0303-114_searchinputfieldunfocused.png "0303 114_SearchInputFieldUnfocused")<br />Campo de entrada de búsqueda no enfocado activo

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `SearchControl.SearchActiveBackground` |
| Primer plano (texto) | `SearchControl.SearchActiveBackground` |
| Borde | `SearchControl.UnfocusedBorder` |
| Separador | `SearchControl.DropDownSeparator` |

**Campo de entrada de búsqueda no enfocado e inactivo**

![Campo de entrada de búsqueda no enfocado e inactivo](../../extensibility/ux-guidelines/media/0303-114-1_searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br />Campo de entrada de búsqueda no enfocado e inactivo

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `SearchControl.Unfocused` |
| Primer plano (texto) | `SearchControl.Unfocused` |
| Borde | `SearchControl.UnfocusedBorder` |
| Separador | `SearchControl.DropDownSeparator` |

**Campo de entrada de búsqueda resaltado (solo texto)**

![Campo de entrada de búsqueda resaltado](../../extensibility/ux-guidelines/media/0303-120_searchinputfieldhighlight.png "0303 120_SearchInputFieldHighlight")<br />Campo de entrada de búsqueda resaltado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `SearchControl.Selection` |
| Primer plano (texto) | `SearchControl.FocusedBackground` |
| Borde | Ninguna |
| Separador | `SearchControl.FocusedDropDownSeparator` |

**Campo de entrada de búsqueda deshabilitado**

![Campo de entrada de búsqueda deshabilitado](../../extensibility/ux-guidelines/media/0303-121_searchinputfielddisabled.png "0303 121_SearchInputFieldDisabled")<br />Campo de entrada de búsqueda deshabilitado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `SearchControl.Disabled` |
| Primer plano (texto) | `SearchControl.Disabled` |
| Borde | `SearchControl.DisabledBorder` |
| Separador | `SearchControl.DropDownSeparator` |

**Botón de acción de búsqueda enfocado**

![Botón de acción de búsqueda enfocado](../../extensibility/ux-guidelines/media/0303-112_searchactionbuttonfocused.png "0303 112_SearchActionButtonFocused")<br />Botón de acción de búsqueda enfocado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | Ninguna |
| Primer plano (glifo de búsqueda) | `SearchControl.SearchGlyph` |
| Primer plano (glifo de detención) | `SearchControl.StopGlyph` |
| Primer plano (glifo de borrado) | `SearchControl.ClearGlyph` |
| Borde | N/D |

**Botón de acción de búsqueda no enfocado**

![Botón de acción de búsqueda no enfocado](../../extensibility/ux-guidelines/media/0303-115_searchactionbuttonunfocused.png "0303 115_SearchActionButtonUnfocused")<br />Botón de acción de búsqueda no enfocado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | N/D |
| Primer plano (glifo de búsqueda) | `SearchControl.SearchGlyph` |
| Primer plano (glifo de detención) | `SearchControl.StopGlyph` |
| Primer plano (glifo de borrado) | `SearchControl.ClearGlyph` |
| Borde | N/D |

**Botón de acción de búsqueda presionado**

![Botón de acción de búsqueda presionado](../../extensibility/ux-guidelines/media/0303-116-1_searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")<br />Botón de acción de búsqueda presionado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `SearchControl.ActionButtonMouseDown` |
| Primer plano (glifo) | `SearchControl.ActionButtonMouseDownGlyph` |
| Borde | `SearchControl.ActionButtonMouseDownBorder` |

**Botón de acción de búsqueda deshabilitado**

![Botón de acción de búsqueda deshabilitado](../../extensibility/ux-guidelines/media/0303-122_searchactionbuttondisabled.png "0303 122_SearchActionButtonDisabled")<br />Botón de acción de búsqueda deshabilitado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | Ninguna |
| Primer plano (glifo) | `SearchControl.ActionButtonDisabledGlyph` |
| Borde | Ninguna |

**Botón de lista desplegable de búsqueda enfocado**

![Botón de lista desplegable de búsqueda centrada en](../../extensibility/ux-guidelines/media/0303-113_searchdropdownbuttonfocused.png "0303 113_SearchDropdownButtonFocused")<br />Botón de lista desplegable de búsqueda enfocado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `SearchControl.FocusedDropDownButton` |
| Primer plano (glifo) | `SearchControl.FocusedDropDownButtonGlyph` |
| Borde | `SearchControl.FocusedDropDownButtonBorder` |

**Botón de lista desplegable de búsqueda no enfocado**

![Botón de lista desplegable de búsqueda no enfocado](../../extensibility/ux-guidelines/media/0303-116_searchdropdownbuttonunfocused.png "0303 116_SearchDropdownButtonUnfocused")<br />Botón de lista desplegable de búsqueda no enfocado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `SearchControl.UnfocusedDropDownButton` |
| Primer plano (glifo) | `SearchControl.UnfocusedDropDownButtonGlyph` |
| Borde | `SearchControl.UnfocusedDropDownButtonBorder` |

**Presiona el botón de lista desplegable de búsqueda**

![Botón de lista desplegable de búsqueda presionado](../../extensibility/ux-guidelines/media/0303-116-2_searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")<br />Presiona el botón de lista desplegable de búsqueda

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `SearchControl.MouseDownDropDownButton` |
| Primer plano (glifo) | `SearchControl.MouseDownDropDownButtonGlyph` |
| Borde | `SearchControl.MouseDownDropDownButtonBorder` |

**Botón de lista desplegable de búsqueda deshabilitado**

![Botón desplegable de búsqueda deshabilitado](../../extensibility/ux-guidelines/media/0303-123_searchdropdownbuttondisabled.png "0303 123_SearchDropdownButtonDisabled")<br />Botón de lista desplegable de búsqueda deshabilitado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | Ninguna |
| Primer plano (glifo) | `SearchControl.DisabledDownButtonGlyph` |
| Borde | Ninguna |

#### <a name="search-drop-down-lists"></a>Listas desplegables de búsqueda
El menú de lista desplegable del cuadro de búsqueda tiene el potencial para verse ligeramente más complejo que otros menús desplegables en Visual Studio. Las secciones de "opciones de búsqueda" y "búsquedas sugeridas" pueden aparecer por sí solos o en el menú, y cada una de ellas se colorea por separado. Además, estas secciones están separadas por una línea cuando aparecen juntas y un borde rodea todo el menú desplegable.

![Lista desplegable de búsqueda (línea roja)](../../extensibility/ux-guidelines/media/0303-124_searchdropdownredline.png "0303 124_SearchDropdownRedline")<br />Lista desplegable de búsqueda (límite)

| Utilice... | No use … |
| --- | --- |
| ... cuando va a crear una lista desplegable de búsqueda personalizada. | ... para las listas desplegables que aparecen en otros contextos. |
| ... los nombres de token correctos para los componentes de la lista correcta. | ... en cualquier combinación de primer plano y fondo distinto del especificado. |

**Elementos de lista desplegable de búsqueda**

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Borde | `SearchControl.PopupBorder` |
| Separador | `SearchControl.PopupSectionHeaderSeparator` |
| Sombra | `Environment.DropShadowBackground` |

**Sugiere búsquedas: estado predeterminado**

![Default búsquedas sugeridas](../../extensibility/ux-guidelines/media/0303-125_searchsuggested.png "0303 125_SearchSuggested")<br />Sugerencias de búsqueda de predeterminado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `SearchControl.PopupItemsListBackgroundGradientBegin`<br />(Delimitadores de degradado para este token que no se usa en la interfaz de usuario con tema.) |
| Primer plano (texto) | `SearchControl.PopupItemText` |

**Sugiere búsquedas: mantenga el puntero de estado**

![Sugiere búsquedas al mantener el mouse](../../extensibility/ux-guidelines/media/0303-128_searchsuggestedhover.png "0303 128_SearchSuggestedHover")<br />Sugerencias de búsqueda al mantener el mouse

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br />(Delimitadores de degradado para este token que no se usa en la interfaz de usuario con tema.) |
| Primer plano (texto) | `SearchControl.PopupMouseOverItemText` |
| Borde | `SearchControl.PopupControlMouseOverBorder` |

**Las opciones de búsqueda: estado predeterminado**

![Casilla de verificación de búsqueda](../../extensibility/ux-guidelines/media/0303-126_searchcheckbox.png "0303 126_SearchCheckbox")<br />Opciones predeterminadas de búsqueda (casilla)

![Las opciones de búsqueda](../../extensibility/ux-guidelines/media/0303-127_searchoptions.png "0303 127_SearchOptions")<br />Opciones predeterminadas de búsqueda (vínculo)

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `SearchControl.PopupSectionBackgroundGradientBegin`<br />(Delimitadores de degradado para este token que no se usa en la interfaz de usuario con tema.) |
| Primer plano (texto de casilla) | `SearchControl.PopupCheckboxText` |
| Primer plano (texto de vínculo) | `SearchControl.PopupButtonText` |
| Fondo de encabezado | `SearchControl.PopupSectionHeaderGradientBegin`<br />(Delimitadores de degradado para este token que no se usa en la interfaz de usuario con tema.) |
| Primer plano (texto de encabezado) | `SearchControl.PopupSectionHeaderText` |

**Las opciones de búsqueda: mantenga el puntero de estado**

![Opciones (casilla) de búsqueda al mantener el mouse](../../extensibility/ux-guidelines/media/0303-129_searchcheckboxhover.png "0303 129_SearchCheckboxHover")<br />Opciones de búsqueda (casilla) al mantener el mouse

![Opciones (vínculo) de búsqueda al mantener el mouse](../../extensibility/ux-guidelines/media/0303-130_searchoptionshover.png "0303 130_SearchOptionsHover")<br />Opciones de búsqueda (vínculo) al mantener el mouse

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br />(Delimitadores de degradado para este token que no se usa en la interfaz de usuario con tema.) |
| Primer plano (texto de casilla) | `SearchControl.PopupCheckboxMouseDownText` |
| Primer plano (texto de vínculo) | `SearchControl.PopupButtonMouseDownText` |
| Borde | `SearchControl.PopupControlMouseOverBorder` |

**Las opciones de búsqueda: estado presionado**

![Presiona las opciones de búsqueda (casilla)](../../extensibility/ux-guidelines/media/0303-131_searchsuggestedpressed.png "0303 131_SearchSuggestedPressed")<br />Presiona las opciones de búsqueda (casilla)

![Presiona las opciones de búsqueda (vínculo)](../../extensibility/ux-guidelines/media/0303-132_searchoptionspressed.png "0303 132_SearchOptionsPressed")<br />Presiona las opciones de búsqueda (vínculo)

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo de casilla | `SearchControl.PopupControlMouseDownBackgroundGradientBegin`<br />`SearchControl.PopupControlMouseDownBackgroundGradientEnd`<br />(Delimitadores de degradado para este token que no se usa en la interfaz de usuario con tema.) |
| Primer plano (texto de casilla) | `SearchControl.PopupCheckboxMouseDownText` |
| Fondo de vínculo | `SearchControl.PopupButtonMouseDownBackgroundGradientBegin`<br />(Delimitadores de degradado para este token que no se usa en la interfaz de usuario con tema.) |
| Primer plano (texto de vínculo) | `SearchControl.PopupButtonMouseDownText` |

###  <a name="BKMK_TreeView"></a> Vistas de árbol
Varias ventanas de herramientas, incluido el Explorador de soluciones, el Explorador de servidores y la vista de clases, implementan un esquema organizativo jerárquico cuyos colores se controlan mediante nombres de colores en el `TreeView` categoría. Todos los elementos de una vista de árbol tienen colores de fondo y de texto. Los elementos que tienen elementos secundarios anidados también tienen glifos que indican si el elemento está expandido o contraído.

![Tree view (redline)](../../extensibility/ux-guidelines/media/0303-147_treeviewredline.png "0303-147_TreeViewRedline")<br />Vista de árbol (límite)

| Utilice... | No use … |
| --- | --- |
| ... en cualquier lugar necesita implementar una vista organizativa jerárquica. | ... por cualquier cosa que no sea similar a una vista de árbol. |
| | ... en cualquier combinación de primer plano y fondo distinto del especificado. |

**Elemento de vista de árbol: estado predeterminado**

![Elemento de vista de árbol predeterminado](../../extensibility/ux-guidelines/media/0303-148_treeview.png "0303 148_TreeView")<br />Elemento de vista de árbol predeterminado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `TreeView.Background` |
| Primer plano (texto) | `TreeView.Background` |
| Primer plano (glifo) | `TreeView.Glyph` |
| Borde | Ninguna |

**Elemento de vista de árbol: mantenga el puntero de estado**

![Elemento de vista de árbol al mantener el mouse](../../extensibility/ux-guidelines/media/0303-149_treeviewhover.png "0303 149_TreeViewHover")<br />Elemento de vista de árbol al mantener el mouse

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `TreeView.Background` |
| Primer plano (texto) | `TreeView.Background` |
| Primer plano (glifo) | `TreeView.GlyphMouseOver` |
| Borde | Ninguna |

**Elemento de vista de árbol: arrastre sobre el estado**

![Elemento de vista de arrastre de árbol a través de](../../extensibility/ux-guidelines/media/0303-150_treeviewdragover.png "0303 150_TreeViewDragOver")<br />Arrastre el elemento de vista de árbol en sobre

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `TreeView.DragOverItem` |
| Primer plano (texto) | `TreeView.DragOverItem` |
| Primer plano (glifo) | `TreeView.DragOverItemGlyph` |
| Borde | Ninguna |

**Elemento de vista de árbol: seleccionado, centra estado**

![Selecciona y centra el elemento de vista de árbol](../../extensibility/ux-guidelines/media/0303-151_treeviewfocused.png "0303 151_TreeViewFocused")<br />Elemento de vista de árbol seleccionado y centrado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `TreeView.SelectedItemActive` |
| Primer plano (texto) | `TreeView.SelectedItemActive` |
| Primer plano (glifo) | `TreeView.SelectedItemActiveGlyph` |
| Borde | `TreeView.FocusVisualBorder` |

**Elemento de vista de árbol: estado seleccionada, sin foco**

![Elemento de vista de árbol seleccionado y sin foco](../../extensibility/ux-guidelines/media/0303-152_treeviewunfocused.png "0303 152_TreeViewUnfocused")<br />Elemento de vista de árbol seleccionado y sin foco

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `TreeView.SelectedItemInactive` |
| Primer plano (texto) | `TreeView.SelectedItemInactive` |
| Primer plano (glifo) | `TreeView.SelectedItemInactiveGlyph` |
| Borde | Ninguna |

**Elemento de vista de árbol: al mantener el mouse, seleccionado y centrado de estado**

![Selecciona y centra el elemento de vista de árbol al mantener el mouse](../../extensibility/ux-guidelines/media/0303-153_treeviewfocusedhover.png "0303 153_TreeViewFocusedHover")<br />Elemento de vista de árbol seleccionado y enfocado al mantener el mouse

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `TreeView.SelectedItemActive` |
| Primer plano (texto) | `TreeView.SelectedItemActive` |
| Primer plano (glifo) | `TreeView.SelectedItemActiveGlyphMouseOver` |
| Borde | `TreeView.FocusVisualBorder` |

**Elemento de vista de árbol: estado activado, seleccionado y sin foco**

![Elemento de vista de árbol seleccionado y no enfocado al mantener el mouse](../../extensibility/ux-guidelines/media/0303-154_treeviewunfocusedhover.png "0303 154_TreeViewUnfocusedHover")<br />Elemento de vista de árbol seleccionado y no enfocado al mantener el mouse

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `TreeView.SelectedItemInactive` |
| Primer plano (texto) | `TreeView.SelectedItemInactive` |
| Primer plano (glifo) | `TreeView.SelectedItemActiveGlyphMouseOver` |
| Borde | Ninguna |

## <a name="shell-appearance"></a>Aspecto del shell

### <a name="background"></a>Fondo
El fondo del entorno consta de dos niveles. El nivel inferior es un color sólido que cubre todo el IDE. El nivel superior se encuentra debajo del área de comandos y entre los canales de ocultación automática de la ventana de herramientas en los extremos izquierdo y derecho del IDE. Las capas de fondo superior e inferior se establecen en el mismo color en los temas claro y oscuro.

![En segundo plano Visual Studio shell (línea roja)](../../extensibility/ux-guidelines/media/0303-187_shellbackgroundredline.png "0303 187_ShellBackgroundRedline")<br />En segundo plano Visual Studio shell (límite)

| Utilice... | No use … |
| --- | --- |
| ... por lugares donde quiere hacer coincidir con el fondo del entorno de Visual Studio. | … como relleno de lugares que no son superficies de fondo. |
| | … como fondo para colocar elementos en primer plano en. |

**Aspecto del shell de nivel inferior**

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `Environment.EnvironmentBackground` |

**Apariencia del shell de nivel superior**

> Los delimitadores de degradado se establecen en el mismo valor de color en los temas claro y oscuro de Visual Studio 2013.

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `Environment.EnvironmentBackgroundGradientBegin`<br />`Environment.EnvironmentBackgroundGradientEnd`<br />`Environment.EnvironmentBackgroundGradientMiddle1`<br />`Environment.EnvironmentBackgroundGradientMiddle2` |

### <a name="command-shelf"></a>Área de comandos
Para los fondos del área de comandos se usan dos conjuntos de nombres de token: un conjunto para la ubicación donde se coloca la barra de menús y uno para la ubicación donde se colocan las barras de comandos. Un grupo individual de la barra de comandos tiene sus propios valores de color de fondo, que se describen con más detalle en la sección "Barra de comandos". El texto de la barra de menús y la barra de comandos se describe en las secciones de barra de menús y barra de comandos, respectivamente.

![Estante de comandos de Visual Studio (línea roja)](../../extensibility/ux-guidelines/media/0303-188_commandshelfredline.png "0303 188_CommandShelfRedline")<br />Estante de comandos de Visual Studio (límite)

| Utilice... | No use … |
| --- | --- |
| ... para las áreas donde se colocan menús o barras de herramientas. | ... para las áreas que no son similares a un área de comandos. |
|... con la combinación de nombre del token de primer plano y de fondo correcto. | |

**Barra de menús del estante de comandos**

> Los delimitadores de degradado se establecen en el mismo valor de color en los temas claro y oscuro de Visual Studio 2013.

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `Environment.CommandShelfHighlightGradientBegin`<br /><br />`Environment.CommandShelfHighlightGradientMiddle`<br />`Environment.CommandShelfHighlightGradientEnd` |

** Comando del estante comando barra **

> Los delimitadores de degradado se establecen en el mismo valor de color en los temas claro y oscuro de Visual Studio 2013.

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `Environment.CommandShelfBackgroundGradientBegin`<br />`Environment.CommandShelfBackgroundGradientMiddle`<br />`Environment.CommandShelfBackgroundGradientEnd` |

## <a name="manifest-designer"></a>Diseñador de manifiestos
El Diseñador de manifiestos se creó para que resulte más fácil editar el archivo de manifiesto en los proyectos de Windows 8 y Windows Phone 8. Aunque no hay ningún marco compartido disponible para su consumo, es conveniente que haga coincidir el diseño y los colores de las pestañas de navegación u orientación con la estructura general. Para obtener más información sobre el diseño, vea [Layout for Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).

![Diseñador de manifiestos (línea roja)](../../extensibility/ux-guidelines/media/0303-175_manifestdesignerredline.png "0303 175_ManifestDesignerRedline")<br />Diseñador de manifiestos (límite)

| Utilice... | No use … |
| --- | --- |
| ... por diseñadores que son similares al diseñador de manifiestos. | … Si tiene más de seis pestañas. |
| ... en lugar de usar controles de ficha en la parte superior de un editor en el documento también. | … para cualquier interfaz de usuario que no está estructurado, como el Diseñador de manifiestos. |

**Ficha seleccionada de diseñador manifiesto: estado predeterminado**

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `ManifestDesigner.TabActive` |
| Borde | Ninguna |

**Panel de descripción seleccionada de diseñador de manifiesto: estado predeterminado**

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `ManifestDesigner.DescriptionPane` |

**Página contenido seleccionado Diseñador de manifiestos: estado predeterminado**

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `ManifestDesigner.Background` |
| Texto del asistente del cuadro de diálogo | `ManifestDesigner.WatermarkText`<br />(Este nombre de símbolo (token) no coincide con su función.) |

**Pestaña del Diseñador de manifiestos: anuló la selección de estado**

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `ManifestDesigner.Tab.Inactive` |

**Pestaña del Diseñador de manifiestos: mantenga el puntero de estado**

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `ManifestDesigner.Tab.Mouseover` |

## <a name="command-structures"></a>Estructuras de comandos

###  <a name="BKMK_CommandMenus"></a> Menús
Los menús pueden aparecer en varios lugares dentro de Visual Studio: la barra de menú principal, insertada en el documento o ventanas de herramientas, o en el botón derecho en diversas ubicaciones en todo el IDE. Las implementaciones de menús asociados con otros elementos de la interfaz de usuario se describen en la sección del elemento respectivo. Se debe usar siempre la implementación de menús estándar proporcionada por el entorno de Visual Studio. Sin embargo, en algunas ocasiones podría no tener acceso a los menús estándar de Visual Studio. En estos casos, use los siguientes nombres de token para asegurarse de que la interfaz de usuario sea coherente con otros menús de Visual Studio.

![Menú de Visual Studio (línea roja)](../../extensibility/ux-guidelines/media/0303-000_menuredline.png "0303 000_MenuRedline")<br />Menú de Visual Studio (límite)

| Utilice... | No use … |
| --- | --- |
| ... cuando necesite crear un menú personalizado.| … el color de fondo por sí solo. Use siempre la combinación de primer plano y fondo tal como se especifica. |
| ... cuando haya un nuevo componente de interfaz de usuario que desee para que coincida con los menús de Visual Studio.| |

#### <a name="menu-titles"></a>Títulos de menú
Los títulos de menú constan de un fondo, un borde y el texto del título, así como un glifo opcional, que suele usarse cuando el menú se encuentra en una barra de comandos.

![Menu title (redline)](../../extensibility/ux-guidelines/media/0303-001_menutitleredline.png "0303-001_MenuTitleRedline")<br />Título de menú (límite)

| Utilice... | No use … |
| --- | --- |
| … cada vez que se va a crear un título de menú personalizado. | ... por cualquier cosa que no desea que siempre coincida con el título de menú. |
| | ... en cualquier combinación de primer plano y fondo distinto del especificado. |

**Título de menú: estado predeterminado**

![Valor predeterminado de título de menú](../../extensibility/ux-guidelines/media/0303-002_menutitledefault.png "0303 002_MenuTitleDefault")<br />Título de menú predeterminado

![Valor predeterminado de título de menú con glifo](../../extensibility/ux-guidelines/media/0303-003_menutitlewithglyphdefault.png "0303 003_MenuTitleWithGlyphDefault")<br />De forma predeterminada el título de menú con glifo

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | Ninguna |
| Primer plano (texto) | `Environment.CommandBarTextActive` |
| Primer plano (glifo) | `Environment.CommandBarMenuGlyph` |
| Borde | Ninguna |

**Título de menú: mantenga el puntero de estado**

![Título de menú al mantener el mouse](../../extensibility/ux-guidelines/media/0303-004_menutitlehover.png "0303 004_MenuTitleHover")<br />Título de menú al mantener el mouse

![Título de menú con glifo al mantener el mouse](../../extensibility/ux-guidelines/media/0303-005_menutitlewithglyphhover.png "0303 005_MenuTitleWithGlyphHover")<br />Título de menú con glifo al mantener el mouse

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Delimitadores de degradado para este token que no se usa en la interfaz de usuario con tema.) |
| Primer plano (texto) | `Environment.CommandBarTextHover` |
| Primer plano (glifo) | `Environment.CommandBarMenuMouseOverGlyph` |
| Borde | `Environment.CommandBarBorder` |

**Título de menú: estado presionado**

![Presiona el título de menú](../../extensibility/ux-guidelines/media/0303-006_menutitlepressed.png "0303 006_MenuTitlePressed")<br />Título de menú presionado

![Presiona el título de menú con glifo](../../extensibility/ux-guidelines/media/0303-007_menutitlewithglyphpressed.png "0303 007_MenuTitleWithGlyphPressed")<br />Presiona el título de menú con glifo

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `Environment.CommandBarMenuBackgroundGradientBegin`<br/>(Delimitadores de degradado para este token que no se usa en la interfaz de usuario con tema.) |
| Primer plano (texto) | `Environment.CommandBarTextActive` |
| Primer plano (glifo) | `Environment.CommandBarMenuMouseDownGlyph` |
| Borde | `Environment.CommandBarMenuBorder`<br />(Solo, parte superior, lados izquierdo y derecho.) |

**Título de menú: estado deshabilitado**

![Deshabilita el título de menú con glifo](../../extensibility/ux-guidelines/media/0303-008_menutitlewithglyphdisabled.png "0303 008_MenuTitleWithGlyphDisabled")<br />Título de menú deshabilitado con glifo

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | Ninguna |
| Primer plano (texto) | `Environment.CommandBarTextInactive` |
| Primer plano (glifo) | `Environment.CommandBarTextInactive` |
| Borde | Ninguna |

#### <a name="menu-items"></a>Elementos de menú
Un elemento de menú individual se compone del texto del menú y un icono opcional, una casilla o un glifo de submenú. Su color de fondo y de texto cambian al mantener el puntero. Este token de color es un par de primer plano y fondo.

![Menu items redline](../../extensibility/ux-guidelines/media/0303-009_menuitemredline.png "0303-009_MenuItemRedline")

| Utilice... | No use … |
|---|---|
| … para cualquier lista desplegable que se inicia desde una barra de menús o barra de comandos. | ... por cualquier lista desplegable en otro contexto. |
| | ... en cualquier combinación de primer plano y fondo distinto del especificado. |

**Los elementos de menú: estado predeterminado**

![Valor predeterminado de los elementos de menú](../../extensibility/ux-guidelines/media/0303-010_menudefault.png "0303 010_MenuDefault")<br />Elementos de menú predeterminado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `Environment.CommandBarMenuBackgroundGradientBegin`<br />(Delimitadores de degradado para este token que no se usa en la interfaz de usuario con tema.) |
| Primer plano (texto) | `Environment.CommandBarTextActive` |
| Primer plano (glifo de submenú) | `Environment.CommandBarMenuSubmenuGlyph` |
| Borde | `Environment.CommandBarMenuBorder` |
| Fondo de canal de iconos | `Environment.CommandBarMenuIconBackground` |
| Separador | `Environment.CommandBarMenuSeparator` |
| Sombra | `Environment.DropShadowBackground` |

**Los elementos de menú: Active y seleccione los Estados**

![Menú activado](../../extensibility/ux-guidelines/media/0303-011_menuchecked.png "0303 011_MenuChecked")<br />Elemento de menú activado

![Menú seleccionado](../../extensibility/ux-guidelines/media/0303-012_menuselected.png "0303 012_MenuSelected")<br />Elemento de menú seleccionado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Marca de verificación | `Environment.CommandBarCheckBox` |
| Fondo de marca de verificación | `Environment.CommandBarSelectedIcon` |
| Fondo de icono | `Environment.CommandBarSelected` |
| Borde de icono | `Environment.CommandBarSelectedBorder` |

**Los elementos de menú: mantenga el puntero de estado**

![Mantener el mouse del menú](../../extensibility/ux-guidelines/media/0303-013_menuhover.png "0303 013_MenuHover")<br />Elemento de menú al mantener el mouse

![Al mantener el mouse de menú activado](../../extensibility/ux-guidelines/media/0303-014_menuhoverchecked.png "0303 014_MenuHoverChecked")<br />Comprueba el elemento de menú al mantener el mouse

![Al mantener el mouse de menú seleccionado](../../extensibility/ux-guidelines/media/0303-015_menuhoverselected.png "0303 015_MenuHoverSelected")<br />Elemento de menú seleccionado al mantener el mouse

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `Environment.CommandBarMenuItemMouseOver` |
| Primer plano (texto) | `Environment.CommandBarMenuItemMouseOver` |
| Primer plano (glifo de submenú) | `Environment.CommandBarMenuMouseOverSubmenuGlyph` |
| Marca de verificación | `Environment.CommandBarCheckBoxMouseOver` |
| Fondo de marca de verificación | `Environment.CommandBarHoverOverSelectedIcon` |
| Fondo de icono | `Environment.CommandBarHoverOverSelected` |
| Borde de icono | `Environment.CommandBarHoverOverSelectedIconBorder` |

**Los elementos de menú: estado deshabilitado**

![Menú deshabilitado](../../extensibility/ux-guidelines/media/0303-016_menudisabled.png "0303 016_MenuDisabled")<br />Elemento de menú deshabilitado

![Menú deshabilitado activado](../../extensibility/ux-guidelines/media/0303-017_menudisabledchecked.png "0303 017_MenuDisabledChecked")<br />Elemento de menú deshabilitado con la marca de verificación

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Primer plano (texto) | `Environment.CommandBarTextInactive` |
| Primer plano (glifo de submenú) | `Environment.CommandBarMenuSubmenuGlyph` |
| Marca de verificación | `Environment.CommandBarCheckBoxDisabled` |
| Fondo de marca de verificación | `Environment.CommandBarSelectedIconDisabled` |

### <a name="command-bars"></a>Barras de comandos
Una barra de comandos puede aparecer en varios lugares en el IDE de Visual Studio, en concreto el estante de comandos y herramienta incrustado en o ventanas de documento.

En general, use siempre la implementación de menús estándar proporcionada por el entorno de Visual Studio. El uso del mecanismo estándar, garantiza que todos los detalles visuales se mostrarán correctamente y que los elementos interactivos se comportarán de forma coherente con otros controles de barra de comandos de Visual Studio. Sin embargo, si necesita crear su propia barra de comandos, asegúrese de diseñarla correctamente mediante los siguientes nombres de token.

![Límite de barra de comandos](../../extensibility/ux-guidelines/media/0303-018_commandbarredline.png "0303 018_CommandBarRedline")<br />Barra de comandos (límite)

![Límite de botón de desbordamiento](../../extensibility/ux-guidelines/media/0303-019_overflowbuttonredline.png "0303 019_OverflowButtonRedline")<br />Botón de desbordamiento (límite)

| Utilice... | No use … |
| --- | --- |
| ... en lugares donde necesita una barra de comandos incrustados, pero son no se puede usar la implementación estándar de barra de comandos de Visual Studio. | … para elementos de interfaz de usuario que no son similares a una barra de comandos. |
| | ... por los componentes de barra de comandos que no sean aquellas para las que se especifican los nombres de token. |

#### <a name="command-bar-groups"></a>Grupos de la barra de comandos
Un grupo de la barra de comandos se compone de un conjunto relacionado de controles de barra de comandos y puede incluir cualquier número de botones, botones de expansión, menús desplegables, cuadros combinados o menús. Los colores de dichos controles se regulan mediante nombres de token independientes y se describen individualmente en esta guía. Se usa una línea divisoria para dividir un grupo de la barra de comandos en subgrupos relacionados.

![Límite de grupo de la barra de comandos](../../extensibility/ux-guidelines/media/0303-020_commandbargroupredline.png "0303 020_CommandBarGroupRedline")<br />Grupo de la barra de comandos (límite)

| Utilice... | No use … |
| --- | --- |
| ... en lugares donde necesita una barra de comandos incrustados, pero son no se puede usar la implementación estándar de barra de comandos de Visual Studio. | … para elementos de interfaz de usuario que no son similares a una barra de comandos. |
| | ... por los componentes de barra de comandos que no sean aquellas para las que se especifican los nombres de token. |

**Grupo de la barra de comandos: estado predeterminado**

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `Environment.CommandBarGradientBegin`<br />(Delimitadores de degradado para este token que no se usa en la interfaz de usuario con tema.) |
| Borde | `Environment.CommandBarToolBarBorder` |
| Controlador de arrastre | `Environment.CommandBarDragHandle` |
| Separador | `Environment.CommandBarToolBarSeparator`<br />`Environment.CommandBarToolBarSeparatorHighlight` |

#### <a name="command-icons"></a>Iconos de comando
![Límite de icono de comando](../../extensibility/ux-guidelines/media/0303-021_commandiconredline1.png "0303 021_CommandIconRedline1")<br />Icono de comando (límite)

![Límite de icono de comando con texto](../../extensibility/ux-guidelines/media/0303-022_commandiconredline2.png "0303 022_CommandIconRedline2")<br />Icono de comando con el texto (línea roja)

| Utilice... | No use … |
| --- | --- |
| … para los botones que se colocará en una barra de comandos. | ... por los controles que tienen sus propios nombres de token. |
| | ... en cualquier combinación de primer plano y fondo distinto del especificado. |

**Icono de comando: estado predeterminado**

![Icono predeterminado de comandos](../../extensibility/ux-guidelines/media/0303-023_commandicondefault.png "0303 023_CommandIconDefault")<br />Icono de comando predeterminado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | N/D (se hereda del fondo de la barra de comandos) |
| Primer plano (texto) | `Environment.CommandBarTextActive` |
| Borde | N/D |

**Icono de comando: estado predeterminado, seleccionada**

![De forma predeterminada, el icono de comando seleccionado](../../extensibility/ux-guidelines/media/0303-024_commandicondefaultselected.png "0303 024_CommandIconDefaultSelected")<br />De forma predeterminada, el icono de comando seleccionado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `Environment.CommandBarSelected` |
| Primer plano (texto) | `Environment.CommandBarTextSelected` |
| Borde | `Environment.CommandBarSelectedBorder` |

**Icono de comando: al mantener el mouse o el enfoque de Estados**

![Icono de comando al mantener el mouse o foco](../../extensibility/ux-guidelines/media/0303-025_commandiconhover.png "0303 025_CommandIconHover")<br />Icono de comando al mantener el mouse o el foco

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Delimitadores de degradado para este token que no se usa en la interfaz de usuario con tema.) |
| Primer plano (texto) | `Environment.CommandBarTextHover` |
| Borde | `Environment.CommandBarBorder` |

**Icono de comando: al mantener el mouse o el enfoque de Estados, seleccionados**

![Selecciona el icono de comando al mantener el mouse o el foco](../../extensibility/ux-guidelines/media/0303-026_commandiconhoverselected.png "0303 026_CommandIconHoverSelected")<br />Icono de comando seleccionado al mantener el mouse o el foco

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `Environment.CommandBarHoverOverSelected` |
| Primer plano (texto) | `Environment.CommandBarTextHoverOverSelected` |
| Borde | `Environment.CommandBarHoverOverSelectedIconBorder` |

 **Icono de comando: estado presionado**

![Presionado el icono de comando](../../extensibility/ux-guidelines/media/0303-027_commandiconpressed.png "0303 027_CommandIconPressed")<br />Icono de comando presionado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `Environment.CommandBarMouseDownBackgroundBegin`<br />(Delimitadores de degradado para este token que no se usa en la interfaz de usuario con tema.) |
| Primer plano (texto) | `Environment.CommandBarTextMouseDown` |
| Borde | `Environment.CommandBarBorder` |

**Icono de comando: estado deshabilitado**

![Icono de comando deshabilitado](../../extensibility/ux-guidelines/media/0303-028_commandicondisabled.png "0303 028_CommandIconDisabled")<br />Icono de comando deshabilitado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | N/D (se hereda del fondo de la barra de comandos) |
| Primer plano (texto) | `Environment.CommandBarTextInactive` |
| Borde | N/D |

####  <a name="BKMK_CommandComboBox"></a> Cuadros combinados de barra de comandos

> [!IMPORTANT]
> Los cuadros combinados son similares a las listas desplegables, pero incluyen un área de texto editable. Si la lista desplegable no incluye un área de texto editable, use los tokens de color para [listas desplegables de la barra de comandos](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown).

![Límite de cuadro combinado de la barra de comandos](../../extensibility/ux-guidelines/media/0303-029_comboboxredline.png "0303 029_ComboBoxRedline")<br />Cuadro combinado de barra de comandos (límite)

| Utilice... | No use … |
| --- | --- |
| ... cuando crear cuadros combinados personalizados. | ... para cualquier cosa que no desea siempre para que coincida con el comando de barra de la interfaz de usuario. |
| ... cuando se crea un control de barra de comandos es similar a un cuadro combinado. | ... cuando tienen acceso a un cuadro combinado con estilo. |

**Campo de entrada de cuadro de cuadro combinado de barra de comandos: estado predeterminado**

![Campo de entrada de cuadro de cuadro combinado de barra de comandos](../../extensibility/ux-guidelines/media/0303-030_comboboxinputfield.png "0303 030_ComboBoxInputField")<br />Campo de entrada de cuadro de cuadro combinado de barra de comandos

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `Environment.ComboBoxBackground` |
| Primer plano (texto) | `Environment.ComboBoxText` |
| Borde | `Environment.ComboBoxBorder` |
| Separador | Sin separador |

**Botón de lista desplegable de barra de comandos: estado predeterminado**

![Desplegable del cuadro combinado&#45;presionado el botón](../../extensibility/ux-guidelines/media/0303-031_comboboxdropdownbutton.png "0303 031_ComboBoxDropdownButton")<br />Botón de lista desplegable de barra de comandos

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | N/D (se hereda del fondo de la barra de comandos) |
| Primer plano (glifo) | `Environment.ComboBoxGlyph` |

**Lista desplegable de barra de comandos: estado predeterminado**

![Lista desplegable de barra de comandos](../../extensibility/ux-guidelines/media/0303-032_comboboxdropdownlist.png "0303 032_ComboBoxDropdownList")<br />Lista desplegable de barra de comandos

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `Environment.ComboBoxPopupBackgroundBegin`<br />(Delimitadores de degradado para este token que no se usa en la interfaz de usuario con tema.) |
| Primer plano (texto) | `Environment.ComboBoxItemText` |
| Borde | `Environment.ComboBoxPopupBorder` |

**Campo de entrada de cuadro de cuadro combinado de barra de comandos: mantenga el puntero de estado**

![Comando barra entrada campo de cuadro combinado al mantener el mouse](../../extensibility/ux-guidelines/media/0303-033_comboboxinputfieldhover.png "0303 033_ComboBoxInputFieldHover")<br />Comando barra entrada campo de cuadro combinado al mantener el mouse

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `Environment.ComboBoxMouseOverBackgroundBegin`<br />(Delimitadores de degradado para este token que no se usa en la interfaz de usuario con tema.) |
| Primer plano (texto) | `Environment.ComboBoxMouseOverText` |
| Borde | `Environment.ComboBoxMouseOverBorder` |
| Separador | `Environment.ComboBoxMouseOverSeparator` |

 **Botón de lista desplegable de barra de comandos: mantenga el puntero de estado**

![Botón de lista desplegable de la barra de comandos al mantener el mouse](../../extensibility/ux-guidelines/media/0303-034_comboboxdropdownbuttonhover.png "0303 034_ComboBoxDropdownButtonHover")<br />Botón de lista desplegable de la barra de comandos al mantener el mouse

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `Environment.ComboBoxButtonMouseOverBackground` |
| Primer plano (glifo) | `Environment.ComboBoxMouseOverGlyph` |

**Lista desplegable de barra de comandos: mantenga el puntero de estado**

 ![Lista de comandos barra desplegable al mantener el mouse](../../extensibility/ux-guidelines/media/0303-035_comboboxdropdownlisthover.png "0303 035_ComboBoxDropdownListHover")<br />Lista de comandos barra desplegable al mantener el mouse

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo (elemento de menú) | `Environment.ComboBoxItemMouseOverBackground` |
| Primer plano (texto) | `Environment.ComboBoxItemMouseOverText` |
| Borde (elemento de menú) | `Environment.ComboBoxItemMouseOverBorder` |

 **Campo de entrada de cuadro de cuadro combinado de barra de comandos: centra el estado**

![Centra el campo de entrada de cuadro combinado de barra de comandos](../../extensibility/ux-guidelines/media/0303-036_comboboxinputfieldfocused.png "0303 036_ComboBoxInputFieldFocused")<br />Centra el campo de entrada de cuadro de cuadro combinado de barra de comandos

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `Environment.ComboBoxFocusedBackground` |
| Primer plano (texto) | `Environment.ComboBoxFocusedText` |
| Borde | `Environment.ComboBoxFocusedBorder` |
| Separador | `Environment.ComboBoxFocusedButtonSeparator` |

**Botón de lista desplegable de barra de comandos: centra el estado**

![Centra el botón desplegable de la barra de comandos](../../extensibility/ux-guidelines/media/0303-037_comboboxdropdownbuttonfocused.png "0303 037_ComboBoxDropdownButtonFocused")<br />Botón desplegable de la barra de comandos centrado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `Environment.ComboBoxFocusedButtonBackground` |
| Primer plano (glifo) | `Environment.ComboBoxFocusedGlyph` |

 **Campo de entrada de cuadro de cuadro combinado de barra de comandos: estado presionado**

![Presiona comando campo de entrada de cuadro combinado de barra](../../extensibility/ux-guidelines/media/0303-038_comboboxinputfieldpressed.png "0303 038_ComboBoxInputFieldPressed")<br />Presiona el campo de entrada de cuadro de cuadro combinado de barra de comandos

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `Environment.ComboBoxMouseDownBackground` |
| Primer plano (texto) | `Environment.ComboBoxMouseDownText` |
| Borde | `Environment.ComboBoxMouseDownBorder` |
| Separador | `Environment.ComboBoxMouseDownSeparator` |

**Botón de lista desplegable de barra de comandos: estado presionado**

![Presiona el botón de lista desplegable de la barra de comandos](../../extensibility/ux-guidelines/media/0303-039_comboboxdropdownbuttonpressed.png "0303 039_ComboBoxDropdownButtonPressed")<br />Presiona el botón de lista desplegable de la barra de comandos

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `Environment.ComboBoxButtonMouseDownBackground` |
| Primer plano (glifo) | `Environment.ComboBoxMouseDownGlyph` |

**Campo de entrada de cuadro de cuadro combinado de barra de comandos: estado deshabilitado**

![Deshabilita el campo de entrada de cuadro combinado de barra de comandos](../../extensibility/ux-guidelines/media/0303-041_comboboxinputfielddisabled.png "0303 041_ComboBoxInputFieldDisabled")<br />Campo de entrada de cuadro combinado de la barra de comandos deshabilitado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `Environment.ComboBoxDisabledBackground` |
| Primer plano (texto) | `Environment.ComboBoxDisabledText` |
| Borde | `Environment.ComboBoxDisabledBorder` |
| Separador | Sin separador |

**Botón de lista desplegable de barra de comandos: estado deshabilitado**

![Deshabilita el botón de lista desplegable de la barra de comandos](../../extensibility/ux-guidelines/media/0303-040_comboboxdropdownbuttondisabled.png "0303 040_ComboBoxDropdownButtonDisabled")<br />Botón desplegable de la barra de comandos deshabilitado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | Ninguna |
| Primer plano (glifo) | `Environment.ComboBoxDisabledGlyph` |

####  <a name="BKMK_CommandDropDown"></a> Barra de comandos desplegables

> [!IMPORTANT]
>  Las listas desplegables son similares a los cuadros combinados, pero carecen de áreas de texto editable. Si la lista desplegable incluye un área de texto editable, use los tokens de color para [cuadros combinados de la barra de comandos](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox).

![Lista desplegable de la barra de comandos (línea roja)](../../extensibility/ux-guidelines/media/0303-042_dropdownredline.png "0303 042_DropdownRedline")<br />Lista desplegable de la barra de comandos (límite)

| Utilice... | No use … |
| --- | --- |
| ... cuando va a crear controles de lista desplegable personalizados. | ... por cualquier cosa que no sea similar a una lista desplegable. |
| | … para los cuadros combinados o botones de expansión. |

**Campo de selección desplegable de barra de comandos: estado predeterminado**

![Valor predeterminado de campo de selección de la lista desplegable de la barra de comandos](../../extensibility/ux-guidelines/media/0303-043_dropdownselectionfield.png "0303 043_DropdownSelectionField")<br />Campo de selección desplegable de barra de comandos predeterminada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `Environment.DropDownBackground` |
| Primer plano (texto) | `DropDownText` |
| Borde | `DropDownBorder` |
| Separador | Sin separador |

**Botón de lista desplegable de barra de comandos: estado predeterminado**

![Botón desplegable de la barra de comandos de predeterminado](../../extensibility/ux-guidelines/media/0303-044_dropdownbutton.png "0303 044_DropdownButton")<br />Botón de lista desplegable de barra de comandos de forma predeterminada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | Ninguna |
| Primer plano (glifo) | `Environment.DropDownGlyph` |

**Lista desplegable de barra de comandos: estado predeterminado**

![Predeterminado de la lista desplegable de la barra de comandos](../../extensibility/ux-guidelines/media/0303-045_dropdownlist.png "0303 045_DropdownList")<br />Lista de desplegable de barra de comandos predeterminada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `Environment.DropDownPopupBackgroundBegin`<br />(Delimitadores de degradado para este token que no se usa en la interfaz de usuario con tema.) |
| Primer plano (texto) | `Environment.ComboBoxItemText` |
| Borde | `Environment.DropDownPopupBorder` |
| Sombra | `Environment.DropShadowBackground` |

**Campo de selección desplegable de barra de comandos: mantenga el puntero de estado**

![Campo de selección desplegable de barra de comandos al mantener el mouse](../../extensibility/ux-guidelines/media/0303-046_dropdownselectionfieldhover.png "0303 046_DropdownSelectionFieldHover")<br />Campo de selección desplegable de barra de comandos al mantener el mouse

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `Environment.DropDownMouseOverBackgroundBegin`<br />(Delimitadores de degradado para este token que no se usa en la interfaz de usuario con tema.) |
| Primer plano (texto) | `Environment.DropDownMouseOverText` |
| Borde | `Environment.DropDownMouseOverBorder` |
| Separador | `Environment.DropDownButtonMouseOverSeparator` |

**Botón de lista desplegable de barra de comandos: mantenga el puntero de estado**

![Botón de lista desplegable de la barra de comandos al mantener el mouse](../../extensibility/ux-guidelines/media/0303-047_dropdownbuttonhover.png "0303 047_DropdownButtonHover")<br />Botón de lista desplegable de la barra de comandos al mantener el mouse

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `Environment.DropDownButtonMouseOverBackground` |
| Primer plano (glifo) | `Environment.DropDownMouseOverGlyph` |

**Lista desplegable de barra de comandos: mantenga el puntero de estado**

![Lista de comandos barra desplegable al mantener el mouse](../../extensibility/ux-guidelines/media/0303-048_dropdownlisthover.png "0303 048_DropdownListHover")<br />Lista de comandos barra desplegable al mantener el mouse

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo (elemento de menú) | `Environment.ComboBoxItemMouseOverBackground` |
| Primer plano (texto) | `Environment.ComboBoxItemMouseOverText` |
| Borde (elemento de menú) | `Environment.ComboBoxItemMouseOverBorder` |

 **Campo de selección desplegable de barra de comandos: estado presionado**

![Quitar&#45;hacia abajo del campo de selección presionada](../../extensibility/ux-guidelines/media/0303-049_dropdownselectionfieldpressed.png "0303 049_DropdownSelectionFieldPressed")<br />Presiona comando barra campo de selección desplegable

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `Environment.DropDownMouseDownBackground` |
| Primer plano (texto) | `Environment.DropDownMouseDownText` |
| Borde | `Environment.DropDownMouseDownBorder` |
| Separador | `Environment.DropDownButtonMouseDownSeparator` |

**Botón de lista desplegable de barra de comandos: estado presionado**

![Presiona el botón de lista desplegable de la barra de comandos](../../extensibility/ux-guidelines/media/0303-050_dropdownbuttonpressed.png "0303 050_DropdownButtonPressed")<br />Presiona el botón de lista desplegable de la barra de comandos

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `Environment.DropDownButtonMouseDownBackground` |
| Primer plano (glifo) | `Environment.DropDownMouseDownGlyph` |

**Campo de selección desplegable de barra de comandos: estado deshabilitado**

![Deshabilita el campo de selección de la lista desplegable de la barra de comandos](../../extensibility/ux-guidelines/media/0303-051_dropdownselectionfielddisabled.png "0303 051_DropdownSelectionFieldDisabled")<br />Campo de selección de la lista desplegable de la barra de comandos deshabilitado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `Environment.DropDownDisabledBackground` |
| Primer plano (texto) | `Environment.DropDownDisabledText` |
| Borde | `Environment.DropDownDisabledBorder` |
| Separador | Sin separador |

**Botón de lista desplegable de barra de comandos: estado deshabilitado**

![Deshabilita el botón de lista desplegable de la barra de comandos](../../extensibility/ux-guidelines/media/0303-052_dropdownbuttondisabled.png "0303 052_DropdownButtonDisabled")<br />Botón desplegable de la barra de comandos deshabilitado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | N/D |
| Primer plano (glifo) | `Environment.DropDownDisabledGlyph` |

#### <a name="command-bar-split-buttons"></a>Botones de expansión de la barra de comandos
Los botones de expansión comparten muchos nombres de token con otros controles de barra de comandos como, por ejemplo, botones, menús y texto de la barra de comandos. Todos los nombres de token de acciones y botones desplegables necesarios se repiten aquí para su comodidad. Listas de lista desplegable del botón de expansión son implementaciones de [barra de menús de comandos](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus).

![Límite de botón de división](../../extensibility/ux-guidelines/media/0303-053_splitbuttonredline.png "0303 053_SplitButtonRedline")<br />Botón de expansión de la barra de comandos (límite)

| Utilice... | No use … |
| --- | --- |
| ... cuando va a crear un botón de expansión personalizado. | … para otros tipos de botones. |
| | ... en cualquier combinación de primer plano y fondo distinto del especificado. |

**Botón de expansión de la barra de comandos: estado predeterminado**

![Predeterminado de botón de expansión de la barra de comandos](../../extensibility/ux-guidelines/media/0303-054_splitbutton.png "0303 054_SplitButton")<br />Botón de expansión de la barra de comandos de forma predeterminada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | Ninguna |
| Primer plano (texto) | `Environment.CommandBarTextActive` |
| Primer plano (glifo) | `Environment.CommandBarSplitButtonGlyph` |
| Borde | N/D |
| Separador | N/D |

**Botón de expansión de la barra de comandos: mantenga el puntero de estado**

![Botón al mantener el mouse de expansión de la barra de comandos](../../extensibility/ux-guidelines/media/0303-055_splitbuttonhover.png "0303 055_SplitButtonHover")<br />Botón al mantener el mouse de expansión de la barra de comandos

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Delimitadores de degradado para este token que no se usa en la interfaz de usuario con tema.) |
| Primer plano (texto) | `Environment.CommandBarTextHover` |
| Primer plano (glifo) | `Environment.CommandBarSplitButtonMouseOverGlyph` |
| Borde | `Environment.CommandBarBorder` |
| Separador | `Environment.CommandBarSplitButtonSeparator` |

**Botón de expansión de la barra de comandos: estado presionado**

![Presiona el botón de expansión de la barra de comandos](../../extensibility/ux-guidelines/media/0303-056_splitbuttonpressed.png "0303 056_SplitButtonPressed")<br />Barra de comandos presionado el botón de expansión

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `Environment.CommandBarMouseDownBackgroundBegin`<br />(Delimitadores de degradado para este token que no se usa en la interfaz de usuario con tema.) |
| Primer plano (texto) | `Environment.CommandBarTextMouseDown` |
| Primer plano (glifo) | `Environment.CommandBarSplitButtonMouseDownGlyph` |
| Borde | `Environment.CommandBarBorder` |
| Separador | N/D |

**Botón de expansión de la barra de comandos: estado deshabilitado**

![Deshabilita el botón de expansión de la barra de comandos](../../extensibility/ux-guidelines/media/0303-057_splitbuttondisabled.png "0303 057_SplitButtonDisabled")<br />Botón de expansión de la barra de comandos deshabilitado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | N/D |
| Primer plano (texto) | `Environment.ComboBoxItemTextInactive` |
| Primer plano (glifo) | `Environment.CommandBarTextInactive` |
| Borde | N/D |
| Separador | N/D |

#### <a name="command-bar-more-options-and-overflow-buttons"></a>Botones de comando de la barra "Más opciones" y "Desbordamiento"
El botón "Más opciones" se usa cuando un grupo de la barra de comandos se puede personalizar al agregar o quitar botones relacionados de barra de comandos. El botón "Desbordamiento" aparece cuando una barra de comandos se trunca debido a la falta de espacio horizontal y, al hacer clic en él, muestra un menú que contiene los botones de la barra de comandos que no pueden mostrarse. Los colores para estos dos botones están controlados por el mismo conjunto de nombres de token.

![Botón "Más opciones" de la barra de comandos (línea roja)](../../extensibility/ux-guidelines/media/0303-058_moreoptionsredline.png "0303 058_MoreOptionsRedline")<br />Botón "Más opciones" de la barra de comandos (límite)

| Utilice... | No use … |
| --- | --- |
| ... por personalizadas "más opciones" o "Desbordamiento" botones. | … para los botones que no tienen una funcionalidad similar a un "Más opciones" o "Desbordamiento" botón. |

**Barra de comandos "Más opciones" y "Desbordamiento" botones: estado predeterminado**

![Botón "Más opciones" de la barra de comandos de predeterminado](../../extensibility/ux-guidelines/media/0303-059_moreoptions.png "0303 059_MoreOptions")<br />Barra de comandos "Más opciones" botón predeterminados

![Valor predeterminado "Desbordamiento" botón de barra de comandos](../../extensibility/ux-guidelines/media/0303-060_overflow.png "0303 060_Overflow")<br />Botón "Desbordamiento" de la barra de comandos predeterminada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `Environment.CommandBarOptionsBackground` |
| Primer plano (glifo) | `Environment.CommandBarOptionsGlyph` |

**Barra de comandos "Más opciones" y "Desbordamiento" botones: mantenga el puntero de estado**

![Botón "Más opciones" mantener el mouse en la barra de comandos](../../extensibility/ux-guidelines/media/0303-061_moreoptionshover.png "0303 061_MoreOptionsHover")<br />Botón "Más opciones" al mantener el mouse de la barra de comandos

![Botón de la barra de comandos 'Overflow' al mantener el mouse](../../extensibility/ux-guidelines/media/0303-062_overflowoptions.png "0303 062_OverflowOptions")<br />Botón de la barra de comandos 'Overflow' al mantener el mouse

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `Environment.CommandBarOptionsMouseOverBackgroundBegin`<br />(Delimitadores de degradado para este token que no se usa en la interfaz de usuario con tema.) |
| Primer plano (glifo) | `Environment.CommandBarOptionsMouseDownGlyph` |

**Barra de comandos "Más opciones" y "Desbordamiento" botones: estado presionado**

![Presiona el botón "Más opciones" de la barra de comandos](../../extensibility/ux-guidelines/media/0303-063_moreoptionspressed.png "0303 063_MoreOptionsPressed")<br />Presiona el botón "Más opciones" de la barra de comandos

![Desbordamiento presionado](../../extensibility/ux-guidelines/media/0303-064_overflowpressed.png "0303 064_OverflowPressed")<br />Presiona el botón "Desbordamiento" de barra de comandos

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `Environment.CommandBarOptionsMouseDownBackgroundBegin`<br />(Delimitadores de degradado para este token que no se usa en la interfaz de usuario con tema.) |
| Primer plano (glifo) | `Environment.CommandBarOptionsMouseDownGlyph` |

## <a name="document-windows"></a>Ventanas de documento
No hay ninguna necesidad de replicar las ventanas de documento, porque le proporciona el entorno de Visual Studio. Sin embargo, quizá prefiera aprovechar los colores que se usan en las ventanas de documento para que la interfaz de usuario se muestre siempre coherente con esta parte del entorno de Visual Studio.

Al utilizar tokens de color de ventana de documento, tenga cuidado al usarlos únicamente para elementos similares y siempre en pares. Si no lo hace, podría obtener resultados inesperados en la interfaz de usuario.

### <a name="document-window-frames"></a>Marcos de ventana de documento
Las ventanas de documento pueden estar acopladas en el IDE o flotantes como una ventana independiente. Cuando una ventana de documento está flotante fuera del IDE, todavía se encuentra en un área de documento y tiene fondo, borde, texto y sus colores de pestaña son los mismos que cuando forma parte del IDE. Sin embargo, el documento se encuentra dentro de un marco que tiene su propio fondo, borde y colores de texto. Cuando las ventanas de herramientas se acoplan en el cuadro del documento, heredan el comportamiento y el color de los nombres de token de ventana de documento para sus pestañas.

![Ventana de documento acoplado (línea roja)](../../extensibility/ux-guidelines/media/0303-065_dockeddocumentwindowredline.png "0303 065_DockedDocumentWindowRedline")<br />Ventana de documento acoplado (límite)

![Ventana de documento flotante (línea roja)](../../extensibility/ux-guidelines/media/0303-066_floatingdocumentwindowredline.png "0303 066_FloatingDocumentWindowRedline")<br />Ventana de documento flotante (límite)

| Utilice... | No use … |
| --- | --- |
| ... en cualquier parte va a crear la interfaz de usuario que desee para que coincida con la ventana de documento. | … para cualquier interfaz de usuario que no desea automáticamente para cambiar si el shell tiene actualiza un tema. |

**Ventana de documento acoplada o flotante: estado predeterminado**

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | Depende del tipo de documento |
| Primer plano (texto) | Depende del tipo de documento |
| Borde | `Environment.ToolWindowBorder` |

**Foco, el marco de ventana de documento flotante: estado predeterminado**

![Predeterminada centrado, marco de ventana de documento flotante](../../extensibility/ux-guidelines/media/0303-067_framefocused.png "0303 067_FrameFocused")<br />Predeterminada centrado, marco de ventana de documento flotante

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `Environment.ToolWindowFloatingFrame` |
| Primer plano (texto) | `Environment.ToolWindowFloatingFrame` |
| Primer plano (glifo) | `Environment.RaftedWindowButtonActiveGlyph` |
| Borde | `Environment.MainWindowActiveDefaultBorder` |
| Borde (glifo) | `Environment.RaftedWindowButtonActiveBorder`<br />(Se establece en transparente) |

**Marco de ventana de documento flotante, sin foco: estado predeterminado**

![Marco de ventana de documento flotante, sin foco predeterminado](../../extensibility/ux-guidelines/media/0303-068_frameunfocused.png "0303 068_FrameUnfocused")<br />Valor predeterminado de marco de ventana de documento flotante, sin foco

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `Environment.ToolWindowFloatingFrameInactive` |
| Primer plano (texto) | `Environment.ToolWindowFloatingFrameInactive` |
| Primer plano (glifo) | `Environment.RaftedWindowButtonInactiveGlyph` |
| Borde | `Environment.MainWindowInactiveBorder` |
| Borde (glifo) | `Environment.RaftedWindowButtonInactiveBorder`<br />(Se establece en transparente) |

**Foco, el marco de ventana de documento flotante: mantenga el puntero de estado**

![Centrado, marco de ventana de documento de flotante al mantener el mouse](../../extensibility/ux-guidelines/media/0303-069_framefocusedhover.png "0303 069_FrameFocusedHover")<br />Centrado, marco de ventana de documento de flotante al mantener el mouse

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo (glifo) | `Environment.RaftedWindowButtonHoverActive` |
| Primer plano (glifo) | `Environment.RaftedWindowButtonHoverActiveGlyph` |
| Borde (glifo) | `Environment.RaftedWindowButtonHoverActiveBorder` |

**Marco de ventana de documento flotante, sin foco: mantenga el puntero de estado**

![Marco de ventana de documento flotante no enfocado al mantener el mouse](../../extensibility/ux-guidelines/media/0303-070_frameunfocusedhover.png "0303 070_FrameUnfocusedHover")<br />Marco de ventana de documento flotante no enfocado al mantener el mouse

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo (glifo) | `EnvironmentRaftedWindowButtonHoverInactive` |
| Primer plano (glifo) | `Environment.RaftedWindowButtonHoverInactiveGlyph` |
| Borde (glifo) | `Environment.RaftedWindowButtonHoverInactiveBorder` |

**Foco, el marco de ventana de documento flotante: estado presionado**

![Centrado, marco de ventana de documento de flotante en prensa](../../extensibility/ux-guidelines/media/0303-071_framefocusedpressed.png "0303 071_FrameFocusedPressed")<br />Centrado, marco de ventana de documento de flotante al presionar

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo (glifo) | `Environment.RaftedWindowButtonDown` |
| Primer plano (glifo) | `Environment.RaftedWindowButtonDownGlyph` |
| Borde (glifo) | `Environment.RaftedWindowButtonDownBorder` |

### <a name="document-tabs"></a>Pestañas de documentos
Las pestañas de documentos se colocan en el canal de pestañas para indicar los documentos que están abiertos actualmente, así como el documento actual activo o seleccionado. Las ventanas de herramientas también se pueden acoplar en el canal de pestañas de documentos si el usuario las coloca allí. En este caso, usan los mismos colores de pestaña que las ventanas de documento. Si va a crear interfaz de usuario que desea que siempre coincida con los colores de las ventanas de documento (lo que incluye las actualizaciones de temas o si se instalan nuevos temas), entonces haga referencia a estos tokens de color.

![Pestañas de documentos (línea roja)](../../extensibility/ux-guidelines/media/0303-072_documenttabredline.png "0303 072_DocumentTabRedline")<br />Pestañas de documentos (límite)

| Utilice... | No use … |
| --- | --- |
| ... en cualquier parte va a crear la interfaz de usuario que desea que coincida con las pestañas de documentos y recoge automáticamente las actualizaciones de tema o nuevos colores del tema. | … para cualquier interfaz de usuario que no desea que cambie automáticamente cuando el shell tiene un tema de actualización. |

#### <a name="open-document-tabs"></a>Pestañas de documentos abiertos
Cada documento abierto tiene una pestaña en el canal de pestañas de documentos que muestra su nombre. Los documentos pueden estar seleccionados o abiertos en segundo plano y sus pestañas reflejan los siguientes estados:

-   La pestaña seleccionada representa el documento que se muestra actualmente en el cuadro de documento. Una pestaña seleccionada tiene un borde de documento que se extiende por todo el borde superior del cuadro de documento.

-   Las pestañas en segundo plano corresponden a cualquier pestaña de documento que no sea la pestaña seleccionada actualmente. Una vez que se hace clic en una de ellas, se convierte en la pestaña seleccionada y adopta todos los colores de fondo, borde y texto de los nombres de token.

![Pestaña de documento abierto (línea roja)](../../extensibility/ux-guidelines/media/0303-073_opendocumenttabredline.png "0303 073_OpenDocumentTabRedline")<br />Pestaña de documento abierto (límite)

| Utilice... | No use … |
| --- | --- |
| ... al crear pestañas de documentos personalizadas. | … para pestañas provisionales (vista previa). |
| | … para cualquier interfaz de usuario que no desea que cambie automáticamente si el shell tiene actualiza un tema. |

**Pestaña de documento seleccionada, con foco**

![Selecciona, centra la pestaña de documento](../../extensibility/ux-guidelines/media/0303-074_selectedtabfocused.png "0303 074_SelectedTabFocused")<br />Pestaña de documento seleccionada, con foco

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `Environment.FileTabSelectedGradientTop`<br />(Delimitadores de degradado para este token que no se usa en la interfaz de usuario con tema.) |
| Primer plano (texto) | `Environment.FileTabSelectedText` |
| Borde | `Environment.FileTabSelectedBorder`<br />(Establecer en el mismo color como fondo). |
| Borde de documento | `Environment.FileTabDocumentBorderBackground` |

**Pestaña de documento seleccionada, sin foco**

![Pestaña de documento seleccionada, sin foco](../../extensibility/ux-guidelines/media/0303-075_selectedtabunfocused.png "0303 075_SelectedTabUnfocused")<br />Pestaña de documento seleccionada, sin foco

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `Environment.FileTabInactiveGradientTop`<br />(Delimitadores de degradado para este token que no se usa en la interfaz de usuario con tema.) |
| Primer plano (texto) | `Environment.FileTabInactiveText` |
| Borde | `Environment.FileTabInactiveBorder`<br />(Establecer en el mismo color como fondo). |
| Borde de documento | `Environment.FileTabInactiveDocumentBorderBackground` |

**Pestaña de documento en segundo plano: estado predeterminado**

![Pestaña de documento predeterminado en segundo plano](../../extensibility/ux-guidelines/media/0303-076_backgroundtab.png "0303 076_BackgroundTab")<br />Pestaña de documento predeterminado en segundo plano

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `Environment.FileTabBackground` |
| Primer plano (texto) | `Environment.FileTabText` |
| Borde | `Environment.FileTabBorder`<br />(Establecer en el mismo color como fondo). |

**Pestaña de documento en segundo plano: mantenga el puntero de estado**

![Pestaña de documento en segundo plano al mantener el mouse](../../extensibility/ux-guidelines/media/0303-077_backgroundtabhover.png "0303 077_BackgroundTabHover")<br />Pestaña de documento en segundo plano al mantener el mouse

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `Environment.FileTabHotGradientTop`<br />(Delimitadores de degradado para este token que no se usa en la interfaz de usuario con tema.) |
| Primer plano (texto) | `Environment.FileTabHotText` |
| Borde | `Environment.FileTabHotBorder`<br />(Establecer en el mismo color como fondo). |

#### <a name="preview-tab"></a>Pestaña de vista previa
También se denomina una pestaña "provisional". La pestaña de vista previa aparece en la parte derecha del canal de pestañas de documentos cuando el usuario hace clic en un elemento de la ventana de herramientas del Explorador de soluciones. Funciona como una vista previa del documento y también proporciona al usuario la posibilidad de mantener el documento abierto en la parte izquierda del canal de pestañas de documentos. Solo se puede abrir una pestaña de vista previa a la vez. Las pestañas de vista previa tienen tanto el estado seleccionado como en segundo plano al igual que las pestañas abiertas y, además, pueden estar con y sin foco en su estado activo.

![Preview tab (redline)](../../extensibility/ux-guidelines/media/0303-078_previewtabredline.png "0303-078_PreviewTabRedline")<br />Pestaña de vista previa (límite)

| Utilice... | No use … |
| --- | --- |
| ... en cualquier lugar que está creando provisional de vista previa y desea algún elemento para que coincida con el color de ficha de vista previa actual. | … para cualquier tipo de documento o pestaña que no sea provisional (versión preliminar). |
| | … para cualquier interfaz de usuario que no desea que cambie automáticamente si el shell tiene actualiza un tema. |

**Pestaña de vista previa seleccionada, con foco**

![Pestaña de vista previa especializado y seleccionado](../../extensibility/ux-guidelines/media/0303-079_previewtabfocused.png "0303 079_PreviewTabFocused")<br />Pestaña de vista previa seleccionada, con foco

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `Environment.FileTabProvisionalSelectedActive` |
| Primer plano (texto) | `Environment.FileTabProvisionalSelectedActiveForeground` |
| Borde | `Environment.FileTabProvisionalSelectedActiveBorder`<br />(Establecer en el mismo color como fondo). |
| Borde de documento | `Environment.FileTabProvisionalSelectedActiveBorder` |

**Pestaña de vista previa seleccionada, sin foco**

![Pestaña de vista previa seleccionada, sin foco](../../extensibility/ux-guidelines/media/0303-080_previewtabunfocused.png "0303 080_PreviewTabUnfocused")<br />Pestaña de vista previa seleccionada, sin foco

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `Environment.FileTabProvisionalSelectedInactive` |
| Primer plano (texto) | `Environment.FileTabProvisionalSelectedInactiveForeground` |
| Borde | `Environment.FileTabProvisionalSelectedInactiveBorder` |
| Borde de documento | `Environment.FileTabProvisionalSelectedInactiveBorder` |

**Pestaña de vista previa en segundo plano: estado predeterminado**

![Pestaña de vista previa en segundo plano predeterminado](../../extensibility/ux-guidelines/media/0303-081_previewbackgroundtab.png "0303 081_PreviewBackgroundTab")<br />Pestaña de vista previa en segundo plano de forma predeterminada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `Environment.FileTabProvisionalInactive` |
| Primer plano (texto) | `Environment.FileTabProvisionalInactiveForeground` |
| Borde | `Environment.FileTabProvisionalInactiveBorder`<br />(Establecer en el mismo color como fondo). |

**Pestaña de vista previa en segundo plano: mantenga el puntero de estado**

![Pestaña de vista previa en segundo plano al mantener el mouse](../../extensibility/ux-guidelines/media/0303-082_previewbackgroundtabhover.png "0303 082_PreviewBackgroundTabHover")<br />Pestaña de vista previa en segundo plano al mantener el mouse

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `Environment.FileTabProvisionalHover` |
| Primer plano (texto) | `Environment.FileTabProvisionalHoverForeground` |
| Borde | `Environment.FileTabProvisionalHoverBorder`<br />(Establecer en el mismo color como fondo). |

#### <a name="document-overflow-button"></a>Botón de desbordamiento de documento
El botón de desbordamiento de documento se muestra si hay uno o varios documentos abiertos, independientemente de si hay espacio vertical en la configuración actual para que quepan todas las pestañas de documentos. El menú desplegable de desbordamiento de documento, que está controlado por la [menú de barra de comandos](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus) colores, muestra una lista de todos los documentos abiertos, visibles y ocultos y los cambios de glifo de desbordamiento según si son todos los documentos abiertos se muestra en el canal de pestañas.

![Botón de desbordamiento de documento (línea roja)](../../extensibility/ux-guidelines/media/0303-083_overflowredline.png "0303 083_OverflowRedline")<br />Botón de desbordamiento de documento (límite)

| Utilice... | No use … |
| --- | --- |
| ... cuando va a crear un botón de desbordamiento de documento personalizadas. | ... por la interfaz de usuario que no sea similar a un botón de desbordamiento. |
| | ... por botones de desbordamiento de barra de comandos. |

**Botón de desbordamiento de documento: estado predeterminado**

![Botón de desbordamiento de documento predeterminado](../../extensibility/ux-guidelines/media/0303-084_overflow.png "0303 084_Overflow")<br />Botón de desbordamiento de documento predeterminado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `Environment.DocWellOverflowButtonBackground` |
| Primer plano (glifo) | `Environment.DocWellOverflowButtonGlyph` |
| Borde | N/D |

**Botón de desbordamiento de documento: mantenga el puntero de estado**

![Botón de desbordamiento de documento al mantener el mouse](../../extensibility/ux-guidelines/media/0303-085_overflowhover.png "0303 085_OverflowHover")<br />Botón de desbordamiento de documento al mantener el puntero

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `Environment.DocWellOverflowButtonMouseOverBackground` |
| Primer plano (glifo) | `Environment.DocWellOverflowButtonMouseOverGlyph` |
| Borde | `Environment.DocWellOverflowButtonMouseOverBorder` |

**Botón de desbordamiento de documento: estado presionado**

![Botón de desbordamiento de documento al presionar](../../extensibility/ux-guidelines/media/0303-086_overflowpressed.png "0303 086_OverflowPressed")<br />Botón de desbordamiento de documento al presionar

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `Environment.DocWellOverflowButtonMouseDownBackground` |
| Primer plano (glifo) | `Environment.DocWellOverflowButtonMouseDownGlyph` |
| Borde | `Environment.DocWellOverflowButtonMouseDownBorder` |

### <a name="tagging"></a>Etiquetado
Visual Studio admite el etiquetado, lo que permite al usuario declarar palabras clave de búsqueda con fines de seguimiento. Por ejemplo, los desarrolladores y los administradores de proyectos pueden usar Team Foundation Server (TFS) para etiquetar elementos de trabajo. Las tablas siguientes proporcionan nombres de colores para la etiqueta en sí y el glifo del "icono de cerrar" que aparecen en los estados Al desplazar el puntero y Seleccionado.

![Etiquetado en Visual Studio (línea roja)](../../extensibility/ux-guidelines/media/0303-176_taggingredline.png "0303 176_TaggingRedline")<br />Etiquetado en Visual Studio (límite)

| Utilice... | No use … |
| --- | --- |
| ... por la interfaz de usuario que admite el etiquetado. | ... por cualquier otro tipo de interfaz de usuario. |

#### <a name="tags"></a>Etiquetas

**Etiqueta: estado predeterminado**

![Etiqueta predeterminada](../../extensibility/ux-guidelines/media/0303-177_tag.png "0303 177_Tag")<br />Etiqueta predeterminada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `Tag.Background` |
| Primer plano (texto) | `Tag.Background` |

**Etiqueta: estado de desplazamiento**

![Al mantener el mouse de etiqueta](../../extensibility/ux-guidelines/media/0303-178_taghover.png "0303 178_TagHover")<br />Etiqueta al mantener el mouse

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `Tag.HoverBackground` |
| Primer plano (texto) | `Tag.HoverBackgroundText` |

**Etiqueta: estado de presionado**

![Presiona etiqueta](../../extensibility/ux-guidelines/media/0303-179_tagpressed.png "0303 179_TagPressed")<br />Etiqueta presionada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `Tag.PressedBackground` |
| Primer plano (texto) | `Tag.PressedBackgroundText` |

**Etiqueta: estado seleccionado**

![Selecciona la etiqueta](../../extensibility/ux-guidelines/media/0303-180_tagselected.png "0303 180_TagSelected")<br />Etiqueta seleccionada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `Tag.SelectedBackground` |
| Primer plano (texto) | `Tag.SelectedBackgroundText` |

#### <a name="close-times-tag-glyph"></a>Cerrar (&times;) glifo de etiqueta

**Cerrar (&times;) glifo de etiqueta: estado predeterminado**

![Predeterminado de cierre (&times;) glifo de etiqueta](../../extensibility/ux-guidelines/media/0303-181_tagglyph.png "0303 181_TagGlyph")<br />Predeterminado de cierre (&times;) glifo de etiqueta

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | N/D |
| Primer plano (glifo) | `Tag.TagHoverGlyph` |

**Cerrar (&times;) glifo de etiqueta: mantenga el puntero de estado**

![Cerrar (&times;) etiquetar glifo al mantener el mouse](../../extensibility/ux-guidelines/media/0303-182_tagglyphhover.png "0303 182_TagGlyphHover")<br />Cerrar (&times;) etiquetar glifo al mantener el mouse

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `Tag.TagHoverGlyphHoverBackground` |
| Primer plano (glifo) | `Tag.TagHoverGlyphHover` |
| Borde | `Tag.TagHoverGlyphHoverBorder` |

**Cerrar (&times;) glifo de etiqueta: estado presionado**

![Presiona cerrar (&times;) glifo de etiqueta](../../extensibility/ux-guidelines/media/0303-183_tagglyphpressed.png "0303 183_TagGlyphPressed")<br />Presiona cerrar (&times;) glifo de etiqueta

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `Tag.TagHoverGlyphPressedBackground` |
| Primer plano (glifo) | `Tag.TagHoverGlyphPressed` |
| Borde | `Tag.TagHoverGlyphPressedBorder` |

**Selecciona la etiqueta de cierre (&times;) glifo: estado predeterminado**

![Etiqueta seleccionada con cierre predeterminada (&times;) glifo](../../extensibility/ux-guidelines/media/0303-184_tagselected.png "0303 184_TagSelected")<br />Etiqueta seleccionada con cierre predeterminada (&times;) glifo

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | N/D |
| Primer plano (glifo) | `Tag.TagSelectedGlyph` |

**Selecciona la etiqueta de cierre (&times;) glifo: mantenga el puntero de estado**

![Selecciona la etiqueta de cierre (&times;) glifo al mantener el mouse](../../extensibility/ux-guidelines/media/0303-185_tagselectedhover.png "0303 185_TagSelectedHover")<br />Selecciona la etiqueta de cierre (&times;) glifo al mantener el mouse


| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `Tag.TagSelectedGlyphHoverBackground` |
| Primer plano (glifo) | `Tag.TagSelectedGlyphHover` |
| Borde | `Tag.TagSelectedGlyphHoverBorder` |

**Selecciona la etiqueta de cierre (&times;) glifo: estado presionado**

![Selecciona, presiona la etiqueta de cierre (&times;) glifo](../../extensibility/ux-guidelines/media/0303-186_tagselectedpressed.png "0303 186_TagSelectedPressed")<br />Selecciona, presiona la etiqueta de cierre (&times;) glifo

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `Tag.TagSelectedGlyphPressedBackground` |
| Primer plano (glifo) | `Tag.TagSelectedGlyphPressed` |
| Borde | `Tag.TagSelectedGlyphPressedBorder` |

## <a name="tool-windows"></a>Ventanas de herramientas
No es necesario replicar las ventanas de herramientas, porque le proporciona el entorno de Visual Studio. Sin embargo, quizá prefiera aprovechar los colores que se usan en las ventanas de herramientas para que la interfaz de usuario se muestre siempre coherente con esta parte del entorno de Visual Studio.

![Ventana de herramientas (línea roja)](../../extensibility/ux-guidelines/media/0303-087_toolwindowredline.png "0303 087_ToolWindowRedline")<br />Ventana de herramientas (límite)

| Utilice... | No use … |
| --- | --- |
| ... en cualquier parte va a crear la interfaz de usuario que desee para que coincida con las ventanas de herramientas. | … para cualquier interfaz de usuario que no desea que cambie automáticamente si el shell tiene actualiza un tema. |

### <a name="tool-window-frame"></a>Marco de ventana de herramientas
Las ventanas de herramientas de Visual Studio se usan para diversas tareas y pueden estar en uno de varios estados diferentes. Si una ventana de herramientas está abierta, se puede asignar a cualquiera de los cuatro lados del área del documento. Estas ventanas también pueden flotar fuera del IDE, lo que permite reubicarlas en cualquier lugar dentro de la pantalla del usuario. Las ventanas flotantes siempre se colocan arriba del IDE. Por último, las ventanas de herramientas se pueden acoplar como ventanas de documento y aparecen como una pestaña en el cuadro de documento. Las ventanas de herramientas que se han acoplado como ventanas de documento se colorean en parte mediante los nombres de token de ventana de documento.

![Marco de ventana de herramientas (línea roja)](../../extensibility/ux-guidelines/media/0303-088_toolwindowframeredline.png "0303 088_ToolWindowFrameRedline")<br />Marco de ventana de herramientas (límite)

| Utilice... | No use … |
| --- | --- |
| ... en cualquier parte va a crear la interfaz de usuario que desee para que coincida con las ventanas de herramientas. | … para cualquier interfaz de usuario que no desea que cambie automáticamente si el shell tiene actualiza un tema. |

**Ventana de herramientas acoplada**

![Ventana de herramientas acoplada](../../extensibility/ux-guidelines/media/0303-089_toolwindowdocked.png "0303 089_ToolWindowDocked")<br />Ventana de herramientas acoplada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `Environment.ToolWindowBackground` |
| Borde | `Environment.ToolWindowBorder` |

**Flotante, centra la ventana de herramientas**

![Flotante, centra la ventana de herramientas](../../extensibility/ux-guidelines/media/0303-090_toolwindowfocused.png "0303 090_ToolWindowFocused")<br />Flotante, centra la ventana de herramientas

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `Environment.ToolWindowBackground` |
| Borde | `Environment.MainWindowActiveDefaultBorder` |

**Flotante, la ventana de herramientas no enfocada**

![Ventana de herramientas flotante, sin foco](../../extensibility/ux-guidelines/media/0303-091_toolwindowunfocused.png "0303 091_ToolWindowUnfocused")<br />Flotante, la ventana de herramientas no enfocada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `Environment.ToolWindowBackground` |
| Borde | `Environment.MainWindowInactiveBorder` |

### <a name="toolbox-like-windows"></a>Ventanas de cuadro de herramientas
El cuadro de herramientas es una de las ventanas de herramientas comunes utilizadas con frecuencia en Visual Studio. Es esencialmente un control de árbol con un tema especial y el estilo aplicado.

![Ventana cuadro de herramientas similares (línea roja)](../../extensibility/ux-guidelines/media/0303-189_toolboxredline.png "0303 189_ToolboxRedline")<br />Ventana cuadro de herramientas similares (límite)

| Utilice... | No use … |
| --- | --- |
| ... cuando diseña una ventana de herramientas que desea que siempre sea coherente con el cuadro de herramientas de shell. | ... por todo lo que no es similar al cuadro de herramientas de interfaz de usuario, o si no está seguro de si la interfaz de usuario tendrá problemas si cambian los colores del cuadro de herramientas de shell. |

**Los nodos del cuadro de herramientas: estado predeterminado**

![Nodo primario de cuadro de herramientas de forma predeterminada](../../extensibility/ux-guidelines/media/0303-190_toolboxparentnode.png "0303 190_ToolboxParentNode")<br />Nodo primario de cuadro de herramientas de forma predeterminada

![Nodo secundario de cuadro de herramientas de forma predeterminada](../../extensibility/ux-guidelines/media/0303-191_toolboxchildnode.png "0303 191_ToolboxChildNode")<br />Nodo secundario de cuadro de herramientas de forma predeterminada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `Environment.ToolboxContent`<br />(Encabezados) |
| Fondo | `Environment.ToolWindowBackground`<br />(Los elementos individuales o ventana completa si no hay controles disponibles) |
| Borde | Ninguna |
| Primer plano (glifo) | `Environment.ToolboxContent` |
| Primer plano (texto) | `Environment.ToolboxContent` |

**Los nodos secundarios del cuadro de herramientas: mantenga el puntero de estado**

![Nodo secundario de cuadro de herramientas al mantener el mouse](../../extensibility/ux-guidelines/media/0303-192_toolboxchildnodehover.png "0303 192_ToolboxChildNodeHover")<br />Nodo secundario de cuadro de herramientas al mantener el mouse

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `Environment.ToolboxContentMouseOver`<br />(Solo para elementos individuales) |
| Borde | Ninguna |
| Primer plano (texto) | `Environment.ToolboxContentMouseOver`<br />(Solo para elementos individuales) |

**Los nodos del cuadro de herramientas seleccionados: centra el estado**

![Nodo primario de cuadro de herramientas seleccionado, centrado](../../extensibility/ux-guidelines/media/0303-193_toolboxparentnodefocused.png "0303 193_ToolboxParentNodeFocused")<br />Nodo primario de cuadro de herramientas seleccionado, con foco

![Nodo secundario de cuadro de herramientas seleccionado, centrado](../../extensibility/ux-guidelines/media/0303-194_toolboxchildnodefocused.png "0303 194_ToolboxChildNodeFocused")<br />Nodo secundario de cuadro de herramientas seleccionado, con foco

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `TreeView.SelectedItemActive`<br />De categoría [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Borde | `TreeView.FocusVisualBorder`<br />De categoría [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Primer plano (glifo) | `TreeView.SelectedItemActive`<br />De categoría [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Primer plano (texto) | `TreeView.SelectedItemActive`<br />De categoría [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |

**Los nodos del cuadro de herramientas seleccionados: estado sin foco**

![Nodo primario de cuadro de herramientas seleccionado, sin foco](../../extensibility/ux-guidelines/media/0303-195_toolboxparentnodeunfocused.png "0303 195_ToolboxParentNodeUnfocused")<br />Nodo primario de cuadro de herramientas seleccionado, sin foco

![Nodo secundario de cuadro de herramientas seleccionado, sin foco](../../extensibility/ux-guidelines/media/0303-196_toolboxchildnodeunfocused.png "0303 196_ToolboxChildNodeUnfocused")<br />Nodo secundario de cuadro de herramientas seleccionado, sin foco

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `TreeView.SelectedItemInactive`<br />De categoría [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Borde | Ninguna |
| Primer plano (glifo) | `TreeView.SelectedItemInactive`<br />De categoría [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Primer plano (texto) | `TreeView.SelectedItemInactive`<br />De categoría [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |

### <a name="tool-window-title-bar"></a>Barra de título de la ventana de herramientas
El borde de la barra de título no es realmente un borde, es una línea gruesa en la parte superior de la barra de título. No tiene un nombre de símbolo (token) para su estado sin foco.

![Barra de título de ventana de herramientas (línea roja)](../../extensibility/ux-guidelines/media/0303-092_toolwindowtitlebarredline.png "0303 092_ToolWindowTitleBarRedline")<br />Barra de título de ventana de herramientas (límite)

| Utilice... | No use … |
| --- | --- |
| ... en cualquier parte va a crear la interfaz de usuario que desee para que coincida con las ventanas de herramientas. | … para cualquier interfaz de usuario que no desea que cambie automáticamente si el shell tiene actualiza un tema. |

**Barra de título con foco**

![Barra de título enfocado](../../extensibility/ux-guidelines/media/0303-093_titlebarfocused.png "0303 093_TitleBarFocused")<br />Barra de título con foco

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `Environment.TitleBarActiveGradientBegin`<br />(Delimitadores de degradado para este token que no se usa en la interfaz de usuario con tema.) |
| Primer plano (texto) | `Environment.TitleBarActiveText` |
| Borde | `Environment.TitleBarActiveBorder`<br />(Establecer en el mismo color como fondo). |
| Controlador de arrastre | `Environment.TitleBarDragHandleActive` |

**Barra de título no enfocado**

![Barra de título no enfocado](../../extensibility/ux-guidelines/media/0303-094_titlebarunfocused.png "0303 094_TitleBarUnfocused")<br />Barra de título sin foco

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `Environment.TitleBarInactiveGradientBegin`<br />(Delimitadores de degradado para este token que no se usa en la interfaz de usuario con tema.) |
| Primer plano (texto) | `Environment.TitleBarInactiveText` |
| Borde | N/D |
| Controlador de arrastre | `Environment.TitleBarDragHandle` |

#### <a name="tool-window-title-bar-buttons"></a>Botones de barra de título de ventana de herramientas
![Botón de la barra de título (línea roja)](../../extensibility/ux-guidelines/media/0303-095_titlebarbuttonredline.png "0303 095_TitleBarButtonRedline")<br />Botón de la barra de título (límite)

| Utilice... | No use … |
| --- | --- |
| … para los botones que aparecen en la interfaz de usuario que usa tokens de color de las barras de título de ventana de herramienta. | … para los botones que aparecen en otras ubicaciones. |
| | ... en cualquier combinación de primer plano y fondo distinto del especificado. |

**Centra los botones de barra de título: estado predeterminado**

![El valor predeterminado, centra los botones de barra de título](../../extensibility/ux-guidelines/media/0303-096_titlebarbuttonfocused.png "0303 096_TitleBarButtonFocused")<br />De forma predeterminada, los botones de barra de título con foco

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | N/D |
| Primer plano (glifo) | `Environment.ToolWindowButtonActiveGlyph` |
| Borde | N/D |

**Los botones de barra de título no enfocado: estado predeterminado**

![De forma predeterminada, los botones de barra de título no enfocado](../../extensibility/ux-guidelines/media/0303-097_titlebarbuttonunfocused.png "0303 097_TitleBarButtonUnfocused")<br />De forma predeterminada, los botones de barra de título no enfocado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | N/D |
| Primer plano (glifo) | `Environment.ToolWindowButtonInactiveGlyph` |
| Borde | N/D |

**Centra los botones de barra de título: mantenga el puntero de estado**

![Enfocada al mantener el mouse en los botones de barra de título](../../extensibility/ux-guidelines/media/0303-098_titlebarbuttonfocusedhover.png "0303 098_TitleBarButtonFocusedHover")<br />Botones de la barra de título enfocado al mantener el mouse

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `Environment.ToolWindowButtonHoverActive` |
| Primer plano (glifo) | `Environment.ToolWindowButtonHoverActiveGlyph` |
| Borde | `Environment.ToolWindowButtonHoverActiveBorder` |

**Los botones de barra de título no enfocado: mantenga el puntero de estado**

![Botones de la barra de título no enfocado al mantener el mouse](../../extensibility/ux-guidelines/media/0303-099_titlebarbuttonunfocusedhover.png "0303 099_TitleBarButtonUnfocusedHover")<br />Botones de la barra de título no enfocado al mantener el mouse

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `Environment.ToolWindowButtonHoverInactive` |
| Primer plano (glifo) | `Environment.ToolWindowButtonHoverInactiveGlyph` |
| Borde | `Environment.ToolWindowButtonHoverInactiveBorder` |

**Centra los botones de barra de título: estado presionado**

![Centra los botones de barra de título en prensa](../../extensibility/ux-guidelines/media/0303-100_titlebarbuttonfocusedpressed.png "0303 100_TitleBarButtonFocusedPressed")<br />Botones de la barra de título con foco al presionar

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `Environment.ToolWindowButtonDown` |
| Primer plano (glifo) | `Environment.ToolWindowButtonDownActiveGlyph` |
| Borde | `Environment.ToolWindowButtonDownBorder` |

**Los botones de barra de título no enfocado: estado presionado**

![Botones de la barra de título no enfocado al presionar](../../extensibility/ux-guidelines/media/0303-101_titlebarbuttonunfocusedpressed.png "0303 101_TitleBarButtonUnfocusedPressed")<br />Botones de la barra de título no enfocado al presionar

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `Environment.ToolWindowButtonDown` |
| Primer plano (glifo) | `Environment.ToolWindowButtonDownInactiveGlyph` |
| Borde | `Environment.ToolWindowButtonDownBorder` |

### <a name="tool-window-tabs"></a>Pestañas de ventana de herramientas
![Pestaña de ventana de herramientas (línea roja)](../../extensibility/ux-guidelines/media/0303-102_toolwindowtabredline.png "0303 102_ToolWindowTabRedline")<br />Pestaña de ventana de herramientas (límite)

| Utilice... | No use … |
| --- | --- |
| ... en cualquier parte va a crear la interfaz de usuario que desee para que coincida con las ventanas de herramientas. | … para cualquier interfaz de usuario que no desea que cambie automáticamente si el shell tiene actualiza un tema. |

**Pestaña de ventana de herramienta seleccionada, con foco**

![Selecciona, centrado en la pestaña de ventana de herramientas](../../extensibility/ux-guidelines/media/0303-103_toolwindowtabfocused.png "0303 103_ToolWindowTabFocused")<br />Pestaña de ventana de herramienta seleccionada, con foco

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `Environment.ToolWindowTabSelectedTab` |
| Primer plano (texto) | `Environment.ToolWindowTabSelectedActiveText` |
| Borde | `Environment.ToolWindowTabSelectedBorder`<br />(Establecer en el mismo color como fondo). |

**Pestaña de ventana de herramienta seleccionada, sin foco**

![Pestaña de ventana de herramienta seleccionada, sin foco](../../extensibility/ux-guidelines/media/0303-104_toolwindowtabunfocused.png "0303 104_ToolWindowTabUnfocused")<br />Pestaña de ventana de herramienta seleccionada, sin foco

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `Environment.ToolWindowTabSelectedTab` |
| Primer plano (texto) | `Environment.ToolWindowTabSelectedText` |
| Borde | `Environment.ToolWindowTabSelectedBorder`<br />(Establecer en el mismo color como fondo). |

**Pestaña de ventana de herramientas en segundo plano: estado predeterminado**

![Pestaña de ventana de herramientas predeterminada en segundo plano](../../extensibility/ux-guidelines/media/0303-105_toolwindowbackgroundtab.png "0303 105_ToolWindowBackgroundTab")<br />Pestaña de ventana de herramientas predeterminada en segundo plano

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `Environment.ToolWindowTabGradientBegin`<br />`Environment.ToolWindowTabGradientEnd`<br />(Delimitadores de degradado establecido en el mismo valor de color en Visual Studio 2013.) |
| Primer plano (texto) | `Environment.ToolWindowTabText` |
| Borde | `Environment.ToolWindowTabBorder` |

**Pestaña de ventana de herramientas en segundo plano: mantenga el puntero de estado**

![Pestaña de ventana de herramientas en segundo plano al mantener el mouse](../../extensibility/ux-guidelines/media/0303-106_toolwindowbackgroundtabhover.png "0303 106_ToolWindowBackgroundTabHover")<br />Pestaña de ventana de herramientas en segundo plano al mantener el puntero

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `Environment.ToolWindowTabMouseOverBackgroundBegin`<br />`Environment.ToolWindowTabMouseOverBackgroundEnd`<br />(Delimitadores de degradado establecido en el mismo valor de color en Visual Studio 2013.) |
| Primer plano (texto) | `Environment.ToolWindowTabMouseOverText` |
| Borde | `Environment.ToolWindowTabMouseOverBorder`<br />(Establecer en el mismo color como fondo). |

### <a name="auto-hide-tabs"></a>Pestaña de ocultación automática

![Pestañas de ocultación automática (línea roja)](../../extensibility/ux-guidelines/media/0303-107_autohideredline.png "0303 107_AutoHideRedline")fichas de ocultación automática (límite)

| Utilice... | No use … |
| --- | --- |
| ... en cualquier parte que está creando la interfaz de usuario que desea hacer coincidir las fichas de la ventana oculta automáticamente la herramienta. | … para cualquier interfaz de usuario que no desea que cambie automáticamente si el shell tiene actualiza un tema. |

**Ocultar automáticamente las pestañas: estado predeterminado**

![Pestaña de ocultación automática predeterminada](../../extensibility/ux-guidelines/media/0303-108_autohidetab.png "0303 108_AutoHideTab")<br />Pestaña de ocultación automática predeterminada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `Environment.AutoHideTabBackgroundBegin`<br />(Delimitadores de degradado para este token que no se usa en la interfaz de usuario con tema.) |
| Primer plano (texto) | `Environment.AutoHideTabText` |
| Borde | `Environment.AutoHideTabBorder` |

**Ocultar automáticamente las pestañas: mantenga el puntero de estado**

![Pestaña de ocultación automática al mantener el mouse](../../extensibility/ux-guidelines/media/0303-109_autohidetabhover.png "0303 109_AutoHideTabHover")<br />Pestaña de ocultación automática al mantener el puntero

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo | `Environment.AutoHideTabMouseOverBackgroundBegin`<br />(Delimitadores de degradado para este token que no se usa en la interfaz de usuario con tema.) |
| Primer plano (texto) | `Environment.AutoHideTabMouseOverText` |
| Borde | `Environment.AutoHideTabMouseOverBorder` |
