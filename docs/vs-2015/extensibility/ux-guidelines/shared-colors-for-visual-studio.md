---
title: Colores compartidos
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 8d11b9a0-6175-4f2e-8e7f-79daee1bfd41
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 87520a7e17d194d7f5cc28665a6f23466bface65
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68154575"
---
# <a name="shared-colors-for-visual-studio"></a>Colores compartidos para Visual Studio

[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Si diseña una interfaz de usuario que usa elementos comunes de shell de Visual Studio, o si quiere que el elemento de la interfaz sea coherente con características similares, use los nombres de token existentes de los archivos de definición de paquete para elegir y asignar colores. Esto garantiza que la interfaz de usuario mantenga la coherencia con el entorno general de Visual Studio y que se actualice automáticamente cuando se agreguen o actualicen temas.

En este artículo se describen los elementos de interfaz de usuario comunes y los nombres de token que estos usan y a los que se puede hacer referencia al crear una interfaz de usuario similar. Para obtener información específica sobre cómo tener acceso a estos tokens de color, vea [The VSColor Service](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).

Asegúrese de usar correctamente los nombres de token:

- **Usar nombres de token en función de la función, no en el color en Sí.** Los colores comunes compartidos están asociados a elementos específicos de la interfaz y solo están destinados para características iguales o similares. Por ejemplo, no vuelva a usar el color de un cuadro combinado presionado para una animación de progreso de giro solo porque le gusta el color. Las funciones del cuadro combinado y de la animación son diferentes, y si se cambia el color asociado con el cuadro combinado, ya no puede ser un color adecuado para el elemento de animación. Un uso coherente del color ayuda a orientar a los usuarios y evitar confusiones.

- **Usar colores de fondo y texto en la combinación correcta.** Los colores de fondo destinados para usarse con texto tendrán un color de texto asociado. No use colores de texto que no sean los que se especifican para el fondo. Si no hay un color de texto asociado, no use ese color de fondo para cualquier superficie en la que tiene pensado mostrar texto. Otras combinaciones de colores de fondo y de texto pueden dar lugar a una interfaz ilegible.

- **Usar colores de control que son adecuados para su ubicación.** En determinados estados, algunos controles de Visual Studio no tienen colores de borde y de fondo independientes. En su lugar, toman los colores de las superficies que están detrás de ellos. Procure usar siempre los nombres de token que sean adecuados para la ubicación donde coloca el control.

> [!IMPORTANT]
> No use tokens que se encuentran en las categorías "Página de inicio" o "Cider".

## <a name="command-structures"></a>Estructuras de comandos

### <a name="BKMK_CommandMenus"></a> Menús

Los menús pueden aparecer en varios lugares dentro de Visual Studio: la barra de menú principal, insertada en el documento o ventanas de herramientas, o en el botón derecho en diversas ubicaciones en todo el IDE. Las implementaciones de menús asociados con otros elementos de la interfaz de usuario se describen en la sección del elemento respectivo. Se debe usar siempre la implementación de menús estándar proporcionada por el entorno de Visual Studio. Sin embargo, en algunas ocasiones podría no tener acceso a los menús estándar de Visual Studio. En estos casos, use los siguientes nombres de token para asegurarse de que la interfaz de usuario sea coherente con otros menús de Visual Studio.

![Revisión de menús](../../extensibility/ux-guidelines/media/0303-000-menuredline.png "0303 000_MenuRedline")

Use…
- siempre que necesite crear un menú personalizado.

- cuando haya un nuevo componente de interfaz de usuario que quiera hacer coincidir con los menús de Visual Studio.

No use…
el color de fondo por sí solo. Use siempre la combinación de primer plano y fondo tal como se especifica.

#### <a name="menu-title"></a>Título de menú

Los títulos de menú constan de un fondo, un borde y el texto del título, así como un glifo opcional, que suele usarse cuando el menú se encuentra en una barra de comandos.

![Revisión de título de menú](../../extensibility/ux-guidelines/media/0303-001-menutitleredline.png "0303 001_MenuTitleRedline")

Use…
cada vez que cree un título de menú personalizado.

No use…
- para cualquier elemento que no desea que siempre coincida con el título de menú.

- en cualquier combinación de primer plano y fondo distinta de la especificada.

  **Valor predeterminado**

  Componente

  Elemento

  Nombre del token: Category.color

  ![Título de menú predeterminado](../../extensibility/ux-guidelines/media/0303-002-menutitledefault.png "0303 002_MenuTitleDefault")

  **Título de menú**

  Fondo

  None

  Primer plano (texto)

  `Environment.CommandBarTextActive`

  ![Título de menú con glifo predeterminado](../../extensibility/ux-guidelines/media/0303-003-menutitlewithglyphdefault.png "0303 003_MenuTitleWithGlyphDefault")

  **Título de menú con glifo**

  Primer plano (glifo)

  `Environment.CommandBarMenuGlyph`

  Borde

  None

  **Al mantener el mouse**

  Componente

  Elemento

  Nombre del token: Category.color

  ![Título de menú al mantener el mouse](../../extensibility/ux-guidelines/media/0303-004-menutitlehover.png "0303 004_MenuTitleHover")

  **Título de menú**

  Fondo

  `Environment.CommandBarMouseOverBackgroundBegin`

  Aunque no se usan en la interfaz de usuario moderna con temas, hay delimitadores de degradado y valores para este fondo.

  Primer plano (texto)

  `Environment.CommandBarTextHover`

  ![Título de menú con glifo al mantener el mouse](../../extensibility/ux-guidelines/media/0303-005-menutitlewithglyphhover.png "0303 005_MenuTitleWithGlyphHover")

  **Título de menú con glifo**

  Primer plano (glifo)

  `Environment.CommandBarMenuMouseOverGlyph`

  Borde

  `Environment.CommandBarBorder`

  **Presionado**

  Componente

  Elemento

  Nombre del token: Category.color

  ![Título de menú presionado](../../extensibility/ux-guidelines/media/0303-006-menutitlepressed.png "0303 006_MenuTitlePressed")

  **Título de menú**

  Fondo

  `Environment.CommandBarMenuBackgroundGradientBegin`

  Aunque no se usan en la interfaz de usuario moderna con temas, hay delimitadores de degradado y valores para este fondo.

  Primer plano (texto)

  `Environment.CommandBarTextActive`

  ![Título de menú con glifo presionado](../../extensibility/ux-guidelines/media/0303-007-menutitlewithglyphpressed.png "0303 007_MenuTitleWithGlyphPressed")

  **Título de menú con glifo**

  Primer plano (glifo)

  `Environment.CommandBarMenuMouseDownGlyph`

  Borde

  `Environment.CommandBarMenuBorder`

  Solo partes izquierda, superior y derecha.

  **Deshabilitado**

  Componente

  Elemento

  Nombre del token: Category.color

  ![Título de menú con glifo deshabilitado](../../extensibility/ux-guidelines/media/0303-008-menutitlewithglyphdisabled.png "0303 008_MenuTitleWithGlyphDisabled")

  **Título de menú con glifo**

  Fondo

  None

  Primer plano (texto)

  `Environment.CommandBarTextInactive`

  Primer plano (glifo)

  `Environment.CommandBarTextInactive`

  Borde

  None

#### <a name="menu"></a>Menú

Un elemento de menú individual se compone del texto del menú y un icono opcional, una casilla o un glifo de submenú. Su color de fondo y de texto cambian al mantener el puntero. Este token de color es un par de primer plano y fondo.

![Revisión de los elementos de menú](../../extensibility/ux-guidelines/media/0303-009-menuitemredline.png "0303 009_MenuItemRedline")

Use…
para cualquier lista desplegable que se inicia desde una barra de menús o una barra de comandos.

No use…
- para cualquier lista desplegable que se muestra en otro contexto.

- en cualquier combinación de primer plano y fondo distinta de la especificada.

  **Valor predeterminado**

  Componente

  Elemento

  Nombre del token: Category.color

  ![Menú predeterminado](../../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303 010_MenuDefault")

  **Menu**

  Fondo

  `Environment.CommandBarMenuBackgroundGradientBegin`

  Aunque no se usan en la interfaz de usuario moderna con temas, hay delimitadores de degradado y valores para este fondo.

  Primer plano (texto)

  `Environment.CommandBarTextActive`

  Primer plano (glifo de submenú)

  `Environment.CommandBarMenuSubmenuGlyph`

  Borde

  `Environment.CommandBarMenuBorder`

  Fondo de canal de iconos

  `Environment.CommandBarMenuIconBackground`

  Separador

  `Environment.CommandBarMenuSeparator`

  Sombra

  `Environment.DropShadowBackground`

  ![Menú activado](../../extensibility/ux-guidelines/media/0303-011-menuchecked.png "0303 011_MenuChecked")

  **Activadas**

  Marca de verificación

  `Environment.CommandBarCheckBox`

  Fondo de marca de verificación

  `Environment.CommandBarSelectedIcon`

  ![Menú seleccionado](../../extensibility/ux-guidelines/media/0303-012-menuselected.png "0303 012_MenuSelected")

  **seleccionado**

  Fondo de icono

  `Environment.CommandBarSelected`

  Borde de icono

  `Environment.CommandBarSelectedBorder`

  **Al mantener el mouse**

  Componente

  Elemento

  Nombre del token: Category.color

  ![Mantener el mouse del menú](../../extensibility/ux-guidelines/media/0303-013-menuhover.png "0303 013_MenuHover")

  **Elemento de menú**

  Fondo

  `Environment.CommandBarMenuItemMouseOver`

  Primer plano (texto)

  `Environment.CommandBarMenuItemMouseOver`

  Primer plano (glifo de submenú)

  `Environment.CommandBarMenuMouseOverSubmenuGlyph`

  ![Al mantener el mouse de menú activado](../../extensibility/ux-guidelines/media/0303-014-menuhoverchecked.png "0303 014_MenuHoverChecked")

  **Activadas**

  Marca de verificación

  `Environment.CommandBarCheckBoxMouseOver`

  Fondo de marca de verificación

  `Environment.CommandBarHoverOverSelectedIcon`

  ![Al mantener el mouse de menú seleccionado](../../extensibility/ux-guidelines/media/0303-015-menuhoverselected.png "0303 015_MenuHoverSelected")

  **seleccionado**

  Fondo de icono

  `Environment.CommandBarHoverOverSelected`

  Borde de icono

  `Environment.CommandBarHoverOverSelectedIconBorder`

  **Deshabilitado**

  Componente

  Elemento

  Nombre del token: Category.color

  ![Menú deshabilitado](../../extensibility/ux-guidelines/media/0303-016-menudisabled.png "0303 016_MenuDisabled")

  Elemento de menú

  Primer plano (texto)

  `Environment.CommandBarTextInactive`

  Primer plano (glifo de submenú)

  `Environment.CommandBarMenuSubmenuGlyph`

  ![Menú deshabilitado activado](../../extensibility/ux-guidelines/media/0303-017-menudisabledchecked.png "0303 017_MenuDisabledChecked")

  Activado

  Marca de verificación

  `Environment.CommandBarCheckBoxDisabled`

  Fondo de marca de verificación

  `Environment.CommandBarSelectedIconDisabled`

### <a name="command-bar"></a>Barra de comandos

La barra de comandos puede aparecer en varios lugares del IDE de Visual Studio, sobre todo en el área de comandos e insertados en ventanas de herramientas o documentos.

En general, use siempre la implementación de menús estándar proporcionada por el entorno de Visual Studio. El uso del mecanismo estándar, garantiza que todos los detalles visuales se mostrarán correctamente y que los elementos interactivos se comportarán de forma coherente con otros controles de barra de comandos de Visual Studio. Sin embargo, si necesita crear su propia barra de comandos, asegúrese de diseñarla correctamente mediante los siguientes nombres de token.

![Límite de barra de comandos](../../extensibility/ux-guidelines/media/0303-018-commandbarredline.png "0303 018_CommandBarRedline")

![Límite de botón de desbordamiento](../../extensibility/ux-guidelines/media/0303-019-overflowbuttonredline.png "0303 019_OverflowButtonRedline")

Use…
en lugares donde se necesita una barra de comandos insertada pero no se puede usar la implementación estándar de barra de comandos de Visual Studio.

No use…
- para elementos de la interfaz de usuario que no sean similares a una barra de comandos.

- para los componentes de barra de comandos distintos de aquellos para los que se especifican nombres de los token.

#### <a name="command-bar-group"></a>Grupo de la barra de comandos

Un grupo de la barra de comandos se compone de un conjunto relacionado de controles de barra de comandos y puede incluir cualquier número de botones, botones de expansión, menús desplegables, cuadros combinados o menús. Los colores de dichos controles se regulan mediante nombres de token independientes y se describen individualmente en esta guía. Se usa una línea divisoria para dividir un grupo de la barra de comandos en subgrupos relacionados.

![Límite de grupo de la barra de comandos](../../extensibility/ux-guidelines/media/0303-020-commandbargroupredline.png "0303 020_CommandBarGroupRedline")

Use…
en lugares donde se necesita una barra de comandos insertada pero no se puede usar la implementación estándar de barra de comandos de Visual Studio.

No use…
- para elementos de la interfaz de usuario que no sean similares a una barra de comandos.

- para los componentes de barra de comandos distintos de aquellos para los que se especifican nombres de los token.

  **Predeterminado** (no hay otros estados)

  Elemento

  Nombre del token: Category.color

  Fondo

  `Environment.CommandBarGradientBegin`

  Aunque no se usan en la interfaz de usuario moderna con temas, hay delimitadores de degradado y valores para este fondo.

  Borde

  `Environment.CommandBarToolBarBorder`

  Controlador de arrastre

  `Environment.CommandBarDragHandle`

  Separador

  `Environment.CommandBarToolBarSeparator`

  `Environment.CommandBarToolBarSeparatorHighlight`

#### <a name="command-icons"></a>Iconos de comando

![Límite de icono de comando](../../extensibility/ux-guidelines/media/0303-021-commandiconredline1.png "0303 021_CommandIconRedline1")

![Límite de icono de comando](../../extensibility/ux-guidelines/media/0303-022-commandiconredline2.png "0303 022_CommandIconRedline2")

Use…
para los botones que se colocarán en una barra de comandos.

No use…
- para controles que tienen sus propios nombres de token.

- en cualquier combinación de primer plano y fondo distinta de la especificada.

  **Valor predeterminado**

  Componente

  Elemento

  Nombre del token: Category.color

  ![Icono predeterminado de comandos](../../extensibility/ux-guidelines/media/0303-023-commandicondefault.png "0303 023_CommandIconDefault")

  **Valor predeterminado**

  Fondo

  N/D (se hereda del fondo de la barra de comandos)

  Primer plano (texto)

  `Environment.CommandBarTextActive`

  Borde

  N/D

  ![Comando predeterminado del icono seleccionado](../../extensibility/ux-guidelines/media/0303-024-commandicondefaultselected.png "0303 024_CommandIconDefaultSelected")

  **seleccionado**

  Fondo

  `Environment.CommandBarSelected`

  Primer plano (texto)

  `Environment.CommandBarTextSelected`

  Borde

  `Environment.CommandBarSelectedBorder`

  **Al mantener el mouse y teclado con foco**

  Componente

  Elemento

  Nombre del token: Category.color

  ![Mantener el mouse el icono de comando](../../extensibility/ux-guidelines/media/0303-025-commandiconhover.png "0303 025_CommandIconHover")

  **Estándar al mantener el mouse**

  Fondo

  `Environment.CommandBarMouseOverBackgroundBegin`

  Aunque no se usan en la interfaz de usuario moderna con temas, hay delimitadores de degradado y valores para este fondo.

  Primer plano (texto)

  `Environment.CommandBarTextHover`

  Borde

  `Environment.CommandBarBorder`

  ![Comando de desplazamiento del icono seleccionado](../../extensibility/ux-guidelines/media/0303-026-commandiconhoverselected.png "0303 026_CommandIconHoverSelected")

  **Seleccionado al mantener el mouse**

  Fondo

  `Environment.CommandBarHoverOverSelected`

  Primer plano (texto)

  `Environment.CommandBarTextHoverOverSelected`

  Borde

  `Environment.CommandBarHoverOverSelectedIconBorder`

  **Presionado**

  Componente

  Elemento

  Nombre del token: Category.color

  ![Icono de comando presionado](../../extensibility/ux-guidelines/media/0303-027-commandiconpressed.png "0303 027_CommandIconPressed")

  **Icono de comando presionado**

  Fondo

  `Environment.CommandBarMouseDownBackgroundBegin`

  Aunque no se usan en la interfaz de usuario moderna con temas, hay delimitadores de degradado y valores para este fondo.

  Primer plano (texto)

  `Environment.CommandBarTextMouseDown`

  Borde

  `Environment.CommandBarBorder`

  **Deshabilitado**

  Componente

  Elemento

  Nombre del token: Category.color

  ![Icono de comando deshabilitado](../../extensibility/ux-guidelines/media/0303-028-commandicondisabled.png "0303 028_CommandIconDisabled")

  **Icono de comando deshabilitado**

  Fondo

  N/D (se hereda del fondo de la barra de comandos)

  Primer plano (texto)

  `Environment.CommandBarTextInactive`

  Borde

  N/D

#### <a name="BKMK_CommandComboBox"></a> Cuadro combinado

> [!IMPORTANT]
> Los cuadros combinados son similares a las listas desplegables, pero incluyen un área de texto editable. Si la lista desplegable no incluye un área de texto editable, use los tokens de color que se encuentran en [Drop-down](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown).

![Límite de cuadro combinado](../../extensibility/ux-guidelines/media/0303-029-comboboxredline.png "0303 029_ComboBoxRedline")

Use…
- al crear cuadros combinados personalizados.

- al crear un control de barra de comandos que sea similar a un cuadro combinado.

  No use…
  - para ningún elemento que no desea que siempre coincida con la interfaz de usuario de la barra de comandos.

- si tiene acceso a un cuadro combinado con estilo.

  **Valor predeterminado**

  Componente

  Elemento

  Nombre del token: Category.color

  ![Campo de entrada de cuadro combinado](../../extensibility/ux-guidelines/media/0303-030-comboboxinputfield.png "0303 030_ComboBoxInputField")

  **Campo de entrada**

  Fondo

  `Environment.ComboBoxBackground`

  Primer plano (texto)

  `Environment.ComboBoxText`

  Borde

  `Environment.ComboBoxBorder`

  Separador

  Sin separador

  ![Desplegable del cuadro combinado&#45;presionado el botón](../../extensibility/ux-guidelines/media/0303-031-comboboxdropdownbutton.png "0303 031_ComboBoxDropdownButton")

  **Botón desplegable**

  Fondo

  N/D (se hereda)

  Primer plano (glifo)

  `Environment.ComboBoxGlyph`

  ![Cuadro combinado&#47;drop&#45;lista desplegable](../../extensibility/ux-guidelines/media/0303-032-comboboxdropdownlist.png "0303 032_ComboBoxDropdownList")

  **Lista desplegable**

  Fondo

  `Environment.ComboBoxPopupBackgroundBegin`

  Aunque no se usan en la interfaz de usuario moderna con temas, hay delimitadores de degradado y valores para este fondo.

  Primer plano (texto)

  `Environment.ComboBoxItemText`

  Borde

  `Environment.ComboBoxPopupBorder`

  **Al mantener el mouse**

  Componente

  Elemento

  Nombre del token: Category.color

  ![Campo de entrada de cuadro combinado al mantener el mouse](../../extensibility/ux-guidelines/media/0303-033-comboboxinputfieldhover.png "0303 033_ComboBoxInputFieldHover")

  **Campo de entrada**

  Fondo

  `Environment.ComboBoxMouseOverBackgroundBegin`

  Aunque no se usan en la interfaz de usuario moderna con temas, hay delimitadores de degradado y valores para este fondo.

  Primer plano (texto)

  `Environment.ComboBoxMouseOverText`

  Borde

  `Environment.ComboBoxMouseOverBorder`

  Separador

  `Environment.ComboBoxMouseOverSeparator`

  ![Cuadro combinado&#47;drop&#45;hacia abajo del botón de desplazamiento](../../extensibility/ux-guidelines/media/0303-034-comboboxdropdownbuttonhover.png "0303 034_ComboBoxDropdownButtonHover")

  **Botón desplegable**

  Fondo

  `Environment.ComboBoxButtonMouseOverBackground`

  Primer plano (glifo)

  `Environment.ComboBoxMouseOverGlyph`

  ![Cuadro combinado&#47;drop&#45;hacia abajo en la lista al mantener el mouse](../../extensibility/ux-guidelines/media/0303-035-comboboxdropdownlisthover.png "0303 035_ComboBoxDropdownListHover")

  **Lista desplegable**

  Fondo (elemento de menú)

  `Environment.ComboBoxItemMouseOverBackground`

  Primer plano (texto)

  `Environment.ComboBoxItemMouseOverText`

  Borde (elemento de menú)

  `Environment.ComboBoxItemMouseOverBorder`

  **Centrado**

  Componente

  Elemento

  Nombre del token: Color.Category

  ![Campo entrada de cuadro combinado enfocado](../../extensibility/ux-guidelines/media/0303-036-comboboxinputfieldfocused.png "0303 036_ComboBoxInputFieldFocused")

  **Campo de entrada**

  Fondo

  `Environment.ComboBoxFocusedBackground`

  Primer plano (texto)

  `Environment.ComboBoxFocusedText`

  Borde

  `Environment.ComboBoxFocusedBorder`

  Separador

  `Environment.ComboBoxFocusedButtonSeparator`

  ![Cuadro combinado&#47;drop&#45;hacia abajo del botón enfocado](../../extensibility/ux-guidelines/media/0303-037-comboboxdropdownbuttonfocused.png "0303 037_ComboBoxDropdownButtonFocused")

  **Botón desplegable**

  Fondo

  `Environment.ComboBoxFocusedButtonBackground`

  Primer plano (glifo)

  `Environment.ComboBoxFocusedGlyph`

  **Presionado**

  Componente

  Elemento

  Nombre del token: Color.Category

  ![Campo entrada de cuadro combinado presionado](../../extensibility/ux-guidelines/media/0303-038-comboboxinputfieldpressed.png "0303 038_ComboBoxInputFieldPressed")

  **Campo de entrada**

  Fondo

  `Environment.ComboBoxMouseDownBackground`

  Primer plano (texto)

  `Environment.ComboBoxMouseDownText`

  Borde

  `Environment.ComboBoxMouseDownBorder`

  Separador

  `Environment.ComboBoxMouseDownSeparator`

  ![Cuadro combinado&#47;drop&#45;presionado el botón presionado](../../extensibility/ux-guidelines/media/0303-039-comboboxdropdownbuttonpressed.png "0303 039_ComboBoxDropdownButtonPressed")

  **Botón desplegable**

  Fondo

  `Environment.ComboBoxButtonMouseDownBackground`

  Primer plano (glifo)

  `Environment.ComboBoxMouseDownGlyph`

  **Deshabilitado**

  ![Campo entrada de cuadro combinado deshabilitado](../../extensibility/ux-guidelines/media/0303-041-comboboxinputfielddisabled.png "0303 041_ComboBoxInputFieldDisabled")

  **Campo de entrada**

  Fondo

  `Environment.ComboBoxDisabledBackground`

  Primer plano (texto)

  `Environment.ComboBoxDisabledText`

  Borde

  `Environment.ComboBoxDisabledBorder`

  Separador

  Sin separador

  ![Cuadro combinado&#47;drop&#45;presionado el botón deshabilitado](../../extensibility/ux-guidelines/media/0303-040-comboboxdropdownbuttondisabled.png "0303 040_ComboBoxDropdownButtonDisabled")

  **Botón desplegable**

  Fondo

  None

  Primer plano (glifo)

  `Environment.ComboBoxDisabledGlyph`

#### <a name="BKMK_CommandDropDown"></a> Lista desplegable

> [!IMPORTANT]
> Las listas desplegables son similares a los cuadros combinados, pero carecen de áreas de texto editable. Si la lista desplegable incluye un área de texto editable, use los tokens de color que se encuentran en [Combo box](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox).

![Quitar&#45;hacia abajo línea roja](../../extensibility/ux-guidelines/media/0303-042-dropdownredline.png "0303 042_DropdownRedline")

Use…
al crear controles de lista desplegable personalizados.

No use…
- para cualquier elemento que no sea similar a una lista desplegable.

- para cuadros combinados o botones de expansión.

  **Valor predeterminado**

  Componente

  Elemento

  Nombre del token: Category.color

  ![Quitar&#45;hacia abajo del campo de selección](../../extensibility/ux-guidelines/media/0303-043-dropdownselectionfield.png "0303 043_DropdownSelectionField")

  **Campo de selección**

  Fondo

  `Environment.DropDownBackground`

  Primer plano (texto)

  `DropDownText`

  Borde

  `DropDownBorder`

  Separador

  Sin separador

  ![Quitar&#45;presionado el botón](../../extensibility/ux-guidelines/media/0303-044-dropdownbutton.png "0303 044_DropdownButton")

  **Botón desplegable**

  Fondo

  None

  Primer plano (glifo)

  `Environment.DropDownGlyph`

  ![Quitar&#45;lista desplegable](../../extensibility/ux-guidelines/media/0303-045-dropdownlist.png "0303 045_DropdownList")

  **Lista desplegable**

  Fondo

  `Environment.DropDownPopupBackgroundBegin`

  Aunque no se usan en la interfaz de usuario moderna con temas, hay delimitadores de degradado y valores para este fondo.

  Primer plano (texto)

  `Environment.ComboBoxItemText`

  Borde

  `Environment.DropDownPopupBorder`

  Sombra

  `Environment.DropShadowBackground`

  **Al mantener el mouse**

  Componente

  Elemento

  Nombre del token: Category.color

  ![Quitar&#45;campo de selección al mantener el mouse hacia abajo](../../extensibility/ux-guidelines/media/0303-046-dropdownselectionfieldhover.png "0303 046_DropdownSelectionFieldHover")

  **Campo de selección**

  Fondo

  `Environment.DropDownMouseOverBackgroundBegin`

  Aunque no se usan en la interfaz de usuario moderna con temas, hay delimitadores de degradado y valores para este fondo.

  Primer plano (texto)

  `Environment.DropDownMouseOverText`

  Borde

  `Environment.DropDownMouseOverBorder`

  Separador

  `Environment.DropDownButtonMouseOverSeparator`

  ![Quitar&#45;hacia abajo del botón de desplazamiento](../../extensibility/ux-guidelines/media/0303-047-dropdownbuttonhover.png "0303 047_DropdownButtonHover")

  **Botón desplegable**

  Fondo

  `Environment.DropDownButtonMouseOverBackground`

  Primer plano (glifo)

  `Environment.DropDownMouseOverGlyph`

  ![Quitar&#45;hacia abajo en la lista al mantener el mouse](../../extensibility/ux-guidelines/media/0303-048-dropdownlisthover.png "0303 048_DropdownListHover")

  **Lista desplegable**

  Fondo (elemento de menú)

  `Environment.ComboBoxItemMouseOverBackground`

  Primer plano (texto)

  `Environment.ComboBoxItemMouseOverText`

  Borde (elemento de menú)

  `Environment.ComboBoxItemMouseOverBorder`

  **Presionado**

  Componente

  Elemento

  Nombre del token: Category.color

  ![Quitar&#45;hacia abajo del campo de selección presionada](../../extensibility/ux-guidelines/media/0303-049-dropdownselectionfieldpressed.png "0303 049_DropdownSelectionFieldPressed")

  **Campo de selección**

  Fondo

  `Environment.DropDownMouseDownBackground`

  Primer plano (texto)

  `Environment.DropDownMouseDownText`

  Borde

  `Environment.DropDownMouseDownBorder`

  Separador

  `Environment.DropDownButtonMouseDownSeparator`

  ![Quitar&#45;presionado el botón presionado](../../extensibility/ux-guidelines/media/0303-050-dropdownbuttonpressed.png "0303 050_DropdownButtonPressed")

  **Botón desplegable**

  Fondo

  `Environment.DropDownButtonMouseDownBackground`

  Primer plano (glifo)

  `Environment.DropDownMouseDownGlyph`

  **Deshabilitado**

  Componente

  Elemento

  Nombre del token: Category.color

  ![Quitar&#45;hacia abajo del campo de selección deshabilitado](../../extensibility/ux-guidelines/media/0303-051-dropdownselectionfielddisabled.png "0303 051_DropdownSelectionFieldDisabled")

  Fondo

  `Environment.DropDownDisabledBackground`

  Primer plano (texto)

  `Environment.DropDownDisabledText`

  Borde

  `Environment.DropDownDisabledBorder`

  Separador

  Sin separador

  ![Quitar&#45;presionado el botón deshabilitado](../../extensibility/ux-guidelines/media/0303-052-dropdownbuttondisabled.png "0303 052_DropdownButtonDisabled")

  Fondo

  N/D

  Primer plano (glifo)

  `Environment.DropDownDisabledGlyph`

#### <a name="split-button"></a>Botón de expansión

Los botones de expansión comparten muchos nombres de token con otros controles de barra de comandos como, por ejemplo, botones, menús y texto de la barra de comandos. Todos los nombres de token de acciones y botones desplegables necesarios se repiten aquí para su comodidad. Las listas desplegables de botón de expansión son implementaciones de la barra de comandos [Menus](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus).

![Límite de botón de división](../../extensibility/ux-guidelines/media/0303-053-splitbuttonredline.png "0303 053_SplitButtonRedline")

Use…
si crea un botón de expansión personalizado.

No use…
- para otros tipos de botones.

- en cualquier combinación de primer plano y fondo distinta de la especificada.

  **Valor predeterminado**

  Componente

  Elemento

  Nombre del token: Category.color

  ![Botón de expansión](../../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303 054_SplitButton")

  **Botón de expansión (valor predeterminado)**

  Fondo

  None

  Primer plano (texto)

  `Environment.CommandBarTextActive`

  Primer plano (glifo)

  `Environment.CommandBarSplitButtonGlyph`

  Borde

  N/D

  Separador

  N/D

  **Al mantener el mouse**

  Componente

  Elemento

  Nombre del token: Category.color

  ![Botón de expansión al mantener el mouse](../../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303 055_SplitButtonHover")

  **Botón de expansión (al mantener el mouse)**

  Fondo

  `Environment.CommandBarMouseOverBackgroundBegin`

  Aunque no se usan en la interfaz de usuario moderna con temas, hay delimitadores de degradado y valores para este fondo.

  Primer plano (texto)

  `Environment.CommandBarTextHover`

  Primer plano (glifo)

  `Environment.CommandBarSplitButtonMouseOverGlyph`

  Borde

  `Environment.CommandBarBorder`

  Separador

  `Environment.CommandBarSplitButtonSeparator`

  **Presionado**

  Componente

  Elemento

  Nombre del token: Category.color

  ![Botón de expansión presionado](../../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303 056_SplitButtonPressed")

  **Botón de expansión (presionado)**

  Fondo

  `Environment.CommandBarMouseDownBackgroundBegin`

  Aunque no se usan en la interfaz de usuario moderna con temas, hay delimitadores de degradado y valores para este fondo.

  Primer plano (texto)

  `Environment.CommandBarTextMouseDown`

  Primer plano (glifo)

  `Environment.CommandBarSplitButtonMouseDownGlyph`

  Borde

  `Environment.CommandBarBorder`

  Separador

  N/D

  **Deshabilitado**

  Componente

  Elemento

  Nombre del token: Category.color

  ![Botón de expansión deshabilitado](../../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303 057_SplitButtonDisabled")

  **Botón de expansión (deshabilitado)**

  Fondo

  N/D

  Primer plano (texto)

  `Environment.ComboBoxItemTextInactive`

  Primer plano (glifo)

  `Environment.CommandBarTextInactive`

  Borde

  N/D

  Separador

  N/D

#### <a name="more-options-and-overflow-buttons"></a>Botones "Más opciones" y "Desbordamiento"
 El botón "Más opciones" se usa cuando un grupo de la barra de comandos se puede personalizar al agregar o quitar botones relacionados de barra de comandos. El botón "Desbordamiento" aparece cuando una barra de comandos se trunca debido a la falta de espacio horizontal y, al hacer clic en él, muestra un menú que contiene los botones de la barra de comandos que no pueden mostrarse. Los colores para estos dos botones están controlados por el mismo conjunto de nombres de token.

 ![Límite de más opciones](../../extensibility/ux-guidelines/media/0303-058-moreoptionsredline.png "0303 058_MoreOptionsRedline")

 Use…
para los botones "Más opciones" o "Desbordamiento" personalizados.

 No use…
para los botones que no tienen una función similar a la de los botones "Más opciones" o "Desbordamiento".

 **Valor predeterminado**

 Componente

 Elemento

 Nombre del token: Category.color

 ![Más opciones](../../extensibility/ux-guidelines/media/0303-059-moreoptions.png "0303 059_MoreOptions")

 **Más opciones**

 ![Botón de desbordamiento](../../extensibility/ux-guidelines/media/0303-060-overflow.png "0303 060_Overflow")

 **desbordamiento**

 Fondo

 `Environment.CommandBarOptionsBackground`

 Primer plano (glifo)

 `Environment.CommandBarOptionsGlyph`

 **Al mantener el mouse**

 Componente

 Elemento

 Nombre del token: Category.color

 ![Más opciones al mantener el mouse](../../extensibility/ux-guidelines/media/0303-061-moreoptionshover.png "0303 061_MoreOptionsHover")

 **Más opciones**

 ![Desbordamiento al mantener el mouse](../../extensibility/ux-guidelines/media/0303-062-overflowoptions.png "0303 062_OverflowOptions")

 **desbordamiento**

 Fondo

 `Environment.CommandBarOptionsMouseOverBackgroundBegin`

 Aunque no se usan en la interfaz de usuario moderna con temas, hay delimitadores de degradado y valores para este fondo.

 Primer plano (glifo)

 `Environment.CommandBarOptionsMouseDownGlyph`

 **Presionado**

 Componente

 Elemento

 Nombre del token: Category.color

 ![Más opciones presionado](../../extensibility/ux-guidelines/media/0303-063-moreoptionspressed.png "0303 063_MoreOptionsPressed")

 **Más opciones**

 ![Desbordamiento presionado](../../extensibility/ux-guidelines/media/0303-064-overflowpressed.png "0303 064_OverflowPressed")

 **desbordamiento**

 Fondo

 `Environment.CommandBarOptionsMouseDownBackgroundBegin`

 Aunque no se usan en la interfaz de usuario moderna con temas, hay delimitadores de degradado y valores para este fondo.

 Primer plano (glifo)

 `Environment.CommandBarOptionsMouseDownGlyph`

## <a name="document-windows"></a>Ventanas de documento
 No es necesario replicar las ventanas de documento, porque las proporciona el entorno de Visual Studio. Sin embargo, quizá prefiera aprovechar los colores que se usan en las ventanas de documento para que la interfaz de usuario se muestre siempre coherente con esta parte del entorno de Visual Studio.

 Si usa tokens de color de ventana de documento, tenga la precaución de usarlos únicamente para elementos similares y siempre en pares. Si no lo hace, tendrá resultados inesperados en la interfaz de usuario.

### <a name="document-window-frame"></a>Marco de ventana de documento
 Las ventanas de documento pueden estar acopladas en el IDE o flotantes como una ventana independiente. Si una ventana de documento está flotante fuera del IDE, aun así se encuentra en el cuadro de un documento y su fondo, borde, texto y sus colores de pestaña son los mismos que cuando forma parte del IDE. Sin embargo, el documento se encuentra dentro de un marco que tiene su propio fondo, borde y colores de texto. Cuando las ventanas de herramientas se acoplan en el cuadro del documento, heredan el comportamiento y el color de los nombres de token de ventana de documento para sus pestañas.

 ![Límite de ventana de documento acoplada](../../extensibility/ux-guidelines/media/0303-065-dockeddocumentwindowredline.png "0303 065_DockedDocumentWindowRedline")

 **Ventana de documento acoplado**

 ![Límite de la ventana de documento flotante](../../extensibility/ux-guidelines/media/0303-066-floatingdocumentwindowredline.png "0303 066_FloatingDocumentWindowRedline")

 **Ventana de documento flotante**

 Use…
en cualquier lugar donde cree una interfaz de usuario que quiere hacer coincidir con la ventana de documento.

 No use…
para cualquier interfaz de usuario que no desea que cambie automáticamente si se actualiza un tema del shell.

 **Valor predeterminado**

 Componente

 Elemento

 Nombre del token: Category.color

 Documento: acoplado o flotante

 Fondo

 Depende del tipo de documento

 Primer plano (texto)

 Depende del tipo de documento

 Borde

 `Environment.ToolWindowBorder`

 ![Marco enfocado](../../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303 067_FrameFocused")

 **Marco: flotante, con foco**

 Fondo

 `Environment.ToolWindowFloatingFrame`

 Primer plano (texto)

 `Environment.ToolWindowFloatingFrame`

 Primer plano (glifo)

 `Environment.RaftedWindowButtonActiveGlyph`

 Borde

 `Environment.MainWindowActiveDefaultBorder`

 Borde (glifo)

 `Environment.RaftedWindowButtonActiveBorder`

 Se establece en transparente

 ![Marco no enfocado](../../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303 068_FrameUnfocused")

 **Marco: flotante, sin foco**

 Fondo

 `Environment.ToolWindowFloatingFrameInactive`

 Primer plano (texto)

 `Environment.ToolWindowFloatingFrameInactive`

 Primer plano (glifo)

 `Environment.RaftedWindowButtonInactiveGlyph`

 Borde

 `Environment.MainWindowInactiveBorder`

 Borde (glifo)

 `Environment.RaftedWindowButtonInactiveBorder`

 Se establece en transparente

 **Al mantener el mouse**

 Componente

 Elemento

 Nombre del token: Category.color

 ![Marco enfocado al mantener el mouse](../../extensibility/ux-guidelines/media/0303-069-framefocusedhover.png "0303 069_FrameFocusedHover")

 **Marco: flotante, con foco**

 Fondo (glifo)

 `Environment.RaftedWindowButtonHoverActive`

 Primer plano (glifo)

 `Environment.RaftedWindowButtonHoverActiveGlyph`

 Borde (glifo)

 `Environment.RaftedWindowButtonHoverActiveBorder`

 ![Marco no enfocado al mantener el mouse](../../extensibility/ux-guidelines/media/0303-070-frameunfocusedhover.png "0303 070_FrameUnfocusedHover")

 **Marco: flotante, sin foco**

 Fondo (glifo)

 `EnvironmentRaftedWindowButtonHoverInactive`

 Primer plano (glifo)

 `Environment.RaftedWindowButtonHoverInactiveGlyph`

 Borde (glifo)

 `Environment.RaftedWindowButtonHoverInactiveBorder`

 **Presionado**

 Componente

 Elemento

 Nombre del token: Category.color

 ![Marco enfocado presionado](../../extensibility/ux-guidelines/media/0303-071-framefocusedpressed.png "0303 071_FrameFocusedPressed")

 **Marco: flotante, con foco**

 Fondo (glifo)

 `Environment.RaftedWindowButtonDown`

 Primer plano (glifo)

 `Environment.RaftedWindowButtonDownGlyph`

 Borde (glifo)

 `Environment.RaftedWindowButtonDownBorder`

### <a name="document-tabs"></a>Pestañas de documentos
 Las pestañas de documentos se colocan en el canal de pestañas para indicar los documentos que están abiertos actualmente, así como el documento actual activo o seleccionado. Las ventanas de herramientas también se pueden acoplar en el canal de pestañas de documentos si el usuario las coloca allí. En este caso, usan los mismos colores de pestaña que las ventanas de documento. Si va a crear interfaz de usuario que desea que siempre coincida con los colores de las ventanas de documento (lo que incluye las actualizaciones de temas o si se instalan nuevos temas), entonces haga referencia a estos tokens de color.

 ![Límite de pestaña de documento](../../extensibility/ux-guidelines/media/0303-072-documenttabredline.png "0303 072_DocumentTabRedline")

 Use…
en cualquier lugar donde cree interfaz de usuario que quiere hacer coincidir con las pestañas de documentos y que seleccione automáticamente actualizaciones de tema o nuevos colores de tema.

 No use…
para cualquier interfaz de usuario que no desea que cambie automáticamente si se actualiza un tema del shell.

#### <a name="open-document-tabs"></a>Pestañas de documentos abiertos
 Cada documento abierto tiene una pestaña en el canal de pestañas de documentos que muestra su nombre. Los documentos pueden estar seleccionados o abiertos en segundo plano y sus pestañas reflejan los siguientes estados:

- La pestaña seleccionada representa el documento que se muestra actualmente en el cuadro de documento. Una pestaña seleccionada tiene un borde de documento que se extiende por todo el borde superior del cuadro de documento.

- Las pestañas en segundo plano corresponden a cualquier pestaña de documento que no sea la pestaña seleccionada actualmente. Una vez que se hace clic en una de ellas, se convierte en la pestaña seleccionada y adopta todos los colores de fondo, borde y texto de los nombres de token.

  ![Límite de pestaña de documento abierto](../../extensibility/ux-guidelines/media/0303-073-opendocumenttabredline.png "0303 073_OpenDocumentTabRedline")

  Use…
  al crear pestañas de documentos personalizadas.

  No use…
  - para pestañas provisionales (vista previa).

- para cualquier interfaz de usuario que no desea que cambie automáticamente si se actualiza un tema del shell.

#### <a name="selected-tab"></a>Pestaña seleccionada
 **Centrado**

 Componente

 Elemento

 Nombre del token: Category.color

 ![Pestaña seleccionada enfocada](../../extensibility/ux-guidelines/media/0303-074-selectedtabfocused.png "0303 074_SelectedTabFocused")

 **Pestaña de documento seleccionada, centrado**

 Fondo

 `Environment.FileTabSelectedGradientTop`

 Aunque no se usan en la interfaz de usuario moderna con temas, hay delimitadores de degradado y valores para este fondo.

 Primer plano (texto)

 `Environment.FileTabSelectedText`

 Borde

 `Environment.FileTabSelectedBorder`

 Se establece en el mismo color que el fondo.

 Borde de documento

 `Environment.FileTabDocumentBorderBackground`

 **Sin foco**

 Componente

 Elemento

 Nombre del token: Category.color

 ![Pestaña seleccionada no enfocada](../../extensibility/ux-guidelines/media/0303-075-selectedtabunfocused.png "0303 075_SelectedTabUnfocused")

 **Pestaña de documento seleccionada, sin foco**

 Fondo

 `Environment.FileTabInactiveGradientTop`

 Aunque no se usan en la interfaz de usuario moderna con temas, hay delimitadores de degradado y valores para este fondo.

 Primer plano (texto)

 `Environment.FileTabInactiveText`

 Borde

 `Environment.FileTabInactiveBorder`

 Se establece en el mismo color que el fondo.

 Borde de documento

 `Environment.FileTabInactiveDocumentBorderBackground`

#### <a name="background-tab"></a>Pestaña en segundo plano
 **Valor predeterminado**

 ![Pestaña en segundo plano](../../extensibility/ux-guidelines/media/0303-076-backgroundtab.png "0303 076_BackgroundTab")

 **Valor predeterminado de pestaña en segundo plano**

 Fondo

 `Environment.FileTabBackground`

 Primer plano (texto)

 `Environment.FileTabText`

 Borde

 `Environment.FileTabBorder`

 Se establece en el mismo color que el fondo.

 **Al mantener el mouse**

 ![Pestaña en segundo plano al mantener el mouse](../../extensibility/ux-guidelines/media/0303-077-backgroundtabhover.png "0303 077_BackgroundTabHover")

 **Pestaña en segundo plano al mantener el mouse**

 Fondo

 `Environment.FileTabHotGradientTop`

 Aunque no se usan en la interfaz de usuario moderna con temas, hay delimitadores de degradado y valores para este fondo.

 Primer plano (texto)

 `Environment.FileTabHotText`

 Borde

 `Environment.FileTabHotBorder`

 Se establece en el mismo color que el fondo.

#### <a name="preview-tab"></a>Pestaña de vista previa

La pestaña de vista previa aparece en la parte derecha del canal de pestañas de documentos cuando el usuario hace clic en un elemento de la ventana de herramientas del Explorador de soluciones. Funciona como una vista previa del documento y también proporciona al usuario la posibilidad de mantener el documento abierto en la parte izquierda del canal de pestañas de documentos. Solo se puede abrir una pestaña de vista previa a la vez. Las pestañas de vista previa tienen tanto el estado seleccionado como en segundo plano al igual que las pestañas abiertas y, además, pueden estar con y sin foco en su estado activo.

![Límite de pestaña de vista previa](../../extensibility/ux-guidelines/media/0303-078-previewtabredline.png "0303 078_PreviewTabRedline")

Use…
en cualquier parte donde cree vista previa provisional y quiere hacer coincidir algún elemento con el color de la pestaña de vista previa actual.

No use…
- para cualquier tipo de documento o pestaña que no sea provisional (vista previa).

- para cualquier interfaz de usuario que no desea que cambie automáticamente si se actualiza un tema del shell.

  **Pestaña de vista previa seleccionada: Centrado**

  Componente

  Elemento

  Nombre del token: Category.color

  ![Pestaña de vista previa enfocada](../../extensibility/ux-guidelines/media/0303-079-previewtabfocused.png "0303 079_PreviewTabFocused")

  **Pestaña de vista previa con foco**

  Fondo

  `Environment.FileTabProvisionalSelectedActive`

  Primer plano (texto)

  `Environment.FileTabProvisionalSelectedActiveForeground`

  Borde

  `Environment.FileTabProvisionalSelectedActiveBorder`

  Se establece en el mismo color que el fondo.

  Borde de documento

  `Environment.FileTabProvisionalSelectedActiveBorder`

  **Pestaña de vista previa seleccionada: Sin foco**

  Componente

  Elemento

  Nombre del token: Category.color

  ![Pestaña de vista previa sin foco](../../extensibility/ux-guidelines/media/0303-080-previewtabunfocused.png "0303 080_PreviewTabUnfocused")

  **Pestaña de vista previa sin foco**

  Fondo

  `Environment.FileTabProvisionalSelectedInactive`

  Primer plano (texto)

  `Environment.FileTabProvisionalSelectedInactiveForeground`

  Borde

  `Environment.FileTabProvisionalSelectedInactiveBorder`

  Borde de documento

  `Environment.FileTabProvisionalSelectedInactiveBorder`

  **Pestaña de vista previa en segundo plano: Valor predeterminado**

  Componente

  Elemento

  Nombre del token: Category.color

  ![Pestaña de vista previa en segundo plano](../../extensibility/ux-guidelines/media/0303-081-previewbackgroundtab.png "0303 081_PreviewBackgroundTab")

  **Pestaña de fondo de pestaña de vista previa**

  Fondo

  `Environment.FileTabProvisionalInactive`

  Primer plano (texto)

  `Environment.FileTabProvisionalInactiveForeground`

  Borde

  `Environment.FileTabProvisionalInactiveBorder`

  Se establece en el mismo color que el fondo.

  **Pestaña de vista previa en segundo plano: Al mantener el mouse**

  Componente

  Elemento

  Nombre del token: Category.color

  ![Pestaña de vista previa en segundo plano al mantener el mouse](../../extensibility/ux-guidelines/media/0303-082-previewbackgroundtabhover.png "0303 082_PreviewBackgroundTabHover")

  **Pestaña de vista previa pestaña en segundo plano al mantener el mouse**

  Fondo

  `Environment.FileTabProvisionalHover`

  Primer plano (texto)

  `Environment.FileTabProvisionalHoverForeground`

  Borde

  `Environment.FileTabProvisionalHoverBorder`

  Se establece en el mismo color que el fondo.

#### <a name="document-overflow-button"></a>Botón de desbordamiento de documento

El botón de desbordamiento de documento se muestra si hay uno o varios documentos abiertos, independientemente de si hay espacio vertical en la configuración actual para que quepan todas las pestañas de documentos. En el menú desplegable de desbordamiento de documento, que está controlado por los colores de **CommandBarMenu** (consulte [Menus](../../misc/shared-colors.md#BKMK_CommandMenus)), se muestra una lista de todos los documentos abiertos (visibles y ocultos) y los cambios de glifo de desbordamiento según si se muestran todos los documentos abiertos en el canal de pestañas.

![Límite de desbordamiento](../../extensibility/ux-guidelines/media/0303-083-overflowredline.png "0303 083_OverflowRedline")

Use…
si crea un botón de desbordamiento de documento personalizado.

No use…
- para interfaz de usuario que no sea similar a un botón de desbordamiento.

- para botones de desbordamiento de la barra de comandos.

  **Valor predeterminado**

  Componente

  Elemento

  Nombre del token: Category.color

  ![Overflow](../../extensibility/ux-guidelines/media/0303-084-overflow.png "0303 084_Overflow")

  **Botón de desbordamiento de documento**

  Fondo

  `Environment.DocWellOverflowButtonBackground`

  Primer plano (glifo)

  `Environment.DocWellOverflowButtonGlyph`

  Borde

  N/D

  **Al mantener el mouse**

  Componente

  Elemento

  Nombre del token: Category.color

  ![Desbordamiento al mantener el mouse](../../extensibility/ux-guidelines/media/0303-085-overflowhover.png "0303 085_OverflowHover")

  **Botón de desbordamiento de documento al mantener el mouse**

  Fondo

  `Environment.DocWellOverflowButtonMouseOverBackground`

  Primer plano (glifo)

  `Environment.DocWellOverflowButtonMouseOverGlyph`

  Borde

  `Environment.DocWellOverflowButtonMouseOverBorder`

  **Presionado**

  Componente

  Elemento

  Nombre del token: Category.color

  ![Desbordamiento presionado](../../extensibility/ux-guidelines/media/0303-086-overflowpressed.png "0303 086_OverflowPressed")

  **Presiona el botón de desbordamiento de documento**

  Fondo

  `Environment.DocWellOverflowButtonMouseDownBackground`

  Primer plano (glifo)

  `Environment.DocWellOverflowButtonMouseDownGlyph`

  Borde

  `Environment.DocWellOverflowButtonMouseDownBorder`

## <a name="tool-windows"></a>Ventanas de herramientas
 No es necesario replicar las ventanas de herramientas, porque las proporciona el entorno de Visual Studio. Sin embargo, quizá prefiera aprovechar los colores que se usan en las ventanas de herramientas para que la interfaz de usuario se muestre siempre coherente con esta parte del entorno de Visual Studio.

 ![Límite de ventana de herramienta](../../extensibility/ux-guidelines/media/0303-087-toolwindowredline.png "0303 087_ToolWindowRedline")

 Use…
en cualquier lugar donde cree interfaz de usuario que desea que coincida con la ventana de herramientas.

 No use…
para cualquier interfaz de usuario que no desea que cambie automáticamente si se actualiza un tema del shell.

### <a name="tool-window-frame"></a>Marco de ventana de herramientas
 Las ventanas de herramientas de Visual Studio se usan para diversas tareas y pueden estar en uno de varios estados diferentes. Si una ventana de herramientas está abierta, se puede asignar a cualquiera de los cuatro lados del área del documento. Estas ventanas también pueden flotar fuera del IDE, lo que permite reubicarlas en cualquier lugar dentro de la pantalla del usuario. Las ventanas flotantes siempre se colocan arriba del IDE. Por último, las ventanas de herramientas se pueden acoplar como ventanas de documento y aparecen como una pestaña en el cuadro de documento. Las ventanas de herramientas que se han acoplado como ventanas de documento se colorean en parte mediante los nombres de token de ventana de documento.

 ![Límite del marco de ventana de herramientas](../../extensibility/ux-guidelines/media/0303-088-toolwindowframeredline.png "0303 088_ToolWindowFrameRedline")

 Use…
en cualquier lugar donde cree interfaz de usuario que desea que coincida con la ventana de herramientas.

 No use…
para cualquier interfaz de usuario que no desea que cambie automáticamente si se actualiza un tema del shell.

 **Acoplado**

 Componente

 Elemento

 Nombre del token: Category.color

 ![Ventana de herramientas acoplada](../../extensibility/ux-guidelines/media/0303-089-toolwindowdocked.png "0303 089_ToolWindowDocked")

 Fondo

 `Environment.ToolWindowBackground`

 Borde

 `Environment.ToolWindowBorder`

 **Flotante: centrado**

 Componente

 Elemento

 Nombre del token: Category.color

 ![Ventana de herramientas enfocada](../../extensibility/ux-guidelines/media/0303-090-toolwindowfocused.png "0303 090_ToolWindowFocused")

 Fondo

 `Environment.ToolWindowBackground`

 Borde

 `Environment.MainWindowActiveDefaultBorder`

 **Flotante: sin foco**

 Componente

 Elemento

 Nombre del token: Category.color

 ![Ventana de herramientas no enfocado](../../extensibility/ux-guidelines/media/0303-091-toolwindowunfocused.png "0303 091_ToolWindowUnfocused")

 Fondo

 `Environment.ToolWindowBackground`

 Borde

 `Environment.MainWindowInactiveBorder`

### <a name="tool-window-title-bar"></a>Barra de título de la ventana de herramientas
 El borde de la barra de título no es realmente un borde, sino una línea gruesa en la parte superior de la barra de título. No tiene un nombre de token para su estado sin foco.

 ![Límite de barra de título de ventana de herramientas](../../extensibility/ux-guidelines/media/0303-092-toolwindowtitlebarredline.png "0303 092_ToolWindowTitleBarRedline")

 Use…
en cualquier lugar donde cree interfaz de usuario que desea que coincida con la ventana de herramientas.

 No use…
para cualquier interfaz de usuario que no desea que cambie automáticamente si se actualiza un tema del shell.

 **Centrado**

 Componente

 Elemento

 Nombre del token: Category.color

 ![Barra de título enfocado](../../extensibility/ux-guidelines/media/0303-093-titlebarfocused.png "0303 093_TitleBarFocused")

 **Barra de título con foco**

 Fondo

 `Environment.TitleBarActiveGradientBegin`

 Aunque no se usan en la interfaz de usuario moderna con temas, hay delimitadores de degradado y valores para este fondo.

 Primer plano (texto)

 `Environment.TitleBarActiveText`

 Borde

 `Environment.TitleBarActiveBorder`

 Se establece en el mismo color que el fondo.

 Controlador de arrastre

 `Environment.TitleBarDragHandleActive`

 **Sin foco**

 Componente

 Elemento

 Nombre del token: Category.color

 ![Barra de título no enfocado](../../extensibility/ux-guidelines/media/0303-094-titlebarunfocused.png "0303 094_TitleBarUnfocused")

 **Barra de título no enfocado**

 Fondo

 `Environment.TitleBarInactiveGradientBegin`

 Aunque no se usan en la interfaz de usuario moderna con temas, hay delimitadores de degradado y valores para este fondo.

 Primer plano (texto)

 `Environment.TitleBarInactiveText`

 Borde

 N/D

 Controlador de arrastre

 `Environment.TitleBarDragHandle`

#### <a name="title-bar-buttons"></a>Botones de la barra de título

![Límite de botón de barra de título](../../extensibility/ux-guidelines/media/0303-095-titlebarbuttonredline.png "0303 095_TitleBarButtonRedline")

Use…
para los botones que aparecen en la interfaz de usuario que usa los tokens de color de las barras de título de la ventana de herramientas.

No use…
- para los botones que aparecen en otras ubicaciones.

- en cualquier combinación de primer plano y fondo distinta de la especificada.

  **Valor predeterminado**

  Componente

  Elemento

  Nombre del token: Category.color

  ![Botón enfocado la barra de título](../../extensibility/ux-guidelines/media/0303-096-titlebarbuttonfocused.png "0303 096_TitleBarButtonFocused")

  **Centrado**

  Fondo

  N/D

  Primer plano (glifo)

  `Environment.ToolWindowButtonActiveGlyph`

  Borde

  N/D

  ![Botón sin foco de la barra de título](../../extensibility/ux-guidelines/media/0303-097-titlebarbuttonunfocused.png "0303 097_TitleBarButtonUnfocused")

  **Sin foco**

  Fondo

  N/D

  Primer plano (glifo)

  `Environment.ToolWindowButtonInactiveGlyph`

  Borde

  N/D

  **Al mantener el mouse**

  Componente

  Elemento

  Nombre del token: Category.color

  ![Botón de barra de título enfocado al mantener el mouse](../../extensibility/ux-guidelines/media/0303-098-titlebarbuttonfocusedhover.png "0303 098_TitleBarButtonFocusedHover")

  **Centrado**

  Fondo

  `Environment.ToolWindowButtonHoverActive`

  Primer plano (glifo)

  `Environment.ToolWindowButtonHoverActiveGlyph`

  Borde

  `Environment.ToolWindowButtonHoverActiveBorder`

  ![No enfocado al mantener el mouse del botón de la barra de título](../../extensibility/ux-guidelines/media/0303-099-titlebarbuttonunfocusedhover.png "0303 099_TitleBarButtonUnfocusedHover")

  **Sin foco**

  Fondo

  `Environment.ToolWindowButtonHoverInactive`

  Primer plano (glifo)

  `Environment.ToolWindowButtonHoverInactiveGlyph`

  Borde

  `Environment.ToolWindowButtonHoverInactiveBorder`

  **Presionado**

  Componente

  Elemento

  Nombre del token: Category.color

  ![Botón enfocado y presionado de la barra de título](../../extensibility/ux-guidelines/media/0303-100-titlebarbuttonfocusedpressed.png "0303 100_TitleBarButtonFocusedPressed")

  **Centrado**

  Fondo

  `Environment.ToolWindowButtonDown`

  Primer plano (glifo)

  `Environment.ToolWindowButtonDownActiveGlyph`

  Borde

  `Environment.ToolWindowButtonDownBorder`

  ![Botón de barra de título no enfocado y presionado](../../extensibility/ux-guidelines/media/0303-101-titlebarbuttonunfocusedpressed.png "0303 101_TitleBarButtonUnfocusedPressed")

  **Sin foco**

  Fondo

  `Environment.ToolWindowButtonDown`

  Primer plano (glifo)

  `Environment.ToolWindowButtonDownInactiveGlyph`

  Borde

  `Environment.ToolWindowButtonDownBorder`

### <a name="tool-window-tabs"></a>Pestañas de ventana de herramientas
 ![Límite de pestaña de ventana de herramienta](../../extensibility/ux-guidelines/media/0303-102-toolwindowtabredline.png "0303 102_ToolWindowTabRedline")

 Use…
en cualquier lugar donde cree interfaz de usuario que desea que coincida con la ventana de herramientas.

 No use…
para cualquier interfaz de usuario que no desea que cambie automáticamente si se actualiza un tema del shell.

 **Pestaña seleccionada**

 Componente

 Elemento

 Nombre del token: Category.color

 ![Pestaña de ventana de herramientas enfocado](../../extensibility/ux-guidelines/media/0303-103-toolwindowtabfocused.png "0303 103_ToolWindowTabFocused")

 **Pestaña de ventana de herramienta seleccionada, con foco**

 Fondo

 `Environment.ToolWindowTabSelectedTab`

 Primer plano (texto)

 `Environment.ToolWindowTabSelectedActiveText`

 Borde

 `Environment.ToolWindowTabSelectedBorder`

 Se establece en el mismo color que el fondo.

 Componente

 Elemento

 Nombre del token: Category.color

 ![Pestaña de ventana de herramientas no enfocado](../../extensibility/ux-guidelines/media/0303-104-toolwindowtabunfocused.png "0303 104_ToolWindowTabUnfocused")

 **Pestaña de ventana de herramienta seleccionada, sin foco**

 Fondo

 `Environment.ToolWindowTabSelectedTab`

 Primer plano (texto)

 `Environment.ToolWindowTabSelectedText`

 Borde

 `Environment.ToolWindowTabSelectedBorder`

 Se establece en el mismo color que el fondo.

 **Pestaña en segundo plano**

 Componente

 Elemento

 Nombre del token: Category.color

 ![Pestaña en segundo plano de ventana de herramienta](../../extensibility/ux-guidelines/media/0303-105-toolwindowbackgroundtab.png "0303 105_ToolWindowBackgroundTab")

 **Pestaña de ventana de herramientas en segundo plano**

 Fondo

 `Environment.ToolWindowTabGradientBegin`

 Los delimitadores de degradado se establecen en el mismo valor de color en Visual Studio 2013.

 `Environment.ToolWindowTabGradientEnd`

 Los delimitadores de degradado se establecen en el mismo valor de color en Visual Studio 2013.

 Primer plano (texto)

 `Environment.ToolWindowTabText`

 Borde

 `Environment.ToolWindowTabBorder`

 Componente

 Elemento

 Nombre del token: Category.color

 ![Pestaña de fondo de ventana de herramientas al mantener el mouse](../../extensibility/ux-guidelines/media/0303-106-toolwindowbackgroundtabhover.png "0303 106_ToolWindowBackgroundTabHover")

 **Pestaña de ventana de herramientas en segundo plano al mantener el mouse**

 Fondo

 `Environment.ToolWindowTabMouseOverBackgroundBegin`

 Los delimitadores de degradado se establecen en el mismo valor de color en Visual Studio 2013.

 `Environment.ToolWindowTabMouseOverBackgroundEnd`

 Los delimitadores de degradado se establecen en el mismo valor de color en Visual Studio 2013.

 Primer plano (texto)

 `Environment.ToolWindowTabMouseOverText`

 Borde

 `Environment.ToolWindowTabMouseOverBorder`

 Se establece en el mismo color que el fondo.

### <a name="auto-hide-tabs"></a>Pestaña de ocultación automática
 ![Auto&#45;ocultar límite](../../extensibility/ux-guidelines/media/0303-107-autohideredline.png "0303 107_AutoHideRedline")

 Use…
en cualquier lugar donde cree interfaz de usuario que desea que coincida con las pestañas de ventana de herramientas de ocultación automática.

 No use…
para cualquier interfaz de usuario que no desea que cambie automáticamente si se actualiza un tema del shell.

 **Valor predeterminado**

 Componente

 Elemento

 Nombre del token: Category.color

 ![Auto&#45;ocultar la ficha](../../extensibility/ux-guidelines/media/0303-108-autohidetab.png "0303 108_AutoHideTab")

 **Pestaña de ocultación automática predeterminada**

 Fondo

 `Environment.AutoHideTabBackgroundBegin`

 Aunque no se usan en la interfaz de usuario moderna con temas, hay delimitadores de degradado y valores para este fondo.

 Primer plano (texto)

 `Environment.AutoHideTabText`

 Borde

 `Environment.AutoHideTabBorder`

 **Al mantener el mouse**

 Componente

 Elemento

 Nombre del token: Category.color

 ![Auto&#45;ocultar la ficha al mantener el mouse](../../extensibility/ux-guidelines/media/0303-109-autohidetabhover.png "0303 109_AutoHideTabHover")

 **Pestaña de ocultación automática al mantener el mouse**

 Fondo

 `Environment.AutoHideTabMouseOverBackgroundBegin`

 Aunque no se usan en la interfaz de usuario moderna con temas, hay delimitadores de degradado y valores para este fondo.

 Primer plano (texto)

 `Environment.AutoHideTabMouseOverText`

 Borde

 `Environment.AutoHideTabMouseOverBorder`

## <a name="common-shared-controls"></a>Controles comunes compartidos
 Si usa una barra de comandos estándar de Visual Studio en su característica, puede acceder a los controles de shell con estilo y no debe volver a basar en modelo estos controles comunes. Sin embargo, si necesita crear una barra de comandos personalizada, también podría ser necesario crear controles personalizados. En ese caso, asegúrese de usar los nombres de token correctos para cada uno de los siguientes controles de modo que la interfaz de usuario sea coherente con el resto de Visual Studio.

### <a name="search-box"></a>Cuadro de búsqueda
 Siempre que sea posible, use el control de búsqueda común proporcionado por el entorno de Visual Studio. Los colores del cuadro de búsqueda se encuentran en la categoría "SearchControl" del archivo **ShellColors.pkgdef** , que contiene los nombres de token para el campo de entrada, el botón de acción, el botón desplegable y el menú desplegable.

 Un cuadro de búsqueda puede tener uno de varios estados, algunos de los cuales son mutuamente excluyentes:

- "Con foco" o "sin foco" se refiere a si el cursor está en el cuadro de texto.

- "Activo" o "inactivo" se refiere a si el usuario ha especificado una consulta de búsqueda en el cuadro de texto.

- "Desplazar el puntero" significa que el usuario ha colocado el puntero sobre el cuadro de búsqueda con el mouse (este estado invalida todos los demás estados).

- "Deshabilitado" significa que la función de búsqueda se ha desactivado para el contexto actual.

  ![Límite de cuadro de búsqueda](../../extensibility/ux-guidelines/media/0303-110-searchboxredline.png "0303 110_SearchBoxRedline")

  Use…
  al diseñar un cuadro de búsqueda personalizado.

  No use…
  - para elementos que no sean un cuadro de búsqueda.

- para elementos que no desea que siempre coincidan con la interfaz de usuario de búsqueda.

  **Centrado**

  Componente

  Elemento

  Nombre del token: Category.color

  ![Campo de entrada de búsqueda enfocado](../../extensibility/ux-guidelines/media/0303-111-searchinputfieldfocused.png "0303 111_SearchInputFieldFocused")

  **Campo de entrada**

  Fondo

  `SearchControl.FocusedBackground`

  Primer plano (texto)

  `SearchControl.FocusedBackground`

  Borde

  `SearchControl.FocusedBorder`

  Separador

  `SearchControl.FocusedDropDownSeparator`

  ![Botón de acción de búsqueda enfocado](../../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303 112_SearchActionButtonFocused")

  **Botón de acción**

  Fondo

  None

  Primer plano (glifo de búsqueda)

  `SearchControl.SearchGlyph`

  Primer plano (glifo de detención)

  `SearchControl.StopGlyph`

  Primer plano (glifo de borrado)

  `SearchControl.ClearGlyph`

  Borde

  N/D

  ![Lista de búsqueda&#45;hacia abajo del botón enfocado](../../extensibility/ux-guidelines/media/0303-113-searchdropdownbuttonfocused.png "0303 113_SearchDropdownButtonFocused")

  **Botón desplegable**

  Fondo

  `SearchControl.FocusedDropDownButton`

  Primer plano (glifo)

  `SearchControl.FocusedDropDownButtonGlyph`

  Borde

  `SearchControl.FocusedDropDownButtonBorder`

  **Sin foco**

  Componente

  Elemento

  Nombre del token: Category.color

  ![Campo de entrada de búsqueda no enfocado](../../extensibility/ux-guidelines/media/0303-114-searchinputfieldunfocused.png "0303 114_SearchInputFieldUnfocused")

  **Campo de entrada activo**

  Fondo

  `SearchControl.SearchActiveBackground`

  Primer plano (texto)

  `SearchControl.SearchActiveBackground`

  Borde

  `SearchControl.UnfocusedBorder`

  Separador

  `SearchControl.DropDownSeparator`

  ![Campo de entrada de búsqueda no enfocado e inactivo](../../extensibility/ux-guidelines/media/0303-114-1-searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")

  **Campo de entrada inactivo**

  Fondo

  `SearchControl.Unfocused`

  Primer plano (texto)

  `SearchControl.Unfocused`

  Borde

  `SearchControl.UnfocusedBorder`

  Separador

  `SearchControl.DropDownSeparator`

  ![Botón de acción de búsqueda no enfocado](../../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303 115_SearchActionButtonUnfocused")

  **Botón de acción**

  Fondo

  N/D

  Primer plano (glifo de búsqueda)

  `SearchControl.SearchGlyph`

  Primer plano (glifo de detención)

  `SearchControl.StopGlyph`

  Primer plano (glifo de borrado)

  `SearchControl.ClearGlyph`

  Borde

  N/D

  ![Lista de búsqueda&#45;presionado el botón sin foco](../../extensibility/ux-guidelines/media/0303-116-searchdropdownbuttonunfocused.png "0303 116_SearchDropdownButtonUnfocused")

  **Botón desplegable**

  Fondo

  `SearchControl.UnfocusedDropDownButton`

  Primer plano (glifo)

  `SearchControl.UnfocusedDropDownButtonGlyph`

  Borde

  `SearchControl.UnfocusedDropDownButtonBorder`

  **Presionado**

  Componente

  Elemento

  Nombre del token: Category.color

  ![Presiona el botón de acción de búsqueda](../../extensibility/ux-guidelines/media/0303-116-1-searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")

  **Botón de acción**

  Fondo

  `SearchControl.ActionButtonMouseDown`

  Primer plano (glifo)

  `SearchControl.ActionButtonMouseDownGlyph`

  Borde

  `SearchControl.ActionButtonMouseDownBorder`

  ![Lista de búsqueda&#45;presionado el botón presionado](../../extensibility/ux-guidelines/media/0303-116-2-searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")

  **Botón desplegable**

  Fondo

  `SearchControl.MouseDownDropDownButton`

  Primer plano (glifo)

  `SearchControl.MouseDownDropDownButtonGlyph`

  Borde

  `SearchControl.MouseDownDropDownButtonBorder`

  **Resaltado (solo texto)**

  Componente

  Elemento

  Nombre del token: Category.color

  ![Resaltado de campo de entrada de búsqueda](../../extensibility/ux-guidelines/media/0303-120-searchinputfieldhighlight.png "0303 120_SearchInputFieldHighlight")

  **Campo de entrada con texto resaltado**

  Fondo

  `SearchControl.Selection`

  Primer plano (texto)

  `SearchControl.FocusedBackground`

  Borde

  None

  Separador

  `SearchControl.FocusedDropDownSeparator`

  **Deshabilitado**

  Componente

  Elemento

  Nombre del token: Category.color

  ![Campo de entrada de búsqueda deshabilitado](../../extensibility/ux-guidelines/media/0303-121-searchinputfielddisabled.png "0303 121_SearchInputFieldDisabled")

  **Campo de entrada**

  Fondo

  `SearchControl.Disabled`

  Primer plano (texto)

  `SearchControl.Disabled`

  Borde

  `SearchControl.DisabledBorder`

  Separador

  `SearchControl.DropDownSeparator`

  ![Botón de acción de búsqueda deshabilitado](../../extensibility/ux-guidelines/media/0303-122-searchactionbuttondisabled.png "0303 122_SearchActionButtonDisabled")

  **Botón de acción**

  Fondo

  None

  Primer plano (glifo)

  `SearchControl.ActionButtonDisabledGlyph`

  Borde

  None

  ![Lista de búsqueda&#45;presionado el botón deshabilitado](../../extensibility/ux-guidelines/media/0303-123-searchdropdownbuttondisabled.png "0303 123_SearchDropdownButtonDisabled")

  **Botón desplegable**

  Fondo

  None

  Primer plano (glifo)

  `SearchControl.DisabledDownButtonGlyph`

  Borde

  None

#### <a name="search-drop-down-lists"></a>Listas desplegables de búsqueda

El menú desplegable del cuadro de búsqueda puede ser ligeramente más complejo que otros menús desplegables en Visual Studio. Las secciones de "búsquedas sugeridas" y "opciones de búsqueda" pueden aparecer solas o juntas en el menú y cada una de ellas se colorea por separado. Además, estas secciones están separadas por una línea cuando aparecen juntas y un borde rodea todo el menú desplegable.

![Lista de búsqueda&#45;hacia abajo línea roja](../../extensibility/ux-guidelines/media/0303-124-searchdropdownredline.png "0303 124_SearchDropdownRedline")

Use…
- si crea una lista desplegable de búsqueda personalizada.

- los nombres de token correctos para los componentes de lista correctos.

  No use…
  - para las listas desplegables que aparecen en otros contextos.

- en cualquier combinación de primer plano y fondo distinta de la especificada.

  **Predeterminado (no hay otros Estados)**

  Elemento

  Nombre del token: Category.color

  Borde

  `SearchControl.PopupBorder`

  Separador

  `SearchControl.PopupSectionHeaderSeparator`

  Sombra

  `Environment.DropShadowBackground`

  **Valor predeterminado**

  Componente

  Elemento

  Nombre del token: Category.color

  ![Búsqueda sugerida](../../extensibility/ux-guidelines/media/0303-125-searchsuggested.png "0303 125_SearchSuggested")

  **Búsquedas sugeridas**

  Fondo

  `SearchControl.PopupItemsListBackgroundGradientBegin`

  Aunque no se usan en la interfaz de usuario moderna con temas, hay delimitadores de degradado y valores para este fondo.

  Primer plano (texto)

  `SearchControl.PopupItemText`

  ![Casilla de verificación de búsqueda](../../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303 126_SearchCheckbox")

  **Opciones de búsqueda (casilla)**

  ![Las opciones de búsqueda](../../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303 127_SearchOptions")

  **Opciones de búsqueda (vínculo)**

  Fondo

  `SearchControl.PopupSectionBackgroundGradientBegin`

  Aunque no se usan en la interfaz de usuario moderna con temas, hay delimitadores de degradado y valores para este fondo.

  Primer plano (texto de casilla)

  `SearchControl.PopupCheckboxText`

  Primer plano (texto de vínculo)

  `SearchControl.PopupButtonText`

  Fondo de encabezado

  `SearchControl.PopupSectionHeaderGradientBegin`

  Aunque no se usan en la interfaz de usuario moderna con temas, hay delimitadores de degradado y valores para este fondo.

  Primer plano (texto de encabezado)

  `SearchControl.PopupSectionHeaderText`

  **Al mantener el mouse**

  Componente

  Elemento

  Nombre del token: Category.color

  ![Búsqueda sugerida al mantener el mouse](../../extensibility/ux-guidelines/media/0303-128-searchsuggestedhover.png "0303 128_SearchSuggestedHover")

  **Búsquedas sugeridas**

  Fondo

  `SearchControl.PopupControlMouseOverBackgroundGradientBegin`

  Aunque no se usan en la interfaz de usuario moderna con temas, hay delimitadores de degradado y valores para este fondo.

  Primer plano (texto)

  `SearchControl.PopupMouseOverItemText`

  Borde

  `SearchControl.PopupControlMouseOverBorder`

  ![Casilla de verificación de búsqueda al mantener el mouse](../../extensibility/ux-guidelines/media/0303-129-searchcheckboxhover.png "0303 129_SearchCheckboxHover")

  **Búsquedas sugeridas (casilla)**

  ![Las opciones al mantener el puntero de búsqueda](../../extensibility/ux-guidelines/media/0303-130-searchoptionshover.png "0303 130_SearchOptionsHover")

  **Opciones de búsqueda**

  Fondo

  `SearchControl.PopupControlMouseOverBackgroundGradientBegin`

  Aunque no se usan en la interfaz de usuario moderna con temas, hay delimitadores de degradado y valores para este fondo.

  Primer plano (texto de casilla)

  `SearchControl.PopupCheckboxMouseDownText`

  Primer plano (texto de vínculo)

  `SearchControl.PopupButtonMouseDownText`

  Borde

  `SearchControl.PopupControlMouseOverBorder`

  **Presionado**

  Componente

  Elemento

  Nombre del token: Category.color

  ![Búsqueda sugerida presionada](../../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303 131_SearchSuggestedPressed")

  **Búsquedas sugeridas (casilla)**

  ![Buscar opciones presionado](../../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303 132_SearchOptionsPressed")

  **Opciones de búsqueda**

  Fondo de casilla

  `SearchControl.PopupControlMouseDownBackgroundGradientBegin`

  Aunque no se usan en la interfaz de usuario moderna con temas, hay delimitadores de degradado y valores para este fondo.

  `SearchControl.PopupControlMouseDownBackgroundGradientEnd`

  Aunque no se usan en la interfaz de usuario moderna con temas, hay delimitadores de degradado y valores para este fondo.

  Primer plano (texto de casilla)

  `SearchControl.PopupCheckboxMouseDownText`

  Fondo de vínculo

  `SearchControl.PopupButtonMouseDownBackgroundGradientBegin`

  Aunque no se usan en la interfaz de usuario moderna con temas, hay delimitadores de degradado y valores para este fondo.

  Primer plano (texto de vínculo)

  `SearchControl.PopupButtonMouseDownText`

### <a name="hyperlink"></a>Hipervínculo
 El hipervínculo es un control que no tiene un par de primer plano y fondo. En todos los casos, use el color de hipervínculo de primer plano, que se muestre adecuadamente en fondos oscuros, grises y blancos. Si no usa el token de color para el control de hipervínculo, verá el color predeterminado del sistema para el estado Presionado, que parpadeará en rojo. Esa es la señal de que no se está usando el token de color correcto del entorno para el control.

 ![Límite de hipervínculo](../../extensibility/ux-guidelines/media/0303-133-hyperlinkredline.png "0303 133_HyperlinkRedline")

 Use…
si es necesario crear un hipervínculo personalizado.

 No use…
para elementos que no sean un hipervínculo.

 **Valor predeterminado**

 Componente

 Elemento

 Nombre del token: Category.color

 ![Hipervínculo predeterminado](../../extensibility/ux-guidelines/media/0303-134-hyperlink.png "0303 134_Hyperlink")

 Primer plano (texto)

 `Environment.PanelHyperlink`

 **Al mantener el mouse**

 Componente

 Elemento

 Nombre del token: Category.color

 ![Hipervínculo al mantener el mouse](../../extensibility/ux-guidelines/media/0303-135-hyperlinkhover.png "0303 135_HyperlinkHover")

 Primer plano (texto)

 `Environment.PanelHyperlinkHover`

 **Presionado**

 Componente

 Elemento

 Nombre del token: Category.color

 ![Hipervínculo presionado](../../extensibility/ux-guidelines/media/0303-136-hyperlinkpressed.png "0303 136_HyperlinkPressed")

 Primer plano (texto)

 `Environment.PanelHyperlinkPressed`

 **Deshabilitado**

 Componente

 Elemento

 Nombre del token: Category.color

 ![Hipervínculo deshabilitado](../../extensibility/ux-guidelines/media/0303-137-hyperlinkdisabled.png "0303 137_HyperlinkDisabled")

 Primer plano (texto)

 `Environment.PanelHyperlinkDisabled`

### <a name="infobar"></a>Barra de información
 Las barras de información se usan para proporcionar más información sobre un determinado contexto y siempre se muestran en la parte superior de una ventana de documento o una ventana de herramientas.

 ![Límite de barra de](../../extensibility/ux-guidelines/media/0303-138-infobarredline.png "0303 138_InfobarRedline")

 Use…
al crear barras de información personalizadas.

 No use…
para elementos de interfaz de usuario que no sean similares a una barra de información.

 Componente

 Elemento

 Nombre del token: Category.color

 ![Infobar](../../extensibility/ux-guidelines/media/0303-139-infobar.png "0303-139_Infobar")

 **Infobar**

 Fondo

 `Environment.InfoBackground`

 Primer plano (texto)

 `Environment.InfoText`

 Borde

 `Environment.ToolWindowBorder`

### <a name="scroll-bar"></a>Barra de desplazamiento
 Las barras de desplazamiento reciben el estilo del entorno de Visual Studio y no es necesario aplicarles un tema. Sin embargo, puede decidir desea aprovechar los colores utilizados en las barras de desplazamiento para que la interfaz de usuario se muestre siempre coherente con esta parte del entorno de Visual Studio.

 ![Límite de barra de desplazamiento](../../extensibility/ux-guidelines/media/0303-140-scrollbarredline.png "0303 140_ScrollbarRedline")

 Use…
si crea interfaz de usuario que quiere hacer coincidir con las barras de desplazamiento de Visual Studio.

 No use … para cualquier cosa que no desea que siempre coincida con la interfaz de usuario de la barra de desplazamiento.

 **Valor predeterminado**

 Componente

 Elemento

 Nombre del token: Category.color

 ![Barra de desplazamiento](../../extensibility/ux-guidelines/media/0303-141-scrollbar.png "0303 141_Scrollbar")

 **Barra de desplazamiento**

 Barra de desplazamiento

 `Environment.ScrollBarBackground`

 Primer plano (control)

 `Environment.ScrollBarThumbBackground`

 ![Flecha de barra de desplazamiento](../../extensibility/ux-guidelines/media/0303-142-scrollbararrow.png "0303 142_ScrollbarArrow")

 **Flecha de desplazamiento**

 Fondo

 `Environment.ScrollBarArrowBackground`

 Se establece en el mismo color que la barra de desplazamiento.

 Primer plano (glifo)

 `Environment.ScrollBarArrowGlyph`

 **Al mantener el mouse**

 Componente

 Elemento

 Nombre del token: Category.color

 ![Barra de desplazamiento al mantener el mouse](../../extensibility/ux-guidelines/media/0303-143-scrollbarhover.png "0303 143_ScrollbarHover")

 **Barra de desplazamiento**

 Barra de desplazamiento

 `Environment.ScrollBarBackground`

 Primer plano (control)

 `Environment.ScrollBarThumbMouseOverBackground`

 ![Flecha de desplazamiento de la barra de desplazamiento](../../extensibility/ux-guidelines/media/0303-144-scrollbararrowhover.png "0303 144_ScrollbarArrowHover")

 **Flecha de desplazamiento**

 Fondo

 `Environment.ScrollBarArrowMouseOverBackground`

 Se establece en el mismo color que la barra de desplazamiento.

 Primer plano (glifo)

 `Environment.ScrollBarArrowGlyphMouseOver`

 **Presionado**

 Componente

 Elemento

 Nombre del token: Category.color

 ![Presiona la barra de desplazamiento](../../extensibility/ux-guidelines/media/0303-145-scrollbarpressed.png "0303 145_ScrollbarPressed")

 **Barra de desplazamiento**

 Barra de desplazamiento

 `Environment.ScrollBarBackground`

 Primer plano (control)

 `Environment.ScrollBarThumbPressedBackground`

 ![Flecha presionada la barra de desplazamiento](../../extensibility/ux-guidelines/media/0303-146-scrollbararrowpressed.png "0303 146_ScrollbarArrowPressed")

 **Flecha de desplazamiento**

 Fondo

 `Environment.ScrollBarArrowPressedBackground`

 Se establece en el mismo color que la barra de desplazamiento.

 Primer plano (glifo)

 `Environment.ScrollBarArrowGlyphPressed`

### <a name="BKMK_TreeView"></a> Vista de árbol

Varias ventanas de herramientas, incluidos el Explorador de soluciones, el Explorador de servidores y la Vista de clases, implementan un esquema organizativo jerárquico cuyos colores se controlan mediante los nombres de colores de la categoría TreeView. Todos los elementos de una vista de árbol tienen colores de fondo y de texto. Los elementos que tienen elementos secundarios anidados también tienen glifos que indican si el elemento está expandido o contraído.

![Límite de la vista de árbol](../../extensibility/ux-guidelines/media/0303-147-treeviewredline.png "0303 147_TreeViewRedline")

Use…
en cualquier lugar en el que es necesario implementar una vista organizativa jerárquica.

No use…
- para cualquier elemento que no sea similar a una vista de árbol.

- en cualquier combinación de primer plano y fondo distinta de la especificada.

  **Valor predeterminado**

  Componente

  Elemento

  Nombre del token: Category.color

  ![Vista de árbol](../../extensibility/ux-guidelines/media/0303-148-treeview.png "0303 148_TreeView")

  Fondo

  `TreeView.Background`

  Primer plano (texto)

  `TreeView.Background`

  Primer plano (glifo)

  `TreeView.Glyph`

  Borde

  None

  **Al mantener el mouse**

  Componente

  Elemento

  Nombre del token: Category.color

  ![Mantener el mouse en la vista de árbol](../../extensibility/ux-guidelines/media/0303-149-treeviewhover.png "0303 149_TreeViewHover")

  Fondo

  `TreeView.Background`

  Primer plano (texto)

  `TreeView.Background`

  Primer plano (glifo)

  `TreeView.GlyphMouseOver`

  Borde

  None

  **Arrastre sobre**

  Componente

  Elemento

  Nombre del token: Category.color

  ![Árbol de la vista dragover](../../extensibility/ux-guidelines/media/0303-150-treeviewdragover.png "0303 150_TreeViewDragOver")

  Fondo

  `TreeView.DragOverItem`

  Primer plano (texto)

  `TreeView.DragOverItem`

  Primer plano (glifo)

  `TreeView.DragOverItemGlyph`

  Borde

  None

  **seleccionado**

  Componente

  Elemento

  Nombre del token: Category.color

  ![Centrados la vista de árbol](../../extensibility/ux-guidelines/media/0303-151-treeviewfocused.png "0303 151_TreeViewFocused")

  **Centrado**

  Fondo

  `TreeView.SelectedItemActive`

  Primer plano (texto)

  `TreeView.SelectedItemActive`

  Primer plano (glifo)

  `TreeView.SelectedItemActiveGlyph`

  Borde

  `TreeView.FocusVisualBorder`

  ![Sin foco de la vista de árbol](../../extensibility/ux-guidelines/media/0303-152-treeviewunfocused.png "0303 152_TreeViewUnfocused")

  **Sin foco**

  Fondo

  `TreeView.SelectedItemInactive`

  Primer plano (texto)

  `TreeView.SelectedItemInactive`

  Primer plano (glifo)

  `TreeView.SelectedItemInactiveGlyph`

  Borde

  None

  **Mantener el mouse seleccionado**

  Componente

  Elemento

  Nombre del token: Category.color

  ![Enfocada al mantener el mouse de vista de árbol](../../extensibility/ux-guidelines/media/0303-153-treeviewfocusedhover.png "0303 153_TreeViewFocusedHover")

  **Centrado**

  Fondo

  `TreeView.SelectedItemActive`

  Primer plano (texto)

  `TreeView.SelectedItemActive`

  Primer plano (glifo)

  `TreeView.SelectedItemActiveGlyphMouseOver`

  Borde

  Ninguno`TreeView.FocusVisualBorder`

  ![Vista no enfocada al mantener el mouse de árbol](../../extensibility/ux-guidelines/media/0303-154-treeviewunfocusedhover.png "0303 154_TreeViewUnfocusedHover")

  **Sin foco**

  Fondo

  `TreeView.SelectedItemInactive`

  Primer plano (texto)

  `TreeView.SelectedItemInactive`

  Primer plano (glifo)

  `TreeView.SelectedItemActiveGlyphMouseOver`

  Borde

  None

### <a name="button-controls"></a>Controles de botón
 ![Límite de control de botón](../../extensibility/ux-guidelines/media/0303-155-buttoncontrolredline.png "0303 155_ButtonControlRedline")

 Use…
para los botones del cuadro de documento que quiere integrar con los temas de Visual Studio (claro, oscuro, azul o un tema de contraste alto del sistema).

 No use…
para los botones que se mostrarán con un fondo personalizado que no forma parte de un tema de Visual Studio.

 **Valor predeterminado**

 Componente

 Elemento

 Nombre del token: Category.color

 ![Botón](../../extensibility/ux-guidelines/media/0303-156-button.png "0303 156_Button")

 Botón

 `CommonControls.Button`

 Borde de botón

 `CommonControls.ButtonBorder`

 **Deshabilitado**

 Componente

 Elemento

 Nombre del token: Category.color

 ![Botón deshabilitado](../../extensibility/ux-guidelines/media/0303-157-buttondisabled.png "0303 157_ButtonDisabled")

 Botón

 `CommonControls.ButtonDisabled`

 Borde de botón

 `CommonControls.ButtonBorderDisabled`

 **Al mantener el mouse**

 Componente

 Elemento

 Nombre del token: Category.color

 ![Botón de desplazamiento](../../extensibility/ux-guidelines/media/0303-158-buttonhover.png "0303 158_ButtonHover")

 Botón

 `CommonControls.ButtonHover`

 Borde de botón

 `CommonControls.ButtonBorderHover`

 **Presionado**

 Componente

 Elemento

 Nombre del token: Category.color

 ![Botón presionado](../../extensibility/ux-guidelines/media/0303-159-buttonpressed.png "0303 159_ButtonPressed")

 Botón

 `CommonControls.ButtonPressed`

 Borde de botón

 `CommonControls.ButtonBorderPressed`

 **Centrado**

 Componente

 Elemento

 Nombre del token: Category.color

 ![Botón enfocado](../../extensibility/ux-guidelines/media/0303-160-buttonfocused.png "0303 160_ButtonFocused")

 Botón

 `CommonControls.ButtonFocused`

 Borde de botón

 `CommonControls.ButtonBorderFocused`

### <a name="check-box-controls"></a>Controles de casilla
 ![Límite de casilla de verificación](../../extensibility/ux-guidelines/media/0303-161-checkboxredline.png "0303 161_CheckboxRedline")

 Use…
para los controles de casilla incluidos en el cuadro de documento.

 No use…
para cualquier interfaz de usuario que no sea un control de casilla.

 **Valor predeterminado**

 Componente

 Elemento

 Nombre del token: Category.color

 ![Casilla de verificación](../../extensibility/ux-guidelines/media/0303-162-checkbox.png "0303 162_Checkbox")

 Fondo

 `CommonControls.CheckBoxBackground`

 Borde

 `CommonControls.CheckBoxBorder`

 Text

 `CommonControls.CheckBoxText`

 Glifo

 `CommonControls.CheckBoxGlyph`

 **Deshabilitado**

 Componente

 Elemento

 Nombre del token: Category.color

 ![Casilla de verificación deshabilitada](../../extensibility/ux-guidelines/media/0303-163-checkboxdisabled.png "0303 163_CheckboxDisabled")

 Fondo

 `CommonControls.CheckBoxBackgroundDisabled`

 Borde

 `CommonControls.CheckBoxBorderDisabled`

 Text

 `CommonControls.CheckBoxTextDisabled`

 Glifo

 `CommonControls.CheckBoxGlyphDisabled`

 **Al mantener el mouse**

 Componente

 Elemento

 Nombre del token: Category.color

 ![Casilla de verificación al mantener el mouse](../../extensibility/ux-guidelines/media/0303-164-checkboxhover.png "0303 164_CheckboxHover")

 Fondo

 `CommonControls.CheckBoxBackgroundHover`

 Borde

 `CommonControls.CheckBoxBorderHover`

 Text

 `CommonControls.CheckBoxTextHover`

 Glifo

 `CommonControls.CheckBoxGlyphHover`

 **Presionado**

 Componente

 Elemento

 Nombre del token: Category.color

 ![Casilla de verificación presionada](../../extensibility/ux-guidelines/media/0303-165-checkboxpressed.png "0303 165_CheckboxPressed")

 Fondo

 `CommonControls.CheckBoxBackgroundPressed`

 Borde

 `CommonControls.CheckBoxBorderPressed`

 Text

 `CommonControls.CheckBoxTextPressed`

 Glifo

 `CommonControls.CheckBoxGlyphPressed`

 **Centrado**

 Componente

 Elemento

 Nombre del token: Category.color

 ![Casilla de verificación centrado](../../extensibility/ux-guidelines/media/0303-166-checkboxfocused.png "0303 166_CheckboxFocused")

 Fondo

 `CommonControls.CheckBoxBackgroundFocused`

 Borde

 `CommonControls.CheckBoxBorderFocused`

 Text

 `CommonControls.CheckBoxTextFocused`

 Glifo

 `CommonControls.CheckBoxGlyphFocused`

### <a name="drop-boxcombo-box-controls"></a>Controles de cuadro combinado o lista desplegable

![Quitar&#45;abajo&#47;límite de cuadro combinado](../../extensibility/ux-guidelines/media/0303-167-dropdowncomboboxredline.png "0303 167_DropDownComboBoxRedline")

Use…
para las listas desplegables y cuadros combinado que forman parte del cuadro de documento.

No use…
- para cualquier interfaz de usuario que no sea una lista desplegable o un cuadro combinado.

- para una [Drop-down](../../misc/shared-colors.md#BKMK_CommandDropDown) o un [Combo box](../../misc/shared-colors.md#BKMK_CommandComboBox) de la barra de comandos.

  **Valor predeterminado**

  Componente

  Elemento

  Nombre del token: Category.color

  ![Quitar&#45;abajo&#47;cuadro combinado](../../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303 168_DropDownComboBox")

  Fondo

  `CommonControls.ComboBoxBackground`

  Borde

  `CommonControls.ComboBoxBorder`

  Text

  `CommonControls.ComboBoxText`

  Separador

  `CommonControls.ComboBoxSeparator`

  Glifo

  `CommonControls.ComboBoxGlyph`

  Fondo de glifo

  `CommonControls.ComboBoxGlyphBackground`

  **Deshabilitado**

  Componente

  Elemento

  Nombre del token: Category.color

  ![Quitar&#45;abajo&#47;deshabilitado del cuadro combinado](../../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303 169_DropDownComboBoxDisabled")

  Fondo

  `CommonControls.ComboBoxBackgroundDisabled`

  Borde

  `CommonControls.ComboBoxBorderDisabled`

  Text

  `CommonControls.ComboBoxTextDisabled`

  Separador

  `CommonControls.ComboBoxSeparatorDisabled`

  Glifo

  `CommonControls.ComboBoxGlyphDisabled`

  Fondo de glifo

  `CommonControls.ComboBoxGlyphBackgroundDisabled`

  **Al mantener el mouse**

  Componente

  Elemento

  Nombre del token: Category.color

  ![Quitar&#45;abajo&#47;cuadro combinado al mantener el mouse](../../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303 170_DropDownComboBoxHover")

  Fondo

  `CommonControls.ComboBoxBackgroundHover`

  Borde

  `CommonControls.ComboBoxBorderHover`

  Text

  `CommonControls.ComboBoxTextHover`

  Separador

  `CommonControls.ComboBoxSeparatorHover`

  Glifo

  `CommonControls.ComboBoxGlyphHover`

  Fondo de glifo

  `CommonControls.ComboBoxGlyphBackgroundHover`

  **Presionado**

  Componente

  Elemento

  Nombre del token: Category.color

  ![Quitar&#45;abajo&#47;presionada del cuadro combinado](../../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303 171_DropDownComboBoxPressed")

  Fondo

  `CommonControls.ComboBoxBackgroundPressed`

  Borde

  `CommonControls.ComboBoxBorderPressed`

  Text

  `CommonControls.ComboBoxTextPressed`

  Separador

  `CommonControls.ComboBoxSeparatorPressed`

  Glifo

  `CommonControls.ComboBoxGlyphPressed`

  Fondo de glifo

  `CommonControls.ComboBoxGlyphBackgroundPressed`

  **Centrado**

  Componente

  Elemento

  Nombre del token: Category.color

  ![Quitar&#45;abajo&#47;cuadro combinado enfocado](../../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303 172_DropDownComboBoxFocused")

  Fondo

  `CommonControls.ComboBoxBackgroundFocused`

  Borde

  `CommonControls.ComboBoxBorderFocused`

  Text

  `CommonControls.ComboBoxTextFocused`

  Separador

  `CommonControls.ComboBoxSeparatorFocused`

  Glifo

  `CommonControls.ComboBoxGlyphFocused`

  Fondo de glifo

  `CommonControls.ComboBoxGlyphBackgroundFocused`

  **Selección de entrada de texto**

  Componente

  Elemento

  Nombre del token: Category.color

  ![Quitar&#45;abajo&#47;entrada de texto de cuadro combinado](../../extensibility/ux-guidelines/media/0303-173-dropdowncomboboxtextinput.png "0303 173_DropDownComboBoxTextInput")

  Resaltar

  `CommonControls.ComboBoxTextInputSelection`

  **Presionado: vista de elemento de lista**

  ![Quitar&#45;abajo&#47;vista de lista del cuadro combinado](../../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303 174_DropDownComboBoxListView")

  Fondo

  `CommonControls.ComboBoxListBackground`

  `CommonControls.ComboBoxListBackgroundHover`

  `CommonControls.ComboBoxListItemBackgroundPressed`

  `CommonControls.ComboBoxListItemBackgroundFocused`

  Borde

  `CommonControls.ComboBoxListBorder`

  `CommonControls.ComboBoxListBorderHover`

  `CommonControls.ComboBoxListBorderPressed`

  `CommonControls.ComboBoxListBorderFocused`

  Texto del elemento

  `CommonControls.ComboBoxListItemText`

  `CommonControls.ComboBoxListItemTextHover`

  `CommonControls.ComboBoxListItemTextPressed`

  `CommonControls.ComboBoxListItemTextFocused`

  Sombra de fondo

  `CommonControls.ComboBoxListBackgroundShadow`

### <a name="tabular-data-grid-controls"></a>Controles de datos tabulares (cuadrícula)
 Los controles de datos tabulares, también conocidos como controles de cuadrícula, son controles comunes de Visual Studio que se pueden usar para presentar grandes cantidades de datos en varias columnas. Los controles estándar de datos tabulares están en varias ubicaciones de Visual Studio: la ventana de herramientas Lista de errores, los informes de IntelliTrace y la vista de montón de memoria, entre otros. Use siempre los controles de datos tabulares estándar que se proporcionan. En raras ocasiones, podría no tener acceso a los controles estándar de datos tabulares. En estos casos, use los siguientes nombres de token para asegurarse de que la interfaz de usuario sea coherente con otros controles de datos tabulares de Visual Studio.

 ![Datos tabulares &#40;control de cuadrícula&#41; límite](../../extensibility/ux-guidelines/media/0303-197-tabulardatagridcontrolredline.png "0303 197_TabularDataGridControlRedline")

 Use…
para controles tabulares o de cuadrícula.

 No use…
para cualquier interfaz de usuario que no sea un control tabular o de cuadrícula.

#### <a name="column-headers"></a>Encabezados de columna
 Los encabezados de columna constan de un fondo, un borde, el texto del título y un glifo opcional que suele usarse cuando se ordena una cuadrícula por esa columna.

 Estado

 Elemento

 Nombre del token: Category.color

 Valor predeterminado

 Fondo

 `Header.Default`

 Primer plano (texto)

 `Environment.CommandBarTextActive`

 Primer plano (glifo)

 `Header.Glyph`

 Borde

 `Header.SeparatorLine`

 Al mantener el puntero

 Fondo

 `Header.MouseOver`

 Primer plano (texto)

 `Environment.CommandBarTextHover`

 Primer plano (glifo)

 `Header.MouseOverGlyph`

 Borde

 `Header.SeparatorLine`

 Presionado

 Fondo

 `CommonControls.CheckBoxBackgroundPressed`

 Primer plano (texto)

 `CommonControls.CheckBoxBorderPressed`

 Primer plano (glifo)

 `CommonControls.CheckBoxTextPressed`

 Borde

 `CommonControls.CheckBoxGlyphPressed`

#### <a name="list-view-items"></a>Elementos de vista lista
 Los elementos de vista de lista constan de un fondo y el contenido. El contenido puede ser texto, un icono o ambos.

 Estado

 Elemento

 Nombre del token: Category.color

 Valor predeterminado

 Fondo

 Transparente

 Primer plano (texto)

 `Environment.CommandBarTextActive`

 Borde

 None

 Seleccionado (activo)

 Fondo

 `TreeView.SelectedItemActive`

 Primer plano (texto)

 `TreeView.SelectedItemActiveText`

 Borde

 None

 Seleccionado (inactivo)

 Fondo

 `TreeView.SelectedItemInactive`

 Primer plano (texto)

 `TreeView.SelectedItemInactiveText`

 Borde

 None

## <a name="manifest-designer"></a>Diseñador de manifiestos

El Diseñador de manifiestos se creó para que resulte más fácil editar el archivo de manifiesto en los proyectos de Windows 8 y Windows Phone 8. Aunque no hay ningún marco compartido disponible para su consumo, es conveniente que haga coincidir el diseño y los colores de las pestañas de navegación u orientación con la estructura general. Para obtener más información sobre el diseño, vea [Layout for Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).

![Límite de diseñador de manifiestos](../../extensibility/ux-guidelines/media/0303-175-manifestdesignerredline.png "0303 175_ManifestDesignerRedline")

Use…
- para los diseñadores que son similares al Diseñador de manifiestos.

- en lugar de usar los controles comunes de pestaña en la parte superior de un editor en el cuadro de documento.

No use…
- si tiene más de seis pestañas.

- para cualquier interfaz de usuario que no tenga la misma estructura que el Diseñador de manifiestos.

  Estado

  Componente

  Elemento

  Nombre del token: Category.color

  Predeterminado (seleccionado)

  Pestaña

  Fondo

  `ManifestDesigner.TabActive`

  Borde

  None

  Panel de descripción

  Fondo

  `ManifestDesigner.DescriptionPane`

  Página de contenido

  Fondo

  `ManifestDesigner.Background`

  Texto del asistente del cuadro de diálogo

  `ManifestDesigner.WatermarkText`

  Este nombre de token no coincide con su función.

  Sin seleccionar

  Tab

  Fondo

  `ManifestDesigner.Tab.Inactive`

  Al mantener el puntero

  Tab

  Fondo

  `ManifestDesigner.Tab.Mouseover`

## <a name="tagging"></a>Etiquetado
 Visual Studio admite el etiquetado, lo que permite al usuario declarar palabras clave de búsqueda con fines de seguimiento. Por ejemplo, los desarrolladores y los administradores de proyectos pueden usar Team Foundation Server (TFS) para etiquetar elementos de trabajo. Las tablas siguientes proporcionan nombres de colores para la etiqueta en sí y el glifo del "icono de cerrar" que aparecen en los estados Al desplazar el puntero y Seleccionado.

 ![Límite de etiquetado](../../extensibility/ux-guidelines/media/0303-176-taggingredline.png "0303 176_TaggingRedline")

 Use…
para la interfaz de usuario que admite el etiquetado.

 No use…
para cualquier otro tipo de interfaz de usuario.

### <a name="tag"></a>Etiqueta
 Componente

 Elemento

 Nombre del token: Category.color

 ![Tag](../../extensibility/ux-guidelines/media/0303-177-tag.png "0303-177_Tag")

 **Valor predeterminado**

 Fondo

 `Tag.Background`

 Primer plano (texto)

 `Tag.Background`

 ![Al mantener el mouse de etiqueta](../../extensibility/ux-guidelines/media/0303-178-taghover.png "0303 178_TagHover")

 **Al mantener el mouse**

 Fondo

 `Tag.HoverBackground`

 Primer plano (texto)

 `Tag.HoverBackgroundText`

 ![Etiqueta presionada](../../extensibility/ux-guidelines/media/0303-179-tagpressed.png "0303 179_TagPressed")

 **Presionado**

 Fondo

 `Tag.PressedBackground`

 Primer plano (texto)

 `Tag.PressedBackgroundText`

 ![Etiqueta seleccionada](../../extensibility/ux-guidelines/media/0303-180-tagselected.png "0303 180_TagSelected")

 **seleccionado**

 Fondo

 `Tag.SelectedBackground`

 Primer plano (texto)

 `Tag.SelectedBackgroundText`

### <a name="glyph-close-icon"></a>Glifo (icono de cerrar)
 **Valor predeterminado**

 Componente

 Elemento

 Nombre del token: Category.color

 ![Etiqueta &#40;glifo&#41;](../../extensibility/ux-guidelines/media/0303-181-tagglyph.png "0303 181_TagGlyph")

 **Predeterminado (valor predeterminado de etiqueta)**

 Fondo

 N/D

 Primer plano (glifo)

 `Tag.TagHoverGlyph`

 **Al mantener el mouse**

 Componente

 Elemento

 Nombre del token: Category.color

 ![Etiqueta &#40;glifo&#41; al mantener el mouse](../../extensibility/ux-guidelines/media/0303-182-tagglyphhover.png "0303 182_TagGlyphHover")

 **Al mantener el mouse (valor predeterminado de etiqueta)**

 Fondo

 `Tag.TagHoverGlyphHoverBackground`

 Primer plano (glifo)

 `Tag.TagHoverGlyphHover`

 Borde

 `Tag.TagHoverGlyphHoverBorder`

 **Presionado**

 Componente

 Elemento

 Nombre del token: Category.color

 ![Etiqueta &#40;glifo&#41; presiona](../../extensibility/ux-guidelines/media/0303-183-tagglyphpressed.png "0303 183_TagGlyphPressed")

 **Presionado (valor predeterminado de etiqueta)**

 Fondo

 `Tag.TagHoverGlyphPressedBackground`

 Primer plano (glifo)

 `Tag.TagHoverGlyphPressed`

 Borde

 `Tag.TagHoverGlyphPressedBorder`

 **Etiqueta seleccionada o glifo predeterminado**

 Componente

 Elemento

 Nombre del token: Category.color

 ![Etiqueta seleccionada](../../extensibility/ux-guidelines/media/0303-184-tagselected.png "0303 184_TagSelected")

 **Predeterminado (etiqueta seleccionada)**

 Fondo

 N/D

 Primer plano (glifo)

 `Tag.TagSelectedGlyph`

 **Etiqueta seleccionada o glifo al mantener el mouse**

 Componente

 Elemento

 Nombre del token: Category.color

 ![Etiqueta seleccionada al mantener el mouse](../../extensibility/ux-guidelines/media/0303-185-tagselectedhover.png "0303 185_TagSelectedHover")

 **Al mantener el mouse (etiqueta seleccionada)**

 Fondo

 `Tag.TagSelectedGlyphHoverBackground`

 Primer plano (glifo)

 `Tag.TagSelectedGlyphHover`

 Borde

 `Tag.TagSelectedGlyphHoverBorder`

 **Etiqueta seleccionada o glifo presionado**

 Componente

 Elemento

 Nombre del token: Category.color

 ![Etiqueta seleccionada presionada](../../extensibility/ux-guidelines/media/0303-186-tagselectedpressed.png "0303 186_TagSelectedPressed")

 **Presionado (etiqueta seleccionada)**

 Fondo

 `Tag.TagSelectedGlyphPressedBackground`

 Primer plano (glifo)

 `Tag.TagSelectedGlyphPressed`

 Borde

 `Tag.TagSelectedGlyphPressedBorder`

## <a name="shell"></a>Shell

### <a name="background"></a>Fondo

El fondo del entorno consta de dos niveles. El nivel inferior es un color sólido que cubre todo el IDE. El nivel superior se encuentra debajo del área de comandos y entre los canales de ocultación automática de la ventana de herramientas en los extremos izquierdo y derecho del IDE. A partir de Visual Studio 2013, los niveles de fondo superior e inferior se establecen en el mismo color en los temas claro y oscuro.

![Límite de fondo del shell](../../extensibility/ux-guidelines/media/0303-187-shellbackgroundredline.png "0303 187_ShellBackgroundRedline")

Use…
para los lugares que quiere hacer coincidir con el fondo del entorno de Visual Studio.

No use…
- como relleno de lugares que no son superficies de fondo.

- como fondo en el que quiere colocar elementos en primer plano.

  Componente

  Elemento

  Nombre del token: Category.color

  Nivel inferior

  Fondo

  `Environment.EnvironmentBackground`

  Componente

  Elemento

  Nombre del token: Category.color

  Nivel superior

  Fondo

  *Delimitadores de degradado establecido en el mismo valor de color en los temas de Visual Studio 2013 Light y oscuro.*

  `Environment.EnvironmentBackgroundGradientBegin`

  `Environment.EnvironmentBackgroundGradientEnd`

  `Environment.EnvironmentBackgroundGradientMiddle1`

  `Environment.EnvironmentBackgroundGradientMiddle2`

### <a name="command-shelf"></a>Área de comandos

Para los fondos del área de comandos se usan dos conjuntos de nombres de token: un conjunto para la ubicación donde se coloca la barra de menús y uno para la ubicación donde se colocan las barras de comandos. Un grupo individual de la barra de comandos tiene sus propios valores de color de fondo, que se describen con más detalle en la sección "Barra de comandos". El texto de la barra de menús y la barra de comandos se describe en las secciones de barra de menús y barra de comandos, respectivamente.

![Límite de shell de comandos](../../extensibility/ux-guidelines/media/0303-188-commandshelfredline.png "0303 188_CommandShelfRedline")

Use…
- para las áreas donde se colocan menús o barras de herramientas.

- con el fondo correcto /? primer plano.

No use…
para áreas que no sean similares a un área de comandos.

  Componente

  Elemento

  Nombre del token: Category.color

  Barra de menús

  Fondo

  *Delimitadores de degradado establecido en el mismo valor de color en los temas de Visual Studio 2013 Light y oscuro.*

  `Environment.CommandShelfHighlightGradientBegin`

  `Environment.CommandShelfHighlightGradientMiddle`

  `Environment.CommandShelfHighlightGradientEnd`

  Barra de comandos

  Fondo

  *Delimitadores de degradado establecido en el mismo valor de color en los temas de Visual Studio 2013 Light y oscuro.*

  `Environment.CommandShelfBackgroundGradientBegin`

  `Environment.CommandShelfBackgroundGradientMiddle`

  `Environment.CommandShelfBackgroundGradientEnd`

## <a name="toolbox"></a>Cuadro de herramientas
 El cuadro de herramientas es una de las ventanas de herramientas comunes que se usa con más frecuencia en Visual Studio. Es esencialmente un control de árbol con un tema y un estilo especial aplicado.

 ![Cuadro de herramientas de línea roja](../../extensibility/ux-guidelines/media/0303-189-toolboxredline.png "0303 189_ToolboxRedline")

 Use…
al diseñar una ventana de herramientas que desea que siempre sea coherente con el cuadro de herramientas del shell.

 No use…
para cualquier elemento que no sea similar a la interfaz de usuario del cuadro de herramientas o si no está seguro de si la interfaz de usuario tendrá problemas si cambian los colores del cuadro de herramientas del shell.

 **Valor predeterminado**

 Componente

 Elemento

 Nombre del token: Category.color

 ![Nodo primario de cuadro de herramientas](../../extensibility/ux-guidelines/media/0303-190-toolboxparentnode.png "0303 190_ToolboxParentNode")

 **Nodo primario**

 ![Nodo secundario de cuadro de herramientas](../../extensibility/ux-guidelines/media/0303-191-toolboxchildnode.png "0303 191_ToolboxChildNode")

 **Nodo secundario**

 Fondo

 `Environment.ToolboxContent`

 Encabezados

 `Environment.ToolWindowBackground`

 Elementos individuales o ventana completa si no hay controles disponibles

 Borde

 None

 Primer plano (glifo)

 `Environment.ToolboxContent`

 Primer plano (texto)

 `Environment.ToolboxContent`

 **Al mantener el mouse**

 Componente

 Elemento

 Nombre del token: Category.color

 ![Nodo secundario de cuadro de herramientas al mantener el mouse](../../extensibility/ux-guidelines/media/0303-192-toolboxchildnodehover.png "0303 192_ToolboxChildNodeHover")

 **Mantener el mouse del cuadro de herramientas en el nodo secundario**

 Fondo

 `Environment.ToolboxContentMouseOver`

 Solo elementos individuales

 Borde

 None

 Primer plano (texto)

 `Environment.ToolboxContentMouseOver`

 Solo elementos individuales

 **seleccionado**

 Componente

 Elemento

 Nombre del token: Category.color

 ![Nodo primario de cuadro de herramientas enfocado](../../extensibility/ux-guidelines/media/0303-193-toolboxparentnodefocused.png "0303 193_ToolboxParentNodeFocused")

 **Nodo primario con foco**

 ![Nodo secundario de cuadro de herramientas enfocado](../../extensibility/ux-guidelines/media/0303-194-toolboxchildnodefocused.png "0303 194_ToolboxChildNodeFocused")

 **Nodo secundario con foco**

 Fondo

 `TreeView.SelectedItemActive`

 De categoría [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView)

 Borde

 `TreeView.FocusVisualBorder`

 De categoría [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView)

 Primer plano (glifo)

 `TreeView.SelectedItemActive`

 De categoría [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView)

 Primer plano (texto)

 `TreeView.SelectedItemActive`

 De categoría [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView)

 ![Nodo primario de cuadro de herramientas no enfocado](../../extensibility/ux-guidelines/media/0303-195-toolboxparentnodeunfocused.png "0303 195_ToolboxParentNodeUnfocused")

 **Nodo primario sin foco**

 ![Nodo secundario de cuadro de herramientas no enfocado](../../extensibility/ux-guidelines/media/0303-196-toolboxchildnodeunfocused.png "0303 196_ToolboxChildNodeUnfocused")

 **Nodo secundario sin foco**

 Fondo

 `TreeView.SelectedItemInactive`

 De categoría [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView)

 Borde

 None

 Primer plano (glifo)

 `TreeView.SelectedItemInactive`

 De categoría [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView)

 Primer plano (texto)

 `TreeView.SelectedItemInactive`

 De categoría [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView)
