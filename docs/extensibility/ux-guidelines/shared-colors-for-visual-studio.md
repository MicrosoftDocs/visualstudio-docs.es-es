---
title: Colores compartidos para Visual Studio ? Microsoft Docs
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: 8d11b9a0-6175-4f2e-8e7f-79daee1bfd41
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3e31e5d9c3d1dc284694bd2db2a9f37d863462ad
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699929"
---
# <a name="shared-colors-for-visual-studio"></a>Colores compartidos para Visual Studio
Al diseñar la interfaz de usuario que usa elementos de shell de Visual Studio comunes, o si desea que el elemento de interfaz sea coherente con características similares, use nombres de token existentes en los archivos de definición de paquete para elegir y asignar colores. Esto garantiza que la interfaz de usuario mantenga la coherencia con el entorno general de Visual Studio y que se actualice automáticamente cuando se agreguen o actualicen temas.

En este artículo se describen los elementos de interfaz de usuario comunes y los nombres de token que estos usan y a los que se puede hacer referencia al crear una interfaz de usuario similar. Para obtener información específica sobre cómo tener acceso a estos tokens de color, vea [The VSColor Service](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).

Asegúrese de usar correctamente los nombres de token:

- **Usar nombres de token basados en función, no en el color en sí.** Los colores comunes compartidos están asociados a elementos específicos de la interfaz y solo están destinados para características iguales o similares. Por ejemplo, no vuelva a usar el color de un cuadro combinado presionado para una animación de progreso de giro solo porque le gusta el color. Las funciones del cuadro combinado y la animación son diferentes, y si el color asociado con el cuadro combinado cambia, es posible que ya no sea un color adecuado para el elemento de animación. Un uso coherente del color ayuda a orientar a los usuarios y evitar confusiones.

- **Usar colores de fondo y de texto en la combinación correcta.** Los colores de fondo destinados para usarse con texto tendrán un color de texto asociado. No use colores de texto que no sean los que se especifican para el fondo. Si no hay un color de texto asociado, no utilice ese color de fondo para ninguna superficie en la que espere mostrar texto. Otras combinaciones de texto y colores de fondo pueden dar lugar a una interfaz ilegible.

- **Usar colores de control adecuados para su ubicación.** En algunos estados, algunos controles de Visual Studio no tienen colores de borde y fondo independientes. En su lugar, toman los colores de las superficies que están detrás de ellos. Procure usar siempre los nombres de token que sean adecuados para la ubicación donde coloca el control.

> [!IMPORTANT]
> No uses tokens que se encuentran en las categorías "Página de inicio" o "Cider".

## <a name="common-shared-controls"></a>Controles comunes compartidos

Cuando use una barra de comandos estándar de Visual Studio en la característica, tendrá acceso a controles de shell con estilo. No debería volver a crear plantillas de estos controles comunes. Sin embargo, si necesita crear una barra de comandos personalizada, también podría ser necesario crear controles personalizados. En ese caso, asegúrese de usar los nombres de token correctos para cada uno de los siguientes controles de modo que la interfaz de usuario sea coherente con el resto de Visual Studio.

### <a name="button-controls"></a>Controles de botón

![Límite de control de botón](../../extensibility/ux-guidelines/media/0303-155_buttoncontrolredline.png "0303-155_ButtonControlRedline")

| Uso... | No utilice ... |
| --- | --- |
| ... para los botones del documento bien que desea integrar con temas de Visual Studio (luz, oscuro, azul o un tema de alto contraste del sistema). | ... para los botones que se mostrarán en un fondo personalizado que no forma parte de un tema de Visual Studio. |

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

**Botón: estado desactivado**

![Botón desactivado](../../extensibility/ux-guidelines/media/03.03.Button.Disabled.png "03.03.Button.Disabled")<br />Botón desactivado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Botón | `CommonControls.ButtonDisabled` |
| Borde de botón | `CommonControls.ButtonBorderDisabled` |

**Botón: estado de desplazamiento**

![Botón al mantener el mouse](../../extensibility/ux-guidelines/media/03.03.Button.hover.png "03.03.Button.hover")<br />Botón al mantener el mouse

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Botón | `CommonControls.ButtonHover` |
| Borde de botón | `CommonControls.ButtonBorderHover` |

**Botón: estado pulsado**

![Botón pulsado](../../extensibility/ux-guidelines/media/03.03.Button.Pressed.png "03.03.Button.Pressed")<br />Botón pulsado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Botón | `CommonControls.ButtonPressed` |
| Borde de botón | `CommonControls.ButtonBorderPressed` |

**Botón: estado enfocado**

![Botón enfocado](../../extensibility/ux-guidelines/media/03.03.Button.Focused.png "03.03.Button.Focused")<br />Botón enfocado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Botón | `CommonControls.ButtonFocused` |
| Borde de botón | `CommonControls.ButtonBorderFocused` |

### <a name="check-box-controls"></a>Controles de casilla
![Casilla de verificación (línea roja)](../../extensibility/ux-guidelines/media/0303-161_checkboxredline.png "0303-161_CheckboxRedline")<br />Casilla de verificación (línea roja)

| Uso... | No utilice ... |
| --- | --- |
| ... para los controles de casilla de verificación contenidos en el pozo del documento. | ... para cualquier interfaz de usuario que no sea un control de casilla de verificación. |

**Casilla de verificación: estado predeterminado**

![casilla](../../extensibility/ux-guidelines/media/0303-162_checkbox.png "0303-162_Checkbox")<br />Casilla de verificación predeterminada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `CommonControls.CheckBoxBackground` |
| Borde | `CommonControls.CheckBoxBorder` |
| Texto | `CommonControls.CheckBoxText` |
| Glifo | `CommonControls.CheckBoxGlyph` |

**Casilla de verificación: estado deshabilitado**

![Casilla de verificación deshabilitada](../../extensibility/ux-guidelines/media/0303-163_checkboxdisabled.png "0303-163_CheckboxDisabled")<br />Casilla de verificación deshabilitada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `CommonControls.CheckBoxBackgroundDisabled` |
| Borde | `CommonControls.CheckBoxBorderDisabled` |
| Texto | `CommonControls.CheckBoxTextDisabled` |
| Glifo | `CommonControls.CheckBoxGlyphDisabled` |

**Casilla de verificación: estado de desplazamiento**

 ![Casilla de verificación al mantener el mouse](../../extensibility/ux-guidelines/media/0303-164_checkboxhover.png "0303-164_CheckboxHover")<br />Casilla de verificación al mantener el mouse

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `CommonControls.CheckBoxBackgroundHover` |
| Borde | `CommonControls.CheckBoxBorderHover` |
| Texto | `CommonControls.CheckBoxTextHover` |
| Glifo | `CommonControls.CheckBoxGlyphHover` |

**Casilla de verificación: estado pulsado**

![Casilla de verificación presionada](../../extensibility/ux-guidelines/media/0303-165_checkboxpressed.png "0303-165_CheckboxPressed")<br />Casilla de verificación presionada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `CommonControls.CheckBoxBackgroundPressed` |
| Borde | `CommonControls.CheckBoxBorderPressed` |
| Texto | `CommonControls.CheckBoxTextPressed` |
| Glifo | `CommonControls.CheckBoxGlyphPressed` |

**Casilla de verificación: estado enfocado**

![Casilla de verificación Enfocada](../../extensibility/ux-guidelines/media/0303-166_checkboxfocused.png "0303-166_CheckboxFocused")<br />Casilla de verificación Enfocada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `CommonControls.CheckBoxBackgroundFocused` |
| Borde | `CommonControls.CheckBoxBorderFocused` |
| Texto | `CommonControls.CheckBoxTextFocused` |
| Glifo | `CommonControls.CheckBoxGlyphFocused` |

### <a name="drop-downs-and-combo-boxes"></a>Desplegables y cajas combinadas
![Cuadro desplegable/combo (línea roja)](../../extensibility/ux-guidelines/media/0303-167_dropdowncomboboxredline.png "0303-167_DropDownComboBoxRedline")<br />Cuadro desplegable/combo (línea roja)

| Uso... | No utilice ... |
| --- | --- |
| ... para menús desplegables y cuadros combinados en el documento bien. | ... para cualquier interfaz de usuario que no sea un cuadro desplegable o combinado. |
| | ... para menús desplegables de la barra de comandos o [cuadros combinados.](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown) [combo boxes](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox) |

**Desplegables y cuadros combinados: estado predeterminado**

![Cuadro desplegable/combo predeterminado](../../extensibility/ux-guidelines/media/0303-168_dropdowncombobox.png "0303-168_DropDownComboBox")<br />Cuadro desplegable/combo predeterminado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `CommonControls.ComboBoxBackground` |
| Borde | `CommonControls.ComboBoxBorder` |
| Texto | `CommonControls.ComboBoxText` |
| Separador | `CommonControls.ComboBoxSeparator` |
| Glifo | `CommonControls.ComboBoxGlyph` |
| Fondo de glifo | `CommonControls.ComboBoxGlyphBackground` |

**Desplegables y cuadros combinados: estado deshabilitado**

![Cuadro desplegable/combo deshabilitado](../../extensibility/ux-guidelines/media/0303-169_dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")<br />Cuadro desplegable/combo deshabilitado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `CommonControls.ComboBoxBackgroundDisabled` |
| Borde | `CommonControls.ComboBoxBorderDisabled` |
| Texto | `CommonControls.ComboBoxTextDisabled` |
| Separador | `CommonControls.ComboBoxSeparatorDisabled` |
| Glifo | `CommonControls.ComboBoxGlyphDisabled` |
| Fondo de glifo | `CommonControls.ComboBoxGlyphBackgroundDisabled` |

**Desplegables y cuadros combinados: estado de desplazamiento**

![Desplegable o cuadro combinado al mantener el mouse](../../extensibility/ux-guidelines/media/0303-170_dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")<br />Desplegable o cuadro combinado al mantener el mouse

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `CommonControls.ComboBoxBackgroundHover` |
| Borde | `CommonControls.ComboBoxBorderHover` |
| Texto | `CommonControls.ComboBoxTextHover` |
| Separador | `CommonControls.ComboBoxSeparatorHover` |
| Glifo | `CommonControls.ComboBoxGlyphHover` |
| Fondo de glifo | `CommonControls.ComboBoxGlyphBackgroundHover` |

**Desplegables y cuadros combinados: estado presionado**

![Cuadro desplegable/combo presionado](../../extensibility/ux-guidelines/media/0303-171_dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")<br />Cuadro desplegable/combo presionado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `CommonControls.ComboBoxBackgroundPressed` |
| Borde | `CommonControls.ComboBoxBorderPressed` |
| Texto | `CommonControls.ComboBoxTextPressed` |
| Separador | `CommonControls.ComboBoxSeparatorPressed` |
| Glifo | `CommonControls.ComboBoxGlyphPressed` |
| Fondo de glifo | `CommonControls.ComboBoxGlyphBackgroundPressed` |

**Vista de elementos de lista de cuadros desplegables y cuadros combinados: estado presionado**

 ![Desplegable/cuadro combinado presionado vista de elementos de lista](../../extensibility/ux-guidelines/media/0303-174_dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")<br />Desplegable/cuadro combinado presionado vista de elementos de lista

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `CommonControls.ComboBoxListBackground`<br />`CommonControls.ComboBoxListBackgroundHover`<br />`CommonControls.ComboBoxListItemBackgroundPressed`<br />`CommonControls.ComboBoxListItemBackgroundFocused` |
| Borde | `CommonControls.ComboBoxListBorder`<br />`CommonControls.ComboBoxListBorderHover`<br />`CommonControls.ComboBoxListBorderPressed`<br />`CommonControls.ComboBoxListBorderFocused` |
| Texto del elemento | `CommonControls.ComboBoxListItemText`<br /> `CommonControls.ComboBoxListItemTextHover`<br />`CommonControls.ComboBoxListItemTextPressed`<br />`CommonControls.ComboBoxListItemTextFocused` |
| Sombra de fondo | `CommonControls.ComboBoxListBackgroundShadow` |

**Desplegables y cuadros combinados: estado enfocado**

![Drop-down/combo box con enfoque](../../extensibility/ux-guidelines/media/0303-172_dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")<br />Drop-down/combo box con enfoque

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `CommonControls.ComboBoxBackgroundFocused` |
| Borde | `CommonControls.ComboBoxBorderFocused` |
| Texto | `CommonControls.ComboBoxTextFocused` |
| Separador | `CommonControls.ComboBoxSeparatorFocused` |
| Glifo | `CommonControls.ComboBoxGlyphFocused` |
| Fondo de glifo | `CommonControls.ComboBoxGlyphBackgroundFocused` |

**Desplegables y cuadros combinados: selección de entrada de texto**

![Selección de entrada de texto de cuadro desplegable/combo](../../extensibility/ux-guidelines/media/0303-173_dropdowncomboboxtextinput.png "0303-173_DropDownComboBoxTextInput")<br />Selección de entrada de texto de cuadro desplegable/combo

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Resaltar | `CommonControls.ComboBoxTextInputSelection` |

### <a name="tabular-data-grid-controls"></a>Controles de datos tabulares (cuadrícula)
Los controles de datos tabulares, también conocidos como controles de cuadrícula, son controles comunes de Visual Studio que se pueden usar para presentar grandes cantidades de datos en varias columnas. Los controles estándar de datos tabulares están en varias ubicaciones de Visual Studio: la ventana de herramientas Lista de errores, los informes de IntelliTrace y la vista de montón de memoria, entre otros. Use siempre los controles de datos tabulares estándar que se proporcionan. En raras ocasiones, podría no tener acceso a los controles estándar de datos tabulares. En estos casos, use los siguientes nombres de token para asegurarse de que la interfaz de usuario sea coherente con otros controles de datos tabulares de Visual Studio.

![Control de datos tabulares/cuadrícula (línea roja)](../../extensibility/ux-guidelines/media/0303-197_tabulardatagridcontrolredline.png "0303-197_TabularDataGridControlRedline")<br />Control de datos tabulares/cuadrícula (línea roja)

| Uso... | No utilice ... |
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

**Encabezado de columna: estado de desplazamiento**

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
| Borde | None |

**Elementos de vista de lista: estado activo**

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `TreeView.SelectedItemActive` |
| Primer plano (texto) | `TreeView.SelectedItemActiveText` |
| Borde | None |

**Elementos de vista de lista: estado inactivo**

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `TreeView.SelectedItemInactive` |
| Primer plano (texto) | `TreeView.SelectedItemInactiveText` |
| Borde | None |

### <a name="ui-text"></a>Texto de la interfaz de usuario

#### <a name="instructional-text"></a>Texto instructivo
El texto instructivo ofrece una explicación principal prominente de qué hacer en un cuadro de diálogo o página de documento.

![Texto instructivo predeterminado](../../extensibility/ux-guidelines/media/0303_InstructionalText.png "0303_InstructionalText.png")<br />Texto instructivo predeterminado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Primer plano (texto) | `Environment.ControlText` |

#### <a name="secondary-instructional-text"></a>Texto instructivo secundario
En las páginas de documentos con mucho texto y controles, algunos textos instructivos utilizan un valor de color diferente. Esto ayuda a transmitir qué información es más importante y disminuye la densidad general de los elementos de la interfaz de usuario. (Véase también la sección siguiente sobre el texto de la sugerencia.)

![Texto instructivo secundario](../../extensibility/ux-guidelines/media/0303_SecondaryInstructionalText.png "0303_SecondaryInstructionalText.png")<br />Texto instructivo secundario

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Primer plano (texto) | `Environment.ControlEditHintText` |

#### <a name="hint-text"></a>Texto de sugerencia
El texto de sugerencia aparece en un control vacío, debajo de un control o en una superficie de documento vacía para mostrar al usuario qué hacer a continuación. Puede utilizar texto de sugerencia con fondos de ventana o control.

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

**Texto de control del cuadro de búsqueda**

> Consulte [cuadros de búsqueda](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_SearchBoxes) de otros tokens de color relacionados con el control de búsqueda.

![Texto de control del cuadro de búsqueda](../../extensibility/ux-guidelines/media/0303_SearchBoxControl.png "0303_SearchBoxControl.png")<br />Texto de control del cuadro de búsqueda

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Primer plano (texto) | `SearchControl.UnfocusedWatermarkText` |

### <a name="hyperlink"></a>Hyperlink
El hipervínculo es un control que no tiene un par de primer plano/fondo. En todos los casos, utilice el color del hipervínculo de primer plano, que aparecerá correctamente en fondos oscuros, grises y blancos. Si no utiliza el token de color para el control de hipervínculo, verá el color predeterminado del sistema para "presionado", que parpadeará en rojo. Esa es la señal de que el control no está utilizando el token de color de entorno correcto.

![Hipervínculo (línea roja)](../../extensibility/ux-guidelines/media/0303-133_hyperlinkredline.png "0303-133_HyperlinkRedline")<br />Hipervínculo (línea roja)

| Uso... | No utilice ... |
| --- | --- |
| ... cuando necesite crear un hipervínculo personalizado. | ... para cualquier cosa que no sea un hipervínculo. |

**Hipervínculo: estado predeterminado**

![Hipervínculo predeterminado](../../extensibility/ux-guidelines/media/0303-134_hyperlink.png "0303-134_Hyperlink")<br />Hipervínculo predeterminado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Primer plano (texto) | `Environment.PanelHyperlink` |

**Hipervínculo: estado de desplazamiento**

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

| Uso... | No utilice ... |
| --- | --- |
| ... al crear barras de información personalizadas. | ... para elementos de interfaz de usuario que no son similares a una barra de información. |

**Barra de información: estado predeterminado**

![Barra de información predeterminada](../../extensibility/ux-guidelines/media/0303-139_infobar.png "0303-139_Infobar")<br />Barra de información predeterminada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `InfoBar.InfoBarBackground` |
| Primer plano (texto) | `InfoBar.InfoBar` |
| Borde | `InfoBar.InfoBarBorder` |

**Botón Cerrar&times;( ) de la barra de información: estado predeterminado**

![Barra de información&times;predeterminada Cerrar ( ) botón](../../extensibility/ux-guidelines/media/0303_InfobarCloseDefault.png "0303_InfobarCloseDefault.png")<br />Barra de información&times;predeterminada Cerrar ( ) botón

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `InfoBar.CloseButton` |
| Borde | `InfoBar.CloseButtonBorder` |
| Glifo | `InfoBar.CloseButtonGlyph` |

**Botón Cerrar&times;( ) de la barra de información: estado de desplazamiento**

![Botón Cerrar&times;( ) de la barra de información al pasar el ratón](../../extensibility/ux-guidelines/media/0303_InfobarCloseHover.png "0303_InfobarCloseHover.png")<br />Botón Cerrar&times;( ) de la barra de información al pasar el ratón

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `InfoBar.CloseButtonHover` |
| Borde | `InfoBar.CloseButtonHoverBorder` |
| Glifo | `InfoBar.CloseButtonHoverGlyph` |

**Botón Cerrar&times;( ) de la barra de información: estado pulsado**

![Botón Cerrar&times;( ) de la barra de información pulsada](../../extensibility/ux-guidelines/media/0303_InfobarClosePressed.png "0303_InfobarClosePressed.png")<br />Botón Cerrar&times;( ) de la barra de información pulsada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `InfoBar.CloseButtonDown` |
| Borde | `InfoBar.CloseButtonDownBorder` |
| Glifo | `InfoBar.CloseButtonDownGlyph` |

**Botón de hipervínculo de la barra de información: estado predeterminado**

![Botón de hipervínculo de la barra de información predeterminada](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonDefault.png "0303_InfobarHyperlinkButtonDefault.png")<br />Botón de hipervínculo de la barra de información predeterminada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Primer plano (texto) | `InfoBar.Hyperlink` |

**Botón de hipervínculo de la barra de información: estado de desplazamiento**

![Botón de hipervínculo de la barra de información al pasar el ratón](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonHover.png "0303_InfobarHyperlinkButtonHover.png")<br />Botón de hipervínculo de la barra de información al pasar el ratón

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Primer plano (texto) | `Infobar.HyperlinkMouseOver`<br />(Con subrayado) |

**Botón de hipervínculo de la barra de información: estado pulsado**

![Botón de hipervínculo de la barra de información pulsada](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonPressed.png "0303_InfobarHyperlinkButtonPressed.png")<br />Botón de hipervínculo de la barra de información pulsada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Primer plano (texto) | `Infobar.HyperlinkMouseDown`<br />(Con subrayado) |

**Hipervínculo en línea de la barra de información (dentro de una oración): estado predeterminado**

![Botón de hipervínculo de la barra de infoens en línea predeterminado](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonDefault.png "0303_InfobarHyperlinkButtonDefault.png")<br />Botón de hipervínculo de la barra de infoens en línea predeterminado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Primer plano (texto) | `InfoBar.Hyperlink` |

**Hipervínculo en línea de la barra de información (dentro de una oración): estado de desplazamiento**

![Botón de hipervínculo en línea de la barra de información al pasar el ratón](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkInlineHover.png "0303_InfobarHyperlinkInlineHover.png")<br />Botón de hipervínculo en línea de la barra de información al pasar el ratón

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Primer plano (texto) | `Infobar.HyperlinkMouseOver`<br />(Con subrayado) |

**Hiperenlace en línea de la barra de información (dentro de una oración): estado presionado**

![Botón de hipervínculo en línea de la barra de información pulsada](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkInlinePressed.png "0303_InfobarHyperlinkInlinePressed.png")<br />Botón de hipervínculo en línea de la barra de información pulsada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Primer plano (texto) | `Infobar.HyperlinkMouseDown`<br />(Con subrayado) |

**Botón de la barra de información: estado predeterminado**

![Botón de barra de información predeterminado](../../extensibility/ux-guidelines/media/0303_InfobarButtonDefault.png "0303_InfobarButtonDefault.png")<br />Botón de barra de información predeterminado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `InfoBar.Button` |
| Primer plano (texto) | `InfoBar.Button` |
| Borde | `InfoBar.ButtonBorder` |

**Botón de la barra de información: estado de desplazamiento**

![Botón de la barra de información al pasar el ratón](../../extensibility/ux-guidelines/media/0303_InfobarButtonHover.png "0303_InfobarButtonHover.png")<br />Botón de la barra de información al pasar el ratón

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `InfoBar.ButtonMouseOver` |
| Primer plano (texto) | `InfoBar.ButtonMouseOver` |
| Borde | `InfoBar.ButtonMouseOverBorder` |

**Botón de la barra de información: estado pulsado**

![Botón de barra de información pulsado](../../extensibility/ux-guidelines/media/0303_InfobarButtonPressed.png "0303_InfobarButtonPressed.png")<br />Botón de barra de información pulsado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `InfoBar.ButtonMouseDown` |
| Primer plano (texto) | `InfoBar.ButtonMouseDown` |
| Borde | `InfoBar.ButtonMouseDownBorder` |

**Botón de la barra de información: estado deshabilitado**

![Botón de barra de información desactivado](../../extensibility/ux-guidelines/media/0303_InfobarButtonDisabled.png "0303_InfobarButtonDisabled.png")<br />Botón de barra de información desactivado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `InfoBar.ButtonDisabled` |
| Primer plano (texto) | `InfoBar.ButtonDisabled` |
| Borde | `InfoBar.ButtonDisabledBorder` |

**Botón de la barra de información: estado enfocado**

![Botón de barra de información enfocado](../../extensibility/ux-guidelines/media/0303_InfobarButtonFocus.png "0303_InfobarButtonFocus.png")<br />Botón de barra de información enfocado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `InfoBar.ButtonFocus` |
| Primer plano (texto) | `InfoBar.ButtonFocus` |
| Borde | `InfoBar.ButtonFocusBorder` |

### <a name="scroll-bars"></a>Barras de desplazamiento
Las barras de desplazamiento tienen el estilo del entorno de Visual Studio y no es necesario que se themeen. Sin embargo, puede decidir que desea aprovechar los colores utilizados en las barras de desplazamiento para que la interfaz de usuario siempre parezca coherente con esta parte del entorno de Visual Studio.

![Barra de desplazamiento (línea roja)](../../extensibility/ux-guidelines/media/0303-140_scrollbarredline.png "0303-140_ScrollbarRedline")<br />Barra de desplazamiento (línea roja)

| Uso... | No utilice ... |
| --- | --- |
| ... al crear la interfaz de usuario que desea que coincida con las barras de desplazamiento de Visual Studio. | ... para cualquier cosa que no desee que siempre coincida con la interfaz de usuario de la barra de desplazamiento. |

**Barra de desplazamiento: estado predeterminado**

![Barra de desplazamiento predeterminada](../../extensibility/ux-guidelines/media/0303-141_scrollbar.png "0303-141_Scrollbar")<br />Barra de desplazamiento predeterminada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Barra de desplazamiento | `Environment.ScrollBarBackground` |
| Primer plano (control) | `Environment.ScrollBarThumbBackground` |

**Barra de desplazamiento: estado de desplazamiento**

![Barra de desplazamiento al mantener el mouse](../../extensibility/ux-guidelines/media/0303-143_scrollbarhover.png "0303-143_ScrollbarHover")<br />Barra de desplazamiento al mantener el mouse

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Barra de desplazamiento | `Environment.ScrollBarBackground` |
| Primer plano (control) | `Environment.ScrollBarThumbMouseOverBackground` |

*Barra de desplazamiento: estado pulsado**

![Barra de desplazamiento pulsada](../../extensibility/ux-guidelines/media/0303-145_scrollbarpressed.png "0303-145_ScrollbarPressed")<br />Barra de desplazamiento pulsada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Barra de desplazamiento | `Environment.ScrollBarBackground` |
| Primer plano (control) | `Environment.ScrollBarThumbPressedBackground` |

**Flecha de barra de desplazamiento: estado predeterminado**

![Flecha de barra de desplazamiento predeterminada](../../extensibility/ux-guidelines/media/0303-142_scrollbararrow.png "0303-142_ScrollbarArrow")<br />Flecha de barra de desplazamiento predeterminada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.ScrollBarArrowBackground`<br />(Establecer en el mismo color que la barra de desplazamiento.) |
| Primer plano (glifo) | `Environment.ScrollBarArrowGlyph` |

**Flecha de la barra de desplazamiento: estado de desplazamiento**

![Flecha de barra de desplazamiento al mantener el mouse](../../extensibility/ux-guidelines/media/0303-144_scrollbararrowhover.png "0303-144_ScrollbarArrowHover")<br />Flecha de barra de desplazamiento al mantener el mouse

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.ScrollBarArrowMouseOverBackground`<br />(Establecer en el mismo color que la barra de desplazamiento.) |
| Primer plano (glifo) | `Environment.ScrollBarArrowGlyphMouseOver` |

**Flecha de la barra de desplazamiento: estado pulsado**

![Flecha de barra de desplazamiento pulsada](../../extensibility/ux-guidelines/media/0303-146_scrollbararrowpressed.png "0303-146_ScrollbarArrowPressed")<br />Flecha de barra de desplazamiento pulsada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.ScrollBarArrowPressedBackground`<br />(Establecer en el mismo color que la barra de desplazamiento.) |
| Primer plano (glifo) | `Environment.ScrollBarArrowGlyphPressed` |

### <a name="search-boxes"></a><a name="BKMK_SearchBoxes"></a>Cuadros de búsqueda
Siempre que sea posible, use el control de búsqueda común proporcionado por el entorno de Visual Studio. Los colores del cuadro de búsqueda se encuentran en la categoría "SearchControl" del archivo **ShellColors.pkgdef** , que contiene los nombres de token para el campo de entrada, el botón de acción, el botón desplegable y el menú desplegable.

Un cuadro de búsqueda puede tener uno de varios estados, algunos de los cuales son mutuamente excluyentes:

- "Con foco" o "sin foco" se refiere a si el cursor está en el cuadro de texto.

- "Activo" o "inactivo" se refiere a si el usuario ha especificado una consulta de búsqueda en el cuadro de texto.

- "Desplazar el puntero" significa que el usuario ha colocado el puntero sobre el cuadro de búsqueda con el mouse (este estado invalida todos los demás estados).

- "Deshabilitado" significa que la función de búsqueda se ha desactivado para el contexto actual.

![Cuadro de búsqueda (línea roja)](../../extensibility/ux-guidelines/media/0303-110_searchboxredline.png "0303-110_SearchBoxRedline")<br />Cuadro de búsqueda (línea roja)

| Uso... | No utilice ... |
| --- | --- |
| ... cuando está diseñando un cuadro de búsqueda personalizado. | ... para cualquier cosa que no sea un cuadro de búsqueda. |
| | ... para cualquier cosa que no quieras que siempre coincida con la interfaz de usuario del cuadro de búsqueda. |

**Campo de entrada de búsqueda focalizado**

![Campo de entrada de búsqueda focalizado](../../extensibility/ux-guidelines/media/0303-111_searchinputfieldfocused.png "0303-111_SearchInputFieldFocused")<br />Campo de entrada de búsqueda focalizado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `SearchControl.FocusedBackground` |
| Primer plano (texto) | `SearchControl.FocusedBackground` |
| Borde | `SearchControl.FocusedBorder` |
| Separador | `SearchControl.FocusedDropDownSeparator` |

**Campo de entrada de búsqueda activo y desenfocado**

![Campo de entrada de búsqueda no enfocado](../../extensibility/ux-guidelines/media/0303-114_searchinputfieldunfocused.png "0303-114_SearchInputFieldUnfocused")<br />Campo de entrada de búsqueda activo y desenfocado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `SearchControl.SearchActiveBackground` |
| Primer plano (texto) | `SearchControl.SearchActiveBackground` |
| Borde | `SearchControl.UnfocusedBorder` |
| Separador | `SearchControl.DropDownSeparator` |

**Campo de entrada de búsqueda desenfocado e inactivo**

![Campo de entrada de búsqueda desenfocado e inactivo](../../extensibility/ux-guidelines/media/0303-114-1_searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br />Campo de entrada de búsqueda desenfocado e inactivo

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
| Borde | None |
| Separador | `SearchControl.FocusedDropDownSeparator` |

**Campo de entrada de búsqueda deshabilitado**

![Campo de entrada de búsqueda deshabilitado](../../extensibility/ux-guidelines/media/0303-121_searchinputfielddisabled.png "0303-121_SearchInputFieldDisabled")<br />Campo de entrada de búsqueda deshabilitado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `SearchControl.Disabled` |
| Primer plano (texto) | `SearchControl.Disabled` |
| Borde | `SearchControl.DisabledBorder` |
| Separador | `SearchControl.DropDownSeparator` |

**Botón de acción de búsqueda focalizada**

![Botón de acción de búsqueda enfocado](../../extensibility/ux-guidelines/media/0303-112_searchactionbuttonfocused.png "0303-112_SearchActionButtonFocused")<br />Botón de acción de búsqueda focalizada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | None |
| Primer plano (glifo de búsqueda) | `SearchControl.SearchGlyph` |
| Primer plano (glifo de detención) | `SearchControl.StopGlyph` |
| Primer plano (glifo de borrado) | `SearchControl.ClearGlyph` |
| Borde | N/D |

**Botón de acción de búsqueda desenfocada**

![Botón de acción de búsqueda desenfocada](../../extensibility/ux-guidelines/media/0303-115_searchactionbuttonunfocused.png "0303-115_SearchActionButtonUnfocused")<br />Botón de acción de búsqueda desenfocada

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

**Botón de acción de búsqueda deshabilitado**

![Botón de acción de búsqueda deshabilitado](../../extensibility/ux-guidelines/media/0303-122_searchactionbuttondisabled.png "0303-122_SearchActionButtonDisabled")<br />Botón de acción de búsqueda deshabilitado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | None |
| Primer plano (glifo) | `SearchControl.ActionButtonDisabledGlyph` |
| Borde | None |

**Botón desplegable de búsqueda focalizada**

![Botón desplegable de búsqueda focalizada](../../extensibility/ux-guidelines/media/0303-113_searchdropdownbuttonfocused.png "0303-113_SearchDropdownButtonFocused")<br />Botón desplegable de búsqueda focalizada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `SearchControl.FocusedDropDownButton` |
| Primer plano (glifo) | `SearchControl.FocusedDropDownButtonGlyph` |
| Borde | `SearchControl.FocusedDropDownButtonBorder` |

**Botón desplegable búsqueda desenfocada**

![Botón desplegable búsqueda desenfocada](../../extensibility/ux-guidelines/media/0303-116_searchdropdownbuttonunfocused.png "0303-116_SearchDropdownButtonUnfocused")<br />Botón desplegable búsqueda desenfocada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `SearchControl.UnfocusedDropDownButton` |
| Primer plano (glifo) | `SearchControl.UnfocusedDropDownButtonGlyph` |
| Borde | `SearchControl.UnfocusedDropDownButtonBorder` |

**Botón desplegable de búsqueda presionado**

![Botón desplegable de búsqueda presionado](../../extensibility/ux-guidelines/media/0303-116-2_searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")<br />Botón desplegable de búsqueda presionado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `SearchControl.MouseDownDropDownButton` |
| Primer plano (glifo) | `SearchControl.MouseDownDropDownButtonGlyph` |
| Borde | `SearchControl.MouseDownDropDownButtonBorder` |

**Botón desplegable de búsqueda deshabilitado**

![Botón desplegable de búsqueda deshabilitado](../../extensibility/ux-guidelines/media/0303-123_searchdropdownbuttondisabled.png "0303-123_SearchDropdownButtonDisabled")<br />Botón desplegable de búsqueda deshabilitado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | None |
| Primer plano (glifo) | `SearchControl.DisabledDownButtonGlyph` |
| Borde | None |

#### <a name="search-drop-down-lists"></a>Listas desplegables de búsqueda
El menú desplegable del cuadro de búsqueda tiene el potencial de ser un poco más complejo que otros menús desplegables en Visual Studio. Las secciones "búsquedas sugeridas" y "opciones de búsqueda" pueden aparecer solas o juntas en el menú, y cada una de ellas se colorea por separado. Además, estas secciones están separadas por una línea cuando aparecen juntas y un borde rodea todo el menú desplegable.

![Lista desplegable de búsqueda (línea roja)](../../extensibility/ux-guidelines/media/0303-124_searchdropdownredline.png "0303-124_SearchDropdownRedline")<br />Lista desplegable de búsqueda (línea roja)

| Uso... | No utilice ... |
| --- | --- |
| ... cuando está creando una lista desplegable de búsqueda personalizada. | ... para listas desplegables que aparecen en otros contextos. |
| ... los nombres de token correctos para los componentes de lista correctos. | ... en cualquier combinación de fondo/primer plano que no sea especificada. |

**Elementos de la lista desplegable de búsqueda**

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Borde | `SearchControl.PopupBorder` |
| Separador | `SearchControl.PopupSectionHeaderSeparator` |
| Shadow | `Environment.DropShadowBackground` |

**Búsquedas sugeridas: estado predeterminado**

![Búsquedas sugeridas por defecto](../../extensibility/ux-guidelines/media/0303-125_searchsuggested.png "0303-125_SearchSuggested")<br />Búsquedas sugeridas por defecto

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `SearchControl.PopupItemsListBackgroundGradientBegin`<br />(Se detiene el degradado para este token no utilizado en la interfaz de usuario temática.) |
| Primer plano (texto) | `SearchControl.PopupItemText` |

**Búsquedas sugeridas: estado de desplazamiento**

![Búsquedas sugeridas al pasar el ratón](../../extensibility/ux-guidelines/media/0303-128_searchsuggestedhover.png "0303-128_SearchSuggestedHover")<br />Búsquedas sugeridas al pasar el ratón

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br />(Se detiene el degradado para este token no utilizado en la interfaz de usuario temática.) |
| Primer plano (texto) | `SearchControl.PopupMouseOverItemText` |
| Borde | `SearchControl.PopupControlMouseOverBorder` |

**Opciones de búsqueda: estado predeterminado**

![Casilla de verificación de búsqueda](../../extensibility/ux-guidelines/media/0303-126_searchcheckbox.png "0303-126_SearchCheckbox")<br />Opciones de búsqueda predeterminadas (casilla de verificación)

![Opciones de búsqueda](../../extensibility/ux-guidelines/media/0303-127_searchoptions.png "0303-127_SearchOptions")<br />Opciones de búsqueda predeterminadas (enlace)

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `SearchControl.PopupSectionBackgroundGradientBegin`<br />(Se detiene el degradado para este token no utilizado en la interfaz de usuario temática.) |
| Primer plano (texto de casilla) | `SearchControl.PopupCheckboxText` |
| Primer plano (texto de vínculo) | `SearchControl.PopupButtonText` |
| Fondo de encabezado | `SearchControl.PopupSectionHeaderGradientBegin`<br />(Se detiene el degradado para este token no utilizado en la interfaz de usuario temática.) |
| Primer plano (texto de encabezado) | `SearchControl.PopupSectionHeaderText` |

**Opciones de búsqueda: estado de desplazamiento**

![Opciones de búsqueda (casilla de verificación) al mantener el mouse](../../extensibility/ux-guidelines/media/0303-129_searchcheckboxhover.png "0303-129_SearchCheckboxHover")<br />Opciones de búsqueda (casilla de verificación) al mantener el mouse

![Opciones de búsqueda (enlace) al mantener el mouse](../../extensibility/ux-guidelines/media/0303-130_searchoptionshover.png "0303-130_SearchOptionsHover")<br />Opciones de búsqueda (enlace) al mantener el mouse

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br />(Se detiene el degradado para este token no utilizado en la interfaz de usuario temática.) |
| Primer plano (texto de casilla) | `SearchControl.PopupCheckboxMouseDownText` |
| Primer plano (texto de vínculo) | `SearchControl.PopupButtonMouseDownText` |
| Borde | `SearchControl.PopupControlMouseOverBorder` |

**Opciones de búsqueda: estado presionado**

![Opciones de búsqueda pulsadas (casilla de verificación)](../../extensibility/ux-guidelines/media/0303-131_searchsuggestedpressed.png "0303-131_SearchSuggestedPressed")<br />Opciones de búsqueda pulsadas (casilla de verificación)

![Opciones de búsqueda prensadas (enlace)](../../extensibility/ux-guidelines/media/0303-132_searchoptionspressed.png "0303-132_SearchOptionsPressed")<br />Opciones de búsqueda prensadas (enlace)

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo de casilla | `SearchControl.PopupControlMouseDownBackgroundGradientBegin`<br />`SearchControl.PopupControlMouseDownBackgroundGradientEnd`<br />(Se detiene el degradado para este token no utilizado en la interfaz de usuario temática.) |
| Primer plano (texto de casilla) | `SearchControl.PopupCheckboxMouseDownText` |
| Fondo de vínculo | `SearchControl.PopupButtonMouseDownBackgroundGradientBegin`<br />(Se detiene el degradado para este token no utilizado en la interfaz de usuario temática.) |
| Primer plano (texto de vínculo) | `SearchControl.PopupButtonMouseDownText` |

### <a name="tree-views"></a><a name="BKMK_TreeView"></a>Vistas a los árboles
Varias ventanas de herramientas, como el Explorador de soluciones, el Explorador de servidores y `TreeView` la vista de clases, implementan un esquema organizativo jerárquico cuyos colores se controlan mediante nombres de color en la categoría. Todos los elementos de una vista de árbol tienen colores de fondo y de texto. Los elementos que tienen elementos secundarios anidados también tienen glifos que indican si el elemento está expandido o contraído.

![Vista de árbol (línea roja)](../../extensibility/ux-guidelines/media/0303-147_treeviewredline.png "0303-147_TreeViewRedline")<br />Vista de árbol (línea roja)

| Uso... | No utilice ... |
| --- | --- |
| ... en cualquier lugar que necesite implementar una vista organizativa jerárquica. | ... para cualquier cosa que no sea similar a una vista de árbol. |
| | ... en cualquier combinación de fondo/primer plano que no sea especificada. |

**Elemento de vista de árbol: estado predeterminado**

![Elemento de vista de árbol predeterminado](../../extensibility/ux-guidelines/media/0303-148_treeview.png "0303-148_TreeView")<br />Elemento de vista de árbol predeterminado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `TreeView.Background` |
| Primer plano (texto) | `TreeView.Background` |
| Primer plano (glifo) | `TreeView.Glyph` |
| Borde | None |

**Elemento de vista de árbol: estado de desplazamiento**

![Elemento de vista de árbol al pasar el ratón](../../extensibility/ux-guidelines/media/0303-149_treeviewhover.png "0303-149_TreeViewHover")<br />Elemento de vista de árbol al pasar el ratón

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `TreeView.Background` |
| Primer plano (texto) | `TreeView.Background` |
| Primer plano (glifo) | `TreeView.GlyphMouseOver` |
| Borde | None |

**Elemento de vista de árbol: arrastre sobre el estado**

![Elemento de vista de árbol al arrastrar sobre](../../extensibility/ux-guidelines/media/0303-150_treeviewdragover.png "0303-150_TreeViewDragOver")<br />Elemento de vista de árbol al arrastrar sobre

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `TreeView.DragOverItem` |
| Primer plano (texto) | `TreeView.DragOverItem` |
| Primer plano (glifo) | `TreeView.DragOverItemGlyph` |
| Borde | None |

**Elemento de vista de árbol: seleccionado, estado enfocado**

![Elemento de vista de árbol seleccionado y enfocado](../../extensibility/ux-guidelines/media/0303-151_treeviewfocused.png "0303-151_TreeViewFocused")<br />Elemento de vista de árbol seleccionado y enfocado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `TreeView.SelectedItemActive` |
| Primer plano (texto) | `TreeView.SelectedItemActive` |
| Primer plano (glifo) | `TreeView.SelectedItemActiveGlyph` |
| Borde | `TreeView.FocusVisualBorder` |

**Elemento de vista de árbol: seleccionado, estado desenfocado**

![Elemento de vista de árbol seleccionado y desenfocado](../../extensibility/ux-guidelines/media/0303-152_treeviewunfocused.png "0303-152_TreeViewUnfocused")<br />Elemento de vista de árbol seleccionado y desenfocado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `TreeView.SelectedItemInactive` |
| Primer plano (texto) | `TreeView.SelectedItemInactive` |
| Primer plano (glifo) | `TreeView.SelectedItemInactiveGlyph` |
| Borde | None |

**Elemento de vista de árbol: estado de desplazamiento, selección y enfoque**

![Elemento de vista de árbol seleccionado y enfocado al mantener el mouse](../../extensibility/ux-guidelines/media/0303-153_treeviewfocusedhover.png "0303-153_TreeViewFocusedHover")<br />Elemento de vista de árbol seleccionado y enfocado al mantener el mouse

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `TreeView.SelectedItemActive` |
| Primer plano (texto) | `TreeView.SelectedItemActive` |
| Primer plano (glifo) | `TreeView.SelectedItemActiveGlyphMouseOver` |
| Borde | `TreeView.FocusVisualBorder` |

**Elemento de vista de árbol: estado de desplazamiento, selección y desenfocado**

![Elemento de vista de árbol seleccionado y desenfocado al mantener el mouse](../../extensibility/ux-guidelines/media/0303-154_treeviewunfocusedhover.png "0303-154_TreeViewUnfocusedHover")<br />Elemento de vista de árbol seleccionado y desenfocado al mantener el mouse

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `TreeView.SelectedItemInactive` |
| Primer plano (texto) | `TreeView.SelectedItemInactive` |
| Primer plano (glifo) | `TreeView.SelectedItemActiveGlyphMouseOver` |
| Borde | None |

## <a name="shell-appearance"></a>Apariencia de Shell

### <a name="background"></a>Información previa
El fondo del entorno consta de dos niveles. El nivel inferior es un color sólido que cubre todo el IDE. El nivel superior se encuentra debajo del área de comandos y entre los canales de ocultación automática de la ventana de herramientas en los extremos izquierdo y derecho del IDE. Las capas de fondo superior e inferior se establecen en el mismo color en los temas Luz y Oscuridad.

![Fondo del shell de Visual Studio (línea roja)](../../extensibility/ux-guidelines/media/0303-187_shellbackgroundredline.png "0303-187_ShellBackgroundRedline")<br />Fondo del shell de Visual Studio (línea roja)

| Uso... | No utilice ... |
| --- | --- |
| ... para los lugares donde desea que coincida con el fondo del entorno de Visual Studio. | ... como relleno para lugares que no son superficies de fondo. |
| | ... como fondo para colocar elementos de primer plano. |

**Apariencia del vaciado de la capa inferior**

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.EnvironmentBackground` |

**Apariencia del vaciado de capa superior**

> Los delimitadores de degradado se establecen en el mismo valor de color en los temas claro y oscuro de Visual Studio 2013.

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.EnvironmentBackgroundGradientBegin`<br />`Environment.EnvironmentBackgroundGradientEnd`<br />`Environment.EnvironmentBackgroundGradientMiddle1`<br />`Environment.EnvironmentBackgroundGradientMiddle2` |

### <a name="command-shelf"></a>Área de comandos
Para los fondos del área de comandos se usan dos conjuntos de nombres de token: un conjunto para la ubicación donde se coloca la barra de menús y uno para la ubicación donde se colocan las barras de comandos. Un grupo individual de la barra de comandos tiene sus propios valores de color de fondo, que se describen con más detalle en la sección "Barra de comandos". El texto de la barra de menús y la barra de comandos se describe en las secciones de barra de menús y barra de comandos, respectivamente.

![Estante de comandos de Visual Studio (línea roja)](../../extensibility/ux-guidelines/media/0303-188_commandshelfredline.png "0303-188_CommandShelfRedline")<br />Estante de comandos de Visual Studio (línea roja)

| Uso... | No utilice ... |
| --- | --- |
| ... para las áreas en las que se colocan menús o barras de herramientas. | ... para áreas que no son similares a un estante de comandos. |
|... con la combinación correcta de nombre de token de fondo/primer plano. | |

**Barra de menús del estante de comandos**

> Los delimitadores de degradado se establecen en el mismo valor de color en los temas claro y oscuro de Visual Studio 2013.

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.CommandShelfHighlightGradientBegin`<br /><br />`Environment.CommandShelfHighlightGradientMiddle`<br />`Environment.CommandShelfHighlightGradientEnd` |

**Barra de comandos del estante de comandos**

> Los delimitadores de degradado se establecen en el mismo valor de color en los temas claro y oscuro de Visual Studio 2013.

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.CommandShelfBackgroundGradientBegin`<br />`Environment.CommandShelfBackgroundGradientMiddle`<br />`Environment.CommandShelfBackgroundGradientEnd` |

## <a name="manifest-designer"></a>Diseñador de manifiestos
El Diseñador de manifiestos se creó para que resulte más fácil editar el archivo de manifiesto en los proyectos de Windows 8 y Windows Phone 8. Aunque no hay ningún marco compartido disponible para su consumo, es conveniente que haga coincidir el diseño y los colores de las pestañas de navegación u orientación con la estructura general. Para obtener más información sobre el diseño, vea [Layout for Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).

![Diseñador de manifiestos (línea roja)](../../extensibility/ux-guidelines/media/0303-175_manifestdesignerredline.png "0303-175_ManifestDesignerRedline")<br />Diseñador de manifiestos (línea roja)

| Uso... | No utilice ... |
| --- | --- |
| ... para diseñadores que son similares al Diseñador de manifiestos. | ... si tienes más de seis pestañas. |
| ... en lugar de usar controles de pestaña comunes en la parte superior de un editor dentro del documento. | ... para cualquier interfaz de usuario que no esté estructurada como el Diseñador de manifiestos. |

**Ficha seleccionada del Diseñador de manifiestos: estado predeterminado**

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `ManifestDesigner.TabActive` |
| Borde | None |

**Panel de descripción seleccionado del Diseñador de manifiestos: estado predeterminado**

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `ManifestDesigner.DescriptionPane` |

**Página de contenido seleccionado del Diseñador de manifiestos: estado predeterminado**

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `ManifestDesigner.Background` |
| Texto del asistente del cuadro de diálogo | `ManifestDesigner.WatermarkText`<br />(Este nombre de token no coincide con su función.) |

**Ficha Diseñador de manifiestos: estado no seleccionado**

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `ManifestDesigner.Tab.Inactive` |

**Ficha Diseñador de manifiestos: estado de desplazamiento**

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `ManifestDesigner.Tab.Mouseover` |

## <a name="command-structures"></a>Estructuras de comandos

### <a name="menus"></a><a name="BKMK_CommandMenus"></a>Menús
Los menús pueden producirse en varios lugares de Visual Studio: la barra de menús principal, incrustada en las ventanas de documentos o herramientas, o al hacer clic con el botón derecho en varias ubicaciones del IDE. Las implementaciones de menús asociados con otros elementos de la interfaz de usuario se describen en la sección del elemento respectivo. Se debe usar siempre la implementación de menús estándar proporcionada por el entorno de Visual Studio. Sin embargo, en algunas ocasiones podría no tener acceso a los menús estándar de Visual Studio. En estos casos, use los siguientes nombres de token para asegurarse de que la interfaz de usuario sea coherente con otros menús de Visual Studio.

![Menú Visual Studio (línea roja)](../../extensibility/ux-guidelines/media/0303-000_menuredline.png "0303-000_MenuRedline")<br />Menú Visual Studio (línea roja)

| Uso... | No utilice ... |
| --- | --- |
| ... cuando necesite crear un menú personalizado.| ... el color de fondo solo. Use siempre la combinación de primer plano y fondo tal como se especifica. |
| ... cuando tenga un nuevo componente de interfaz de usuario que desea que coincida con los menús de Visual Studio.| |

#### <a name="menu-titles"></a>Títulos del menú
Los títulos de menú constan de un fondo, un borde y el texto del título, así como un glifo opcional, que suele usarse cuando el menú se encuentra en una barra de comandos.

![Título del menú (línea roja)](../../extensibility/ux-guidelines/media/0303-001_menutitleredline.png "0303-001_MenuTitleRedline")<br />Título del menú (línea roja)

| Uso... | No utilice ... |
| --- | --- |
| ... cada vez que esté creando un título de menú personalizado. | ... para cualquier cosa que no quieras que coincida siempre con el título del menú. |
| | ... en cualquier combinación de fondo/primer plano que no sea especificada. |

**Título del menú: estado predeterminado**

![Título del menú predeterminado](../../extensibility/ux-guidelines/media/0303-002_menutitledefault.png "0303-002_MenuTitleDefault")<br />Título del menú predeterminado

![Título del menú predeterminado con glifo](../../extensibility/ux-guidelines/media/0303-003_menutitlewithglyphdefault.png "0303-003_MenuTitleWithGlyphDefault")<br />Título del menú predeterminado con glifo

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | None |
| Primer plano (texto) | `Environment.CommandBarTextActive` |
| Primer plano (glifo) | `Environment.CommandBarMenuGlyph` |
| Borde | None |

**Título del menú: estado de desplazamiento**

![Título de menú al mantener el mouse](../../extensibility/ux-guidelines/media/0303-004_menutitlehover.png "0303-004_MenuTitleHover")<br />Título de menú al mantener el mouse

![Título de menú con glifo al mantener el mouse](../../extensibility/ux-guidelines/media/0303-005_menutitlewithglyphhover.png "0303-005_MenuTitleWithGlyphHover")<br />Título de menú con glifo al mantener el mouse

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Se detiene el degradado para este token no utilizado en la interfaz de usuario temática.) |
| Primer plano (texto) | `Environment.CommandBarTextHover` |
| Primer plano (glifo) | `Environment.CommandBarMenuMouseOverGlyph` |
| Borde | `Environment.CommandBarBorder` |

**Título del menú: estado pulsado**

![Título del menú presionado](../../extensibility/ux-guidelines/media/0303-006_menutitlepressed.png "0303-006_MenuTitlePressed")<br />Título del menú presionado

![Título del menú presionado con glifo](../../extensibility/ux-guidelines/media/0303-007_menutitlewithglyphpressed.png "0303-007_MenuTitleWithGlyphPressed")<br />Título del menú presionado con glifo

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.CommandBarMenuBackgroundGradientBegin`<br/>(Se detiene el degradado para este token no utilizado en la interfaz de usuario temática.) |
| Primer plano (texto) | `Environment.CommandBarTextActive` |
| Primer plano (glifo) | `Environment.CommandBarMenuMouseDownGlyph` |
| Borde | `Environment.CommandBarMenuBorder`<br />(Solo lados izquierdo, superior y derecho.) |

**Título del menú: estado deshabilitado**

![Título del menú deshabilitado con glifo](../../extensibility/ux-guidelines/media/0303-008_menutitlewithglyphdisabled.png "0303-008_MenuTitleWithGlyphDisabled")<br />Título del menú deshabilitado con glifo

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | None |
| Primer plano (texto) | `Environment.CommandBarTextInactive` |
| Primer plano (glifo) | `Environment.CommandBarTextInactive` |
| Borde | None |

#### <a name="menu-items"></a>Elementos de menú
Un elemento de menú individual se compone del texto del menú y un icono opcional, una casilla o un glifo de submenú. Su color de fondo y de texto cambian al mantener el puntero. Este token de color es un par de primer plano y fondo.

![Revisión de elementos de menú](../../extensibility/ux-guidelines/media/0303-009_menuitemredline.png "0303-009_MenuItemRedline")

| Uso... | No utilice ... |
|---|---|
| ... para cualquier lista desplegable que se inicie desde una barra de menús o una barra de comandos. | ... para cualquier lista desplegable en otro contexto. |
| | ... en cualquier combinación de fondo/primer plano que no sea especificada. |

**Elementos del menú: estado predeterminado**

![Elementos de menú predeterminados](../../extensibility/ux-guidelines/media/0303-010_menudefault.png "0303-010_MenuDefault")<br />Elementos de menú predeterminados

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.CommandBarMenuBackgroundGradientBegin`<br />(Se detiene el degradado para este token no utilizado en la interfaz de usuario temática.) |
| Primer plano (texto) | `Environment.CommandBarTextActive` |
| Primer plano (glifo de submenú) | `Environment.CommandBarMenuSubmenuGlyph` |
| Borde | `Environment.CommandBarMenuBorder` |
| Fondo de canal de iconos | `Environment.CommandBarMenuIconBackground` |
| Separador | `Environment.CommandBarMenuSeparator` |
| Shadow | `Environment.DropShadowBackground` |

**Elementos del menú: estados marcados y seleccionados**

![Menú activado](../../extensibility/ux-guidelines/media/0303-011_menuchecked.png "0303-011_MenuChecked")<br />Elemento de menú activado

![Menú seleccionado](../../extensibility/ux-guidelines/media/0303-012_menuselected.png "0303-012_MenuSelected")<br />Elemento de menú seleccionado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Marca de verificación | `Environment.CommandBarCheckBox` |
| Fondo de marca de verificación | `Environment.CommandBarSelectedIcon` |
| Fondo de icono | `Environment.CommandBarSelected` |
| Borde de icono | `Environment.CommandBarSelectedBorder` |

**Elementos del menú: estado de desplazamiento**

![Menú al mantener el mouse](../../extensibility/ux-guidelines/media/0303-013_menuhover.png "0303-013_MenuHover")<br />Elemento del menú al pasar el ratón

![Menú activado al mantener el mouse](../../extensibility/ux-guidelines/media/0303-014_menuhoverchecked.png "0303-014_MenuHoverChecked")<br />Elemento de menú activado al pasar el ratón

![Menú seleccionado al mantener el mouse](../../extensibility/ux-guidelines/media/0303-015_menuhoverselected.png "0303-015_MenuHoverSelected")<br />Elemento de menú seleccionado al pasar el ratón

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.CommandBarMenuItemMouseOver` |
| Primer plano (texto) | `Environment.CommandBarMenuItemMouseOverText` |
| Primer plano (glifo de submenú) | `Environment.CommandBarMenuMouseOverSubmenuGlyph` |
| Marca de verificación | `Environment.CommandBarCheckBoxMouseOver` |
| Fondo de marca de verificación | `Environment.CommandBarHoverOverSelectedIcon` |
| Fondo de icono | `Environment.CommandBarHoverOverSelected` |
| Borde de icono | `Environment.CommandBarHoverOverSelectedIconBorder` |

**Elementos del menú: estado deshabilitado**

![Menú deshabilitado](../../extensibility/ux-guidelines/media/0303-016_menudisabled.png "0303-016_MenuDisabled")<br />Elemento de menú deshabilitado

![Menú deshabilitado activado](../../extensibility/ux-guidelines/media/0303-017_menudisabledchecked.png "0303-017_MenuDisabledChecked")<br />Elemento de menú deshabilitado con marca de verificación

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Primer plano (texto) | `Environment.CommandBarTextInactive` |
| Primer plano (glifo de submenú) | `Environment.CommandBarMenuSubmenuGlyph` |
| Marca de verificación | `Environment.CommandBarCheckBoxDisabled` |
| Fondo de marca de verificación | `Environment.CommandBarSelectedIconDisabled` |

### <a name="command-bars"></a>Barras de comandos
Una barra de comandos puede aparecer en varios lugares dentro del IDE de Visual Studio, especialmente el estante de comandos e incrustado en ventanas de herramientas o documentos.

En general, use siempre la implementación de menús estándar proporcionada por el entorno de Visual Studio. El uso del mecanismo estándar, garantiza que todos los detalles visuales se mostrarán correctamente y que los elementos interactivos se comportarán de forma coherente con otros controles de barra de comandos de Visual Studio. Sin embargo, si necesita crear su propia barra de comandos, asegúrese de diseñarla correctamente mediante los siguientes nombres de token.

![Límite de barra de comandos](../../extensibility/ux-guidelines/media/0303-018_commandbarredline.png "0303-018_CommandBarRedline")<br />Barra de comandos (línea roja)

![Límite de botón de desbordamiento](../../extensibility/ux-guidelines/media/0303-019_overflowbuttonredline.png "0303-019_OverflowButtonRedline")<br />Botón de desbordamiento (línea roja)

| Uso... | No utilice ... |
| --- | --- |
| ... en lugares donde necesita una barra de comandos incrustada, pero no puede usar la implementación estándar de la barra de comandos de Visual Studio. | ... para los elementos de la interfaz de usuario que no son similares a una barra de comandos. |
| | ... para componentes de barra de comandos distintos de los para los que se especifican nombres de token. |

#### <a name="command-bar-groups"></a>Grupos de barras de comandos
Un grupo de la barra de comandos se compone de un conjunto relacionado de controles de barra de comandos y puede incluir cualquier número de botones, botones de expansión, menús desplegables, cuadros combinados o menús. Los colores de dichos controles se regulan mediante nombres de token independientes y se describen individualmente en esta guía. Se usa una línea divisoria para dividir un grupo de la barra de comandos en subgrupos relacionados.

![Límite de grupo de la barra de comandos](../../extensibility/ux-guidelines/media/0303-020_commandbargroupredline.png "0303-020_CommandBarGroupRedline")<br />Grupo de barras de comandos (línea roja)

| Uso... | No utilice ... |
| --- | --- |
| ... en lugares donde necesita una barra de comandos incrustada, pero no puede usar la implementación estándar de la barra de comandos de Visual Studio. | ... para los elementos de la interfaz de usuario que no son similares a una barra de comandos. |
| | ... para componentes de barra de comandos distintos de los para los que se especifican nombres de token. |

**Grupo de barras de comandos: estado predeterminado**

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.CommandBarGradientBegin`<br />(Se detiene el degradado para este token no utilizado en la interfaz de usuario temática.) |
| Borde | `Environment.CommandBarToolBarBorder` |
| Controlador de arrastre | `Environment.CommandBarDragHandle` |
| Separador | `Environment.CommandBarToolBarSeparator`<br />`Environment.CommandBarToolBarSeparatorHighlight` |

#### <a name="command-icons"></a>Iconos de comando
![Límite de icono de comando](../../extensibility/ux-guidelines/media/0303-021_commandiconredline1.png "0303-021_CommandIconRedline1")<br />Icono de comando (línea roja)

![Icono de comando con texto en línea roja](../../extensibility/ux-guidelines/media/0303-022_commandiconredline2.png "0303-022_CommandIconRedline2")<br />Icono de comando con texto (línea roja)

| Uso... | No utilice ... |
| --- | --- |
| ... para cualquier botón que se colocará en una barra de comandos. | ... para los controles que tienen sus propios nombres de token. |
| | ... en cualquier combinación de fondo/primer plano que no sea especificada. |

**Icono de comando: estado predeterminado**

![Icono de comando predeterminado](../../extensibility/ux-guidelines/media/0303-023_commandicondefault.png "0303-023_CommandIconDefault")<br />Icono de comando predeterminado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | N/D (se hereda del fondo de la barra de comandos) |
| Primer plano (texto) | `Environment.CommandBarTextActive` |
| Borde | N/D |

**Icono de comando: estado predeterminado, seleccionado**

![Por defecto, icono de comando seleccionado](../../extensibility/ux-guidelines/media/0303-024_commandicondefaultselected.png "0303-024_CommandIconDefaultSelected")<br />Por defecto, icono de comando seleccionado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.CommandBarSelected` |
| Primer plano (texto) | `Environment.CommandBarTextSelected` |
| Borde | `Environment.CommandBarSelectedBorder` |

**Icono de comando: estados de desplazamiento o enfoque**

![Icono de comando al pasar el ratón o enfocen](../../extensibility/ux-guidelines/media/0303-025_commandiconhover.png "0303-025_CommandIconHover")<br />Icono de comando al pasar el ratón o enfocen

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Se detiene el degradado para este token no utilizado en la interfaz de usuario temática.) |
| Primer plano (texto) | `Environment.CommandBarTextHover` |
| Borde | `Environment.CommandBarBorder` |

**Icono de comando: estados de desplazamiento o enfoque, seleccionados**

![Icono de comando seleccionado al mantener el mouse o el enfoque](../../extensibility/ux-guidelines/media/0303-026_commandiconhoverselected.png "0303-026_CommandIconHoverSelected")<br />Icono de comando seleccionado al mantener el mouse o el enfoque

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.CommandBarHoverOverSelected` |
| Primer plano (texto) | `Environment.CommandBarTextHoverOverSelected` |
| Borde | `Environment.CommandBarHoverOverSelectedIconBorder` |

 **Icono de comando: estado presionado**

![Icono de comando presionado](../../extensibility/ux-guidelines/media/0303-027_commandiconpressed.png "0303-027_CommandIconPressed")<br />Icono de comando presionado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.CommandBarMouseDownBackgroundBegin`<br />(Se detiene el degradado para este token no utilizado en la interfaz de usuario temática.) |
| Primer plano (texto) | `Environment.CommandBarTextMouseDown` |
| Borde | `Environment.CommandBarBorder` |

**Icono de comando: estado deshabilitado**

![Icono de comando deshabilitado](../../extensibility/ux-guidelines/media/0303-028_commandicondisabled.png "0303-028_CommandIconDisabled")<br />Icono de comando deshabilitado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | N/D (se hereda del fondo de la barra de comandos) |
| Primer plano (texto) | `Environment.CommandBarTextInactive` |
| Borde | N/D |

#### <a name="command-bar-combo-boxes"></a><a name="BKMK_CommandComboBox"></a>Cuadros combinados de la barra de comandos

> [!IMPORTANT]
> Los cuadros combinados son similares a las listas desplegables, pero incluyen un área de texto editable. Si el menú desplegable no incluye una región de texto editable, utilice los tokens de color para los [menús desplegables](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown)de la barra de comandos.

![Barra de comandos combo box redline](../../extensibility/ux-guidelines/media/0303-029_comboboxredline.png "0303-029_ComboBoxRedline")<br />Cuadro combinado barra de comandos (línea roja)

| Uso... | No utilice ... |
| --- | --- |
| ... al crear cuadros combinados personalizados. | ... para cualquier cosa que no desee que coincida siempre con la interfaz de usuario de la barra de comandos. |
| ... al crear un control de barra de comandos que es similar a un cuadro combinado. | ... cuando tiene sin tener acceso a un cuadro combinado con estilo. |

**Campo de entrada del cuadro combinado de la barra de comandos: estado predeterminado**

![Campo de entrada del cuadro combinado de la barra de comandos](../../extensibility/ux-guidelines/media/0303-030_comboboxinputfield.png "0303-030_ComboBoxInputField")<br />Campo de entrada del cuadro combinado de la barra de comandos

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.ComboBoxBackground` |
| Primer plano (texto) | `Environment.ComboBoxText` |
| Borde | `Environment.ComboBoxBorder` |
| Separador | Sin separador |

**Botón desplegable de la barra de comandos: estado predeterminado**

![Cuadro combinado&#45;botón desplegable](../../extensibility/ux-guidelines/media/0303-031_comboboxdropdownbutton.png "0303-031_ComboBoxDropdownButton")<br />Botón desplegable de la barra de comandos

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | N/D (se hereda del fondo de la barra de comandos) |
| Primer plano (glifo) | `Environment.ComboBoxGlyph` |

**Lista desplegable de la barra de comandos: estado predeterminado**

![Lista desplegable de la barra de comandos](../../extensibility/ux-guidelines/media/0303-032_comboboxdropdownlist.png "0303-032_ComboBoxDropdownList")<br />Lista desplegable de la barra de comandos

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.ComboBoxPopupBackgroundBegin`<br />(Se detiene el degradado para este token no utilizado en la interfaz de usuario temática.) |
| Primer plano (texto) | `Environment.ComboBoxItemText` |
| Borde | `Environment.ComboBoxPopupBorder` |

**Campo de entrada del cuadro combinado de la barra de comandos: estado de desplazamiento**

![Campo de entrada del cuadro combinado de la barra de comandos al pasar el ratón](../../extensibility/ux-guidelines/media/0303-033_comboboxinputfieldhover.png "0303-033_ComboBoxInputFieldHover")<br />Campo de entrada del cuadro combinado de la barra de comandos al pasar el ratón

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.ComboBoxMouseOverBackgroundBegin`<br />(Se detiene el degradado para este token no utilizado en la interfaz de usuario temática.) |
| Primer plano (texto) | `Environment.ComboBoxMouseOverText` |
| Borde | `Environment.ComboBoxMouseOverBorder` |
| Separador | `Environment.ComboBoxMouseOverSeparator` |

 **Botón desplegable de la barra de comandos: estado de desplazamiento**

![Botón desplegable de la barra de comandos al pasar el ratón](../../extensibility/ux-guidelines/media/0303-034_comboboxdropdownbuttonhover.png "0303-034_ComboBoxDropdownButtonHover")<br />Botón desplegable de la barra de comandos al pasar el ratón

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.ComboBoxButtonMouseOverBackground` |
| Primer plano (glifo) | `Environment.ComboBoxMouseOverGlyph` |

**Lista desplegable de la barra de comandos: estado de desplazamiento**

 ![Lista desplegable de la barra de comandos al pasar el ratón](../../extensibility/ux-guidelines/media/0303-035_comboboxdropdownlisthover.png "0303-035_ComboBoxDropdownListHover")<br />Lista desplegable de la barra de comandos al pasar el ratón

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo (elemento de menú) | `Environment.ComboBoxItemMouseOverBackground` |
| Primer plano (texto) | `Environment.ComboBoxItemMouseOverText` |
| Borde (elemento de menú) | `Environment.ComboBoxItemMouseOverBorder` |

 **Campo de entrada del cuadro combinado de la barra de comandos: estado enfocado**

![Campo de entrada de cuadro combinado de barra de comandos enfocado](../../extensibility/ux-guidelines/media/0303-036_comboboxinputfieldfocused.png "0303-036_ComboBoxInputFieldFocused")<br />Campo de entrada de cuadro combinado de barra de comandos enfocado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.ComboBoxFocusedBackground` |
| Primer plano (texto) | `Environment.ComboBoxFocusedText` |
| Borde | `Environment.ComboBoxFocusedBorder` |
| Separador | `Environment.ComboBoxFocusedButtonSeparator` |

**Botón desplegable de la barra de comandos: estado enfocado**

![Botón desplegable de la barra de comandos enfocado](../../extensibility/ux-guidelines/media/0303-037_comboboxdropdownbuttonfocused.png "0303-037_ComboBoxDropdownButtonFocused")<br />Botón desplegable de la barra de comandos enfocado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.ComboBoxFocusedButtonBackground` |
| Primer plano (glifo) | `Environment.ComboBoxFocusedGlyph` |

 **Campo de entrada del cuadro combinado de la barra de comandos: estado presionado**

![Campo de entrada del cuadro combinado de la barra de comandos presionada](../../extensibility/ux-guidelines/media/0303-038_comboboxinputfieldpressed.png "0303-038_ComboBoxInputFieldPressed")<br />Campo de entrada del cuadro combinado de la barra de comandos presionada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.ComboBoxMouseDownBackground` |
| Primer plano (texto) | `Environment.ComboBoxMouseDownText` |
| Borde | `Environment.ComboBoxMouseDownBorder` |
| Separador | `Environment.ComboBoxMouseDownSeparator` |

**Botón desplegable de la barra de comandos: estado pulsado**

![Botón desplegable de la barra de comandos pulsada](../../extensibility/ux-guidelines/media/0303-039_comboboxdropdownbuttonpressed.png "0303-039_ComboBoxDropdownButtonPressed")<br />Botón desplegable de la barra de comandos pulsada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.ComboBoxButtonMouseDownBackground` |
| Primer plano (glifo) | `Environment.ComboBoxMouseDownGlyph` |

**Campo de entrada del cuadro combinado de la barra de comandos: estado deshabilitado**

![Campo de entrada del cuadro combinado de la barra de comandos desactivada](../../extensibility/ux-guidelines/media/0303-041_comboboxinputfielddisabled.png "0303-041_ComboBoxInputFieldDisabled")<br />Campo de entrada del cuadro combinado de la barra de comandos desactivada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.ComboBoxDisabledBackground` |
| Primer plano (texto) | `Environment.ComboBoxDisabledText` |
| Borde | `Environment.ComboBoxDisabledBorder` |
| Separador | Sin separador |

**Botón desplegable de la barra de comandos: estado deshabilitado**

![Botón desplegable de la barra de comandos desactivada](../../extensibility/ux-guidelines/media/0303-040_comboboxdropdownbuttondisabled.png "0303-040_ComboBoxDropdownButtonDisabled")<br />Botón desplegable de la barra de comandos desactivada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | None |
| Primer plano (glifo) | `Environment.ComboBoxDisabledGlyph` |

#### <a name="command-bar-drop-downs"></a><a name="BKMK_CommandDropDown"></a>Menús desplegables de la barra de comandos

> [!IMPORTANT]
> Las listas desplegables son similares a los cuadros combinados, pero carecen de áreas de texto editable. Si el menú desplegable incluye una región de texto editable, utilice los tokens de color para los [cuadros combinados](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox)de la barra de comandos.

![Lista desplegable de la barra de comandos (línea roja)](../../extensibility/ux-guidelines/media/0303-042_dropdownredline.png "0303-042_DropdownRedline")<br />Lista desplegable de la barra de comandos (línea roja)

| Uso... | No utilice ... |
| --- | --- |
| ... cuando se crean controles de lista desplegable personalizados. | ... para cualquier cosa que no sea similar a una lista desplegable. |
| | ... para cuadros combinados o botones divididos. |

**Campo de selección desplegable de la barra de comandos: estado predeterminado**

![Campo de selección desplegable de la barra de comandos predeterminada](../../extensibility/ux-guidelines/media/0303-043_dropdownselectionfield.png "0303-043_DropdownSelectionField")<br />Campo de selección desplegable de la barra de comandos predeterminada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.DropDownBackground` |
| Primer plano (texto) | `DropDownText` |
| Borde | `DropDownBorder` |
| Separador | Sin separador |

**Botón desplegable de la barra de comandos: estado predeterminado**

![Botón desplegable de la barra de comandos predeterminada](../../extensibility/ux-guidelines/media/0303-044_dropdownbutton.png "0303-044_DropdownButton")<br />Botón desplegable de la barra de comandos predeterminada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | None |
| Primer plano (glifo) | `Environment.DropDownGlyph` |

**Lista desplegable de la barra de comandos: estado predeterminado**

![Lista desplegable de la barra de comandos predeterminada](../../extensibility/ux-guidelines/media/0303-045_dropdownlist.png "0303-045_DropdownList")<br />Lista desplegable de la barra de comandos predeterminada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.DropDownPopupBackgroundBegin`<br />(Se detiene el degradado para este token no utilizado en la interfaz de usuario temática.) |
| Primer plano (texto) | `Environment.ComboBoxItemText` |
| Borde | `Environment.DropDownPopupBorder` |
| Shadow | `Environment.DropShadowBackground` |

**Campo de selección desplegable de la barra de comandos: estado de desplazamiento**

![Campo de selección desplegable de la barra de comandos al pasar el ratón](../../extensibility/ux-guidelines/media/0303-046_dropdownselectionfieldhover.png "0303-046_DropdownSelectionFieldHover")<br />Campo de selección desplegable de la barra de comandos al pasar el ratón

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.DropDownMouseOverBackgroundBegin`<br />(Se detiene el degradado para este token no utilizado en la interfaz de usuario temática.) |
| Primer plano (texto) | `Environment.DropDownMouseOverText` |
| Borde | `Environment.DropDownMouseOverBorder` |
| Separador | `Environment.DropDownButtonMouseOverSeparator` |

**Botón desplegable de la barra de comandos: estado de desplazamiento**

![Botón desplegable de la barra de comandos al pasar el ratón](../../extensibility/ux-guidelines/media/0303-047_dropdownbuttonhover.png "0303-047_DropdownButtonHover")<br />Botón desplegable de la barra de comandos al pasar el ratón

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.DropDownButtonMouseOverBackground` |
| Primer plano (glifo) | `Environment.DropDownMouseOverGlyph` |

**Lista desplegable de la barra de comandos: estado de desplazamiento**

![Lista desplegable de la barra de comandos al pasar el ratón](../../extensibility/ux-guidelines/media/0303-048_dropdownlisthover.png "0303-048_DropdownListHover")<br />Lista desplegable de la barra de comandos al pasar el ratón

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo (elemento de menú) | `Environment.ComboBoxItemMouseOverBackground` |
| Primer plano (texto) | `Environment.ComboBoxItemMouseOverText` |
| Borde (elemento de menú) | `Environment.ComboBoxItemMouseOverBorder` |

 **Campo de selección desplegable de la barra de comandos: estado pulsado**

![Suelte&#45;campo de selección presionado](../../extensibility/ux-guidelines/media/0303-049_dropdownselectionfieldpressed.png "0303-049_DropdownSelectionFieldPressed")<br />Campo de selección desplegable de la barra de comandos pulsada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.DropDownMouseDownBackground` |
| Primer plano (texto) | `Environment.DropDownMouseDownText` |
| Borde | `Environment.DropDownMouseDownBorder` |
| Separador | `Environment.DropDownButtonMouseDownSeparator` |

**Botón desplegable de la barra de comandos: estado pulsado**

![Botón desplegable de la barra de comandos pulsada](../../extensibility/ux-guidelines/media/0303-050_dropdownbuttonpressed.png "0303-050_DropdownButtonPressed")<br />Botón desplegable de la barra de comandos pulsada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.DropDownButtonMouseDownBackground` |
| Primer plano (glifo) | `Environment.DropDownMouseDownGlyph` |

**Campo de selección desplegable de la barra de comandos: estado deshabilitado**

![Campo de selección desplegable de la barra de comandos desactivada](../../extensibility/ux-guidelines/media/0303-051_dropdownselectionfielddisabled.png "0303-051_DropdownSelectionFieldDisabled")<br />Campo de selección desplegable de la barra de comandos desactivada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.DropDownDisabledBackground` |
| Primer plano (texto) | `Environment.DropDownDisabledText` |
| Borde | `Environment.DropDownDisabledBorder` |
| Separador | Sin separador |

**Botón desplegable de la barra de comandos: estado deshabilitado**

![Botón desplegable de la barra de comandos desactivada](../../extensibility/ux-guidelines/media/0303-052_dropdownbuttondisabled.png "0303-052_DropdownButtonDisabled")<br />Botón desplegable de la barra de comandos desactivada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | N/D |
| Primer plano (glifo) | `Environment.DropDownDisabledGlyph` |

#### <a name="command-bar-split-buttons"></a>Botones divididos en la barra de comandos
Los botones de expansión comparten muchos nombres de token con otros controles de barra de comandos como, por ejemplo, botones, menús y texto de la barra de comandos. Todos los nombres de token de acciones y botones desplegables necesarios se repiten aquí para su comodidad. Las listas desplegables de botones divididos son implementaciones de menús de la barra de [comandos.](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus)

![Límite de botón de expansión](../../extensibility/ux-guidelines/media/0303-053_splitbuttonredline.png "0303-053_SplitButtonRedline")<br />Botón de división de la barra de comandos (línea roja)

| Uso... | No utilice ... |
| --- | --- |
| ... cuando se crea un botón de división personalizado. | ... para otros tipos de botones. |
| | ... en cualquier combinación de fondo/primer plano que no sea especificada. |

**Botón de división de la barra de comandos: estado predeterminado**

![Botón de división de la barra de comandos por defecto](../../extensibility/ux-guidelines/media/0303-054_splitbutton.png "0303-054_SplitButton")<br />Botón de división de la barra de comandos por defecto

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | None |
| Primer plano (texto) | `Environment.CommandBarTextActive` |
| Primer plano (glifo) | `Environment.CommandBarSplitButtonGlyph` |
| Borde | N/D |
| Separador | N/D |

**Botón de división de la barra de comandos: estado de desplazamiento**

![Botón de división de la barra de comandos al pasar el ratón](../../extensibility/ux-guidelines/media/0303-055_splitbuttonhover.png "0303-055_SplitButtonHover")<br />Botón de división de la barra de comandos al pasar el ratón

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Se detiene el degradado para este token no utilizado en la interfaz de usuario temática.) |
| Primer plano (texto) | `Environment.CommandBarTextHover` |
| Primer plano (glifo) | `Environment.CommandBarSplitButtonMouseOverGlyph` |
| Borde | `Environment.CommandBarBorder` |
| Separador | `Environment.CommandBarSplitButtonSeparator` |

**Botón de división de la barra de comandos: estado pulsado**

![Botón de división de la barra de comandos pulsada](../../extensibility/ux-guidelines/media/0303-056_splitbuttonpressed.png "0303-056_SplitButtonPressed")<br />Botón de división de la barra de comandos pulsada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.CommandBarMouseDownBackgroundBegin`<br />(Se detiene el degradado para este token no utilizado en la interfaz de usuario temática.) |
| Primer plano (texto) | `Environment.CommandBarTextMouseDown` |
| Primer plano (glifo) | `Environment.CommandBarSplitButtonMouseDownGlyph` |
| Borde | `Environment.CommandBarBorder` |
| Separador | N/D |

**Botón de división de la barra de comandos: estado deshabilitado**

![Botón de división de la barra de comandos desactivada](../../extensibility/ux-guidelines/media/0303-057_splitbuttondisabled.png "0303-057_SplitButtonDisabled")<br />Botón de división de la barra de comandos desactivada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | N/D |
| Primer plano (texto) | `Environment.ComboBoxItemTextInactive` |
| Primer plano (glifo) | `Environment.CommandBarTextInactive` |
| Borde | N/D |
| Separador | N/D |

#### <a name="command-bar-more-options-and-overflow-buttons"></a>Barra de comandos 'Más opciones' y 'Desbordamiento' botones
El botón "Más opciones" se usa cuando un grupo de la barra de comandos se puede personalizar al agregar o quitar botones relacionados de barra de comandos. El botón "Desbordamiento" aparece cuando una barra de comandos se trunca debido a la falta de espacio horizontal y, al hacer clic en él, muestra un menú que contiene los botones de la barra de comandos que no pueden mostrarse. Los colores para estos dos botones están controlados por el mismo conjunto de nombres de token.

![Barra de comandos 'Más opciones' botón (línea roja)](../../extensibility/ux-guidelines/media/0303-058_moreoptionsredline.png "0303-058_MoreOptionsRedline")<br />Barra de comandos 'Más opciones' botón (línea roja)

| Uso... | No utilice ... |
| --- | --- |
| ... para los botones personalizados "Más opciones" o "Desbordamiento". | ... para botones que no tienen una funcionalidad similar a un botón "Más opciones" o "Desbordamiento". |

**Botones de la barra de comandos 'Más opciones' y 'Desbordamiento': estado predeterminado**

![Botón de la barra de comandos predeterminada 'Más opciones'](../../extensibility/ux-guidelines/media/0303-059_moreoptions.png "0303-059_MoreOptions")<br />Botón de la barra de comandos predeterminada 'Más opciones'

![Botón 'Desbordamiento' de la barra de comandos predeterminada](../../extensibility/ux-guidelines/media/0303-060_overflow.png "0303-060_Overflow")<br />Botón 'Desbordamiento' de la barra de comandos predeterminada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.CommandBarOptionsBackground` |
| Primer plano (glifo) | `Environment.CommandBarOptionsGlyph` |

**Botones de la barra de comandos 'Más opciones' y 'Desbordamiento': estado de desplazamiento**

![Barra de comandos 'Más opciones' al pasar el ratón](../../extensibility/ux-guidelines/media/0303-061_moreoptionshover.png "0303-061_MoreOptionsHover")<br />Barra de comandos 'Más opciones' al pasar el ratón

![Botón 'Desbordamiento' de la barra de comandos al pasar el ratón](../../extensibility/ux-guidelines/media/0303-062_overflowoptions.png "0303-062_OverflowOptions")<br />Botón 'Desbordamiento' de la barra de comandos al pasar el ratón

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.CommandBarOptionsMouseOverBackgroundBegin`<br />(Se detiene el degradado para este token no utilizado en la interfaz de usuario temática.) |
| Primer plano (glifo) | `Environment.CommandBarOptionsMouseDownGlyph` |

**Botones de la barra de comandos 'Más opciones' y 'Desbordamiento': estado pulsado**

![Botón de la barra de comandos pulsada 'Más opciones'](../../extensibility/ux-guidelines/media/0303-063_moreoptionspressed.png "0303-063_MoreOptionsPressed")<br />Botón de la barra de comandos pulsada 'Más opciones'

![Desbordamiento presionado](../../extensibility/ux-guidelines/media/0303-064_overflowpressed.png "0303-064_OverflowPressed")<br />Botón de la barra de comandos pulsada 'Desbordamiento'

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.CommandBarOptionsMouseDownBackgroundBegin`<br />(Se detiene el degradado para este token no utilizado en la interfaz de usuario temática.) |
| Primer plano (glifo) | `Environment.CommandBarOptionsMouseDownGlyph` |

## <a name="document-windows"></a>Ventanas de documento
No es necesario replicar las ventanas de documento, porque las proporciona el entorno de Visual Studio. Sin embargo, quizá prefiera aprovechar los colores que se usan en las ventanas de documento para que la interfaz de usuario se muestre siempre coherente con esta parte del entorno de Visual Studio.

Cuando utilice tokens de color de ventana de documento, tenga cuidado de usarlos solo para elementos similares y siempre en pares. Si no lo hace, es posible que obtenga resultados inesperados en la interfaz de usuario.

### <a name="document-window-frames"></a>Marcos de ventanas de documentos
Las ventanas de documento pueden estar acopladas en el IDE o flotantes como una ventana independiente. Cuando una ventana de documento está flotando fuera del IDE, todavía se encuentra en un documento bien y tiene colores de fondo, borde, texto y tabulación que son los mismos que cuando forma parte del IDE. Sin embargo, el documento se encuentra dentro de un marco que tiene su propio fondo, borde y colores de texto. Cuando las ventanas de herramientas se acoplan en el cuadro del documento, heredan el comportamiento y el color de los nombres de token de ventana de documento para sus pestañas.

![Ventana de documento acoplado (línea roja)](../../extensibility/ux-guidelines/media/0303-065_dockeddocumentwindowredline.png "0303-065_DockedDocumentWindowRedline")<br />Ventana de documento acoplado (línea roja)

![Ventana de documento flotante (línea roja)](../../extensibility/ux-guidelines/media/0303-066_floatingdocumentwindowredline.png "0303-066_FloatingDocumentWindowRedline")<br />Ventana de documento flotante (línea roja)

| Uso... | No utilice ... |
| --- | --- |
| ... en cualquier lugar en el que esté creando la interfaz de usuario que desea que coincida con la ventana del documento. | ...  para cualquier interfaz de usuario que no desee cambiar automáticamente si el shell tiene una actualización del tema. |

**Ventana de documento acoplada o flotante: estado predeterminado**

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | Depende del tipo de documento |
| Primer plano (texto) | Depende del tipo de documento |
| Borde | `Environment.ToolWindowBorder` |

**Marco de ventana de documento flotante y enfocado: estado predeterminado**

![Marco de ventana de documento flotante y enfocado por defecto](../../extensibility/ux-guidelines/media/0303-067_framefocused.png "0303-067_FrameFocused")<br />Marco de ventana de documento flotante y enfocado por defecto

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.ToolWindowFloatingFrame` |
| Primer plano (texto) | `Environment.ToolWindowFloatingFrame` |
| Primer plano (glifo) | `Environment.RaftedWindowButtonActiveGlyph` |
| Borde | `Environment.MainWindowActiveDefaultBorder` |
| Borde (glifo) | `Environment.RaftedWindowButtonActiveBorder`<br />(Establecer en transparente) |

**Marco de ventana de documento flotante y desenfocado: estado predeterminado**

![Marco de ventana de documento flotante y desenfocado por defecto](../../extensibility/ux-guidelines/media/0303-068_frameunfocused.png "0303-068_FrameUnfocused")<br />Marco de ventana de documento flotante y desenfocado por defecto

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.ToolWindowFloatingFrameInactive` |
| Primer plano (texto) | `Environment.ToolWindowFloatingFrameInactive` |
| Primer plano (glifo) | `Environment.RaftedWindowButtonInactiveGlyph` |
| Borde | `Environment.MainWindowInactiveBorder` |
| Borde (glifo) | `Environment.RaftedWindowButtonInactiveBorder`<br />(Establecer en transparente) |

**Marco de ventana de documento flotante y enfocado: estado de desplazamiento**

![Marco de ventana de documento flotante y enfocado al pasar el ratón](../../extensibility/ux-guidelines/media/0303-069_framefocusedhover.png "0303-069_FrameFocusedHover")<br />Marco de ventana de documento flotante y enfocado al pasar el ratón

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo (glifo) | `Environment.RaftedWindowButtonHoverActive` |
| Primer plano (glifo) | `Environment.RaftedWindowButtonHoverActiveGlyph` |
| Borde (glifo) | `Environment.RaftedWindowButtonHoverActiveBorder` |

**Marco de ventana de documento flotante y desenfocado: estado de desplazamiento**

![Marco de ventana de documento flotante y desenfocado al mantener el mouse](../../extensibility/ux-guidelines/media/0303-070_frameunfocusedhover.png "0303-070_FrameUnfocusedHover")<br />Marco de ventana de documento flotante y desenfocado al mantener el mouse

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo (glifo) | `EnvironmentRaftedWindowButtonHoverInactive` |
| Primer plano (glifo) | `Environment.RaftedWindowButtonHoverInactiveGlyph` |
| Borde (glifo) | `Environment.RaftedWindowButtonHoverInactiveBorder` |

**Marco de ventana de documento flotante y enfocado: estado pulsado**

![Marco de ventana de documento flotante y enfocado en la prensa](../../extensibility/ux-guidelines/media/0303-071_framefocusedpressed.png "0303-071_FrameFocusedPressed")<br />Marco de ventana de documento flotante y enfocado en la prensa

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Fondo (glifo) | `Environment.RaftedWindowButtonDown` |
| Primer plano (glifo) | `Environment.RaftedWindowButtonDownGlyph` |
| Borde (glifo) | `Environment.RaftedWindowButtonDownBorder` |

### <a name="document-tabs"></a>Pestañas de documentos
Las pestañas de documentos se colocan en el canal de pestañas para indicar los documentos que están abiertos actualmente, así como el documento actual activo o seleccionado. Las ventanas de herramientas también se pueden acoplar en el canal de pestañas de documentos si el usuario las coloca allí. En este caso, usan los mismos colores de pestaña que las ventanas de documento. Si va a crear interfaz de usuario que desea que siempre coincida con los colores de las ventanas de documento (lo que incluye las actualizaciones de temas o si se instalan nuevos temas), entonces haga referencia a estos tokens de color.

![Fichas Documento (línea roja)](../../extensibility/ux-guidelines/media/0303-072_documenttabredline.png "0303-072_DocumentTabRedline")<br />Fichas Documento (línea roja)

| Uso... | No utilice ... |
| --- | --- |
| ... en cualquier lugar en el que esté creando la interfaz de usuario que desea que coincida con las pestañas del documento y recoger automáticamente las actualizaciones del tema o los nuevos colores del tema. | ... para cualquier interfaz de usuario que no desee cambiar automáticamente cuando el shell tiene una actualización del tema. |

#### <a name="open-document-tabs"></a>Pestañas de documentos abiertos
Cada documento abierto tiene una pestaña en el canal de pestañas de documentos que muestra su nombre. Los documentos pueden estar seleccionados o abiertos en segundo plano y sus pestañas reflejan los siguientes estados:

- La pestaña seleccionada representa el documento que se muestra actualmente en el cuadro de documento. Una pestaña seleccionada tiene un borde de documento que se extiende por todo el borde superior del cuadro de documento.

- Las pestañas de fondo son las fichas de documento que no son la pestaña seleccionada actualmente. Una vez hecho clic, se convierten en la pestaña seleccionada y adquieren todos los colores de fondo, borde y texto de esos nombres de token.

![Ficha Abrir documento (línea roja)](../../extensibility/ux-guidelines/media/0303-073_opendocumenttabredline.png "0303-073_OpenDocumentTabRedline")<br />Ficha Abrir documento (línea roja)

| Uso... | No utilice ... |
| --- | --- |
| ... cuando crea pestañas de documentos personalizadas. | ... para las pestañas provisionales (versión preliminar). |
| | ... para cualquier interfaz de usuario que no desee cambiar automáticamente si el shell tiene una actualización del tema. |

**Pestaña Documento seleccionado y enfocado**

![Pestaña Documento seleccionado y enfocado](../../extensibility/ux-guidelines/media/0303-074_selectedtabfocused.png "0303-074_SelectedTabFocused")<br />Pestaña Documento seleccionado y enfocado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.FileTabSelectedGradientTop`<br />(Se detiene el degradado para este token no utilizado en la interfaz de usuario temática.) |
| Primer plano (texto) | `Environment.FileTabSelectedText` |
| Borde | `Environment.FileTabSelectedBorder`<br />(Establecer en el mismo color que el fondo.) |
| Borde de documento | `Environment.FileTabDocumentBorderBackground` |

**Pestaña Documento seleccionado y desenfocado**

![Pestaña Documento seleccionado y desenfocado](../../extensibility/ux-guidelines/media/0303-075_selectedtabunfocused.png "0303-075_SelectedTabUnfocused")<br />Pestaña Documento seleccionado y desenfocado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.FileTabInactiveGradientTop`<br />(Se detiene el degradado para este token no utilizado en la interfaz de usuario temática.) |
| Primer plano (texto) | `Environment.FileTabInactiveText` |
| Borde | `Environment.FileTabInactiveBorder`<br />(Establecer en el mismo color que el fondo.) |
| Borde de documento | `Environment.FileTabInactiveDocumentBorderBackground` |

**Ficha Documento de fondo: estado predeterminado**

![Ficha Documento de fondo predeterminado](../../extensibility/ux-guidelines/media/0303-076_backgroundtab.png "0303-076_BackgroundTab")<br />Ficha Documento de fondo predeterminado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.FileTabBackground` |
| Primer plano (texto) | `Environment.FileTabText` |
| Borde | `Environment.FileTabBorder`<br />(Establecer en el mismo color que el fondo.) |

**Ficha Documento de fondo: estado de desplazamiento**

![Ficha Documento de fondo al pasar el ratón](../../extensibility/ux-guidelines/media/0303-077_backgroundtabhover.png "0303-077_BackgroundTabHover")<br />Ficha Documento de fondo al pasar el ratón

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.FileTabHotGradientTop`<br />(Se detiene el degradado para este token no utilizado en la interfaz de usuario temática.) |
| Primer plano (texto) | `Environment.FileTabHotText` |
| Borde | `Environment.FileTabHotBorder`<br />(Establecer en el mismo color que el fondo.) |

#### <a name="preview-tab"></a>Pestaña de vista previa
También se denomina pestaña "provisional". La pestaña de vista previa aparece en el lado derecho del canal de ficha del documento cuando el usuario hace clic en un elemento de la ventana de herramientas del Explorador de soluciones. Funciona como una vista previa del documento y también proporciona al usuario la posibilidad de mantener el documento abierto en la parte izquierda del canal de pestañas de documentos. Solo se puede abrir una pestaña de vista previa a la vez. Las pestañas de vista previa tienen tanto el estado seleccionado como en segundo plano al igual que las pestañas abiertas y, además, pueden estar con y sin foco en su estado activo.

![Ficha Vista previa (línea roja)](../../extensibility/ux-guidelines/media/0303-078_previewtabredline.png "0303-078_PreviewTabRedline")<br />Ficha Vista previa (línea roja)

| Uso... | No utilice ... |
| --- | --- |
| ... en cualquier lugar en el que esté creando una vista previa provisional y desee que algún elemento coincida con el color actual de la pestaña de vista previa. | ... para cualquier tipo de documento o pestaña que no sea provisional (versión preliminar). |
| | ... para cualquier interfaz de usuario que no desee cambiar automáticamente si el shell tiene una actualización del tema. |

**Pestaña de vista previa seleccionada y enfocada**

![Pestaña de vista previa seleccionada y enfocada](../../extensibility/ux-guidelines/media/0303-079_previewtabfocused.png "0303-079_PreviewTabFocused")<br />Pestaña de vista previa seleccionada y enfocada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.FileTabProvisionalSelectedActive` |
| Primer plano (texto) | `Environment.FileTabProvisionalSelectedActiveForeground` |
| Borde | `Environment.FileTabProvisionalSelectedActiveBorder`<br />(Establecer en el mismo color que el fondo.) |
| Borde de documento | `Environment.FileTabProvisionalSelectedActiveBorder` |

**Pestaña de vista previa seleccionada y desenfocada**

![Pestaña de vista previa seleccionada y desenfocada](../../extensibility/ux-guidelines/media/0303-080_previewtabunfocused.png "0303-080_PreviewTabUnfocused")<br />Pestaña de vista previa seleccionada y desenfocada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.FileTabProvisionalSelectedInactive` |
| Primer plano (texto) | `Environment.FileTabProvisionalSelectedInactiveForeground` |
| Borde | `Environment.FileTabProvisionalSelectedInactiveBorder` |
| Borde de documento | `Environment.FileTabProvisionalSelectedInactiveBorder` |

**Pestaña de vista previa de fondo: estado predeterminado**

![Pestaña de vista previa de fondo predeterminada](../../extensibility/ux-guidelines/media/0303-081_previewbackgroundtab.png "0303-081_PreviewBackgroundTab")<br />Pestaña de vista previa de fondo predeterminada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.FileTabProvisionalInactive` |
| Primer plano (texto) | `Environment.FileTabProvisionalInactiveForeground` |
| Borde | `Environment.FileTabProvisionalInactiveBorder`<br />(Establecer en el mismo color que el fondo.) |

**Pestaña de vista previa de fondo: estado de desplazamiento**

![Pestaña de vista previa de fondo al pasar el ratón](../../extensibility/ux-guidelines/media/0303-082_previewbackgroundtabhover.png "0303-082_PreviewBackgroundTabHover")<br />Pestaña de vista previa de fondo al pasar el ratón

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.FileTabProvisionalHover` |
| Primer plano (texto) | `Environment.FileTabProvisionalHoverForeground` |
| Borde | `Environment.FileTabProvisionalHoverBorder`<br />(Establecer en el mismo color que el fondo.) |

#### <a name="document-overflow-button"></a>Botón de desbordamiento de documento
El botón de desbordamiento de documento se muestra si hay uno o varios documentos abiertos, independientemente de si hay espacio vertical en la configuración actual para que quepan todas las pestañas de documentos. El menú desplegable de desbordamiento de documentos, que se controla mediante los colores del menú de la barra de [comandos,](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus) muestra una lista de todos los documentos abiertos, tanto visibles como ocultos, y el glifo de desbordamiento cambia en función de si todos los documentos abiertos se muestran en el canal de ficha.

![Botón de desbordamiento de documento (línea roja)](../../extensibility/ux-guidelines/media/0303-083_overflowredline.png "0303-083_OverflowRedline")<br />Botón de desbordamiento de documento (línea roja)

| Uso... | No utilice ... |
| --- | --- |
| ... cuando se crea un botón de desbordamiento de documento personalizado. | ... para la interfaz de usuario que no es similar a un botón de desbordamiento. |
| | ... para los botones de desbordamiento de la barra de comandos. |

**Botón de desbordamiento de documento: estado predeterminado**

![Botón de desbordamiento de documento predeterminado](../../extensibility/ux-guidelines/media/0303-084_overflow.png "0303-084_Overflow")<br />Botón de desbordamiento de documento predeterminado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.DocWellOverflowButtonBackground` |
| Primer plano (glifo) | `Environment.DocWellOverflowButtonGlyph` |
| Borde | N/D |

**Botón de desbordamiento de documento: estado de desplazamiento**

![Botón de desbordamiento de documento al mantener el puntero](../../extensibility/ux-guidelines/media/0303-085_overflowhover.png "0303-085_OverflowHover")<br />Botón de desbordamiento de documento al mantener el puntero

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.DocWellOverflowButtonMouseOverBackground` |
| Primer plano (glifo) | `Environment.DocWellOverflowButtonMouseOverGlyph` |
| Borde | `Environment.DocWellOverflowButtonMouseOverBorder` |

**Botón de desbordamiento del documento: estado pulsado**

![Botón de desbordamiento de documentos al presionar](../../extensibility/ux-guidelines/media/0303-086_overflowpressed.png "0303-086_OverflowPressed")<br />Botón de desbordamiento de documentos al presionar

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.DocWellOverflowButtonMouseDownBackground` |
| Primer plano (glifo) | `Environment.DocWellOverflowButtonMouseDownGlyph` |
| Borde | `Environment.DocWellOverflowButtonMouseDownBorder` |

### <a name="tagging"></a>Etiquetado
Visual Studio admite el etiquetado, lo que permite al usuario declarar palabras clave de búsqueda con fines de seguimiento. Por ejemplo, los desarrolladores y los administradores de proyectos pueden usar Team Foundation Server (TFS) para etiquetar elementos de trabajo. Las tablas siguientes proporcionan nombres de colores para la etiqueta en sí y el glifo del "icono de cerrar" que aparecen en los estados Al desplazar el puntero y Seleccionado.

![Etiquetado en Visual Studio (línea roja)](../../extensibility/ux-guidelines/media/0303-176_taggingredline.png "0303-176_TaggingRedline")<br />Etiquetado en Visual Studio (línea roja)

| Uso... | No utilice ... |
| --- | --- |
| ... para la interfaz de usuario que admite el etiquetado. | ... para cualquier otro tipo de interfaz de usuario. |

#### <a name="tags"></a>Etiquetas

**Etiqueta: estado predeterminado**

![Etiqueta predeterminada](../../extensibility/ux-guidelines/media/0303-177_tag.png "0303-177_Tag")<br />Etiqueta predeterminada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Tag.Background` |
| Primer plano (texto) | `Tag.Background` |

**Etiqueta: estado de desplazamiento**

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

#### <a name="close-times-tag-glyph"></a>Cerrar&times;glifo de etiqueta ( )

**Cerrar&times;( ) glifo de etiqueta: estado predeterminado**

![Glifo de&times;etiqueta De cierre predeterminado ( )](../../extensibility/ux-guidelines/media/0303-181_tagglyph.png "0303-181_TagGlyph")<br />Glifo de&times;etiqueta De cierre predeterminado ( )

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | N/D |
| Primer plano (glifo) | `Tag.TagHoverGlyph` |

**Cerrar&times;( ) glifo de etiqueta: estado de desplazamiento**

![Cerrar&times;( ) glifo de etiqueta al mantener el mouse](../../extensibility/ux-guidelines/media/0303-182_tagglyphhover.png "0303-182_TagGlyphHover")<br />Cerrar&times;( ) glifo de etiqueta al mantener el mouse

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Tag.TagHoverGlyphHoverBackground` |
| Primer plano (glifo) | `Tag.TagHoverGlyphHover` |
| Borde | `Tag.TagHoverGlyphHoverBorder` |

**Cerrar&times;( ) glifo de etiqueta: estado presionado**

![Pictograma de etiqueta De cierre presionado (&times;)](../../extensibility/ux-guidelines/media/0303-183_tagglyphpressed.png "0303-183_TagGlyphPressed")<br />Pictograma de etiqueta De cierre presionado (&times;)

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Tag.TagHoverGlyphPressedBackground` |
| Primer plano (glifo) | `Tag.TagHoverGlyphPressed` |
| Borde | `Tag.TagHoverGlyphPressedBorder` |

**Etiqueta seleccionada con&times;glifo Cerrar ( ): estado predeterminado**

![Etiqueta seleccionada predeterminada&times;con glifo Cerrar ( )](../../extensibility/ux-guidelines/media/0303-184_tagselected.png "0303-184_TagSelected")<br />Etiqueta seleccionada predeterminada&times;con glifo Cerrar ( )

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | N/D |
| Primer plano (glifo) | `Tag.TagSelectedGlyph` |

**Etiqueta seleccionada con&times;el glifo Cerrar ( ): estado de desplazamiento: estado de desplazamiento**

![Etiqueta seleccionada con&times;el glifo Cerrar ( ) al mantener el mouse](../../extensibility/ux-guidelines/media/0303-185_tagselectedhover.png "0303-185_TagSelectedHover")<br />Etiqueta seleccionada con&times;el glifo Cerrar ( ) al mantener el mouse

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Tag.TagSelectedGlyphHoverBackground` |
| Primer plano (glifo) | `Tag.TagSelectedGlyphHover` |
| Borde | `Tag.TagSelectedGlyphHoverBorder` |

**Etiqueta seleccionada con&times;glifo Cerrar ( ): estado presionado**

![Etiqueta seleccionada y presionada&times;con el glifo Cerrar ( )](../../extensibility/ux-guidelines/media/0303-186_tagselectedpressed.png "0303-186_TagSelectedPressed")<br />Etiqueta seleccionada y presionada&times;con el glifo Cerrar ( )

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Tag.TagSelectedGlyphPressedBackground` |
| Primer plano (glifo) | `Tag.TagSelectedGlyphPressed` |
| Borde | `Tag.TagSelectedGlyphPressedBorder` |

## <a name="tool-windows"></a>Ventanas de herramientas
No es necesario replicar las ventanas de herramientas, ya que las proporciona el entorno de Visual Studio. Sin embargo, quizá prefiera aprovechar los colores que se usan en las ventanas de herramientas para que la interfaz de usuario se muestre siempre coherente con esta parte del entorno de Visual Studio.

![Ventana de herramientas (línea roja)](../../extensibility/ux-guidelines/media/0303-087_toolwindowredline.png "0303-087_ToolWindowRedline")<br />Ventana de herramientas (línea roja)

| Uso... | No utilice ... |
| --- | --- |
| ... en cualquier lugar en el que esté creando la interfaz de usuario que desea que coincida con las ventanas de herramientas. | ... para cualquier interfaz de usuario que no desee cambiar automáticamente si el shell tiene una actualización del tema. |

### <a name="tool-window-frame"></a>Marco de ventana de herramientas
Las ventanas de herramientas de Visual Studio se usan para diversas tareas y pueden estar en uno de varios estados diferentes. Si una ventana de herramientas está abierta, se puede asignar a cualquiera de los cuatro lados del área del documento. Estas ventanas también pueden flotar fuera del IDE, lo que permite reubicarlas en cualquier lugar dentro de la pantalla del usuario. Las ventanas flotantes siempre se colocan arriba del IDE. Por último, las ventanas de herramientas se pueden acoplar como ventanas de documento y aparecen como una pestaña en el cuadro de documento. Las ventanas de herramientas que se han acoplado como ventanas de documento se colorean en parte mediante los nombres de token de ventana de documento.

![Marco de la ventana de la herramienta (línea roja)](../../extensibility/ux-guidelines/media/0303-088_toolwindowframeredline.png "0303-088_ToolWindowFrameRedline")<br />Marco de la ventana de la herramienta (línea roja)

| Uso... | No utilice ... |
| --- | --- |
| ...  en cualquier lugar en el que esté creando la interfaz de usuario que desea que coincida con las ventanas de herramientas. | ... para cualquier interfaz de usuario que no desee cambiar automáticamente si el shell tiene una actualización del tema. |

**Ventana de herramientas acoplada**

![Ventana de herramientas acoplada](../../extensibility/ux-guidelines/media/0303-089_toolwindowdocked.png "0303-089_ToolWindowDocked")<br />Ventana de herramientas acoplada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.ToolWindowBackground` |
| Borde | `Environment.ToolWindowBorder` |

**Ventana de herramientas flotante y enfocada**

![Ventana de herramientas flotante y enfocada](../../extensibility/ux-guidelines/media/0303-090_toolwindowfocused.png "0303-090_ToolWindowFocused")<br />Ventana de herramientas flotante y enfocada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.ToolWindowBackground` |
| Borde | `Environment.MainWindowActiveDefaultBorder` |

**Ventana de herramientas flotante y desenfocada**

![Ventana de herramientas flotante y desenfocada](../../extensibility/ux-guidelines/media/0303-091_toolwindowunfocused.png "0303-091_ToolWindowUnfocused")<br />Ventana de herramientas flotante y desenfocada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.ToolWindowBackground` |
| Borde | `Environment.MainWindowInactiveBorder` |

### <a name="toolbox-like-windows"></a>Ventanas tipo caja de herramientas
El cuadro de herramientas es una de las ventanas de herramientas comunes más utilizadas en Visual Studio. Es esencialmente un control de árbol con un tema especial y estilo aplicado.

![Ventana de tipo Caja de herramientas (línea roja)](../../extensibility/ux-guidelines/media/0303-189_toolboxredline.png "0303-189_ToolboxRedline")<br />Ventana de tipo Caja de herramientas (línea roja)

| Uso... | No utilice ... |
| --- | --- |
| ... cuando está diseñando una ventana de herramientas que desea que siempre sea coherente con la caja de herramientas del shell. | ... para cualquier cosa que no sea similar a la interfaz de usuario del cuadro de herramientas, o si no está seguro de si la interfaz de usuario tendrá problemas si cambian los colores del cuadro de herramientas del shell. |

**Nodos de Toolbox: estado predeterminado**

![Nodo primario de la caja de herramientas predeterminada](../../extensibility/ux-guidelines/media/0303-190_toolboxparentnode.png "0303-190_ToolboxParentNode")<br />Nodo primario de la caja de herramientas predeterminada

![Nodo secundario de la caja de herramientas predeterminada](../../extensibility/ux-guidelines/media/0303-191_toolboxchildnode.png "0303-191_ToolboxChildNode")<br />Nodo secundario de la caja de herramientas predeterminada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.ToolboxContent`<br />(Encabezados) |
| Información previa | `Environment.ToolWindowBackground`<br />(Elementos individuales o ventana completa si no hay controles disponibles) |
| Borde | None |
| Primer plano (glifo) | `Environment.ToolboxContent` |
| Primer plano (texto) | `Environment.ToolboxContent` |

**Nodos secundarios de Toolbox: estado de desplazamiento**

![Nodo secundario de cuadro de herramientas al mantener el mouse](../../extensibility/ux-guidelines/media/0303-192_toolboxchildnodehover.png "0303-192_ToolboxChildNodeHover")<br />Nodo secundario de cuadro de herramientas al mantener el mouse

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.ToolboxContentMouseOver`<br />(Sólo artículos individuales) |
| Borde | None |
| Primer plano (texto) | `Environment.ToolboxContentMouseOver`<br />(Sólo artículos individuales) |

**Nodos de caja de herramientas seleccionados: estado enfocado**

![Nodo principal de la caja de herramientas seleccionado y centrado](../../extensibility/ux-guidelines/media/0303-193_toolboxparentnodefocused.png "0303-193_ToolboxParentNodeFocused")<br />Nodo principal de la caja de herramientas seleccionado y centrado

![Nodo secundario de la caja de herramientas centrado y seleccionado](../../extensibility/ux-guidelines/media/0303-194_toolboxchildnodefocused.png "0303-194_ToolboxChildNodeFocused")<br />Nodo secundario de la caja de herramientas centrado y seleccionado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `TreeView.SelectedItemActive`<br />De categoría [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Borde | `TreeView.FocusVisualBorder`<br />De categoría [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Primer plano (glifo) | `TreeView.SelectedItemActive`<br />De categoría [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Primer plano (texto) | `TreeView.SelectedItemActive`<br />De categoría [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |

**Nodos de caja de herramientas seleccionados: estado desenfocado**

![Nodo primario de la caja de herramientas seleccionado y desenfocado](../../extensibility/ux-guidelines/media/0303-195_toolboxparentnodeunfocused.png "0303-195_ToolboxParentNodeUnfocused")<br />Nodo primario de la caja de herramientas seleccionado y desenfocado

![Nodo secundario de la caja de herramientas seleccionado y desenfocado](../../extensibility/ux-guidelines/media/0303-196_toolboxchildnodeunfocused.png "0303-196_ToolboxChildNodeUnfocused")<br />Nodo secundario de la caja de herramientas seleccionado y desenfocado

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `TreeView.SelectedItemInactive`<br />De categoría [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Borde | None |
| Primer plano (glifo) | `TreeView.SelectedItemInactive`<br />De categoría [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Primer plano (texto) | `TreeView.SelectedItemInactive`<br />De categoría [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |

### <a name="tool-window-title-bar"></a>Barra de título de la ventana de herramientas
El borde de la barra de título no es un borde verdadero, es una línea gruesa en la parte superior de la barra de título. No tiene un nombre de token para su estado desenfocado.

![Barra de título de la ventana de herramientas (línea roja)](../../extensibility/ux-guidelines/media/0303-092_toolwindowtitlebarredline.png "0303-092_ToolWindowTitleBarRedline")<br />Barra de título de la ventana de herramientas (línea roja)

| Uso... | No utilice ... |
| --- | --- |
| ... en cualquier lugar en el que esté creando la interfaz de usuario que desea que coincida con las ventanas de herramientas. | ... para cualquier interfaz de usuario que no desee cambiar automáticamente si el shell tiene una actualización del tema. |

**Barra de título con foco**

![Barra de título con foco](../../extensibility/ux-guidelines/media/0303-093_titlebarfocused.png "0303-093_TitleBarFocused")<br />Barra de título con foco

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.TitleBarActiveGradientBegin`<br />(Se detiene el degradado para este token no utilizado en la interfaz de usuario temática.) |
| Primer plano (texto) | `Environment.TitleBarActiveText` |
| Borde | `Environment.TitleBarActiveBorder`<br />(Establecer en el mismo color que el fondo.) |
| Controlador de arrastre | `Environment.TitleBarDragHandleActive` |

**Barra de título sin foco**

![Barra de título no enfocada](../../extensibility/ux-guidelines/media/0303-094_titlebarunfocused.png "0303-094_TitleBarUnfocused")<br />Barra de título sin foco

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.TitleBarInactiveGradientBegin`<br />(Se detiene el degradado para este token no utilizado en la interfaz de usuario temática.) |
| Primer plano (texto) | `Environment.TitleBarInactiveText` |
| Borde | N/D |
| Controlador de arrastre | `Environment.TitleBarDragHandle` |

#### <a name="tool-window-title-bar-buttons"></a>Botones de la barra de título de la ventana de herramientas
![Botón de la barra de título (línea roja)](../../extensibility/ux-guidelines/media/0303-095_titlebarbuttonredline.png "0303-095_TitleBarButtonRedline")<br />Botón de la barra de título (línea roja)

| Uso... | No utilice ... |
| --- | --- |
| ... para los botones que aparecen en la interfaz de usuario que usa tokens de color de las barras de título de la ventana de herramientas. | ... para botones que aparecen en otras ubicaciones. |
| | ... en cualquier combinación de fondo/primer plano que no sea especificada. |

**Botones de la barra de título enfocados: estado predeterminado**

![Botones de barra de título predeterminados y enfocados](../../extensibility/ux-guidelines/media/0303-096_titlebarbuttonfocused.png "0303-096_TitleBarButtonFocused")<br />Botones de barra de título predeterminados y enfocados

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | N/D |
| Primer plano (glifo) | `Environment.ToolWindowButtonActiveGlyph` |
| Borde | N/D |

**Botones de la barra de título desenfocados: estado predeterminado**

![Botones de barra de título predeterminados y desenfocados](../../extensibility/ux-guidelines/media/0303-097_titlebarbuttonunfocused.png "0303-097_TitleBarButtonUnfocused")<br />Botones de barra de título predeterminados y desenfocados

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | N/D |
| Primer plano (glifo) | `Environment.ToolWindowButtonInactiveGlyph` |
| Borde | N/D |

**Botones de la barra de título enfocados: estado de desplazamiento**

![Botones de la barra de título enfocados al pasar el ratón](../../extensibility/ux-guidelines/media/0303-098_titlebarbuttonfocusedhover.png "0303-098_TitleBarButtonFocusedHover")<br />Botones de la barra de título enfocados al pasar el ratón

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.ToolWindowButtonHoverActive` |
| Primer plano (glifo) | `Environment.ToolWindowButtonHoverActiveGlyph` |
| Borde | `Environment.ToolWindowButtonHoverActiveBorder` |

**Botones de la barra de título desenfocados: estado de desplazamiento**

![Botones de la barra de título desenfocados al pasar el ratón](../../extensibility/ux-guidelines/media/0303-099_titlebarbuttonunfocusedhover.png "0303-099_TitleBarButtonUnfocusedHover")<br />Botones de la barra de título desenfocados al pasar el ratón

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.ToolWindowButtonHoverInactive` |
| Primer plano (glifo) | `Environment.ToolWindowButtonHoverInactiveGlyph` |
| Borde | `Environment.ToolWindowButtonHoverInactiveBorder` |

**Botones de la barra de título enfocados: estado presionado**

![Botones de la barra de título enfocados en la prensa](../../extensibility/ux-guidelines/media/0303-100_titlebarbuttonfocusedpressed.png "0303-100_TitleBarButtonFocusedPressed")<br />Botones de la barra de título enfocados en la prensa

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.ToolWindowButtonDown` |
| Primer plano (glifo) | `Environment.ToolWindowButtonDownActiveGlyph` |
| Borde | `Environment.ToolWindowButtonDownBorder` |

**Botones de la barra de título desenfocados: estado pulsado**

![Botones de barra de título desenfocados al presionar](../../extensibility/ux-guidelines/media/0303-101_titlebarbuttonunfocusedpressed.png "0303-101_TitleBarButtonUnfocusedPressed")<br />Botones de barra de título desenfocados al presionar

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.ToolWindowButtonDown` |
| Primer plano (glifo) | `Environment.ToolWindowButtonDownInactiveGlyph` |
| Borde | `Environment.ToolWindowButtonDownBorder` |

### <a name="tool-window-tabs"></a>Pestañas de ventana de herramientas
![Pestaña Ventana de herramientas (línea roja)](../../extensibility/ux-guidelines/media/0303-102_toolwindowtabredline.png "0303-102_ToolWindowTabRedline")<br />Pestaña Ventana de herramientas (línea roja)

| Uso... | No utilice ... |
| --- | --- |
| ... en cualquier lugar en el que esté creando la interfaz de usuario que desea que coincida con las ventanas de herramientas. | ... para cualquier interfaz de usuario que no desee cambiar automáticamente si el shell tiene una actualización del tema. |

**Pestaña de ventana de herramienta seleccionada, con foco**

![Pestaña de ventana de herramienta seleccionada, con foco](../../extensibility/ux-guidelines/media/0303-103_toolwindowtabfocused.png "0303-103_ToolWindowTabFocused")<br />Pestaña de ventana de herramienta seleccionada, con foco

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.ToolWindowTabSelectedTab` |
| Primer plano (texto) | `Environment.ToolWindowTabSelectedActiveText` |
| Borde | `Environment.ToolWindowTabSelectedBorder`<br />(Establecer en el mismo color que el fondo.) |

**Pestaña de ventana de herramienta seleccionada, sin foco**

![Pestaña de ventana de herramienta seleccionada, sin foco](../../extensibility/ux-guidelines/media/0303-104_toolwindowtabunfocused.png "0303-104_ToolWindowTabUnfocused")<br />Pestaña de ventana de herramienta seleccionada, sin foco

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.ToolWindowTabSelectedTab` |
| Primer plano (texto) | `Environment.ToolWindowTabSelectedText` |
| Borde | `Environment.ToolWindowTabSelectedBorder`<br />(Establecer en el mismo color que el fondo.) |

**Pestaña de la ventana de la herramienta de fondo: estado predeterminado**

![Ficha predeterminada de la ventana de la ventana de la herramienta de fondo](../../extensibility/ux-guidelines/media/0303-105_toolwindowbackgroundtab.png "0303-105_ToolWindowBackgroundTab")<br />Ficha predeterminada de la ventana de la ventana de la herramienta de fondo

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.ToolWindowTabGradientBegin`<br />`Environment.ToolWindowTabGradientEnd`<br />(Gradient se detiene establecido en el mismo valor de color en Visual Studio 2013.) |
| Primer plano (texto) | `Environment.ToolWindowTabText` |
| Borde | `Environment.ToolWindowTabBorder` |

**Pestaña de la ventana de la herramienta de fondo: estado de desplazamiento**

![Pestaña de ventana de herramientas en segundo plano al mantener el puntero](../../extensibility/ux-guidelines/media/0303-106_toolwindowbackgroundtabhover.png "0303-106_ToolWindowBackgroundTabHover")<br />Pestaña de ventana de herramientas en segundo plano al mantener el puntero

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.ToolWindowTabMouseOverBackgroundBegin`<br />`Environment.ToolWindowTabMouseOverBackgroundEnd`<br />(Gradient se detiene establecido en el mismo valor de color en Visual Studio 2013.) |
| Primer plano (texto) | `Environment.ToolWindowTabMouseOverText` |
| Borde | `Environment.ToolWindowTabMouseOverBorder`<br />(Establecer en el mismo color que el fondo.) |

### <a name="auto-hide-tabs"></a>Pestaña de ocultación automática

![Ocultar automáticamente pestañas (línea roja)](../../extensibility/ux-guidelines/media/0303-107_autohideredline.png "0303-107_AutoHideRedline") Ocultar automáticamente pestañas (línea roja)

| Uso... | No utilice ... |
| --- | --- |
| ... en cualquier lugar en el que esté creando la interfaz de usuario que desea que coincida con las pestañas de la ventana de herramientas ocultas automáticamente. | ... para cualquier interfaz de usuario que no desee cambiar automáticamente si el shell tiene una actualización del tema. |

**Ocultar pestañas automáticamente: estado predeterminado**

![Pestaña de ocultación automática predeterminada](../../extensibility/ux-guidelines/media/0303-108_autohidetab.png "0303-108_AutoHideTab")<br />Pestaña de ocultación automática predeterminada

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.AutoHideTabBackgroundBegin`<br />(Se detiene el degradado para este token no utilizado en la interfaz de usuario temática.) |
| Primer plano (texto) | `Environment.AutoHideTabText` |
| Borde | `Environment.AutoHideTabBorder` |

**Ocultar pestañas automáticamente: estado de desplazamiento**

![Pestaña de ocultación automática al mantener el puntero](../../extensibility/ux-guidelines/media/0303-109_autohidetabhover.png "0303-109_AutoHideTabHover")<br />Pestaña de ocultación automática al mantener el puntero

| Elemento | Nombre del token: Category.color |
| --- | --- |
| Información previa | `Environment.AutoHideTabMouseOverBackgroundBegin`<br />(Se detiene el degradado para este token no utilizado en la interfaz de usuario temática.) |
| Primer plano (texto) | `Environment.AutoHideTabMouseOverText` |
| Borde | `Environment.AutoHideTabMouseOverBorder` |
