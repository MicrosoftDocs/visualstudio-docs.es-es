---
title: Colores compartidos | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: 9d3186f3-07d2-441f-b33e-435e95d8a0b8
caps.latest.revision: 11
ms.author: brgeorge
ms.openlocfilehash: 76c04680b63eb362e02fdf26d817660d671b3b52
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85548361"
---
# <a name="shared-colors"></a>Colores compartidos
Inserte aquí la introducción.  
  
## <a name="shared-colors"></a>Colores compartidos  
 Si diseña una interfaz de usuario que usa elementos comunes de shell de Visual Studio, o si quiere que el elemento de la interfaz sea coherente con características similares, use los nombres de token existentes de los archivos de definición de paquete para elegir y asignar colores. Esto garantiza que la interfaz de usuario mantenga la coherencia con el entorno general de Visual Studio y que se actualice automáticamente cuando se agreguen o actualicen temas.  
  
 En este artículo se describen los elementos de interfaz de usuario comunes y los nombres de token que estos usan y a los que se puede hacer referencia al crear una interfaz de usuario similar. Para obtener información específica sobre cómo tener acceso a estos tokens de color, vea [The VSColor Service](../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).  
  
 Asegúrese de usar correctamente los nombres de token:  
  
- **Usar nombres de token basados en función, no en el color en sí.** Los colores comunes compartidos están asociados a elementos específicos de la interfaz y solo están destinados para características iguales o similares. Por ejemplo, no vuelva a usar el color de un cuadro combinado presionado para una animación de progreso de giro solo porque le gusta el color. Las funciones del cuadro combinado y de la animación son diferentes, y si se cambia el color asociado con el cuadro combinado, ya no puede ser un color adecuado para el elemento de animación. Un uso coherente del color ayuda a orientar a los usuarios y evitar confusiones.  
  
- **Usar colores de fondo y de texto en la combinación correcta.** Los colores de fondo destinados para usarse con texto tendrán un color de texto asociado. No use colores de texto que no sean los que se especifican para el fondo. Si no hay un color de texto asociado, no use ese color de fondo para cualquier superficie en la que tiene pensado mostrar texto. Otras combinaciones de colores de fondo y de texto pueden dar lugar a una interfaz ilegible.  
  
- **Usar colores de control adecuados para su ubicación.** En determinados estados, algunos controles de Visual Studio no tienen colores de borde y de fondo independientes. En su lugar, toman los colores de las superficies que están detrás de ellos. Procure usar siempre los nombres de token que sean adecuados para la ubicación donde coloca el control.  
  
> [!IMPORTANT]
> No use los tokens que se encuentran en las categorías "Página de inicio" o "Cider".  
  
### <a name="command-structures"></a>Estructuras de comandos  
  
#### <a name="menus"></a><a name="BKMK_CommandMenus"></a>Restringi  
 Los menús pueden aparecer en varios lugares de Visual Studio 2013: en la barra de menús principal, insertados en ventanas de documento o ventanas de herramientas, o al hacer clic con el botón derecho en diversas ubicaciones del IDE. Las implementaciones de menús asociados con otros elementos de la interfaz de usuario se describen en la sección del elemento respectivo. Se debe usar siempre la implementación de menús estándar proporcionada por el entorno de Visual Studio. Sin embargo, en algunas ocasiones podría no tener acceso a los menús estándar de Visual Studio. En estos casos, use los siguientes nombres de token para asegurarse de que la interfaz de usuario sea coherente con otros menús de Visual Studio.  
  
 ![Revisión de menús](../extensibility/ux-guidelines/media/0303-000-menuredline.png "0303-000_MenuRedline")  
  
Use…  
- siempre que necesite crear un menú personalizado.  
  
- cuando haya un nuevo componente de interfaz de usuario que quiera hacer coincidir con los menús de Visual Studio.  
  
No use…  
el color de fondo por sí solo. Use siempre la combinación de primer plano y fondo tal como se especifica.  
  
##### <a name="menu-title"></a>Título de menú  
 Los títulos de menú constan de un fondo, un borde y el texto del título, así como un glifo opcional, que suele usarse cuando el menú se encuentra en una barra de comandos.  
  
 ![Revisión de título de menú](../extensibility/ux-guidelines/media/0303-001-menutitleredline.png "0303-001_MenuTitleRedline")  
  
Use…  
cada vez que cree un título de menú personalizado.  
  
No use…  
- para cualquier elemento que no desea que siempre coincida con el título de menú.  
  
- en cualquier combinación de primer plano y fondo distinta de la especificada.  
  
  **Valor predeterminado**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Título de menú predeterminado](../extensibility/ux-guidelines/media/0303-002-menutitledefault.png "0303-002_MenuTitleDefault")<br /><br /> **Título de menú**|Fondo|None|  
|![Título de menú predeterminado](../extensibility/ux-guidelines/media/0303-002-menutitledefault.png "0303-002_MenuTitleDefault")<br /><br /> **Título de menú**|Primer plano (texto)|`Environment.CommandBarTextActive`|  
|![Título de menú con glifo predeterminado](../extensibility/ux-guidelines/media/0303-003-menutitlewithglyphdefault.png "0303-003_MenuTitleWithGlyphDefault")<br /><br /> **Título de menú con glifo**|Primer plano (glifo)|`Environment.CommandBarMenuGlyph`|  
|![Título de menú con glifo predeterminado](../extensibility/ux-guidelines/media/0303-003-menutitlewithglyphdefault.png "0303-003_MenuTitleWithGlyphDefault")<br /><br /> **Título de menú con glifo**|Borde|None|  
  
 **Al mantener el puntero**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Título de menú al mantener el mouse](../extensibility/ux-guidelines/media/0303-004-menutitlehover.png "0303-004_MenuTitleHover")<br /><br /> **Título de menú**|Fondo|`Environment.CommandBarMouseOverBackgroundBegin`<br /><br /> Aunque no se usan en la interfaz de usuario moderna con temas, hay delimitadores de degradado y valores para este fondo.|  
|![Título de menú al mantener el mouse](../extensibility/ux-guidelines/media/0303-004-menutitlehover.png "0303-004_MenuTitleHover")<br /><br /> **Título de menú**|Primer plano (texto)|`Environment.CommandBarTextHover`|  
|![Título de menú con glifo al mantener el mouse](../extensibility/ux-guidelines/media/0303-005-menutitlewithglyphhover.png "0303-005_MenuTitleWithGlyphHover")<br /><br /> **Título de menú con glifo**|Primer plano (glifo)|`Environment.CommandBarMenuMouseOverGlyph`|  
|![Título de menú con glifo al mantener el mouse](../extensibility/ux-guidelines/media/0303-005-menutitlewithglyphhover.png "0303-005_MenuTitleWithGlyphHover")<br /><br /> **Título de menú con glifo**|Borde|`Environment.CommandBarBorder`|  
  
 **Pressed**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Título de menú presionado](../extensibility/ux-guidelines/media/0303-006-menutitlepressed.png "0303-006_MenuTitlePressed")<br /><br /> **Título de menú**|Fondo|`Environment.CommandBarMenuBackgroundGradientBegin`<br /><br /> Aunque no se usan en la interfaz de usuario moderna con temas, hay delimitadores de degradado y valores para este fondo.|  
|![Título de menú presionado](../extensibility/ux-guidelines/media/0303-006-menutitlepressed.png "0303-006_MenuTitlePressed")<br /><br /> **Título de menú**|Primer plano (texto)|`Environment.CommandBarTextActive`|  
|![Título de menú con glifo presionado](../extensibility/ux-guidelines/media/0303-007-menutitlewithglyphpressed.png "0303-007_MenuTitleWithGlyphPressed")<br /><br /> **Título de menú con glifo**|Primer plano (glifo)|`Environment.CommandBarMenuMouseDownGlyph`|  
|![Título de menú con glifo presionado](../extensibility/ux-guidelines/media/0303-007-menutitlewithglyphpressed.png "0303-007_MenuTitleWithGlyphPressed")<br /><br /> **Título de menú con glifo**|Borde|`Environment.CommandBarMenuBorder`<br /><br /> Solo partes izquierda, superior y derecha.|  
  
 **Deshabilitada**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Título de menú con glifo deshabilitado](../extensibility/ux-guidelines/media/0303-008-menutitlewithglyphdisabled.png "0303-008_MenuTitleWithGlyphDisabled")<br /><br /> **Título de menú con glifo**|Fondo|None|  
|![Título de menú con glifo deshabilitado](../extensibility/ux-guidelines/media/0303-008-menutitlewithglyphdisabled.png "0303-008_MenuTitleWithGlyphDisabled")<br /><br /> **Título de menú con glifo**|Primer plano (texto)|`Environment.CommandBarTextInactive`|  
|![Título de menú con glifo deshabilitado](../extensibility/ux-guidelines/media/0303-008-menutitlewithglyphdisabled.png "0303-008_MenuTitleWithGlyphDisabled")<br /><br /> **Título de menú con glifo**|Primer plano (glifo)|`Environment.CommandBarTextInactive`|  
|![Título de menú con glifo deshabilitado](../extensibility/ux-guidelines/media/0303-008-menutitlewithglyphdisabled.png "0303-008_MenuTitleWithGlyphDisabled")<br /><br /> **Título de menú con glifo**|Borde|None|  
  
##### <a name="menu"></a>Menú  
 Un elemento de menú individual se compone del texto del menú y un icono opcional, una casilla o un glifo de submenú. Su color de fondo y de texto cambian al mantener el puntero. Este token de color es un par de primer plano y fondo.  
  
 ![Revisión de elementos de menú](../extensibility/ux-guidelines/media/0303-009-menuitemredline.png "0303-009_MenuItemRedline")  
  
 Use…  
 para cualquier lista desplegable que se inicia desde una barra de menús o una barra de comandos.  
  
No use…  
- para cualquier lista desplegable que se muestra en otro contexto.  

- en cualquier combinación de primer plano y fondo distinta de la especificada.  
  
  **Valor predeterminado**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Menú predeterminado](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303-010_MenuDefault")<br /><br /> **Menú**|Fondo|`Environment.CommandBarMenuBackgroundGradientBegin`<br /><br /> Aunque no se usan en la interfaz de usuario moderna con temas, hay delimitadores de degradado y valores para este fondo.|  
|![Menú predeterminado](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303-010_MenuDefault")<br /><br /> **Menú**|Primer plano (texto)|`Environment.CommandBarTextActive`|  
|![Menú predeterminado](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303-010_MenuDefault")<br /><br /> **Menú**|Primer plano (glifo de submenú)|`Environment.CommandBarMenuSubmenuGlyph`|  
|![Menú predeterminado](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303-010_MenuDefault")<br /><br /> **Menú**|Borde|`Environment.CommandBarMenuBorder`|  
|![Menú predeterminado](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303-010_MenuDefault")<br /><br /> **Menú**|Fondo de canal de iconos|`Environment.CommandBarMenuIconBackground`|  
|![Menú predeterminado](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303-010_MenuDefault")<br /><br /> **Menú**|Separador|`Environment.CommandBarMenuSeparator`|  
|![Menú predeterminado](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303-010_MenuDefault")<br /><br /> **Menú**|Shadow|`Environment.DropShadowBackground`|  
|![Menú activado](../extensibility/ux-guidelines/media/0303-011-menuchecked.png "0303-011_MenuChecked")<br /><br /> **Incorpora**|Marca de verificación|`Environment.CommandBarCheckBox`|  
|![Menú activado](../extensibility/ux-guidelines/media/0303-011-menuchecked.png "0303-011_MenuChecked")<br /><br /> **Incorpora**|Fondo de marca de verificación|`Environment.CommandBarSelectedIcon`|  
|![Menú seleccionado](../extensibility/ux-guidelines/media/0303-012-menuselected.png "0303-012_MenuSelected")<br /><br /> **Selected**|Fondo de icono|`Environment.CommandBarSelected`|  
|![Menú seleccionado](../extensibility/ux-guidelines/media/0303-012-menuselected.png "0303-012_MenuSelected")<br /><br /> **Selected**|Borde de icono|`Environment.CommandBarSelectedBorder`|  
  
 **Al mantener el puntero**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Menú al mantener el mouse](../extensibility/ux-guidelines/media/0303-013-menuhover.png "0303-013_MenuHover")<br /><br /> **Elemento de menú**|Fondo|`Environment.CommandBarMenuItemMouseOver`|  
|![Menú al mantener el mouse](../extensibility/ux-guidelines/media/0303-013-menuhover.png "0303-013_MenuHover")<br /><br /> **Elemento de menú**|Primer plano (texto)|`Environment.CommandBarMenuItemMouseOver`|  
|![Menú al mantener el mouse](../extensibility/ux-guidelines/media/0303-013-menuhover.png "0303-013_MenuHover")<br /><br /> **Elemento de menú**|Primer plano (glifo de submenú)|`Environment.CommandBarMenuMouseOverSubmenuGlyph`|  
|![Menú activado al mantener el mouse](../extensibility/ux-guidelines/media/0303-014-menuhoverchecked.png "0303-014_MenuHoverChecked")<br /><br /> **Incorpora**|Marca de verificación|`Environment.CommandBarCheckBoxMouseOver`|  
|![Menú activado al mantener el mouse](../extensibility/ux-guidelines/media/0303-014-menuhoverchecked.png "0303-014_MenuHoverChecked")<br /><br /> **Incorpora**|Fondo de marca de verificación|`Environment.CommandBarHoverOverSelectedIcon`|  
|![Menú seleccionado al mantener el mouse](../extensibility/ux-guidelines/media/0303-015-menuhoverselected.png "0303-015_MenuHoverSelected")<br /><br /> **Selected**|Fondo de icono|`Environment.CommandBarHoverOverSelected`|  
|![Menú seleccionado al mantener el mouse](../extensibility/ux-guidelines/media/0303-015-menuhoverselected.png "0303-015_MenuHoverSelected")<br /><br /> **Selected**|Borde de icono|`Environment.CommandBarHoverOverSelectedIconBorder`|  
  
 **Deshabilitada**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Menú deshabilitado](../extensibility/ux-guidelines/media/0303-016-menudisabled.png "0303-016_MenuDisabled")<br /><br /> Elemento de menú|Primer plano (texto)|`Environment.CommandBarTextInactive`|  
|![Menú deshabilitado](../extensibility/ux-guidelines/media/0303-016-menudisabled.png "0303-016_MenuDisabled")<br /><br /> Elemento de menú|Primer plano (glifo de submenú)|`Environment.CommandBarMenuSubmenuGlyph`|  
|![Menú deshabilitado activado](../extensibility/ux-guidelines/media/0303-017-menudisabledchecked.png "0303-017_MenuDisabledChecked")<br /><br /> Activado|Marca de verificación|`Environment.CommandBarCheckBoxDisabled`|  
|![Menú deshabilitado activado](../extensibility/ux-guidelines/media/0303-017-menudisabledchecked.png "0303-017_MenuDisabledChecked")<br /><br /> Activado|Fondo de marca de verificación|`Environment.CommandBarSelectedIconDisabled`|  
  
#### <a name="command-bar"></a>Barra de comandos  
 La barra de comandos puede aparecer en varios lugares del IDE de Visual Studio, sobre todo en el área de comandos e insertados en ventanas de herramientas o documentos.  
  
 En general, use siempre la implementación de menús estándar proporcionada por el entorno de Visual Studio. El uso del mecanismo estándar, garantiza que todos los detalles visuales se mostrarán correctamente y que los elementos interactivos se comportarán de forma coherente con otros controles de barra de comandos de Visual Studio. Sin embargo, si necesita crear su propia barra de comandos, asegúrese de diseñarla correctamente mediante los siguientes nombres de token.  
  
 ![Límite de barra de comandos](../extensibility/ux-guidelines/media/0303-018-commandbarredline.png "0303-018_CommandBarRedline")  
  
 ![Límite de botón de desbordamiento](../extensibility/ux-guidelines/media/0303-019-overflowbuttonredline.png "0303-019_OverflowButtonRedline")  
  
 Use…  
 en lugares donde se necesita una barra de comandos insertada pero no se puede usar la implementación estándar de barra de comandos de Visual Studio.  
  
No use…  
- para elementos de la interfaz de usuario que no sean similares a una barra de comandos.  

- para los componentes de barra de comandos distintos de aquellos para los que se especifican nombres de los token.  
  
##### <a name="command-bar-group"></a>Grupo de la barra de comandos  
 Un grupo de la barra de comandos se compone de un conjunto relacionado de controles de barra de comandos y puede incluir cualquier número de botones, botones de expansión, menús desplegables, cuadros combinados o menús. Los colores de dichos controles se regulan mediante nombres de token independientes y se describen individualmente en esta guía. Se usa una línea divisoria para dividir un grupo de la barra de comandos en subgrupos relacionados.  
  
 ![Límite de grupo de la barra de comandos](../extensibility/ux-guidelines/media/0303-020-commandbargroupredline.png "0303-020_CommandBarGroupRedline")  
  
 Use…  
 en lugares donde se necesita una barra de comandos insertada pero no se puede usar la implementación estándar de barra de comandos de Visual Studio.  
  
No use…  
- para elementos de la interfaz de usuario que no sean similares a una barra de comandos.  

- para los componentes de barra de comandos distintos de aquellos para los que se especifican nombres de los token.  
  
  **Predeterminado** (ningún otro Estado)  
  
|Elemento|Nombre del token: Category.color|  
|-------------|--------------------------------|  
|Fondo|`Environment.CommandBarGradientBegin`<br /><br /> Aunque no se usan en la interfaz de usuario moderna con temas, hay delimitadores de degradado y valores para este fondo.|  
|Borde|`Environment.CommandBarToolBarBorder`|  
|Controlador de arrastre|`Environment.CommandBarDragHandle`|  
|Separador|`Environment.CommandBarToolBarSeparator`<br /><br /> `Environment.CommandBarToolBarSeparatorHighlight`|  
  
##### <a name="command-icons"></a>Iconos de comando  
 ![Límite de icono de comando](../extensibility/ux-guidelines/media/0303-021-commandiconredline1.png "0303-021_CommandIconRedline1")  
  
 ![Límite de icono de comando](../extensibility/ux-guidelines/media/0303-022-commandiconredline2.png "0303-022_CommandIconRedline2")  
  
 Use…  
 para los botones que se colocarán en una barra de comandos.  
  
No use…  
- para controles que tienen sus propios nombres de token.  

- en cualquier combinación de primer plano y fondo distinta de la especificada.  
  
  **Valor predeterminado**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Icono de comando predeterminado](../extensibility/ux-guidelines/media/0303-023-commandicondefault.png "0303-023_CommandIconDefault")<br /><br /> **Valor predeterminado**|Fondo|N/D (se hereda del fondo de la barra de comandos)|  
|![Icono de comando predeterminado](../extensibility/ux-guidelines/media/0303-023-commandicondefault.png "0303-023_CommandIconDefault")<br /><br /> **Valor predeterminado**|Primer plano (texto)|`Environment.CommandBarTextActive`|  
|![Icono de comando predeterminado](../extensibility/ux-guidelines/media/0303-023-commandicondefault.png "0303-023_CommandIconDefault")<br /><br /> **Valor predeterminado**|Borde|N/D|  
|![Icono de comando predeterminado seleccionado](../extensibility/ux-guidelines/media/0303-024-commandicondefaultselected.png "0303-024_CommandIconDefaultSelected")<br /><br /> **Selected**|Fondo|`Environment.CommandBarSelected`|  
|![Icono de comando predeterminado seleccionado](../extensibility/ux-guidelines/media/0303-024-commandicondefaultselected.png "0303-024_CommandIconDefaultSelected")<br /><br /> **Selected**|Primer plano (texto)|`Environment.CommandBarTextSelected`|  
|![Icono de comando predeterminado seleccionado](../extensibility/ux-guidelines/media/0303-024-commandicondefaultselected.png "0303-024_CommandIconDefaultSelected")<br /><br /> **Selected**|Borde|`Environment.CommandBarSelectedBorder`|  
  
 **Al mantener el puntero y teclado con foco**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Icono de comandos al mantener el mouse](../extensibility/ux-guidelines/media/0303-025-commandiconhover.png "0303-025_CommandIconHover")<br /><br /> **Estándar al mantener el puntero**|Fondo|`Environment.CommandBarMouseOverBackgroundBegin`<br /><br /> Aunque no se usan en la interfaz de usuario moderna con temas, hay delimitadores de degradado y valores para este fondo.|  
|![Icono de comandos al mantener el mouse](../extensibility/ux-guidelines/media/0303-025-commandiconhover.png "0303-025_CommandIconHover")<br /><br /> **Estándar al mantener el puntero**|Primer plano (texto)|`Environment.CommandBarTextHover`|  
|![Icono de comandos al mantener el mouse](../extensibility/ux-guidelines/media/0303-025-commandiconhover.png "0303-025_CommandIconHover")<br /><br /> **Estándar al mantener el puntero**|Borde|`Environment.CommandBarBorder`|  
|![Icono de comandos al mantener el mouse seleccionado](../extensibility/ux-guidelines/media/0303-026-commandiconhoverselected.png "0303-026_CommandIconHoverSelected")<br /><br /> **Seleccionado al mantener el puntero**|Fondo|`Environment.CommandBarHoverOverSelected`|  
|![Icono de comandos al mantener el mouse seleccionado](../extensibility/ux-guidelines/media/0303-026-commandiconhoverselected.png "0303-026_CommandIconHoverSelected")<br /><br /> **Seleccionado al mantener el puntero**|Primer plano (texto)|`Environment.CommandBarTextHoverOverSelected`|  
|![Icono de comandos al mantener el mouse seleccionado](../extensibility/ux-guidelines/media/0303-026-commandiconhoverselected.png "0303-026_CommandIconHoverSelected")<br /><br /> **Seleccionado al mantener el puntero**|Borde|`Environment.CommandBarHoverOverSelectedIconBorder`|  
  
 **Pressed**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Icono de comando presionado](../extensibility/ux-guidelines/media/0303-027-commandiconpressed.png "0303-027_CommandIconPressed")<br /><br /> **Icono de comando presionado**|Fondo|`Environment.CommandBarMouseDownBackgroundBegin`<br /><br /> Aunque no se usan en la interfaz de usuario moderna con temas, hay delimitadores de degradado y valores para este fondo.|  
|![Icono de comando presionado](../extensibility/ux-guidelines/media/0303-027-commandiconpressed.png "0303-027_CommandIconPressed")<br /><br /> **Icono de comando presionado**|Primer plano (texto)|`Environment.CommandBarTextMouseDown`|  
|![Icono de comando presionado](../extensibility/ux-guidelines/media/0303-027-commandiconpressed.png "0303-027_CommandIconPressed")<br /><br /> **Icono de comando presionado**|Borde|`Environment.CommandBarBorder`|  
  
 **Deshabilitada**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Icono de comando deshabilitado](../extensibility/ux-guidelines/media/0303-028-commandicondisabled.png "0303-028_CommandIconDisabled")<br /><br /> **Icono de comando deshabilitado**|Fondo|N/D (se hereda del fondo de la barra de comandos)|  
|![Icono de comando deshabilitado](../extensibility/ux-guidelines/media/0303-028-commandicondisabled.png "0303-028_CommandIconDisabled")<br /><br /> **Icono de comando deshabilitado**|Primer plano (texto)|`Environment.CommandBarTextInactive`|  
|![Icono de comando deshabilitado](../extensibility/ux-guidelines/media/0303-028-commandicondisabled.png "0303-028_CommandIconDisabled")<br /><br /> **Icono de comando deshabilitado**|Borde|N/D|  
  
##### <a name="combo-box"></a><a name="BKMK_CommandComboBox"></a>Cuadro combinado  
  
> [!IMPORTANT]
> Los cuadros combinados son similares a las listas desplegables, pero incluyen un área de texto editable. Si la lista desplegable no incluye un área de texto editable, use los tokens de color que se encuentran en [Drop-down](../misc/shared-colors.md#BKMK_CommandDropDown).  
  
 ![Límite de cuadro combinado](../extensibility/ux-guidelines/media/0303-029-comboboxredline.png "0303-029_ComboBoxRedline")  
  
Use…  
- al crear cuadros combinados personalizados.  

- al crear un control de barra de comandos que sea similar a un cuadro combinado.  

No use…  
- para ningún elemento que no desea que siempre coincida con la interfaz de usuario de la barra de comandos.  

- si tiene acceso a un cuadro combinado con estilo.  
  
  **Valor predeterminado**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Campo de entrada de cuadro combinado](../extensibility/ux-guidelines/media/0303-030-comboboxinputfield.png "0303-030_ComboBoxInputField")<br /><br /> **Campo de entrada**|Fondo|`Environment.ComboBoxBackground`|  
|![Campo de entrada de cuadro combinado](../extensibility/ux-guidelines/media/0303-030-comboboxinputfield.png "0303-030_ComboBoxInputField")<br /><br /> **Campo de entrada**|Primer plano (texto)|`Environment.ComboBoxText`|  
|![Campo de entrada de cuadro combinado](../extensibility/ux-guidelines/media/0303-030-comboboxinputfield.png "0303-030_ComboBoxInputField")<br /><br /> **Campo de entrada**|Borde|`Environment.ComboBoxBorder`|  
|![Campo de entrada de cuadro combinado](../extensibility/ux-guidelines/media/0303-030-comboboxinputfield.png "0303-030_ComboBoxInputField")<br /><br /> **Campo de entrada**|Separador|Sin separador|  
|![Botón desplegable de&#45;de cuadro combinado](../extensibility/ux-guidelines/media/0303-031-comboboxdropdownbutton.png "0303-031_ComboBoxDropdownButton")<br /><br /> **Botón desplegable**|Fondo|N/D (se hereda)|  
|![Botón desplegable de&#45;de cuadro combinado](../extensibility/ux-guidelines/media/0303-031-comboboxdropdownbutton.png "0303-031_ComboBoxDropdownButton")<br /><br /> **Botón desplegable**|Primer plano (glifo)|`Environment.ComboBoxGlyph`|  
|![Cuadro combinado&#47;lista desplegable&#45;](../extensibility/ux-guidelines/media/0303-032-comboboxdropdownlist.png "0303-032_ComboBoxDropdownList")<br /><br /> **Lista desplegable**|Fondo|`Environment.ComboBoxPopupBackgroundBegin`<br /><br /> Aunque no se usan en la interfaz de usuario moderna con temas, hay delimitadores de degradado y valores para este fondo.|  
|![Cuadro combinado&#47;lista desplegable&#45;](../extensibility/ux-guidelines/media/0303-032-comboboxdropdownlist.png "0303-032_ComboBoxDropdownList")<br /><br /> **Lista desplegable**|Primer plano (texto)|`Environment.ComboBoxItemText`|  
|![Cuadro combinado&#47;lista desplegable&#45;](../extensibility/ux-guidelines/media/0303-032-comboboxdropdownlist.png "0303-032_ComboBoxDropdownList")<br /><br /> **Lista desplegable**|Borde|`Environment.ComboBoxPopupBorder`|  
  
 **Al mantener el puntero**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Campo de entrada de cuadro combinado al mantener el mouse](../extensibility/ux-guidelines/media/0303-033-comboboxinputfieldhover.png "0303-033_ComboBoxInputFieldHover")<br /><br /> **Campo de entrada**|Fondo|`Environment.ComboBoxMouseOverBackgroundBegin`<br /><br /> Aunque no se usan en la interfaz de usuario moderna con temas, hay delimitadores de degradado y valores para este fondo.|  
|![Campo de entrada de cuadro combinado al mantener el mouse](../extensibility/ux-guidelines/media/0303-033-comboboxinputfieldhover.png "0303-033_ComboBoxInputFieldHover")<br /><br /> **Campo de entrada**|Primer plano (texto)|`Environment.ComboBoxMouseOverText`|  
|![Campo de entrada de cuadro combinado al mantener el mouse](../extensibility/ux-guidelines/media/0303-033-comboboxinputfieldhover.png "0303-033_ComboBoxInputFieldHover")<br /><br /> **Campo de entrada**|Borde|`Environment.ComboBoxMouseOverBorder`|  
|![Campo de entrada de cuadro combinado al mantener el mouse](../extensibility/ux-guidelines/media/0303-033-comboboxinputfieldhover.png "0303-033_ComboBoxInputFieldHover")<br /><br /> **Campo de entrada**|Separador|`Environment.ComboBoxMouseOverSeparator`|  
|![Cuadro combinado&#47;soltar&#45;botón abajo al mantener el mouse](../extensibility/ux-guidelines/media/0303-034-comboboxdropdownbuttonhover.png "0303-034_ComboBoxDropdownButtonHover")<br /><br /> **Botón desplegable**|Fondo|`Environment.ComboBoxButtonMouseOverBackground`|  
|![Cuadro combinado&#47;soltar&#45;botón abajo al mantener el mouse](../extensibility/ux-guidelines/media/0303-034-comboboxdropdownbuttonhover.png "0303-034_ComboBoxDropdownButtonHover")<br /><br /> **Botón desplegable**|Primer plano (glifo)|`Environment.ComboBoxMouseOverGlyph`|  
|![Cuadro combinado&#47;quitar&#45;lista desplegable al mantener el mouse](../extensibility/ux-guidelines/media/0303-035-comboboxdropdownlisthover.png "0303-035_ComboBoxDropdownListHover")<br /><br /> **Lista desplegable**|Fondo (elemento de menú)|`Environment.ComboBoxItemMouseOverBackground`|  
|![Cuadro combinado&#47;quitar&#45;lista desplegable al mantener el mouse](../extensibility/ux-guidelines/media/0303-035-comboboxdropdownlisthover.png "0303-035_ComboBoxDropdownListHover")<br /><br /> **Lista desplegable**|Primer plano (texto)|`Environment.ComboBoxItemMouseOverText`|  
|![Cuadro combinado&#47;quitar&#45;lista desplegable al mantener el mouse](../extensibility/ux-guidelines/media/0303-035-comboboxdropdownlisthover.png "0303-035_ComboBoxDropdownListHover")<br /><br /> **Lista desplegable**|Borde (elemento de menú)|`Environment.ComboBoxItemMouseOverBorder`|  
  
 **Focused**  
  
|Componente|Elemento|Nombre del token: Color.category|  
|---------------|-------------|--------------------------------|  
|![Campo de entrada de cuadro combinado enfocado](../extensibility/ux-guidelines/media/0303-036-comboboxinputfieldfocused.png "0303-036_ComboBoxInputFieldFocused")<br /><br /> **Campo de entrada**|Fondo|`Environment.ComboBoxFocusedBackground`|  
|![Campo de entrada de cuadro combinado enfocado](../extensibility/ux-guidelines/media/0303-036-comboboxinputfieldfocused.png "0303-036_ComboBoxInputFieldFocused")<br /><br /> **Campo de entrada**|Primer plano (texto)|`Environment.ComboBoxFocusedText`|  
|![Campo de entrada de cuadro combinado enfocado](../extensibility/ux-guidelines/media/0303-036-comboboxinputfieldfocused.png "0303-036_ComboBoxInputFieldFocused")<br /><br /> **Campo de entrada**|Borde|`Environment.ComboBoxFocusedBorder`|  
|![Campo de entrada de cuadro combinado enfocado](../extensibility/ux-guidelines/media/0303-036-comboboxinputfieldfocused.png "0303-036_ComboBoxInputFieldFocused")<br /><br /> **Campo de entrada**|Separador|`Environment.ComboBoxFocusedButtonSeparator`|  
|![Cuadro combinado&#47;colocar&#45;botón abajo centrado](../extensibility/ux-guidelines/media/0303-037-comboboxdropdownbuttonfocused.png "0303-037_ComboBoxDropdownButtonFocused")<br /><br /> **Botón desplegable**|Fondo|`Environment.ComboBoxFocusedButtonBackground`|  
|![Cuadro combinado&#47;colocar&#45;botón abajo centrado](../extensibility/ux-guidelines/media/0303-037-comboboxdropdownbuttonfocused.png "0303-037_ComboBoxDropdownButtonFocused")<br /><br /> **Botón desplegable**|Primer plano (glifo)|`Environment.ComboBoxFocusedGlyph`|  
  
 **Pressed**  
  
|Componente|Elemento|Nombre del token: Color.category|  
|---------------|-------------|--------------------------------|  
|![Campo entrada de cuadro combinado presionado](../extensibility/ux-guidelines/media/0303-038-comboboxinputfieldpressed.png "0303-038_ComboBoxInputFieldPressed")<br /><br /> **Campo de entrada**|Fondo|`Environment.ComboBoxMouseDownBackground`|  
|![Campo entrada de cuadro combinado presionado](../extensibility/ux-guidelines/media/0303-038-comboboxinputfieldpressed.png "0303-038_ComboBoxInputFieldPressed")<br /><br /> **Campo de entrada**|Primer plano (texto)|`Environment.ComboBoxMouseDownText`|  
|![Campo entrada de cuadro combinado presionado](../extensibility/ux-guidelines/media/0303-038-comboboxinputfieldpressed.png "0303-038_ComboBoxInputFieldPressed")<br /><br /> **Campo de entrada**|Borde|`Environment.ComboBoxMouseDownBorder`|  
|![Campo entrada de cuadro combinado presionado](../extensibility/ux-guidelines/media/0303-038-comboboxinputfieldpressed.png "0303-038_ComboBoxInputFieldPressed")<br /><br /> **Campo de entrada**|Separador|`Environment.ComboBoxMouseDownSeparator`|  
|![Cuadro combinado&#47;soltar&#45;botón abajo presionado](../extensibility/ux-guidelines/media/0303-039-comboboxdropdownbuttonpressed.png "0303-039_ComboBoxDropdownButtonPressed")<br /><br /> **Botón desplegable**|Fondo|`Environment.ComboBoxButtonMouseDownBackground`|  
|![Cuadro combinado&#47;soltar&#45;botón abajo presionado](../extensibility/ux-guidelines/media/0303-039-comboboxdropdownbuttonpressed.png "0303-039_ComboBoxDropdownButtonPressed")<br /><br /> **Botón desplegable**|Primer plano (glifo)|`Environment.ComboBoxMouseDownGlyph`|  
  
 **Deshabilitada**  
  
|Componente|Elemento|Nombre del token: Color.category|  
|---------------|-------------|--------------------------------|  
|![Campo entrada de cuadro combinado deshabilitado](../extensibility/ux-guidelines/media/0303-041-comboboxinputfielddisabled.png "0303-041_ComboBoxInputFieldDisabled")<br /><br /> **Campo de entrada**|Fondo|`Environment.ComboBoxDisabledBackground`|  
|![Campo entrada de cuadro combinado deshabilitado](../extensibility/ux-guidelines/media/0303-041-comboboxinputfielddisabled.png "0303-041_ComboBoxInputFieldDisabled")<br /><br /> **Campo de entrada**|Primer plano (texto)|`Environment.ComboBoxDisabledText`|  
|![Campo entrada de cuadro combinado deshabilitado](../extensibility/ux-guidelines/media/0303-041-comboboxinputfielddisabled.png "0303-041_ComboBoxInputFieldDisabled")<br /><br /> **Campo de entrada**|Borde|`Environment.ComboBoxDisabledBorder`|  
|![Campo entrada de cuadro combinado deshabilitado](../extensibility/ux-guidelines/media/0303-041-comboboxinputfielddisabled.png "0303-041_ComboBoxInputFieldDisabled")<br /><br /> **Campo de entrada**|Separador|Sin separador|  
|![Cuadro combinado&#47;quitar&#45;botón abajo deshabilitado](../extensibility/ux-guidelines/media/0303-040-comboboxdropdownbuttondisabled.png "0303-040_ComboBoxDropdownButtonDisabled")<br /><br /> **Botón desplegable**|Fondo|None|  
|![Cuadro combinado&#47;quitar&#45;botón abajo deshabilitado](../extensibility/ux-guidelines/media/0303-040-comboboxdropdownbuttondisabled.png "0303-040_ComboBoxDropdownButtonDisabled")<br /><br /> **Botón desplegable**|Primer plano (glifo)|`Environment.ComboBoxDisabledGlyph`|  
  
##### <a name="drop-down"></a><a name="BKMK_CommandDropDown"></a>Lista desplegable  
  
> [!IMPORTANT]
> Las listas desplegables son similares a los cuadros combinados, pero carecen de áreas de texto editable. Si la lista desplegable incluye un área de texto editable, use los tokens de color que se encuentran en [Combo box](../misc/shared-colors.md#BKMK_CommandComboBox).  
  
 ![Colocar&#45;abajo hacia abajo](../extensibility/ux-guidelines/media/0303-042-dropdownredline.png "0303-042_DropdownRedline")  
  
 Use…  
 al crear controles de lista desplegable personalizados.  
  
No use…  
- para cualquier elemento que no sea similar a una lista desplegable.  

- para cuadros combinados o botones de expansión.  
  
  **Valor predeterminado**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Quitar&#45;campo de selección hacia abajo](../extensibility/ux-guidelines/media/0303-043-dropdownselectionfield.png "0303-043_DropdownSelectionField")<br /><br /> **Campo de selección**|Fondo|`Environment.DropDownBackground`|  
|![Quitar&#45;campo de selección hacia abajo](../extensibility/ux-guidelines/media/0303-043-dropdownselectionfield.png "0303-043_DropdownSelectionField")<br /><br /> **Campo de selección**|Primer plano (texto)|`DropDownText`|  
|![Quitar&#45;campo de selección hacia abajo](../extensibility/ux-guidelines/media/0303-043-dropdownselectionfield.png "0303-043_DropdownSelectionField")<br /><br /> **Campo de selección**|Borde|`DropDownBorder`|  
|![Quitar&#45;campo de selección hacia abajo](../extensibility/ux-guidelines/media/0303-043-dropdownselectionfield.png "0303-043_DropdownSelectionField")<br /><br /> **Campo de selección**|Separador|Sin separador|  
|![Botón desplegable&#45;](../extensibility/ux-guidelines/media/0303-044-dropdownbutton.png "0303-044_DropdownButton")<br /><br /> **Botón desplegable**|Fondo|None|  
|![Botón desplegable&#45;](../extensibility/ux-guidelines/media/0303-044-dropdownbutton.png "0303-044_DropdownButton")<br /><br /> **Botón desplegable**|Primer plano (glifo)|`Environment.DropDownGlyph`|  
|![Quitar&#45;lista desplegable](../extensibility/ux-guidelines/media/0303-045-dropdownlist.png "0303-045_DropdownList")<br /><br /> **Lista desplegable**|Fondo|`Environment.DropDownPopupBackgroundBegin`<br /><br /> Aunque no se usan en la interfaz de usuario moderna con temas, hay delimitadores de degradado y valores para este fondo.|  
|![Quitar&#45;lista desplegable](../extensibility/ux-guidelines/media/0303-045-dropdownlist.png "0303-045_DropdownList")<br /><br /> **Lista desplegable**|Primer plano (texto)|`Environment.ComboBoxItemText`|  
|![Quitar&#45;lista desplegable](../extensibility/ux-guidelines/media/0303-045-dropdownlist.png "0303-045_DropdownList")<br /><br /> **Lista desplegable**|Borde|`Environment.DropDownPopupBorder`|  
|![Quitar&#45;lista desplegable](../extensibility/ux-guidelines/media/0303-045-dropdownlist.png "0303-045_DropdownList")<br /><br /> **Lista desplegable**|Shadow|`Environment.DropShadowBackground`|  
  
 **Al mantener el puntero**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Quitar&#45;campo de selección hacia abajo al mantener el mouse](../extensibility/ux-guidelines/media/0303-046-dropdownselectionfieldhover.png "0303-046_DropdownSelectionFieldHover")<br /><br /> **Campo de selección**|Fondo|`Environment.DropDownMouseOverBackgroundBegin`<br /><br /> Aunque no se usan en la interfaz de usuario moderna con temas, hay delimitadores de degradado y valores para este fondo.|  
|![Quitar&#45;campo de selección hacia abajo al mantener el mouse](../extensibility/ux-guidelines/media/0303-046-dropdownselectionfieldhover.png "0303-046_DropdownSelectionFieldHover")<br /><br /> **Campo de selección**|Primer plano (texto)|`Environment.DropDownMouseOverText`|  
|![Quitar&#45;campo de selección hacia abajo al mantener el mouse](../extensibility/ux-guidelines/media/0303-046-dropdownselectionfieldhover.png "0303-046_DropdownSelectionFieldHover")<br /><br /> **Campo de selección**|Borde|`Environment.DropDownMouseOverBorder`|  
|![Quitar&#45;campo de selección hacia abajo al mantener el mouse](../extensibility/ux-guidelines/media/0303-046-dropdownselectionfieldhover.png "0303-046_DropdownSelectionFieldHover")<br /><br /> **Campo de selección**|Separador|`Environment.DropDownButtonMouseOverSeparator`|  
|![Desplazar&#45;botón abajo al mantener el mouse](../extensibility/ux-guidelines/media/0303-047-dropdownbuttonhover.png "0303-047_DropdownButtonHover")<br /><br /> **Botón desplegable**|Fondo|`Environment.DropDownButtonMouseOverBackground`|  
|![Desplazar&#45;botón abajo al mantener el mouse](../extensibility/ux-guidelines/media/0303-047-dropdownbuttonhover.png "0303-047_DropdownButtonHover")<br /><br /> **Botón desplegable**|Primer plano (glifo)|`Environment.DropDownMouseOverGlyph`|  
|![Quitar&#45;lista desplegable al mantener el mouse](../extensibility/ux-guidelines/media/0303-048-dropdownlisthover.png "0303-048_DropdownListHover")<br /><br /> **Lista desplegable**|Fondo (elemento de menú)|`Environment.ComboBoxItemMouseOverBackground`|  
|![Quitar&#45;lista desplegable al mantener el mouse](../extensibility/ux-guidelines/media/0303-048-dropdownlisthover.png "0303-048_DropdownListHover")<br /><br /> **Lista desplegable**|Primer plano (texto)|`Environment.ComboBoxItemMouseOverText`|  
|![Quitar&#45;lista desplegable al mantener el mouse](../extensibility/ux-guidelines/media/0303-048-dropdownlisthover.png "0303-048_DropdownListHover")<br /><br /> **Lista desplegable**|Borde (elemento de menú)|`Environment.ComboBoxItemMouseOverBorder`|  
  
 **Pressed**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Quitar&#45;campo de selección hacia abajo presionado](../extensibility/ux-guidelines/media/0303-049-dropdownselectionfieldpressed.png "0303-049_DropdownSelectionFieldPressed")<br /><br /> **Campo de selección**|Fondo|`Environment.DropDownMouseDownBackground`|  
|![Quitar&#45;campo de selección hacia abajo presionado](../extensibility/ux-guidelines/media/0303-049-dropdownselectionfieldpressed.png "0303-049_DropdownSelectionFieldPressed")<br /><br /> **Campo de selección**|Primer plano (texto)|`Environment.DropDownMouseDownText`|  
|![Quitar&#45;campo de selección hacia abajo presionado](../extensibility/ux-guidelines/media/0303-049-dropdownselectionfieldpressed.png "0303-049_DropdownSelectionFieldPressed")<br /><br /> **Campo de selección**|Borde|`Environment.DropDownMouseDownBorder`|  
|![Quitar&#45;campo de selección hacia abajo presionado](../extensibility/ux-guidelines/media/0303-049-dropdownselectionfieldpressed.png "0303-049_DropdownSelectionFieldPressed")<br /><br /> **Campo de selección**|Separador|`Environment.DropDownButtonMouseDownSeparator`|  
|![Botón desplegable&#45;presionado](../extensibility/ux-guidelines/media/0303-050-dropdownbuttonpressed.png "0303-050_DropdownButtonPressed")<br /><br /> **Botón desplegable**|Fondo|`Environment.DropDownButtonMouseDownBackground`|  
|![Botón desplegable&#45;presionado](../extensibility/ux-guidelines/media/0303-050-dropdownbuttonpressed.png "0303-050_DropdownButtonPressed")<br /><br /> **Botón desplegable**|Primer plano (glifo)|`Environment.DropDownMouseDownGlyph`|  
  
 **Deshabilitada**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Quitar&#45;campo de selección hacia abajo deshabilitado](../extensibility/ux-guidelines/media/0303-051-dropdownselectionfielddisabled.png "0303-051_DropdownSelectionFieldDisabled")|Fondo|`Environment.DropDownDisabledBackground`|  
|![Quitar&#45;campo de selección hacia abajo deshabilitado](../extensibility/ux-guidelines/media/0303-051-dropdownselectionfielddisabled.png "0303-051_DropdownSelectionFieldDisabled")|Primer plano (texto)|`Environment.DropDownDisabledText`|  
|![Quitar&#45;campo de selección hacia abajo deshabilitado](../extensibility/ux-guidelines/media/0303-051-dropdownselectionfielddisabled.png "0303-051_DropdownSelectionFieldDisabled")|Borde|`Environment.DropDownDisabledBorder`|  
|![Quitar&#45;campo de selección hacia abajo deshabilitado](../extensibility/ux-guidelines/media/0303-051-dropdownselectionfielddisabled.png "0303-051_DropdownSelectionFieldDisabled")|Separador|Sin separador|  
|![Botón desplegable&#45;deshabilitado](../extensibility/ux-guidelines/media/0303-052-dropdownbuttondisabled.png "0303-052_DropdownButtonDisabled")|Fondo|N/D|  
|![Botón desplegable&#45;deshabilitado](../extensibility/ux-guidelines/media/0303-052-dropdownbuttondisabled.png "0303-052_DropdownButtonDisabled")|Primer plano (glifo)|`Environment.DropDownDisabledGlyph`|  
  
##### <a name="split-button"></a>Botón de expansión  
 Los botones de expansión comparten muchos nombres de token con otros controles de barra de comandos como, por ejemplo, botones, menús y texto de la barra de comandos. Todos los nombres de token de acciones y botones desplegables necesarios se repiten aquí para su comodidad. Las listas desplegables de botón de expansión son implementaciones de la barra de comandos [Menus](../misc/shared-colors.md#BKMK_CommandMenus).  
  
 ![Límite de botón de expansión](../extensibility/ux-guidelines/media/0303-053-splitbuttonredline.png "0303-053_SplitButtonRedline")  
  
 Use…  
 si crea un botón de expansión personalizado.  
  
No use…  
- para otros tipos de botones.  

- en cualquier combinación de primer plano y fondo distinta de la especificada.  
  
  **Valor predeterminado**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Botón de expansión](../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303-054_SplitButton")<br /><br /> **Botón de expansión (predeterminado)**|Fondo|None|  
|![Botón de expansión](../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303-054_SplitButton")<br /><br /> **Botón de expansión (predeterminado)**|Primer plano (texto)|`Environment.CommandBarTextActive`|  
|![Botón de expansión](../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303-054_SplitButton")<br /><br /> **Botón de expansión (predeterminado)**|Primer plano (glifo)|`Environment.CommandBarSplitButtonGlyph`|  
|![Botón de expansión](../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303-054_SplitButton")<br /><br /> **Botón de expansión (predeterminado)**|Borde|N/D|  
|![Botón de expansión](../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303-054_SplitButton")<br /><br /> **Botón de expansión (predeterminado)**|Separador|N/D|  
  
 **Al mantener el puntero**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Botón de expansión al mantener el mouse](../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303-055_SplitButtonHover")<br /><br /> **Botón de expansión (al mantener el puntero)**|Fondo|`Environment.CommandBarMouseOverBackgroundBegin`<br /><br /> Aunque no se usan en la interfaz de usuario moderna con temas, hay delimitadores de degradado y valores para este fondo.|  
|![Botón de expansión al mantener el mouse](../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303-055_SplitButtonHover")<br /><br /> **Botón de expansión (al mantener el puntero)**|Primer plano (texto)|`Environment.CommandBarTextHover`|  
|![Botón de expansión al mantener el mouse](../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303-055_SplitButtonHover")<br /><br /> **Botón de expansión (al mantener el puntero)**|Primer plano (glifo)|`Environment.CommandBarSplitButtonMouseOverGlyph`|  
|![Botón de expansión al mantener el mouse](../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303-055_SplitButtonHover")<br /><br /> **Botón de expansión (al mantener el puntero)**|Borde|`Environment.CommandBarBorder`|  
|![Botón de expansión al mantener el mouse](../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303-055_SplitButtonHover")<br /><br /> **Botón de expansión (al mantener el puntero)**|Separador|`Environment.CommandBarSplitButtonSeparator`|  
  
 **Pressed**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Botón de expansión presionado](../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303-056_SplitButtonPressed")<br /><br /> **Botón de expansión (presionado)**|Fondo|`Environment.CommandBarMouseDownBackgroundBegin`<br /><br /> Aunque no se usan en la interfaz de usuario moderna con temas, hay delimitadores de degradado y valores para este fondo.|  
|![Botón de expansión presionado](../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303-056_SplitButtonPressed")<br /><br /> **Botón de expansión (presionado)**|Primer plano (texto)|`Environment.CommandBarTextMouseDown`|  
|![Botón de expansión presionado](../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303-056_SplitButtonPressed")<br /><br /> **Botón de expansión (presionado)**|Primer plano (glifo)|`Environment.CommandBarSplitButtonMouseDownGlyph`|  
|![Botón de expansión presionado](../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303-056_SplitButtonPressed")<br /><br /> **Botón de expansión (presionado)**|Borde|`Environment.CommandBarBorder`|  
|![Botón de expansión presionado](../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303-056_SplitButtonPressed")<br /><br /> **Botón de expansión (presionado)**|Separador|N/D|  
  
 **Deshabilitada**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Botón de expansión deshabilitado](../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303-057_SplitButtonDisabled")<br /><br /> **Botón de expansión (deshabilitado)**|Fondo|N/D|  
|![Botón de expansión deshabilitado](../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303-057_SplitButtonDisabled")<br /><br /> **Botón de expansión (deshabilitado)**|Primer plano (texto)|`Environment.ComboBoxItemTextInactive`|  
|![Botón de expansión deshabilitado](../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303-057_SplitButtonDisabled")<br /><br /> **Botón de expansión (deshabilitado)**|Primer plano (glifo)|`Environment.CommandBarTextInactive`|  
|![Botón de expansión deshabilitado](../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303-057_SplitButtonDisabled")<br /><br /> **Botón de expansión (deshabilitado)**|Borde|N/D|  
|![Botón de expansión deshabilitado](../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303-057_SplitButtonDisabled")<br /><br /> **Botón de expansión (deshabilitado)**|Separador|N/D|  
  
##### <a name="more-options-and-overflow-buttons"></a>Botones "Más opciones" y "Desbordamiento"  
 El botón "Más opciones" se usa cuando un grupo de la barra de comandos se puede personalizar al agregar o quitar botones relacionados de barra de comandos. El botón "Desbordamiento" aparece cuando una barra de comandos se trunca debido a la falta de espacio horizontal y, al hacer clic en él, muestra un menú que contiene los botones de la barra de comandos que no pueden mostrarse. Los colores para estos dos botones están controlados por el mismo conjunto de nombres de token.  
  
 ![Límite de Más opciones](../extensibility/ux-guidelines/media/0303-058-moreoptionsredline.png "0303-058_MoreOptionsRedline")  
  
 Use…  
 para los botones "Más opciones" o "Desbordamiento" personalizados.  
  
 No use…  
 para los botones que no tienen una función similar a la de los botones "Más opciones" o "Desbordamiento".  
  
 **Valor predeterminado**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Más opciones](../extensibility/ux-guidelines/media/0303-059-moreoptions.png "0303-059_MoreOptions")<br /><br /> **Más opciones**|Fondo|`Environment.CommandBarOptionsBackground`|  
|![Más opciones](../extensibility/ux-guidelines/media/0303-059-moreoptions.png "0303-059_MoreOptions")<br /><br /> **Más opciones**|Primer plano (glifo)|`Environment.CommandBarOptionsGlyph`|  
|![Botón de desbordamiento](../extensibility/ux-guidelines/media/0303-060-overflow.png "0303-060_Overflow")<br /><br /> **Desbordamiento**|Fondo|`Environment.CommandBarOptionsBackground`|  
|![Botón de desbordamiento](../extensibility/ux-guidelines/media/0303-060-overflow.png "0303-060_Overflow")<br /><br /> **Desbordamiento**|Primer plano (glifo)|`Environment.CommandBarOptionsGlyph`|  
  
 **Al mantener el puntero**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Más opciones al mantener el mouse](../extensibility/ux-guidelines/media/0303-061-moreoptionshover.png "0303-061_MoreOptionsHover")<br /><br /> **Más opciones**|Fondo|`Environment.CommandBarOptionsMouseOverBackgroundBegin`<br /><br /> Aunque no se usan en la interfaz de usuario moderna con temas, hay delimitadores de degradado y valores para este fondo.|  
|![Más opciones al mantener el mouse](../extensibility/ux-guidelines/media/0303-061-moreoptionshover.png "0303-061_MoreOptionsHover")<br /><br /> **Más opciones**|Primer plano (glifo)|`Environment.CommandBarOptionsMouseDownGlyph`|  
|![Desbordamiento al mantener el mouse](../extensibility/ux-guidelines/media/0303-062-overflowoptions.png "0303-062_OverflowOptions")<br /><br /> **Desbordamiento**|Fondo|`Environment.CommandBarOptionsMouseOverBackgroundBegin`<br /><br /> Aunque no se usan en la interfaz de usuario moderna con temas, hay delimitadores de degradado y valores para este fondo.|  
|![Desbordamiento al mantener el mouse](../extensibility/ux-guidelines/media/0303-062-overflowoptions.png "0303-062_OverflowOptions")<br /><br /> **Desbordamiento**|Primer plano (glifo)|`Environment.CommandBarOptionsMouseDownGlyph`|  
  
 **Pressed**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Más opciones presionado](../extensibility/ux-guidelines/media/0303-063-moreoptionspressed.png "0303-063_MoreOptionsPressed")<br /><br /> **Más opciones**|Fondo|`Environment.CommandBarOptionsMouseDownBackgroundBegin`<br /><br /> Aunque no se usan en la interfaz de usuario moderna con temas, hay delimitadores de degradado y valores para este fondo.|  
|![Más opciones presionado](../extensibility/ux-guidelines/media/0303-063-moreoptionspressed.png "0303-063_MoreOptionsPressed")<br /><br /> **Más opciones**|Primer plano (glifo)|`Environment.CommandBarOptionsMouseDownGlyph`|  
|![Desbordamiento presionado](../extensibility/ux-guidelines/media/0303-064-overflowpressed.png "0303-064_OverflowPressed")<br /><br /> **Desbordamiento**|Fondo|`Environment.CommandBarOptionsMouseDownBackgroundBegin`<br /><br /> Aunque no se usan en la interfaz de usuario moderna con temas, hay delimitadores de degradado y valores para este fondo.|  
|![Desbordamiento presionado](../extensibility/ux-guidelines/media/0303-064-overflowpressed.png "0303-064_OverflowPressed")<br /><br /> **Desbordamiento**|Primer plano (glifo)|`Environment.CommandBarOptionsMouseDownGlyph`|  
  
### <a name="document-windows"></a>Ventanas de documento  
 No es necesario replicar las ventanas de documento, porque las proporciona el entorno de Visual Studio. Sin embargo, quizá prefiera aprovechar los colores que se usan en las ventanas de documento para que la interfaz de usuario se muestre siempre coherente con esta parte del entorno de Visual Studio.  
  
 Si usa tokens de color de ventana de documento, tenga la precaución de usarlos únicamente para elementos similares y siempre en pares. Si no lo hace, tendrá resultados inesperados en la interfaz de usuario.  
  
#### <a name="document-window-frame"></a>Marco de ventana de documento  
 Las ventanas de documento pueden estar acopladas en el IDE o flotantes como una ventana independiente. Si una ventana de documento está flotante fuera del IDE, aun así se encuentra en el cuadro de un documento y su fondo, borde, texto y sus colores de pestaña son los mismos que cuando forma parte del IDE. Sin embargo, el documento se encuentra dentro de un marco que tiene su propio fondo, borde y colores de texto. Cuando las ventanas de herramientas se acoplan en el cuadro del documento, heredan el comportamiento y el color de los nombres de token de ventana de documento para sus pestañas.  
  
 ![Límite de ventana de documento acoplado](../extensibility/ux-guidelines/media/0303-065-dockeddocumentwindowredline.png "0303-065_DockedDocumentWindowRedline")  
  
 **Ventana de documento acoplada**  
  
 ![Límite de ventana de documento flotante](../extensibility/ux-guidelines/media/0303-066-floatingdocumentwindowredline.png "0303-066_FloatingDocumentWindowRedline")  
  
 **Ventana de documento flotante**  
  
 Use…  
 en cualquier lugar donde cree una interfaz de usuario que quiere hacer coincidir con la ventana de documento.  
  
 No use…  
 para cualquier interfaz de usuario que no desea que cambie automáticamente si se actualiza un tema del shell.  
  
 **Valor predeterminado**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|Documento: acoplado o flotante|Fondo|Depende del tipo de documento|  
|Documento: acoplado o flotante|Primer plano (texto)|Depende del tipo de documento|  
|Documento: acoplado o flotante|Borde|`Environment.ToolWindowBorder`|  
|![Marco enfocado](../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303-067_FrameFocused")<br /><br /> **Marco: flotante, con foco**|Fondo|`Environment.ToolWindowFloatingFrame`|  
|![Marco enfocado](../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303-067_FrameFocused")<br /><br /> **Marco: flotante, con foco**|Primer plano (texto)|`Environment.ToolWindowFloatingFrame`|  
|![Marco enfocado](../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303-067_FrameFocused")<br /><br /> **Marco: flotante, con foco**|Primer plano (glifo)|`Environment.RaftedWindowButtonActiveGlyph`|  
|![Marco enfocado](../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303-067_FrameFocused")<br /><br /> **Marco: flotante, con foco**|Borde|`Environment.MainWindowActiveDefaultBorder`|  
|![Marco enfocado](../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303-067_FrameFocused")<br /><br /> **Marco: flotante, con foco**|Borde (glifo)|`Environment.RaftedWindowButtonActiveBorder`<br /><br /> Se establece en transparente|  
|![Marco no enfocado](../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303-068_FrameUnfocused")<br /><br /> **Marco: flotante, sin foco**|Fondo|`Environment.ToolWindowFloatingFrameInactive`|  
|![Marco no enfocado](../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303-068_FrameUnfocused")<br /><br /> **Marco: flotante, sin foco**|Primer plano (texto)|`Environment.ToolWindowFloatingFrameInactive`|  
|![Marco no enfocado](../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303-068_FrameUnfocused")<br /><br /> **Marco: flotante, sin foco**|Primer plano (glifo)|`Environment.RaftedWindowButtonInactiveGlyph`|  
|![Marco no enfocado](../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303-068_FrameUnfocused")<br /><br /> **Marco: flotante, sin foco**|Borde|`Environment.MainWindowInactiveBorder`|  
|![Marco no enfocado](../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303-068_FrameUnfocused")<br /><br /> **Marco: flotante, sin foco**|Borde (glifo)|`Environment.RaftedWindowButtonInactiveBorder`<br /><br /> Se establece en transparente|  
  
 **Al mantener el puntero**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Marco enfocado al mantener el mouse](../extensibility/ux-guidelines/media/0303-069-framefocusedhover.png "0303-069_FrameFocusedHover")<br /><br /> **Marco: flotante, con foco**|Fondo (glifo)|`Environment.RaftedWindowButtonHoverActive`|  
|![Marco enfocado al mantener el mouse](../extensibility/ux-guidelines/media/0303-069-framefocusedhover.png "0303-069_FrameFocusedHover")<br /><br /> **Marco: flotante, con foco**|Primer plano (glifo)|`Environment.RaftedWindowButtonHoverActiveGlyph`|  
|![Marco enfocado al mantener el mouse](../extensibility/ux-guidelines/media/0303-069-framefocusedhover.png "0303-069_FrameFocusedHover")<br /><br /> **Marco: flotante, con foco**|Borde (glifo)|`Environment.RaftedWindowButtonHoverActiveBorder`|  
|![Marco no enfocado al mantener el mouse](../extensibility/ux-guidelines/media/0303-070-frameunfocusedhover.png "0303-070_FrameUnfocusedHover")<br /><br /> **Marco: flotante, sin foco**|Fondo (glifo)|`EnvironmentRaftedWindowButtonHoverInactive`|  
|![Marco no enfocado al mantener el mouse](../extensibility/ux-guidelines/media/0303-070-frameunfocusedhover.png "0303-070_FrameUnfocusedHover")<br /><br /> **Marco: flotante, sin foco**|Primer plano (glifo)|`Environment.RaftedWindowButtonHoverInactiveGlyph`|  
|![Marco no enfocado al mantener el mouse](../extensibility/ux-guidelines/media/0303-070-frameunfocusedhover.png "0303-070_FrameUnfocusedHover")<br /><br /> **Marco: flotante, sin foco**|Borde (glifo)|`Environment.RaftedWindowButtonHoverInactiveBorder`|  
  
 **Pressed**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Marco enfocado presionado](../extensibility/ux-guidelines/media/0303-071-framefocusedpressed.png "0303-071_FrameFocusedPressed")<br /><br /> **Marco: flotante, con foco**|Fondo (glifo)|`Environment.RaftedWindowButtonDown`|  
|![Marco enfocado presionado](../extensibility/ux-guidelines/media/0303-071-framefocusedpressed.png "0303-071_FrameFocusedPressed")<br /><br /> **Marco: flotante, con foco**|Primer plano (glifo)|`Environment.RaftedWindowButtonDownGlyph`|  
|![Marco enfocado presionado](../extensibility/ux-guidelines/media/0303-071-framefocusedpressed.png "0303-071_FrameFocusedPressed")<br /><br /> **Marco: flotante, con foco**|Borde (glifo)|`Environment.RaftedWindowButtonDownBorder`|  
  
#### <a name="document-tabs"></a>Pestañas de documentos  
 Las pestañas de documentos se colocan en el canal de pestañas para indicar los documentos que están abiertos actualmente, así como el documento actual activo o seleccionado. Las ventanas de herramientas también se pueden acoplar en el canal de pestañas de documentos si el usuario las coloca allí. En este caso, usan los mismos colores de pestaña que las ventanas de documento. Si va a crear interfaz de usuario que desea que siempre coincida con los colores de las ventanas de documento (lo que incluye las actualizaciones de temas o si se instalan nuevos temas), entonces haga referencia a estos tokens de color.  
  
 ![Límite de pestaña de documento](../extensibility/ux-guidelines/media/0303-072-documenttabredline.png "0303-072_DocumentTabRedline")  
  
 Use…  
 en cualquier lugar donde cree interfaz de usuario que quiere hacer coincidir con las pestañas de documentos y que seleccione automáticamente actualizaciones de tema o nuevos colores de tema.  
  
 No use…  
 para cualquier interfaz de usuario que no desea que cambie automáticamente si se actualiza un tema del shell.  
  
##### <a name="open-document-tabs"></a>Pestañas de documentos abiertos  
 Cada documento abierto tiene una pestaña en el canal de pestañas de documentos que muestra su nombre. Los documentos pueden estar seleccionados o abiertos en segundo plano y sus pestañas reflejan los siguientes estados:  
  
- La pestaña seleccionada representa el documento que se muestra actualmente en el cuadro de documento. Una pestaña seleccionada tiene un borde de documento que se extiende por todo el borde superior del cuadro de documento.  
  
- Las pestañas de fondo son cualquier pestaña de documento que no sea la pestaña seleccionada actualmente. Una vez que haga clic en ella, se convertirán en la pestaña seleccionada y adquirirán todos los colores de fondo, borde y texto de los nombres de token.  
  
  ![Límite de pestaña de documento abierto](../extensibility/ux-guidelines/media/0303-073-opendocumenttabredline.png "0303-073_OpenDocumentTabRedline")  
  
  Use…  
  al crear pestañas de documentos personalizadas.  
  
  No use…  
  - para pestañas provisionales (vista previa).  
  
- para cualquier interfaz de usuario que no desea que cambie automáticamente si se actualiza un tema del shell.  
  
##### <a name="selected-tab"></a>Pestaña seleccionada  
 **Focused**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Pestaña seleccionada enfocada](../extensibility/ux-guidelines/media/0303-074-selectedtabfocused.png "0303-074_SelectedTabFocused")<br /><br /> **Pestaña de documento seleccionada, con foco**|Fondo|`Environment.FileTabSelectedGradientTop`<br /><br /> Aunque no se usan en la interfaz de usuario moderna con temas, hay delimitadores de degradado y valores para este fondo.|  
|![Pestaña seleccionada enfocada](../extensibility/ux-guidelines/media/0303-074-selectedtabfocused.png "0303-074_SelectedTabFocused")<br /><br /> **Pestaña de documento seleccionada, con foco**|Primer plano (texto)|`Environment.FileTabSelectedText`|  
|![Pestaña seleccionada enfocada](../extensibility/ux-guidelines/media/0303-074-selectedtabfocused.png "0303-074_SelectedTabFocused")<br /><br /> **Pestaña de documento seleccionada, con foco**|Borde|`Environment.FileTabSelectedBorder`<br /><br /> Se establece en el mismo color que el fondo.|  
|![Pestaña seleccionada enfocada](../extensibility/ux-guidelines/media/0303-074-selectedtabfocused.png "0303-074_SelectedTabFocused")<br /><br /> **Pestaña de documento seleccionada, con foco**|Borde de documento|`Environment.FileTabDocumentBorderBackground`|  
  
 **Sin foco**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Pestaña seleccionada no enfocada](../extensibility/ux-guidelines/media/0303-075-selectedtabunfocused.png "0303-075_SelectedTabUnfocused")<br /><br /> **Pestaña de documento seleccionada, sin foco**|Fondo|`Environment.FileTabInactiveGradientTop`<br /><br /> Aunque no se usan en la interfaz de usuario moderna con temas, hay delimitadores de degradado y valores para este fondo.|  
|![Pestaña seleccionada no enfocada](../extensibility/ux-guidelines/media/0303-075-selectedtabunfocused.png "0303-075_SelectedTabUnfocused")<br /><br /> **Pestaña de documento seleccionada, sin foco**|Primer plano (texto)|`Environment.FileTabInactiveText`|  
|![Pestaña seleccionada no enfocada](../extensibility/ux-guidelines/media/0303-075-selectedtabunfocused.png "0303-075_SelectedTabUnfocused")<br /><br /> **Pestaña de documento seleccionada, sin foco**|Borde|`Environment.FileTabInactiveBorder`<br /><br /> Se establece en el mismo color que el fondo.|  
|![Pestaña seleccionada no enfocada](../extensibility/ux-guidelines/media/0303-075-selectedtabunfocused.png "0303-075_SelectedTabUnfocused")<br /><br /> **Pestaña de documento seleccionada, sin foco**|Borde de documento|`Environment.FileTabInactiveDocumentBorderBackground`|  
  
##### <a name="background-tab"></a>Pestaña en segundo plano  
 **Valor predeterminado**  
  
|Componente|Elemento|Nombre del token: Color.category|  
|---------------|-------------|--------------------------------|  
|![Pestaña en segundo plano](../extensibility/ux-guidelines/media/0303-076-backgroundtab.png "0303-076_BackgroundTab")<br /><br /> **Valor predeterminado de pestaña en segundo plano**|Fondo|`Environment.FileTabBackground`|  
|![Pestaña en segundo plano](../extensibility/ux-guidelines/media/0303-076-backgroundtab.png "0303-076_BackgroundTab")<br /><br /> **Valor predeterminado de pestaña en segundo plano**|Primer plano (texto)|`Environment.FileTabText`|  
|![Pestaña en segundo plano](../extensibility/ux-guidelines/media/0303-076-backgroundtab.png "0303-076_BackgroundTab")<br /><br /> **Valor predeterminado de pestaña en segundo plano**|Borde|`Environment.FileTabBorder`<br /><br /> Se establece en el mismo color que el fondo.|  
  
 **Al mantener el puntero**  
  
|Componente|Elemento|Nombre del token: Color.category|  
|---------------|-------------|--------------------------------|  
|![Pestaña en segundo plano al mantener el puntero](../extensibility/ux-guidelines/media/0303-077-backgroundtabhover.png "0303-077_BackgroundTabHover")<br /><br /> **Pestaña en segundo plano al mantener el puntero**|Fondo|`Environment.FileTabHotGradientTop`<br /><br /> Aunque no se usan en la interfaz de usuario moderna con temas, hay delimitadores de degradado y valores para este fondo.|  
|![Pestaña en segundo plano al mantener el puntero](../extensibility/ux-guidelines/media/0303-077-backgroundtabhover.png "0303-077_BackgroundTabHover")<br /><br /> **Pestaña en segundo plano al mantener el puntero**|Primer plano (texto)|`Environment.FileTabHotText`|  
|![Pestaña en segundo plano al mantener el puntero](../extensibility/ux-guidelines/media/0303-077-backgroundtabhover.png "0303-077_BackgroundTabHover")<br /><br /> **Pestaña en segundo plano al mantener el puntero**|Borde|`Environment.FileTabHotBorder`<br /><br /> Se establece en el mismo color que el fondo.|  
  
##### <a name="preview-tab"></a>Pestaña de vista previa  
 La pestaña de vista previa aparece en la parte derecha del canal de pestañas de documentos cuando el usuario hace clic en un elemento de la ventana de herramientas del Explorador de soluciones. Funciona como una vista previa del documento y también proporciona al usuario la posibilidad de mantener el documento abierto en la parte izquierda del canal de pestañas de documentos. Solo se puede abrir una pestaña de vista previa a la vez. Las pestañas de vista previa tienen tanto el estado seleccionado como en segundo plano al igual que las pestañas abiertas y, además, pueden estar con y sin foco en su estado activo.  
  
 ![Límite de pestaña de vista previa](../extensibility/ux-guidelines/media/0303-078-previewtabredline.png "0303-078_PreviewTabRedline")  
  
 Use…  
 en cualquier parte donde cree vista previa provisional y quiere hacer coincidir algún elemento con el color de la pestaña de vista previa actual.  
  
No use…  
- para cualquier tipo de documento o pestaña que no sea provisional (vista previa).  

- para cualquier interfaz de usuario que no desea que cambie automáticamente si se actualiza un tema del shell.  
  
  **Pestaña de vista previa seleccionada: con foco**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Pestaña de vista previa enfocada](../extensibility/ux-guidelines/media/0303-079-previewtabfocused.png "0303-079_PreviewTabFocused")<br /><br /> **Pestaña de vista previa con foco**|Fondo|`Environment.FileTabProvisionalSelectedActive`|  
|![Pestaña de vista previa enfocada](../extensibility/ux-guidelines/media/0303-079-previewtabfocused.png "0303-079_PreviewTabFocused")<br /><br /> **Pestaña de vista previa con foco**|Primer plano (texto)|`Environment.FileTabProvisionalSelectedActiveForeground`|  
|![Pestaña de vista previa enfocada](../extensibility/ux-guidelines/media/0303-079-previewtabfocused.png "0303-079_PreviewTabFocused")<br /><br /> **Pestaña de vista previa con foco**|Borde|`Environment.FileTabProvisionalSelectedActiveBorder`<br /><br /> Se establece en el mismo color que el fondo.|  
|![Pestaña de vista previa enfocada](../extensibility/ux-guidelines/media/0303-079-previewtabfocused.png "0303-079_PreviewTabFocused")<br /><br /> **Pestaña de vista previa con foco**|Borde de documento|`Environment.FileTabProvisionalSelectedActiveBorder`|  
  
 **Pestaña de vista previa seleccionada: sin foco**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Pestaña de vista previa no enfocada](../extensibility/ux-guidelines/media/0303-080-previewtabunfocused.png "0303-080_PreviewTabUnfocused")<br /><br /> **Pestaña de vista previa sin foco**|Fondo|`Environment.FileTabProvisionalSelectedInactive`|  
|![Pestaña de vista previa no enfocada](../extensibility/ux-guidelines/media/0303-080-previewtabunfocused.png "0303-080_PreviewTabUnfocused")<br /><br /> **Pestaña de vista previa sin foco**|Primer plano (texto)|`Environment.FileTabProvisionalSelectedInactiveForeground`|  
|![Pestaña de vista previa no enfocada](../extensibility/ux-guidelines/media/0303-080-previewtabunfocused.png "0303-080_PreviewTabUnfocused")<br /><br /> **Pestaña de vista previa sin foco**|Borde|`Environment.FileTabProvisionalSelectedInactiveBorder`|  
|![Pestaña de vista previa no enfocada](../extensibility/ux-guidelines/media/0303-080-previewtabunfocused.png "0303-080_PreviewTabUnfocused")<br /><br /> **Pestaña de vista previa sin foco**|Borde de documento|`Environment.FileTabProvisionalSelectedInactiveBorder`|  
  
 **Pestaña de vista previa en segundo plano: predeterminada**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Pestaña de vista previa en segundo plano](../extensibility/ux-guidelines/media/0303-081-previewbackgroundtab.png "0303-081_PreviewBackgroundTab")<br /><br /> **Pestaña en segundo plano de la pestaña de vista previa**|Fondo|`Environment.FileTabProvisionalInactive`|  
|![Pestaña de vista previa en segundo plano](../extensibility/ux-guidelines/media/0303-081-previewbackgroundtab.png "0303-081_PreviewBackgroundTab")<br /><br /> **Pestaña en segundo plano de la pestaña de vista previa**|Primer plano (texto)|`Environment.FileTabProvisionalInactiveForeground`|  
|![Pestaña de vista previa en segundo plano](../extensibility/ux-guidelines/media/0303-081-previewbackgroundtab.png "0303-081_PreviewBackgroundTab")<br /><br /> **Pestaña en segundo plano de la pestaña de vista previa**|Borde|`Environment.FileTabProvisionalInactiveBorder`<br /><br /> Se establece en el mismo color que el fondo.|  
  
 **Pestaña de vista previa en segundo plano: al mantener el puntero**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Pestaña de vista previa en segundo plano al mantener el mouse](../extensibility/ux-guidelines/media/0303-082-previewbackgroundtabhover.png "0303-082_PreviewBackgroundTabHover")<br /><br /> **Pestaña en segundo plano de la pestaña de vista previa al mantener el puntero**|Fondo|`Environment.FileTabProvisionalHover`|  
|![Pestaña de vista previa en segundo plano al mantener el mouse](../extensibility/ux-guidelines/media/0303-082-previewbackgroundtabhover.png "0303-082_PreviewBackgroundTabHover")<br /><br /> **Pestaña en segundo plano de la pestaña de vista previa al mantener el puntero**|Primer plano (texto)|`Environment.FileTabProvisionalHoverForeground`|  
|![Pestaña de vista previa en segundo plano al mantener el mouse](../extensibility/ux-guidelines/media/0303-082-previewbackgroundtabhover.png "0303-082_PreviewBackgroundTabHover")<br /><br /> **Pestaña en segundo plano de la pestaña de vista previa al mantener el puntero**|Borde|`Environment.FileTabProvisionalHoverBorder`<br /><br /> Se establece en el mismo color que el fondo.|  
  
##### <a name="document-overflow-button"></a>Botón de desbordamiento de documento  
 El botón de desbordamiento de documento se muestra si hay uno o varios documentos abiertos, independientemente de si hay espacio vertical en la configuración actual para que quepan todas las pestañas de documentos. En el menú desplegable de desbordamiento de documento, que está controlado por los colores de **CommandBarMenu** (consulte [Menus](../misc/shared-colors.md#BKMK_CommandMenus)), se muestra una lista de todos los documentos abiertos (visibles y ocultos) y los cambios de glifo de desbordamiento según si se muestran todos los documentos abiertos en el canal de pestañas.  
  
 ![Límite de desbordamiento](../extensibility/ux-guidelines/media/0303-083-overflowredline.png "0303-083_OverflowRedline")  
  
Use…  
si crea un botón de desbordamiento de documento personalizado.  

No use…  
- para interfaz de usuario que no sea similar a un botón de desbordamiento.  

- para botones de desbordamiento de la barra de comandos.  
  
  **Valor predeterminado**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Desbordamiento](../extensibility/ux-guidelines/media/0303-084-overflow.png "0303-084_Overflow")<br /><br /> **Botón de desbordamiento de documento**|Fondo|`Environment.DocWellOverflowButtonBackground`|  
|![Desbordamiento](../extensibility/ux-guidelines/media/0303-084-overflow.png "0303-084_Overflow")<br /><br /> **Botón de desbordamiento de documento**|Primer plano (glifo)|`Environment.DocWellOverflowButtonGlyph`|  
|![Desbordamiento](../extensibility/ux-guidelines/media/0303-084-overflow.png "0303-084_Overflow")<br /><br /> **Botón de desbordamiento de documento**|Borde|N/D|  
  
 **Al mantener el puntero**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Desbordamiento al mantener el mouse](../extensibility/ux-guidelines/media/0303-085-overflowhover.png "0303-085_OverflowHover")<br /><br /> **Botón de desbordamiento de documento al mantener el puntero**|Fondo|`Environment.DocWellOverflowButtonMouseOverBackground`|  
|![Desbordamiento al mantener el mouse](../extensibility/ux-guidelines/media/0303-085-overflowhover.png "0303-085_OverflowHover")<br /><br /> **Botón de desbordamiento de documento al mantener el puntero**|Primer plano (glifo)|`Environment.DocWellOverflowButtonMouseOverGlyph`|  
|![Desbordamiento al mantener el mouse](../extensibility/ux-guidelines/media/0303-085-overflowhover.png "0303-085_OverflowHover")<br /><br /> **Botón de desbordamiento de documento al mantener el puntero**|Borde|`Environment.DocWellOverflowButtonMouseOverBorder`|  
  
 **Pressed**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Desbordamiento presionado](../extensibility/ux-guidelines/media/0303-086-overflowpressed.png "0303-086_OverflowPressed")<br /><br /> **Botón de desbordamiento de documento presionado**|Fondo|`Environment.DocWellOverflowButtonMouseDownBackground`|  
|![Desbordamiento presionado](../extensibility/ux-guidelines/media/0303-086-overflowpressed.png "0303-086_OverflowPressed")<br /><br /> **Botón de desbordamiento de documento presionado**|Primer plano (glifo)|`Environment.DocWellOverflowButtonMouseDownGlyph`|  
|![Desbordamiento presionado](../extensibility/ux-guidelines/media/0303-086-overflowpressed.png "0303-086_OverflowPressed")<br /><br /> **Botón de desbordamiento de documento presionado**|Borde|`Environment.DocWellOverflowButtonMouseDownBorder`|  
  
### <a name="tool-windows"></a>Ventanas de herramientas  
 No es necesario replicar las ventanas de herramientas, porque las proporciona el entorno de Visual Studio. Sin embargo, quizá prefiera aprovechar los colores que se usan en las ventanas de herramientas para que la interfaz de usuario se muestre siempre coherente con esta parte del entorno de Visual Studio.  
  
 ![Límite de ventana de herramientas](../extensibility/ux-guidelines/media/0303-087-toolwindowredline.png "0303-087_ToolWindowRedline")  
  
 Use…  
 en cualquier lugar donde cree interfaz de usuario que desea que coincida con la ventana de herramientas.  
  
 No use…  
 para cualquier interfaz de usuario que no desea que cambie automáticamente si se actualiza un tema del shell.  
  
#### <a name="tool-window-frame"></a>Marco de ventana de herramientas  
 Las ventanas de herramientas de Visual Studio se usan para diversas tareas y pueden estar en uno de varios estados diferentes. Si una ventana de herramientas está abierta, se puede asignar a cualquiera de los cuatro lados del área del documento. Estas ventanas también pueden flotar fuera del IDE, lo que permite reubicarlas en cualquier lugar dentro de la pantalla del usuario. Las ventanas flotantes siempre se colocan arriba del IDE. Por último, las ventanas de herramientas se pueden acoplar como ventanas de documento y aparecen como una pestaña en el cuadro de documento. Las ventanas de herramientas que se han acoplado como ventanas de documento se colorean en parte mediante los nombres de token de ventana de documento.  
  
 ![Límite de marco de ventana de herramienta](../extensibility/ux-guidelines/media/0303-088-toolwindowframeredline.png "0303-088_ToolWindowFrameRedline")  
  
 Use…  
 en cualquier lugar donde cree interfaz de usuario que desea que coincida con la ventana de herramientas.  
  
 No use…  
 para cualquier interfaz de usuario que no desea que cambie automáticamente si se actualiza un tema del shell.  
  
 **Acoplado**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Ventana de herramientas acoplada](../extensibility/ux-guidelines/media/0303-089-toolwindowdocked.png "0303-089_ToolWindowDocked")|Fondo|`Environment.ToolWindowBackground`|  
|![Ventana de herramientas acoplada](../extensibility/ux-guidelines/media/0303-089-toolwindowdocked.png "0303-089_ToolWindowDocked")|Borde|`Environment.ToolWindowBorder`|  
  
 **Flotante, con foco**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Ventana de herramientas enfocada](../extensibility/ux-guidelines/media/0303-090-toolwindowfocused.png "0303-090_ToolWindowFocused")|Fondo|`Environment.ToolWindowBackground`|  
|![Ventana de herramientas enfocada](../extensibility/ux-guidelines/media/0303-090-toolwindowfocused.png "0303-090_ToolWindowFocused")|Borde|`Environment.MainWindowActiveDefaultBorder`|  
  
 **Flotante, sin foco**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Ventana de herramientas no enfocada](../extensibility/ux-guidelines/media/0303-091-toolwindowunfocused.png "0303-091_ToolWindowUnfocused")|Fondo|`Environment.ToolWindowBackground`|  
|![Ventana de herramientas no enfocada](../extensibility/ux-guidelines/media/0303-091-toolwindowunfocused.png "0303-091_ToolWindowUnfocused")|Borde|`Environment.MainWindowInactiveBorder`|  
  
#### <a name="tool-window-title-bar"></a>Barra de título de la ventana de herramientas  
 El borde de la barra de título no es realmente un borde, sino una línea gruesa en la parte superior de la barra de título. No tiene un nombre de token para su estado sin foco.  
  
 ![Límite de barra de título de ventana de herramienta](../extensibility/ux-guidelines/media/0303-092-toolwindowtitlebarredline.png "0303-092_ToolWindowTitleBarRedline")  
  
 Use…  
 en cualquier lugar donde cree interfaz de usuario que desea que coincida con la ventana de herramientas.  
  
 No use…  
 para cualquier interfaz de usuario que no desea que cambie automáticamente si se actualiza un tema del shell.  
  
 **Focused**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Barra de título enfocada](../extensibility/ux-guidelines/media/0303-093-titlebarfocused.png "0303-093_TitleBarFocused")<br /><br /> **Barra de título con foco**|Fondo|`Environment.TitleBarActiveGradientBegin`<br /><br /> Aunque no se usan en la interfaz de usuario moderna con temas, hay delimitadores de degradado y valores para este fondo.|  
|![Barra de título enfocada](../extensibility/ux-guidelines/media/0303-093-titlebarfocused.png "0303-093_TitleBarFocused")<br /><br /> **Barra de título con foco**|Primer plano (texto)|`Environment.TitleBarActiveText`|  
|![Barra de título enfocada](../extensibility/ux-guidelines/media/0303-093-titlebarfocused.png "0303-093_TitleBarFocused")<br /><br /> **Barra de título con foco**|Borde|`Environment.TitleBarActiveBorder`<br /><br /> Se establece en el mismo color que el fondo.|  
|![Barra de título enfocada](../extensibility/ux-guidelines/media/0303-093-titlebarfocused.png "0303-093_TitleBarFocused")<br /><br /> **Barra de título con foco**|Controlador de arrastre|`Environment.TitleBarDragHandleActive`|  
  
 **Sin foco**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Barra de título no enfocada](../extensibility/ux-guidelines/media/0303-094-titlebarunfocused.png "0303-094_TitleBarUnfocused")<br /><br /> **Barra de título sin foco**|Fondo|`Environment.TitleBarInactiveGradientBegin`<br /><br /> Aunque no se usan en la interfaz de usuario moderna con temas, hay delimitadores de degradado y valores para este fondo.|  
|![Barra de título no enfocada](../extensibility/ux-guidelines/media/0303-094-titlebarunfocused.png "0303-094_TitleBarUnfocused")<br /><br /> **Barra de título sin foco**|Primer plano (texto)|`Environment.TitleBarInactiveText`|  
|![Barra de título no enfocada](../extensibility/ux-guidelines/media/0303-094-titlebarunfocused.png "0303-094_TitleBarUnfocused")<br /><br /> **Barra de título sin foco**|Borde|N/D|  
|![Barra de título no enfocada](../extensibility/ux-guidelines/media/0303-094-titlebarunfocused.png "0303-094_TitleBarUnfocused")<br /><br /> **Barra de título sin foco**|Controlador de arrastre|`Environment.TitleBarDragHandle`|  
  
##### <a name="title-bar-buttons"></a>Botones de la barra de título  
 ![Límite de botón de la barra de título](../extensibility/ux-guidelines/media/0303-095-titlebarbuttonredline.png "0303-095_TitleBarButtonRedline")  
  
 Use…  
 para los botones que aparecen en la interfaz de usuario que usa los tokens de color de las barras de título de la ventana de herramientas.  
  
No use…  
- para los botones que aparecen en otras ubicaciones.  

- en cualquier combinación de primer plano y fondo distinta de la especificada.  
  
  **Valor predeterminado**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Botón de la barra de título enfocado](../extensibility/ux-guidelines/media/0303-096-titlebarbuttonfocused.png "0303-096_TitleBarButtonFocused")<br /><br /> **Focused**|Fondo|N/D|  
|![Botón de la barra de título enfocado](../extensibility/ux-guidelines/media/0303-096-titlebarbuttonfocused.png "0303-096_TitleBarButtonFocused")<br /><br /> **Focused**|Primer plano (glifo)|`Environment.ToolWindowButtonActiveGlyph`|  
|![Botón de la barra de título enfocado](../extensibility/ux-guidelines/media/0303-096-titlebarbuttonfocused.png "0303-096_TitleBarButtonFocused")<br /><br /> **Focused**|Borde|N/D|  
|![Botón de la barra de título no enfocado](../extensibility/ux-guidelines/media/0303-097-titlebarbuttonunfocused.png "0303-097_TitleBarButtonUnfocused")<br /><br /> **Sin foco**|Fondo|N/D|  
|![Botón de la barra de título no enfocado](../extensibility/ux-guidelines/media/0303-097-titlebarbuttonunfocused.png "0303-097_TitleBarButtonUnfocused")<br /><br /> **Sin foco**|Primer plano (glifo)|`Environment.ToolWindowButtonInactiveGlyph`|  
|![Botón de la barra de título no enfocado](../extensibility/ux-guidelines/media/0303-097-titlebarbuttonunfocused.png "0303-097_TitleBarButtonUnfocused")<br /><br /> **Sin foco**|Borde|N/D|  
  
 **Al mantener el puntero**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Botón de la barra de título enfocado al mantener el mouse](../extensibility/ux-guidelines/media/0303-098-titlebarbuttonfocusedhover.png "0303-098_TitleBarButtonFocusedHover")<br /><br /> **Focused**|Fondo|`Environment.ToolWindowButtonHoverActive`|  
|![Botón de la barra de título enfocado al mantener el mouse](../extensibility/ux-guidelines/media/0303-098-titlebarbuttonfocusedhover.png "0303-098_TitleBarButtonFocusedHover")<br /><br /> **Focused**|Primer plano (glifo)|`Environment.ToolWindowButtonHoverActiveGlyph`|  
|![Botón de la barra de título enfocado al mantener el mouse](../extensibility/ux-guidelines/media/0303-098-titlebarbuttonfocusedhover.png "0303-098_TitleBarButtonFocusedHover")<br /><br /> **Focused**|Borde|`Environment.ToolWindowButtonHoverActiveBorder`|  
|![Botón de la barra de título no enfocado al mantener el mouse](../extensibility/ux-guidelines/media/0303-099-titlebarbuttonunfocusedhover.png "0303-099_TitleBarButtonUnfocusedHover")<br /><br /> **Sin foco**|Fondo|`Environment.ToolWindowButtonHoverInactive`|  
|![Botón de la barra de título no enfocado al mantener el mouse](../extensibility/ux-guidelines/media/0303-099-titlebarbuttonunfocusedhover.png "0303-099_TitleBarButtonUnfocusedHover")<br /><br /> **Sin foco**|Primer plano (glifo)|`Environment.ToolWindowButtonHoverInactiveGlyph`|  
|![Botón de la barra de título no enfocado al mantener el mouse](../extensibility/ux-guidelines/media/0303-099-titlebarbuttonunfocusedhover.png "0303-099_TitleBarButtonUnfocusedHover")<br /><br /> **Sin foco**|Borde|`Environment.ToolWindowButtonHoverInactiveBorder`|  
  
 **Pressed**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Botón de la barra de título enfocado y presionado](../extensibility/ux-guidelines/media/0303-100-titlebarbuttonfocusedpressed.png "0303-100_TitleBarButtonFocusedPressed")<br /><br /> **Focused**|Fondo|`Environment.ToolWindowButtonDown`|  
|![Botón de la barra de título enfocado y presionado](../extensibility/ux-guidelines/media/0303-100-titlebarbuttonfocusedpressed.png "0303-100_TitleBarButtonFocusedPressed")<br /><br /> **Focused**|Primer plano (glifo)|`Environment.ToolWindowButtonDownActiveGlyph`|  
|![Botón de la barra de título enfocado y presionado](../extensibility/ux-guidelines/media/0303-100-titlebarbuttonfocusedpressed.png "0303-100_TitleBarButtonFocusedPressed")<br /><br /> **Focused**|Borde|`Environment.ToolWindowButtonDownBorder`|  
|![Botón de la barra de título no enfocado y presionado](../extensibility/ux-guidelines/media/0303-101-titlebarbuttonunfocusedpressed.png "0303-101_TitleBarButtonUnfocusedPressed")<br /><br /> **Sin foco**|Fondo|`Environment.ToolWindowButtonDown`|  
|![Botón de la barra de título no enfocado y presionado](../extensibility/ux-guidelines/media/0303-101-titlebarbuttonunfocusedpressed.png "0303-101_TitleBarButtonUnfocusedPressed")<br /><br /> **Sin foco**|Primer plano (glifo)|`Environment.ToolWindowButtonDownInactiveGlyph`|  
|![Botón de la barra de título no enfocado y presionado](../extensibility/ux-guidelines/media/0303-101-titlebarbuttonunfocusedpressed.png "0303-101_TitleBarButtonUnfocusedPressed")<br /><br /> **Sin foco**|Borde|`Environment.ToolWindowButtonDownBorder`|  
  
#### <a name="tool-window-tabs"></a>Pestañas de ventana de herramientas  
 ![Límite de pestaña de ventana de herramientas](../extensibility/ux-guidelines/media/0303-102-toolwindowtabredline.png "0303-102_ToolWindowTabRedline")  
  
 Use…  
 en cualquier lugar donde cree interfaz de usuario que desea que coincida con la ventana de herramientas.  
  
 No use…  
 para cualquier interfaz de usuario que no desea que cambie automáticamente si se actualiza un tema del shell.  
  
 **Pestaña seleccionada**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Pestaña de ventana de herramientas enfocada](../extensibility/ux-guidelines/media/0303-103-toolwindowtabfocused.png "0303-103_ToolWindowTabFocused")<br /><br /> **Pestaña de ventana de herramienta seleccionada, con foco**|Fondo|`Environment.ToolWindowTabSelectedTab`|  
|![Pestaña de ventana de herramientas enfocada](../extensibility/ux-guidelines/media/0303-103-toolwindowtabfocused.png "0303-103_ToolWindowTabFocused")<br /><br /> **Pestaña de ventana de herramienta seleccionada, con foco**|Primer plano (texto)|`Environment.ToolWindowTabSelectedActiveText`|  
|![Pestaña de ventana de herramientas enfocada](../extensibility/ux-guidelines/media/0303-103-toolwindowtabfocused.png "0303-103_ToolWindowTabFocused")<br /><br /> **Pestaña de ventana de herramienta seleccionada, con foco**|Borde|`Environment.ToolWindowTabSelectedBorder`<br /><br /> Se establece en el mismo color que el fondo.|  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Pestaña de ventana de herramientas no enfocada](../extensibility/ux-guidelines/media/0303-104-toolwindowtabunfocused.png "0303-104_ToolWindowTabUnfocused")<br /><br /> **Pestaña de ventana de herramienta seleccionada, sin foco**|Fondo|`Environment.ToolWindowTabSelectedTab`|  
|![Pestaña de ventana de herramientas no enfocada](../extensibility/ux-guidelines/media/0303-104-toolwindowtabunfocused.png "0303-104_ToolWindowTabUnfocused")<br /><br /> **Pestaña de ventana de herramienta seleccionada, sin foco**|Primer plano (texto)|`Environment.ToolWindowTabSelectedText`|  
|![Pestaña de ventana de herramientas no enfocada](../extensibility/ux-guidelines/media/0303-104-toolwindowtabunfocused.png "0303-104_ToolWindowTabUnfocused")<br /><br /> **Pestaña de ventana de herramienta seleccionada, sin foco**|Borde|`Environment.ToolWindowTabSelectedBorder`<br /><br /> Se establece en el mismo color que el fondo.|  
  
 **Pestaña en segundo plano**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Pestaña de ventana de herramientas en segundo plano](../extensibility/ux-guidelines/media/0303-105-toolwindowbackgroundtab.png "0303-105_ToolWindowBackgroundTab")<br /><br /> **Pestaña de ventana de herramientas en segundo plano**|Fondo|`Environment.ToolWindowTabGradientBegin`<br /><br /> Los delimitadores de degradado se establecen en el mismo valor de color en Visual Studio 2013.<br /><br /> `Environment.ToolWindowTabGradientEnd`<br /><br /> Los delimitadores de degradado se establecen en el mismo valor de color en Visual Studio 2013.|  
|![Pestaña de ventana de herramientas en segundo plano](../extensibility/ux-guidelines/media/0303-105-toolwindowbackgroundtab.png "0303-105_ToolWindowBackgroundTab")<br /><br /> **Pestaña de ventana de herramientas en segundo plano**|Primer plano (texto)|`Environment.ToolWindowTabText`|  
|![Pestaña de ventana de herramientas en segundo plano](../extensibility/ux-guidelines/media/0303-105-toolwindowbackgroundtab.png "0303-105_ToolWindowBackgroundTab")<br /><br /> **Pestaña de ventana de herramientas en segundo plano**|Borde|`Environment.ToolWindowTabBorder`|  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Pestaña de ventana de herramientas en segundo plano al mantener el mouse](../extensibility/ux-guidelines/media/0303-106-toolwindowbackgroundtabhover.png "0303-106_ToolWindowBackgroundTabHover")<br /><br /> **Pestaña de ventana de herramientas en segundo plano al mantener el puntero**|Fondo|`Environment.ToolWindowTabMouseOverBackgroundBegin`<br /><br /> Los delimitadores de degradado se establecen en el mismo valor de color en Visual Studio 2013.<br /><br /> `Environment.ToolWindowTabMouseOverBackgroundEnd`<br /><br /> Los delimitadores de degradado se establecen en el mismo valor de color en Visual Studio 2013.|  
|![Pestaña de ventana de herramientas en segundo plano al mantener el mouse](../extensibility/ux-guidelines/media/0303-106-toolwindowbackgroundtabhover.png "0303-106_ToolWindowBackgroundTabHover")<br /><br /> **Pestaña de ventana de herramientas en segundo plano al mantener el puntero**|Primer plano (texto)|`Environment.ToolWindowTabMouseOverText`|  
|![Pestaña de ventana de herramientas en segundo plano al mantener el mouse](../extensibility/ux-guidelines/media/0303-106-toolwindowbackgroundtabhover.png "0303-106_ToolWindowBackgroundTabHover")<br /><br /> **Pestaña de ventana de herramientas en segundo plano al mantener el puntero**|Borde|`Environment.ToolWindowTabMouseOverBorder`<br /><br /> Se establece en el mismo color que el fondo.|  
  
#### <a name="auto-hide-tabs"></a>Pestaña de ocultación automática  
 ![Auto&#45;ocultar la función de la roja](../extensibility/ux-guidelines/media/0303-107-autohideredline.png "0303-107_AutoHideRedline")  
  
 Use…  
 en cualquier lugar donde cree interfaz de usuario que desea que coincida con las pestañas de ventana de herramientas de ocultación automática.  
  
 No use…  
 para cualquier interfaz de usuario que no desea que cambie automáticamente si se actualiza un tema del shell.  
  
 **Valor predeterminado**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Ficha ocultar auto&#45;](../extensibility/ux-guidelines/media/0303-108-autohidetab.png "0303-108_AutoHideTab")<br /><br /> **Pestaña de ocultación automática predeterminada**|Fondo|`Environment.AutoHideTabBackgroundBegin`<br /><br /> Aunque no se usan en la interfaz de usuario moderna con temas, hay delimitadores de degradado y valores para este fondo.|  
|![Ficha ocultar auto&#45;](../extensibility/ux-guidelines/media/0303-108-autohidetab.png "0303-108_AutoHideTab")<br /><br /> **Pestaña de ocultación automática predeterminada**|Primer plano (texto)|`Environment.AutoHideTabText`|  
|![Ficha ocultar auto&#45;](../extensibility/ux-guidelines/media/0303-108-autohidetab.png "0303-108_AutoHideTab")<br /><br /> **Pestaña de ocultación automática predeterminada**|Borde|`Environment.AutoHideTabBorder`|  
  
 **Al mantener el puntero**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Ficha ocultar auto&#45;al mantener el mouse](../extensibility/ux-guidelines/media/0303-109-autohidetabhover.png "0303-109_AutoHideTabHover")<br /><br /> **Pestaña de ocultación automática al mantener el puntero**|Fondo|`Environment.AutoHideTabMouseOverBackgroundBegin`<br /><br /> Aunque no se usan en la interfaz de usuario moderna con temas, hay delimitadores de degradado y valores para este fondo.|  
|![Ficha ocultar auto&#45;al mantener el mouse](../extensibility/ux-guidelines/media/0303-109-autohidetabhover.png "0303-109_AutoHideTabHover")<br /><br /> **Pestaña de ocultación automática al mantener el puntero**|Primer plano (texto)|`Environment.AutoHideTabMouseOverText`|  
|![Ficha ocultar auto&#45;al mantener el mouse](../extensibility/ux-guidelines/media/0303-109-autohidetabhover.png "0303-109_AutoHideTabHover")<br /><br /> **Pestaña de ocultación automática al mantener el puntero**|Borde|`Environment.AutoHideTabMouseOverBorder`|  
  
### <a name="common-shared-controls"></a>Controles comunes compartidos  
 Si usa una barra de comandos estándar de Visual Studio en su característica, puede acceder a los controles de shell con estilo y no debe volver a basar en modelo estos controles comunes. Sin embargo, si necesita crear una barra de comandos personalizada, también podría ser necesario crear controles personalizados. En ese caso, asegúrese de usar los nombres de token correctos para cada uno de los siguientes controles de modo que la interfaz de usuario sea coherente con el resto de Visual Studio.  
  
#### <a name="search-box"></a>Cuadro de búsqueda  
 Siempre que sea posible, use el control de búsqueda común proporcionado por el entorno de Visual Studio. Los colores del cuadro de búsqueda se encuentran en la categoría "SearchControl" del archivo **ShellColors.pkgdef** , que contiene los nombres de token para el campo de entrada, el botón de acción, el botón desplegable y el menú desplegable.  
  
 Un cuadro de búsqueda puede tener uno de varios estados, algunos de los cuales son mutuamente excluyentes:  
  
- "Con foco" o "sin foco" se refiere a si el cursor está en el cuadro de texto.  
  
- "Activo" o "inactivo" se refiere a si el usuario ha especificado una consulta de búsqueda en el cuadro de texto.  
  
- "Desplazar el puntero" significa que el usuario ha colocado el puntero sobre el cuadro de búsqueda con el mouse (este estado invalida todos los demás estados).  
  
- "Deshabilitado" significa que la función de búsqueda se ha desactivado para el contexto actual.  
  
  ![Límite de cuadro de búsqueda](../extensibility/ux-guidelines/media/0303-110-searchboxredline.png "0303-110_SearchBoxRedline")  
  
  Use…  
  al diseñar un cuadro de búsqueda personalizado.  
  
  No use…  
  - para elementos que no sean un cuadro de búsqueda.  
  
- para elementos que no desea que siempre coincidan con la interfaz de usuario de búsqueda.  
  
  **Focused**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Campo de entrada de búsqueda enfocado](../extensibility/ux-guidelines/media/0303-111-searchinputfieldfocused.png "0303-111_SearchInputFieldFocused")<br /><br /> **Campo de entrada**|Fondo|`SearchControl.FocusedBackground`|  
|![Campo de entrada de búsqueda enfocado](../extensibility/ux-guidelines/media/0303-111-searchinputfieldfocused.png "0303-111_SearchInputFieldFocused")<br /><br /> **Campo de entrada**|Primer plano (texto)|`SearchControl.FocusedBackground`|  
|![Campo de entrada de búsqueda enfocado](../extensibility/ux-guidelines/media/0303-111-searchinputfieldfocused.png "0303-111_SearchInputFieldFocused")<br /><br /> **Campo de entrada**|Borde|`SearchControl.FocusedBorder`|  
|![Campo de entrada de búsqueda enfocado](../extensibility/ux-guidelines/media/0303-111-searchinputfieldfocused.png "0303-111_SearchInputFieldFocused")<br /><br /> **Campo de entrada**|Separador|`SearchControl.FocusedDropDownSeparator`|  
|![Botón de acción de búsqueda enfocado](../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303-112_SearchActionButtonFocused")<br /><br /> **Botón de acción**|Fondo|None|  
|![Botón de acción de búsqueda enfocado](../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303-112_SearchActionButtonFocused")<br /><br /> **Botón de acción**|Primer plano (glifo de búsqueda)|`SearchControl.SearchGlyph`|  
|![Botón de acción de búsqueda enfocado](../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303-112_SearchActionButtonFocused")<br /><br /> **Botón de acción**|Primer plano (glifo de detención)|`SearchControl.StopGlyph`|  
|![Botón de acción de búsqueda enfocado](../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303-112_SearchActionButtonFocused")<br /><br /> **Botón de acción**|Primer plano (glifo de borrado)|`SearchControl.ClearGlyph`|  
|![Botón de acción de búsqueda enfocado](../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303-112_SearchActionButtonFocused")<br /><br /> **Botón de acción**|Borde|N/D|  
|![Botón desplegable de&#45;de búsqueda centrado](../extensibility/ux-guidelines/media/0303-113-searchdropdownbuttonfocused.png "0303-113_SearchDropdownButtonFocused")<br /><br /> **Botón desplegable**|Fondo|`SearchControl.FocusedDropDownButton`|  
|![Botón desplegable de&#45;de búsqueda centrado](../extensibility/ux-guidelines/media/0303-113-searchdropdownbuttonfocused.png "0303-113_SearchDropdownButtonFocused")<br /><br /> **Botón desplegable**|Primer plano (glifo)|`SearchControl.FocusedDropDownButtonGlyph`|  
|![Botón desplegable de&#45;de búsqueda centrado](../extensibility/ux-guidelines/media/0303-113-searchdropdownbuttonfocused.png "0303-113_SearchDropdownButtonFocused")<br /><br /> **Botón desplegable**|Borde|`SearchControl.FocusedDropDownButtonBorder`|  
  
 **Sin foco**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Campo de entrada de búsqueda no enfocado](../extensibility/ux-guidelines/media/0303-114-searchinputfieldunfocused.png "0303-114_SearchInputFieldUnfocused")<br /><br /> **Campo de entrada activo**|Fondo|`SearchControl.SearchActiveBackground`|  
|![Campo de entrada de búsqueda no enfocado](../extensibility/ux-guidelines/media/0303-114-searchinputfieldunfocused.png "0303-114_SearchInputFieldUnfocused")<br /><br /> **Campo de entrada activo**|Primer plano (texto)|`SearchControl.SearchActiveBackground`|  
|![Campo de entrada de búsqueda no enfocado](../extensibility/ux-guidelines/media/0303-114-searchinputfieldunfocused.png "0303-114_SearchInputFieldUnfocused")<br /><br /> **Campo de entrada activo**|Borde|`SearchControl.UnfocusedBorder`|  
|![Campo de entrada de búsqueda no enfocado](../extensibility/ux-guidelines/media/0303-114-searchinputfieldunfocused.png "0303-114_SearchInputFieldUnfocused")<br /><br /> **Campo de entrada activo**|Separador|`SearchControl.DropDownSeparator`|  
|![Campo de entrada de búsqueda no enfocado e inactivo](../extensibility/ux-guidelines/media/0303-114-1-searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br /><br /> **Campo de entrada inactivo**|Fondo|`SearchControl.Unfocused`|  
|![Campo de entrada de búsqueda no enfocado e inactivo](../extensibility/ux-guidelines/media/0303-114-1-searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br /><br /> **Campo de entrada inactivo**|Primer plano (texto)|`SearchControl.Unfocused`|  
|![Campo de entrada de búsqueda no enfocado e inactivo](../extensibility/ux-guidelines/media/0303-114-1-searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br /><br /> **Campo de entrada inactivo**|Borde|`SearchControl.UnfocusedBorder`|  
|![Campo de entrada de búsqueda no enfocado e inactivo](../extensibility/ux-guidelines/media/0303-114-1-searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br /><br /> **Campo de entrada inactivo**|Separador|`SearchControl.DropDownSeparator`|  
|![Botón de acción de búsqueda no enfocado](../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303-115_SearchActionButtonUnfocused")<br /><br /> **Botón de acción**|Fondo|N/D|  
|![Botón de acción de búsqueda no enfocado](../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303-115_SearchActionButtonUnfocused")<br /><br /> **Botón de acción**|Primer plano (glifo de búsqueda)|`SearchControl.SearchGlyph`|  
|![Botón de acción de búsqueda no enfocado](../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303-115_SearchActionButtonUnfocused")<br /><br /> **Botón de acción**|Primer plano (glifo de detención)|`SearchControl.StopGlyph`|  
|![Botón de acción de búsqueda no enfocado](../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303-115_SearchActionButtonUnfocused")<br /><br /> **Botón de acción**|Primer plano (glifo de borrado)|`SearchControl.ClearGlyph`|  
|![Botón de acción de búsqueda no enfocado](../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303-115_SearchActionButtonUnfocused")<br /><br /> **Botón de acción**|Borde|N/D|  
|![Botón de&#45;de la lista desplegable de búsqueda no enfocado](../extensibility/ux-guidelines/media/0303-116-searchdropdownbuttonunfocused.png "0303-116_SearchDropdownButtonUnfocused")<br /><br /> **Botón desplegable**|Fondo|`SearchControl.UnfocusedDropDownButton`|  
|![Botón de&#45;de la lista desplegable de búsqueda no enfocado](../extensibility/ux-guidelines/media/0303-116-searchdropdownbuttonunfocused.png "0303-116_SearchDropdownButtonUnfocused")<br /><br /> **Botón desplegable**|Primer plano (glifo)|`SearchControl.UnfocusedDropDownButtonGlyph`|  
|![Botón de&#45;de la lista desplegable de búsqueda no enfocado](../extensibility/ux-guidelines/media/0303-116-searchdropdownbuttonunfocused.png "0303-116_SearchDropdownButtonUnfocused")<br /><br /> **Botón desplegable**|Borde|`SearchControl.UnfocusedDropDownButtonBorder`|  
  
 **Pressed**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Botón de acción de búsqueda presionado](../extensibility/ux-guidelines/media/0303-116-1-searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")<br /><br /> **Botón de acción**|Fondo|`SearchControl.ActionButtonMouseDown`|  
|![Botón de acción de búsqueda presionado](../extensibility/ux-guidelines/media/0303-116-1-searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")<br /><br /> **Botón de acción**|Primer plano (glifo)|`SearchControl.ActionButtonMouseDownGlyph`|  
|![Botón de acción de búsqueda presionado](../extensibility/ux-guidelines/media/0303-116-1-searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")<br /><br /> **Botón de acción**|Borde|`SearchControl.ActionButtonMouseDownBorder`|  
|![Botón desplegable de búsqueda&#45;presionado](../extensibility/ux-guidelines/media/0303-116-2-searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")<br /><br /> **Botón desplegable**|Fondo|`SearchControl.MouseDownDropDownButton`|  
|![Botón desplegable de búsqueda&#45;presionado](../extensibility/ux-guidelines/media/0303-116-2-searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")<br /><br /> **Botón desplegable**|Primer plano (glifo)|`SearchControl.MouseDownDropDownButtonGlyph`|  
|![Botón desplegable de búsqueda&#45;presionado](../extensibility/ux-guidelines/media/0303-116-2-searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")<br /><br /> **Botón desplegable**|Borde|`SearchControl.MouseDownDropDownButtonBorder`|  
  
 **Resaltado (solo texto)**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Campo de entrada de búsqueda resaltado](../extensibility/ux-guidelines/media/0303-120-searchinputfieldhighlight.png "0303-120_SearchInputFieldHighlight")<br /><br /> **Campo de entrada con texto resaltado**|Fondo|`SearchControl.Selection`|  
|![Campo de entrada de búsqueda resaltado](../extensibility/ux-guidelines/media/0303-120-searchinputfieldhighlight.png "0303-120_SearchInputFieldHighlight")<br /><br /> **Campo de entrada con texto resaltado**|Primer plano (texto)|`SearchControl.FocusedBackground`|  
|![Campo de entrada de búsqueda resaltado](../extensibility/ux-guidelines/media/0303-120-searchinputfieldhighlight.png "0303-120_SearchInputFieldHighlight")<br /><br /> **Campo de entrada con texto resaltado**|Borde|None|  
|![Campo de entrada de búsqueda resaltado](../extensibility/ux-guidelines/media/0303-120-searchinputfieldhighlight.png "0303-120_SearchInputFieldHighlight")<br /><br /> **Campo de entrada con texto resaltado**|Separador|`SearchControl.FocusedDropDownSeparator`|  
  
 **Deshabilitada**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Campo de entrada de búsqueda deshabilitado](../extensibility/ux-guidelines/media/0303-121-searchinputfielddisabled.png "0303-121_SearchInputFieldDisabled")<br /><br /> **Campo de entrada**|Fondo|`SearchControl.Disabled`|  
|![Campo de entrada de búsqueda deshabilitado](../extensibility/ux-guidelines/media/0303-121-searchinputfielddisabled.png "0303-121_SearchInputFieldDisabled")<br /><br /> **Campo de entrada**|Primer plano (texto)|`SearchControl.Disabled`|  
|![Campo de entrada de búsqueda deshabilitado](../extensibility/ux-guidelines/media/0303-121-searchinputfielddisabled.png "0303-121_SearchInputFieldDisabled")<br /><br /> **Campo de entrada**|Borde|`SearchControl.DisabledBorder`|  
|![Campo de entrada de búsqueda deshabilitado](../extensibility/ux-guidelines/media/0303-121-searchinputfielddisabled.png "0303-121_SearchInputFieldDisabled")<br /><br /> **Campo de entrada**|Separador|`SearchControl.DropDownSeparator`|  
|![Botón de acción de búsqueda deshabilitado](../extensibility/ux-guidelines/media/0303-122-searchactionbuttondisabled.png "0303-122_SearchActionButtonDisabled")<br /><br /> **Botón de acción**|Fondo|None|  
|![Botón de acción de búsqueda deshabilitado](../extensibility/ux-guidelines/media/0303-122-searchactionbuttondisabled.png "0303-122_SearchActionButtonDisabled")<br /><br /> **Botón de acción**|Primer plano (glifo)|`SearchControl.ActionButtonDisabledGlyph`|  
|![Botón de acción de búsqueda deshabilitado](../extensibility/ux-guidelines/media/0303-122-searchactionbuttondisabled.png "0303-122_SearchActionButtonDisabled")<br /><br /> **Botón de acción**|Borde|None|  
|![Botón desplegable Buscar&#45;deshabilitado](../extensibility/ux-guidelines/media/0303-123-searchdropdownbuttondisabled.png "0303-123_SearchDropdownButtonDisabled")<br /><br /> **Botón desplegable**|Fondo|None|  
|![Botón desplegable Buscar&#45;deshabilitado](../extensibility/ux-guidelines/media/0303-123-searchdropdownbuttondisabled.png "0303-123_SearchDropdownButtonDisabled")<br /><br /> **Botón desplegable**|Primer plano (glifo)|`SearchControl.DisabledDownButtonGlyph`|  
|![Botón desplegable Buscar&#45;deshabilitado](../extensibility/ux-guidelines/media/0303-123-searchdropdownbuttondisabled.png "0303-123_SearchDropdownButtonDisabled")<br /><br /> **Botón desplegable**|Borde|None|  
  
##### <a name="search-drop-down-lists"></a>Listas desplegables de búsqueda  
 El menú desplegable del cuadro de búsqueda puede ser ligeramente más complejo que otros menús desplegables en Visual Studio. Las secciones de "búsquedas sugeridas" y "opciones de búsqueda" pueden aparecer solas o juntas en el menú y cada una de ellas se colorea por separado. Además, estas secciones están separadas por una línea cuando aparecen juntas y un borde rodea todo el menú desplegable.  
  
 ![&#45;de la lista desplegable de búsqueda](../extensibility/ux-guidelines/media/0303-124-searchdropdownredline.png "0303-124_SearchDropdownRedline")  
  
Use…  
- si crea una lista desplegable de búsqueda personalizada.  

- los nombres de token correctos para los componentes de lista correctos.  

No use…  
- para las listas desplegables que aparecen en otros contextos.  

- en cualquier combinación de primer plano y fondo distinta de la especificada.  
  
  **Predeterminado (no hay otros estados)**  
  
|Elemento|Nombre del token: Category.color|  
|-------------|--------------------------------|  
|Borde|`SearchControl.PopupBorder`|  
|Separador|`SearchControl.PopupSectionHeaderSeparator`|  
|Shadow|`Environment.DropShadowBackground`|  
  
 **Valor predeterminado**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Búsqueda sugerida](../extensibility/ux-guidelines/media/0303-125-searchsuggested.png "0303-125_SearchSuggested")<br /><br /> **Búsquedas sugeridas**|Fondo|`SearchControl.PopupItemsListBackgroundGradientBegin`<br /><br /> Aunque no se usan en la interfaz de usuario moderna con temas, hay delimitadores de degradado y valores para este fondo.|  
|![Búsqueda sugerida](../extensibility/ux-guidelines/media/0303-125-searchsuggested.png "0303-125_SearchSuggested")<br /><br /> **Búsquedas sugeridas**|Primer plano (texto)|`SearchControl.PopupItemText`|  
|![Casilla de verificación de búsqueda](../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303-126_SearchCheckbox")<br /><br /> **Opciones de búsqueda (casilla)**|Fondo|`SearchControl.PopupSectionBackgroundGradientBegin`<br /><br /> Aunque no se usan en la interfaz de usuario moderna con temas, hay delimitadores de degradado y valores para este fondo.|  
|![Opciones de búsqueda](../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303-127_SearchOptions")<br /><br /> **Opciones de búsqueda (vínculo)**|Fondo|`SearchControl.PopupSectionBackgroundGradientBegin`<br /><br /> Aunque no se usan en la interfaz de usuario moderna con temas, hay delimitadores de degradado y valores para este fondo.|  
|![Casilla de verificación de búsqueda](../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303-126_SearchCheckbox")<br /><br /> **Opciones de búsqueda (casilla)**|Primer plano (texto de casilla)|`SearchControl.PopupCheckboxText`|  
|![Opciones de búsqueda](../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303-127_SearchOptions")<br /><br /> **Opciones de búsqueda (vínculo)**|Primer plano (texto de casilla)|`SearchControl.PopupCheckboxText`|  
|![Casilla de verificación de búsqueda](../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303-126_SearchCheckbox")<br /><br /> **Opciones de búsqueda (casilla)**|Primer plano (texto de vínculo)|`SearchControl.PopupButtonText`|  
|![Opciones de búsqueda](../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303-127_SearchOptions")<br /><br /> **Opciones de búsqueda (vínculo)**|Primer plano (texto de vínculo)|`SearchControl.PopupButtonText`|  
|![Casilla de verificación de búsqueda](../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303-126_SearchCheckbox")<br /><br /> **Opciones de búsqueda (casilla)**|Fondo de encabezado|`SearchControl.PopupSectionHeaderGradientBegin`<br /><br /> Aunque no se usan en la interfaz de usuario moderna con temas, hay delimitadores de degradado y valores para este fondo.|  
|![Opciones de búsqueda](../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303-127_SearchOptions")<br /><br /> **Opciones de búsqueda (vínculo)**|Fondo de encabezado|`SearchControl.PopupSectionHeaderGradientBegin`<br /><br /> Aunque no se usan en la interfaz de usuario moderna con temas, hay delimitadores de degradado y valores para este fondo.|  
|![Casilla de verificación de búsqueda](../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303-126_SearchCheckbox")<br /><br /> **Opciones de búsqueda (casilla)**|Primer plano (texto de encabezado)|`SearchControl.PopupSectionHeaderText`|  
|![Opciones de búsqueda](../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303-127_SearchOptions")<br /><br /> **Opciones de búsqueda (vínculo)**|Primer plano (texto de encabezado)|`SearchControl.PopupSectionHeaderText`|  
  
 **Al mantener el puntero**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Búsqueda sugerida al mantener el mouse](../extensibility/ux-guidelines/media/0303-128-searchsuggestedhover.png "0303-128_SearchSuggestedHover")<br /><br /> **Búsquedas sugeridas**|Fondo|`SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br /><br /> Aunque no se usan en la interfaz de usuario moderna con temas, hay delimitadores de degradado y valores para este fondo.|  
|![Búsqueda sugerida al mantener el mouse](../extensibility/ux-guidelines/media/0303-128-searchsuggestedhover.png "0303-128_SearchSuggestedHover")<br /><br /> **Búsquedas sugeridas**|Primer plano (texto)|`SearchControl.PopupMouseOverItemText`|  
|![Búsqueda sugerida al mantener el mouse](../extensibility/ux-guidelines/media/0303-128-searchsuggestedhover.png "0303-128_SearchSuggestedHover")<br /><br /> **Búsquedas sugeridas**|Borde|`SearchControl.PopupControlMouseOverBorder`|  
|![Casilla de verificación de búsqueda al mantener el mouse](../extensibility/ux-guidelines/media/0303-129-searchcheckboxhover.png "0303-129_SearchCheckboxHover")<br /><br /> **Búsquedas sugeridas (casilla)**|Fondo|`SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br /><br /> Aunque no se usan en la interfaz de usuario moderna con temas, hay delimitadores de degradado y valores para este fondo.|  
|![Opciones de búsqueda al mantener el mouse](../extensibility/ux-guidelines/media/0303-130-searchoptionshover.png "0303-130_SearchOptionsHover")<br /><br /> **Opciones de búsqueda**|Fondo|`SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br /><br /> Aunque no se usan en la interfaz de usuario moderna con temas, hay delimitadores de degradado y valores para este fondo.|  
|![Casilla de verificación de búsqueda al mantener el mouse](../extensibility/ux-guidelines/media/0303-129-searchcheckboxhover.png "0303-129_SearchCheckboxHover")<br /><br /> **Búsquedas sugeridas (casilla)**|Primer plano (texto de casilla)|`SearchControl.PopupCheckboxMouseDownText`|  
|![Opciones de búsqueda al mantener el mouse](../extensibility/ux-guidelines/media/0303-130-searchoptionshover.png "0303-130_SearchOptionsHover")<br /><br /> **Opciones de búsqueda**|Primer plano (texto de casilla)|`SearchControl.PopupCheckboxMouseDownText`|  
|![Casilla de verificación de búsqueda al mantener el mouse](../extensibility/ux-guidelines/media/0303-129-searchcheckboxhover.png "0303-129_SearchCheckboxHover")<br /><br /> **Búsquedas sugeridas (casilla)**|Primer plano (texto de vínculo)|`SearchControl.PopupButtonMouseDownText`|  
|![Opciones de búsqueda al mantener el mouse](../extensibility/ux-guidelines/media/0303-130-searchoptionshover.png "0303-130_SearchOptionsHover")<br /><br /> **Opciones de búsqueda**|Primer plano (texto de vínculo)|`SearchControl.PopupButtonMouseDownText`|  
|![Casilla de verificación de búsqueda al mantener el mouse](../extensibility/ux-guidelines/media/0303-129-searchcheckboxhover.png "0303-129_SearchCheckboxHover")<br /><br /> **Búsquedas sugeridas (casilla)**|Borde|`SearchControl.PopupControlMouseOverBorder`|  
|![Opciones de búsqueda al mantener el mouse](../extensibility/ux-guidelines/media/0303-130-searchoptionshover.png "0303-130_SearchOptionsHover")<br /><br /> **Opciones de búsqueda**|Borde|`SearchControl.PopupControlMouseOverBorder`|  
  
 **Pressed**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Búsqueda sugerida presionada](../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303-131_SearchSuggestedPressed")<br /><br /> **Búsquedas sugeridas (casilla)**|Fondo de casilla|`SearchControl.PopupControlMouseDownBackgroundGradientBegin`<br /><br /> Aunque no se usan en la interfaz de usuario moderna con temas, hay delimitadores de degradado y valores para este fondo.|  
|![Opciones de búsqueda presionadas](../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303-132_SearchOptionsPressed")<br /><br /> **Opciones de búsqueda**|Fondo de casilla|`SearchControl.PopupControlMouseDownBackgroundGradientBegin`<br /><br /> Aunque no se usan en la interfaz de usuario moderna con temas, hay delimitadores de degradado y valores para este fondo.|  
|![Búsqueda sugerida presionada](../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303-131_SearchSuggestedPressed")<br /><br /> **Búsquedas sugeridas (casilla)**|Fondo de casilla|`SearchControl.PopupControlMouseDownBackgroundGradientEnd`<br /><br /> Aunque no se usan en la interfaz de usuario moderna con temas, hay delimitadores de degradado y valores para este fondo.|  
|![Opciones de búsqueda presionadas](../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303-132_SearchOptionsPressed")<br /><br /> **Opciones de búsqueda**|Fondo de casilla|`SearchControl.PopupControlMouseDownBackgroundGradientEnd`<br /><br /> Aunque no se usan en la interfaz de usuario moderna con temas, hay delimitadores de degradado y valores para este fondo.|  
|![Búsqueda sugerida presionada](../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303-131_SearchSuggestedPressed")<br /><br /> **Búsquedas sugeridas (casilla)**|Primer plano (texto de casilla)|`SearchControl.PopupCheckboxMouseDownText`|  
|![Opciones de búsqueda presionadas](../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303-132_SearchOptionsPressed")<br /><br /> **Opciones de búsqueda**|Primer plano (texto de casilla)|`SearchControl.PopupCheckboxMouseDownText`|  
|![Búsqueda sugerida presionada](../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303-131_SearchSuggestedPressed")<br /><br /> **Búsquedas sugeridas (casilla)**|Fondo de vínculo|`SearchControl.PopupButtonMouseDownBackgroundGradientBegin`<br /><br /> Aunque no se usan en la interfaz de usuario moderna con temas, hay delimitadores de degradado y valores para este fondo.|  
|![Opciones de búsqueda presionadas](../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303-132_SearchOptionsPressed")<br /><br /> **Opciones de búsqueda**|Fondo de vínculo|`SearchControl.PopupButtonMouseDownBackgroundGradientBegin`<br /><br /> Aunque no se usan en la interfaz de usuario moderna con temas, hay delimitadores de degradado y valores para este fondo.|  
|![Búsqueda sugerida presionada](../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303-131_SearchSuggestedPressed")<br /><br /> **Búsquedas sugeridas (casilla)**|Primer plano (texto de vínculo)|`SearchControl.PopupButtonMouseDownText`|  
|![Opciones de búsqueda presionadas](../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303-132_SearchOptionsPressed")<br /><br /> **Opciones de búsqueda**|Primer plano (texto de vínculo)|`SearchControl.PopupButtonMouseDownText`|  
  
#### <a name="hyperlink"></a>Hyperlink  
 El hipervínculo es un control que no tiene un par de primer plano y fondo. En todos los casos, use el color de hipervínculo de primer plano, que se muestre adecuadamente en fondos oscuros, grises y blancos. Si no usa el token de color para el control de hipervínculo, verá el color predeterminado del sistema para el estado Presionado, que parpadeará en rojo. Esa es la señal de que no se está usando el token de color correcto del entorno para el control.  
  
 ![Límite de hipervínculo](../extensibility/ux-guidelines/media/0303-133-hyperlinkredline.png "0303-133_HyperlinkRedline")  
  
 Use…  
 si es necesario crear un hipervínculo personalizado.  
  
 No use…  
 para elementos que no sean un hipervínculo.  
  
 **Valor predeterminado**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Hipervínculo predeterminado](../extensibility/ux-guidelines/media/0303-134-hyperlink.png "0303-134_Hyperlink")|Primer plano (texto)|`Environment.PanelHyperlink`|  
  
 **Al mantener el puntero**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Hipervínculo al mantener el mouse](../extensibility/ux-guidelines/media/0303-135-hyperlinkhover.png "0303-135_HyperlinkHover")|Primer plano (texto)|`Environment.PanelHyperlinkHover`|  
  
 **Pressed**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Hipervínculo presionado](../extensibility/ux-guidelines/media/0303-136-hyperlinkpressed.png "0303-136_HyperlinkPressed")|Primer plano (texto)|`Environment.PanelHyperlinkPressed`|  
  
 **Deshabilitada**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Hipervínculo deshabilitado](../extensibility/ux-guidelines/media/0303-137-hyperlinkdisabled.png "0303-137_HyperlinkDisabled")|Primer plano (texto)|`Environment.PanelHyperlinkDisabled`|  
  
#### <a name="infobar"></a>Barra de información  
 Las barras de información se usan para proporcionar más información sobre un determinado contexto y siempre se muestran en la parte superior de una ventana de documento o una ventana de herramientas.  
  
 ![Límite de barra de información](../extensibility/ux-guidelines/media/0303-138-infobarredline.png "0303-138_InfobarRedline")  
  
 Use…  
 al crear barras de información personalizadas.  
  
 No use…  
 para elementos de interfaz de usuario que no sean similares a una barra de información.  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Barra de información](../extensibility/ux-guidelines/media/0303-139-infobar.png "0303-139_Infobar")<br /><br /> **Barra de información**|Fondo|`Environment.InfoBackground`|  
|![Barra de información](../extensibility/ux-guidelines/media/0303-139-infobar.png "0303-139_Infobar")<br /><br /> **Barra de información**|Primer plano (texto)|`Environment.InfoText`|  
|![Barra de información](../extensibility/ux-guidelines/media/0303-139-infobar.png "0303-139_Infobar")<br /><br /> **Barra de información**|Borde|`Environment.ToolWindowBorder`|  
  
#### <a name="scroll-bar"></a>Barra de desplazamiento  
 Las barras de desplazamiento reciben el estilo del entorno de Visual Studio y no es necesario aplicarles un tema. Sin embargo, puede decidir que desea aprovechar los colores que se usan en las barras de desplazamiento para que la interfaz de usuario siempre parezca coherente con esta parte del entorno de Visual Studio.  
  
 ![Límite de barra de desplazamiento](../extensibility/ux-guidelines/media/0303-140-scrollbarredline.png "0303-140_ScrollbarRedline")  
  
 Use…  
 si crea interfaz de usuario que quiere hacer coincidir con las barras de desplazamiento de Visual Studio.  
  
 No use…  
 para cualquier elemento que no desea que siempre coincida con la interfaz de usuario de la barra de desplazamiento.  
  
 **Valor predeterminado**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Barra de desplazamiento](../extensibility/ux-guidelines/media/0303-141-scrollbar.png "0303-141_Scrollbar")<br /><br /> **Desplazamiento**|Barra de desplazamiento|`Environment.ScrollBarBackground`|  
|![Barra de desplazamiento](../extensibility/ux-guidelines/media/0303-141-scrollbar.png "0303-141_Scrollbar")<br /><br /> **Desplazamiento**|Primer plano (control)|`Environment.ScrollBarThumbBackground`|  
|![Flecha de barra de desplazamiento](../extensibility/ux-guidelines/media/0303-142-scrollbararrow.png "0303-142_ScrollbarArrow")<br /><br /> **Flecha de desplazamiento**|Fondo|`Environment.ScrollBarArrowBackground`<br /><br /> Se establece en el mismo color que la barra de desplazamiento.|  
|![Flecha de barra de desplazamiento](../extensibility/ux-guidelines/media/0303-142-scrollbararrow.png "0303-142_ScrollbarArrow")<br /><br /> **Flecha de desplazamiento**|Primer plano (glifo)|`Environment.ScrollBarArrowGlyph`|  
  
 **Al mantener el puntero**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Barra de desplazamiento al mantener el mouse](../extensibility/ux-guidelines/media/0303-143-scrollbarhover.png "0303-143_ScrollbarHover")<br /><br /> **Desplazamiento**|Barra de desplazamiento|`Environment.ScrollBarBackground`|  
|![Barra de desplazamiento al mantener el mouse](../extensibility/ux-guidelines/media/0303-143-scrollbarhover.png "0303-143_ScrollbarHover")<br /><br /> **Desplazamiento**|Primer plano (control)|`Environment.ScrollBarThumbMouseOverBackground`|  
|![Flecha de barra de desplazamiento al mantener el mouse](../extensibility/ux-guidelines/media/0303-144-scrollbararrowhover.png "0303-144_ScrollbarArrowHover")<br /><br /> **Flecha de desplazamiento**|Fondo|`Environment.ScrollBarArrowMouseOverBackground`<br /><br /> Se establece en el mismo color que la barra de desplazamiento.|  
|![Flecha de barra de desplazamiento al mantener el mouse](../extensibility/ux-guidelines/media/0303-144-scrollbararrowhover.png "0303-144_ScrollbarArrowHover")<br /><br /> **Flecha de desplazamiento**|Primer plano (glifo)|`Environment.ScrollBarArrowGlyphMouseOver`|  
  
 **Pressed**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Barra de desplazamiento presionada](../extensibility/ux-guidelines/media/0303-145-scrollbarpressed.png "0303-145_ScrollbarPressed")<br /><br /> **Desplazamiento**|Barra de desplazamiento|`Environment.ScrollBarBackground`|  
|![Barra de desplazamiento presionada](../extensibility/ux-guidelines/media/0303-145-scrollbarpressed.png "0303-145_ScrollbarPressed")<br /><br /> **Desplazamiento**|Primer plano (control)|`Environment.ScrollBarThumbPressedBackground`|  
|![Flecha de la barra de desplazamiento presionada](../extensibility/ux-guidelines/media/0303-146-scrollbararrowpressed.png "0303-146_ScrollbarArrowPressed")<br /><br /> **Flecha de desplazamiento**|Fondo|`Environment.ScrollBarArrowPressedBackground`<br /><br /> Se establece en el mismo color que la barra de desplazamiento.|  
|![Flecha de la barra de desplazamiento presionada](../extensibility/ux-guidelines/media/0303-146-scrollbararrowpressed.png "0303-146_ScrollbarArrowPressed")<br /><br /> **Flecha de desplazamiento**|Primer plano (glifo)|`Environment.ScrollBarArrowGlyphPressed`|  
  
#### <a name="tree-view"></a><a name="BKMK_TreeView"></a>Vista de árbol  
 Varias ventanas de herramientas, incluidos el Explorador de soluciones, el Explorador de servidores y la Vista de clases, implementan un esquema organizativo jerárquico cuyos colores se controlan mediante los nombres de colores de la categoría TreeView. Todos los elementos de una vista de árbol tienen colores de fondo y de texto. Los elementos que tienen elementos secundarios anidados también tienen glifos que indican si el elemento está expandido o contraído.  
  
 ![Límite de vista de árbol](../extensibility/ux-guidelines/media/0303-147-treeviewredline.png "0303-147_TreeViewRedline")  
  
 Use…  
 en cualquier lugar en el que es necesario implementar una vista organizativa jerárquica.  
  
No use…  
- para cualquier elemento que no sea similar a una vista de árbol.  

- en cualquier combinación de primer plano y fondo distinta de la especificada.  
  
  **Valor predeterminado**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Vista de árbol](../extensibility/ux-guidelines/media/0303-148-treeview.png "0303-148_TreeView")|Fondo|`TreeView.Background`|  
|![Vista de árbol](../extensibility/ux-guidelines/media/0303-148-treeview.png "0303-148_TreeView")|Primer plano (texto)|`TreeView.Background`|  
|![Vista de árbol](../extensibility/ux-guidelines/media/0303-148-treeview.png "0303-148_TreeView")|Primer plano (glifo)|`TreeView.Glyph`|  
|![Vista de árbol](../extensibility/ux-guidelines/media/0303-148-treeview.png "0303-148_TreeView")|Borde|None|  
  
 **Al mantener el puntero**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Vista de árbol al mantener el mouse](../extensibility/ux-guidelines/media/0303-149-treeviewhover.png "0303-149_TreeViewHover")|Fondo|`TreeView.Background`|  
|![Vista de árbol al mantener el mouse](../extensibility/ux-guidelines/media/0303-149-treeviewhover.png "0303-149_TreeViewHover")|Primer plano (texto)|`TreeView.Background`|  
|![Vista de árbol al mantener el mouse](../extensibility/ux-guidelines/media/0303-149-treeviewhover.png "0303-149_TreeViewHover")|Primer plano (glifo)|`TreeView.GlyphMouseOver`|  
|![Vista de árbol al mantener el mouse](../extensibility/ux-guidelines/media/0303-149-treeviewhover.png "0303-149_TreeViewHover")|Borde|None|  
  
 **Al arrastrar por encima**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Vista de árbol al arrastrar](../extensibility/ux-guidelines/media/0303-150-treeviewdragover.png "0303-150_TreeViewDragOver")|Fondo|`TreeView.DragOverItem`|  
|![Vista de árbol al arrastrar](../extensibility/ux-guidelines/media/0303-150-treeviewdragover.png "0303-150_TreeViewDragOver")|Primer plano (texto)|`TreeView.DragOverItem`|  
|![Vista de árbol al arrastrar](../extensibility/ux-guidelines/media/0303-150-treeviewdragover.png "0303-150_TreeViewDragOver")|Primer plano (glifo)|`TreeView.DragOverItemGlyph`|  
|![Vista de árbol al arrastrar](../extensibility/ux-guidelines/media/0303-150-treeviewdragover.png "0303-150_TreeViewDragOver")|Borde|None|  
  
 **Selected**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Vista de árbol enfocada](../extensibility/ux-guidelines/media/0303-151-treeviewfocused.png "0303-151_TreeViewFocused")<br /><br /> **Focused**|Fondo|`TreeView.SelectedItemActive`|  
|![Vista de árbol enfocada](../extensibility/ux-guidelines/media/0303-151-treeviewfocused.png "0303-151_TreeViewFocused")<br /><br /> **Focused**|Primer plano (texto)|`TreeView.SelectedItemActive`|  
|![Vista de árbol enfocada](../extensibility/ux-guidelines/media/0303-151-treeviewfocused.png "0303-151_TreeViewFocused")<br /><br /> **Focused**|Primer plano (glifo)|`TreeView.SelectedItemActiveGlyph`|  
|![Vista de árbol enfocada](../extensibility/ux-guidelines/media/0303-151-treeviewfocused.png "0303-151_TreeViewFocused")<br /><br /> **Focused**|Borde|`TreeView.FocusVisualBorder`|  
|![Vista de árbol no enfocada](../extensibility/ux-guidelines/media/0303-152-treeviewunfocused.png "0303-152_TreeViewUnfocused")<br /><br /> **Sin foco**|Fondo|`TreeView.SelectedItemInactive`|  
|![Vista de árbol no enfocada](../extensibility/ux-guidelines/media/0303-152-treeviewunfocused.png "0303-152_TreeViewUnfocused")<br /><br /> **Sin foco**|Primer plano (texto)|`TreeView.SelectedItemInactive`|  
|![Vista de árbol no enfocada](../extensibility/ux-guidelines/media/0303-152-treeviewunfocused.png "0303-152_TreeViewUnfocused")<br /><br /> **Sin foco**|Primer plano (glifo)|`TreeView.SelectedItemInactiveGlyph`|  
|![Vista de árbol no enfocada](../extensibility/ux-guidelines/media/0303-152-treeviewunfocused.png "0303-152_TreeViewUnfocused")<br /><br /> **Sin foco**|Borde|None|  
  
 **Al mantener el puntero sobre la selección**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Vista de árbol enfocada al mantener el mouse](../extensibility/ux-guidelines/media/0303-153-treeviewfocusedhover.png "0303-153_TreeViewFocusedHover")<br /><br /> **Focused**|Fondo|`TreeView.SelectedItemActive`|  
|![Vista de árbol enfocada al mantener el mouse](../extensibility/ux-guidelines/media/0303-153-treeviewfocusedhover.png "0303-153_TreeViewFocusedHover")<br /><br /> **Focused**|Primer plano (texto)|`TreeView.SelectedItemActive`|  
|![Vista de árbol enfocada al mantener el mouse](../extensibility/ux-guidelines/media/0303-153-treeviewfocusedhover.png "0303-153_TreeViewFocusedHover")<br /><br /> **Focused**|Primer plano (glifo)|`TreeView.SelectedItemActiveGlyphMouseOver`|  
|![Vista de árbol enfocada al mantener el mouse](../extensibility/ux-guidelines/media/0303-153-treeviewfocusedhover.png "0303-153_TreeViewFocusedHover")<br /><br /> **Focused**|Borde|Ninguno`TreeView.FocusVisualBorder`|  
|![Vista de árbol no enfocada al mantener el mouse](../extensibility/ux-guidelines/media/0303-154-treeviewunfocusedhover.png "0303-154_TreeViewUnfocusedHover")<br /><br /> **Sin foco**|Fondo|`TreeView.SelectedItemInactive`|  
|![Vista de árbol no enfocada al mantener el mouse](../extensibility/ux-guidelines/media/0303-154-treeviewunfocusedhover.png "0303-154_TreeViewUnfocusedHover")<br /><br /> **Sin foco**|Primer plano (texto)|`TreeView.SelectedItemInactive`|  
|![Vista de árbol no enfocada al mantener el mouse](../extensibility/ux-guidelines/media/0303-154-treeviewunfocusedhover.png "0303-154_TreeViewUnfocusedHover")<br /><br /> **Sin foco**|Primer plano (glifo)|`TreeView.SelectedItemActiveGlyphMouseOver`|  
|![Vista de árbol no enfocada al mantener el mouse](../extensibility/ux-guidelines/media/0303-154-treeviewunfocusedhover.png "0303-154_TreeViewUnfocusedHover")<br /><br /> **Sin foco**|Borde|None|  
  
#### <a name="button-controls"></a>Controles de botón  
 ![Límite de control de botón](../extensibility/ux-guidelines/media/0303-155-buttoncontrolredline.png "0303-155_ButtonControlRedline")  
  
 Use…  
 para los botones del cuadro de documento que quiere integrar con los temas de Visual Studio (claro, oscuro, azul o un tema de contraste alto del sistema).  
  
 No use…  
 para los botones que se mostrarán con un fondo personalizado que no forma parte de un tema de Visual Studio.  
  
 **Valor predeterminado**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Botón](../extensibility/ux-guidelines/media/0303-156-button.png "0303-156_Button")|Botón|`CommonControls.Button`|  
|![Botón](../extensibility/ux-guidelines/media/0303-156-button.png "0303-156_Button")|Borde de botón|`CommonControls.ButtonBorder`|  
  
 **Deshabilitada**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Botón deshabilitado](../extensibility/ux-guidelines/media/0303-157-buttondisabled.png "0303-157_ButtonDisabled")|Botón|`CommonControls.ButtonDisabled`|  
|![Botón deshabilitado](../extensibility/ux-guidelines/media/0303-157-buttondisabled.png "0303-157_ButtonDisabled")|Borde de botón|`CommonControls.ButtonBorderDisabled`|  
  
 **Al mantener el puntero**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Botón al mantener el mouse](../extensibility/ux-guidelines/media/0303-158-buttonhover.png "0303-158_ButtonHover")|Botón|`CommonControls.ButtonHover`|  
|![Botón al mantener el mouse](../extensibility/ux-guidelines/media/0303-158-buttonhover.png "0303-158_ButtonHover")|Borde de botón|`CommonControls.ButtonBorderHover`|  
  
 **Pressed**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Botón presionado](../extensibility/ux-guidelines/media/0303-159-buttonpressed.png "0303-159_ButtonPressed")|Botón|`CommonControls.ButtonPressed`|  
|![Botón presionado](../extensibility/ux-guidelines/media/0303-159-buttonpressed.png "0303-159_ButtonPressed")|Borde de botón|`CommonControls.ButtonBorderPressed`|  
  
 **Focused**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Botón enfocado](../extensibility/ux-guidelines/media/0303-160-buttonfocused.png "0303-160_ButtonFocused")|Botón|`CommonControls.ButtonFocused`|  
|![Botón enfocado](../extensibility/ux-guidelines/media/0303-160-buttonfocused.png "0303-160_ButtonFocused")|Borde de botón|`CommonControls.ButtonBorderFocused`|  
  
#### <a name="check-box-controls"></a>Controles de casilla  
 ![Límite de casilla de verificación](../extensibility/ux-guidelines/media/0303-161-checkboxredline.png "0303-161_CheckboxRedline")  
  
 Use…  
 para los controles de casilla incluidos en el cuadro de documento.  
  
 No use…  
 para cualquier interfaz de usuario que no sea un control de casilla.  
  
 **Valor predeterminado**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Casilla](../extensibility/ux-guidelines/media/0303-162-checkbox.png "0303-162_Checkbox")|Fondo|`CommonControls.CheckBoxBackground`|  
|![Casilla](../extensibility/ux-guidelines/media/0303-162-checkbox.png "0303-162_Checkbox")|Borde|`CommonControls.CheckBoxBorder`|  
|![Casilla](../extensibility/ux-guidelines/media/0303-162-checkbox.png "0303-162_Checkbox")|Text|`CommonControls.CheckBoxText`|  
|![Casilla](../extensibility/ux-guidelines/media/0303-162-checkbox.png "0303-162_Checkbox")|Glifo|`CommonControls.CheckBoxGlyph`|  
  
 **Deshabilitada**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Casilla de verificación deshabilitada](../extensibility/ux-guidelines/media/0303-163-checkboxdisabled.png "0303-163_CheckboxDisabled")|Fondo|`CommonControls.CheckBoxBackgroundDisabled`|  
|![Casilla de verificación deshabilitada](../extensibility/ux-guidelines/media/0303-163-checkboxdisabled.png "0303-163_CheckboxDisabled")|Borde|`CommonControls.CheckBoxBorderDisabled`|  
|![Casilla de verificación deshabilitada](../extensibility/ux-guidelines/media/0303-163-checkboxdisabled.png "0303-163_CheckboxDisabled")|Text|`CommonControls.CheckBoxTextDisabled`|  
|![Casilla de verificación deshabilitada](../extensibility/ux-guidelines/media/0303-163-checkboxdisabled.png "0303-163_CheckboxDisabled")|Glifo|`CommonControls.CheckBoxGlyphDisabled`|  
  
 **Al mantener el puntero**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Casilla de verificación al mantener el mouse](../extensibility/ux-guidelines/media/0303-164-checkboxhover.png "0303-164_CheckboxHover")|Fondo|`CommonControls.CheckBoxBackgroundHover`|  
|![Casilla de verificación al mantener el mouse](../extensibility/ux-guidelines/media/0303-164-checkboxhover.png "0303-164_CheckboxHover")|Borde|`CommonControls.CheckBoxBorderHover`|  
|![Casilla de verificación al mantener el mouse](../extensibility/ux-guidelines/media/0303-164-checkboxhover.png "0303-164_CheckboxHover")|Text|`CommonControls.CheckBoxTextHover`|  
|![Casilla de verificación al mantener el mouse](../extensibility/ux-guidelines/media/0303-164-checkboxhover.png "0303-164_CheckboxHover")|Glifo|`CommonControls.CheckBoxGlyphHover`|  
  
 **Pressed**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Casilla de verificación presionada](../extensibility/ux-guidelines/media/0303-165-checkboxpressed.png "0303-165_CheckboxPressed")|Fondo|`CommonControls.CheckBoxBackgroundPressed`|  
|![Casilla de verificación presionada](../extensibility/ux-guidelines/media/0303-165-checkboxpressed.png "0303-165_CheckboxPressed")|Borde|`CommonControls.CheckBoxBorderPressed`|  
|![Casilla de verificación presionada](../extensibility/ux-guidelines/media/0303-165-checkboxpressed.png "0303-165_CheckboxPressed")|Text|`CommonControls.CheckBoxTextPressed`|  
|![Casilla de verificación presionada](../extensibility/ux-guidelines/media/0303-165-checkboxpressed.png "0303-165_CheckboxPressed")|Glifo|`CommonControls.CheckBoxGlyphPressed`|  
  
 **Focused**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Casilla de verificación enfocada](../extensibility/ux-guidelines/media/0303-166-checkboxfocused.png "0303-166_CheckboxFocused")|Fondo|`CommonControls.CheckBoxBackgroundFocused`|  
|![Casilla de verificación enfocada](../extensibility/ux-guidelines/media/0303-166-checkboxfocused.png "0303-166_CheckboxFocused")|Borde|`CommonControls.CheckBoxBorderFocused`|  
|![Casilla de verificación enfocada](../extensibility/ux-guidelines/media/0303-166-checkboxfocused.png "0303-166_CheckboxFocused")|Text|`CommonControls.CheckBoxTextFocused`|  
|![Casilla de verificación enfocada](../extensibility/ux-guidelines/media/0303-166-checkboxfocused.png "0303-166_CheckboxFocused")|Glifo|`CommonControls.CheckBoxGlyphFocused`|  
  
#### <a name="drop-boxcombo-box-controls"></a>Controles de cuadro combinado o lista desplegable  
 ![Colocar&#45;abajo&#47;cuadro combinado de la roja](../extensibility/ux-guidelines/media/0303-167-dropdowncomboboxredline.png "0303-167_DropDownComboBoxRedline")  
  
Use…  
para las listas desplegables y cuadros combinado que forman parte del cuadro de documento.  

No use…  
- para cualquier interfaz de usuario que no sea una lista desplegable o un cuadro combinado.  

- para una [Drop-down](../misc/shared-colors.md#BKMK_CommandDropDown) o un [Combo box](../misc/shared-colors.md#BKMK_CommandComboBox) de la barra de comandos.  
  
  **Valor predeterminado**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Quitar&#45;&#47;cuadro combinado](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303-168_DropDownComboBox")|Fondo|`CommonControls.ComboBoxBackground`|  
|![Quitar&#45;&#47;cuadro combinado](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303-168_DropDownComboBox")|Borde|`CommonControls.ComboBoxBorder`|  
|![Quitar&#45;&#47;cuadro combinado](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303-168_DropDownComboBox")|Text|`CommonControls.ComboBoxText`|  
|![Quitar&#45;&#47;cuadro combinado](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303-168_DropDownComboBox")|Separador|`CommonControls.ComboBoxSeparator`|  
|![Quitar&#45;&#47;cuadro combinado](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303-168_DropDownComboBox")|Glifo|`CommonControls.ComboBoxGlyph`|  
|![Quitar&#45;&#47;cuadro combinado](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303-168_DropDownComboBox")|Fondo de glifo|`CommonControls.ComboBoxGlyphBackground`|  
  
 **Deshabilitada**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Quitar&#45;inferior&#47;cuadro combinado deshabilitado](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")|Fondo|`CommonControls.ComboBoxBackgroundDisabled`|  
|![Quitar&#45;inferior&#47;cuadro combinado deshabilitado](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")|Borde|`CommonControls.ComboBoxBorderDisabled`|  
|![Quitar&#45;inferior&#47;cuadro combinado deshabilitado](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")|Text|`CommonControls.ComboBoxTextDisabled`|  
|![Quitar&#45;inferior&#47;cuadro combinado deshabilitado](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")|Separador|`CommonControls.ComboBoxSeparatorDisabled`|  
|![Quitar&#45;inferior&#47;cuadro combinado deshabilitado](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")|Glifo|`CommonControls.ComboBoxGlyphDisabled`|  
|![Quitar&#45;inferior&#47;cuadro combinado deshabilitado](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")|Fondo de glifo|`CommonControls.ComboBoxGlyphBackgroundDisabled`|  
  
 **Al mantener el puntero**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Desplegable&#45;&#47;cuadro combinado al mantener el mouse](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")|Fondo|`CommonControls.ComboBoxBackgroundHover`|  
|![Desplegable&#45;&#47;cuadro combinado al mantener el mouse](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")|Borde|`CommonControls.ComboBoxBorderHover`|  
|![Desplegable&#45;&#47;cuadro combinado al mantener el mouse](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")|Text|`CommonControls.ComboBoxTextHover`|  
|![Desplegable&#45;&#47;cuadro combinado al mantener el mouse](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")|Separador|`CommonControls.ComboBoxSeparatorHover`|  
|![Desplegable&#45;&#47;cuadro combinado al mantener el mouse](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")|Glifo|`CommonControls.ComboBoxGlyphHover`|  
|![Desplegable&#45;&#47;cuadro combinado al mantener el mouse](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")|Fondo de glifo|`CommonControls.ComboBoxGlyphBackgroundHover`|  
  
 **Pressed**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Desplegable&#45;&#47;cuadro combinado presionado](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")|Fondo|`CommonControls.ComboBoxBackgroundPressed`|  
|![Desplegable&#45;&#47;cuadro combinado presionado](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")|Borde|`CommonControls.ComboBoxBorderPressed`|  
|![Desplegable&#45;&#47;cuadro combinado presionado](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")|Text|`CommonControls.ComboBoxTextPressed`|  
|![Desplegable&#45;&#47;cuadro combinado presionado](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")|Separador|`CommonControls.ComboBoxSeparatorPressed`|  
|![Desplegable&#45;&#47;cuadro combinado presionado](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")|Glifo|`CommonControls.ComboBoxGlyphPressed`|  
|![Desplegable&#45;&#47;cuadro combinado presionado](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")|Fondo de glifo|`CommonControls.ComboBoxGlyphBackgroundPressed`|  
  
 **Focused**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Descartar&#45;&#47;cuadro combinado enfocado](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")|Fondo|`CommonControls.ComboBoxBackgroundFocused`|  
|![Descartar&#45;&#47;cuadro combinado enfocado](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")|Borde|`CommonControls.ComboBoxBorderFocused`|  
|![Descartar&#45;&#47;cuadro combinado enfocado](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")|Text|`CommonControls.ComboBoxTextFocused`|  
|![Descartar&#45;&#47;cuadro combinado enfocado](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")|Separador|`CommonControls.ComboBoxSeparatorFocused`|  
|![Descartar&#45;&#47;cuadro combinado enfocado](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")|Glifo|`CommonControls.ComboBoxGlyphFocused`|  
|![Descartar&#45;&#47;cuadro combinado enfocado](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")|Fondo de glifo|`CommonControls.ComboBoxGlyphBackgroundFocused`|  
  
 **Selección de entrada de texto**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Colocar&#45;abajo&#47;entrada de texto de cuadro combinado](../extensibility/ux-guidelines/media/0303-173-dropdowncomboboxtextinput.png "0303-173_DropDownComboBoxTextInput")|Resaltar|`CommonControls.ComboBoxTextInputSelection`|  
  
 **Presionado: vista de elementos de lista**  
  
|Componente|Elemento|Nombre del token: Color.category|  
|---------------|-------------|--------------------------------|  
|![Quitar&#45;abajo&#47;vista de lista de cuadro combinado](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Fondo|`CommonControls.ComboBoxListBackground`|  
|![Quitar&#45;abajo&#47;vista de lista de cuadro combinado](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Fondo|`CommonControls.ComboBoxListBackgroundHover`|  
|![Quitar&#45;abajo&#47;vista de lista de cuadro combinado](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Fondo|`CommonControls.ComboBoxListItemBackgroundPressed`|  
|![Quitar&#45;abajo&#47;vista de lista de cuadro combinado](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Fondo|`CommonControls.ComboBoxListItemBackgroundFocused`|  
|![Quitar&#45;abajo&#47;vista de lista de cuadro combinado](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Borde|`CommonControls.ComboBoxListBorder`|  
|![Quitar&#45;abajo&#47;vista de lista de cuadro combinado](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Borde|`CommonControls.ComboBoxListBorderHover`|  
|![Quitar&#45;abajo&#47;vista de lista de cuadro combinado](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Borde|`CommonControls.ComboBoxListBorderPressed`|  
|![Quitar&#45;abajo&#47;vista de lista de cuadro combinado](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Borde|`CommonControls.ComboBoxListBorderFocused`|  
|![Quitar&#45;abajo&#47;vista de lista de cuadro combinado](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Texto del elemento|`CommonControls.ComboBoxListItemText`|  
|![Quitar&#45;abajo&#47;vista de lista de cuadro combinado](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Texto del elemento|`CommonControls.ComboBoxListItemTextHover`|  
|![Quitar&#45;abajo&#47;vista de lista de cuadro combinado](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Texto del elemento|`CommonControls.ComboBoxListItemTextPressed`|  
|![Quitar&#45;abajo&#47;vista de lista de cuadro combinado](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Texto del elemento|`CommonControls.ComboBoxListItemTextFocused`|  
|![Quitar&#45;abajo&#47;vista de lista de cuadro combinado](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Sombra de fondo|`CommonControls.ComboBoxListBackgroundShadow`|  
  
#### <a name="tabular-data-grid-controls"></a>Controles de datos tabulares (cuadrícula)  
 Los controles de datos tabulares, también conocidos como controles de cuadrícula, son controles comunes de Visual Studio que se pueden usar para presentar grandes cantidades de datos en varias columnas. Los controles estándar de datos tabulares están en varias ubicaciones de Visual Studio: la ventana de herramientas Lista de errores, los informes de IntelliTrace y la vista de montón de memoria, entre otros. Use siempre los controles de datos tabulares estándar que se proporcionan. En raras ocasiones, podría no tener acceso a los controles estándar de datos tabulares. En estos casos, use los siguientes nombres de token para asegurarse de que la interfaz de usuario sea coherente con otros controles de datos tabulares de Visual Studio.  
  
 ![Control de cuadrícula de &#40;de datos tabulares&#41; línea roja](../extensibility/ux-guidelines/media/0303-197-tabulardatagridcontrolredline.png "0303-197_TabularDataGridControlRedline")  
  
 Use…  
 para controles tabulares o de cuadrícula.  
  
 No use…  
 para cualquier interfaz de usuario que no sea un control tabular o de cuadrícula.  
  
##### <a name="column-headers"></a>Encabezados de columna  
 Los encabezados de columna constan de un fondo, un borde, el texto del título y un glifo opcional que suele usarse cuando se ordena una cuadrícula por esa columna.  
  
|State|Elemento|Nombre del token: Category.color|  
|-----------|-------------|--------------------------------|  
|Predeterminado|Fondo|`Header.Default`|  
|Predeterminado|Primer plano (texto)|`Environment.CommandBarTextActive`|  
|Predeterminado|Primer plano (glifo)|`Header.Glyph`|  
|Predeterminado|Borde|`Header.SeparatorLine`|  
|Al mantener el puntero|Fondo|`Header.MouseOver`|  
|Al mantener el puntero|Primer plano (texto)|`Environment.CommandBarTextHover`|  
|Al mantener el puntero|Primer plano (glifo)|`Header.MouseOverGlyph`|  
|Al mantener el puntero|Borde|`Header.SeparatorLine`|  
|Presionado|Fondo|`CommonControls.CheckBoxBackgroundPressed`|  
|Presionado|Primer plano (texto)|`CommonControls.CheckBoxBorderPressed`|  
|Presionado|Primer plano (glifo)|`CommonControls.CheckBoxTextPressed`|  
|Presionado|Borde|`CommonControls.CheckBoxGlyphPressed`|  
  
##### <a name="list-view-items"></a>Elementos de vista lista  
 Los elementos de vista de lista constan de un fondo y el contenido. El contenido puede ser texto, un icono o ambos.  
  
|State|Elemento|Nombre del token: Category.color|  
|-----------|-------------|--------------------------------|  
|Predeterminado|Fondo|Transparente|  
|Predeterminado|Primer plano (texto)|`Environment.CommandBarTextActive`|  
|Predeterminado|Borde|None|  
|Seleccionado (activo)|Fondo|`TreeView.SelectedItemActive`|  
|Seleccionado (activo)|Primer plano (texto)|`TreeView.SelectedItemActiveText`|  
|Seleccionado (activo)|Borde|None|  
|Seleccionado (inactivo)|Fondo|`TreeView.SelectedItemInactive`|  
|Seleccionado (inactivo)|Primer plano (texto)|`TreeView.SelectedItemInactiveText`|  
|Seleccionado (inactivo)|Borde|None|  
  
### <a name="manifest-designer"></a>Diseñador de manifiestos  
 El Diseñador de manifiestos se creó para que resulte más fácil editar el archivo de manifiesto en los proyectos de Windows 8 y Windows Phone 8. Aunque no hay ningún marco compartido disponible para su consumo, es conveniente que haga coincidir el diseño y los colores de las pestañas de navegación u orientación con la estructura general. Para obtener más información sobre el diseño, vea [Layout for Visual Studio](../extensibility/ux-guidelines/layout-for-visual-studio.md).  
  
 ![Límite de diseñador de manifiestos](../extensibility/ux-guidelines/media/0303-175-manifestdesignerredline.png "0303-175_ManifestDesignerRedline")  
  
Use…  
- para los diseñadores que son similares al Diseñador de manifiestos.  

- en lugar de usar los controles comunes de pestaña en la parte superior de un editor en el cuadro de documento.  

No use…  
- si tiene más de seis pestañas.  

- para cualquier interfaz de usuario que no tenga la misma estructura que el Diseñador de manifiestos.  
  
|State|Componente|Elemento|Nombre del token: Category.color|  
|-----------|---------------|-------------|--------------------------------|  
|Predeterminado (seleccionado)|Pestaña|Fondo|`ManifestDesigner.TabActive`|  
|Predeterminado (seleccionado)|Pestaña|Borde|None|  
|Predeterminado (seleccionado)|Panel de descripción|Fondo|`ManifestDesigner.DescriptionPane`|  
|Predeterminado (seleccionado)|Página de contenido|Fondo|`ManifestDesigner.Background`|  
|Predeterminado (seleccionado)|Página de contenido|Texto del asistente del cuadro de diálogo|`ManifestDesigner.WatermarkText`<br /><br /> Este nombre de token no coincide con su función.|  
|Sin seleccionar|Pestaña|Fondo|`ManifestDesigner.Tab.Inactive`|  
|Al mantener el puntero|Pestaña|Fondo|`ManifestDesigner.Tab.Mouseover`|  
  
### <a name="tagging"></a>Etiquetado  
 Visual Studio admite el etiquetado, lo que permite al usuario declarar palabras clave de búsqueda con fines de seguimiento. Por ejemplo, los desarrolladores y los administradores de proyectos pueden usar Team Foundation Server (TFS) para etiquetar elementos de trabajo. Las tablas siguientes proporcionan nombres de colores para la etiqueta en sí y el glifo del "icono de cerrar" que aparecen en los estados Al desplazar el puntero y Seleccionado.  
  
 ![Límite de etiquetado](../extensibility/ux-guidelines/media/0303-176-taggingredline.png "0303-176_TaggingRedline")  
  
 Use…  
 para la interfaz de usuario que admite el etiquetado.  
  
 No use…  
 para cualquier otro tipo de interfaz de usuario.  
  
#### <a name="tag"></a>Etiqueta  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Tag](../extensibility/ux-guidelines/media/0303-177-tag.png "0303-177_Tag")<br /><br /> **Valor predeterminado**|Fondo|`Tag.Background`|  
|![Tag](../extensibility/ux-guidelines/media/0303-177-tag.png "0303-177_Tag")<br /><br /> **Valor predeterminado**|Primer plano (texto)|`Tag.Background`|  
|![Etiqueta al mantener el mouse](../extensibility/ux-guidelines/media/0303-178-taghover.png "0303-178_TagHover")<br /><br /> **Al mantener el puntero**|Fondo|`Tag.HoverBackground`|  
|![Etiqueta al mantener el mouse](../extensibility/ux-guidelines/media/0303-178-taghover.png "0303-178_TagHover")<br /><br /> **Al mantener el puntero**|Primer plano (texto)|`Tag.HoverBackgroundText`|  
|![Etiqueta presionada](../extensibility/ux-guidelines/media/0303-179-tagpressed.png "0303-179_TagPressed")<br /><br /> **Pressed**|Fondo|`Tag.PressedBackground`|  
|![Etiqueta presionada](../extensibility/ux-guidelines/media/0303-179-tagpressed.png "0303-179_TagPressed")<br /><br /> **Pressed**|Primer plano (texto)|`Tag.PressedBackgroundText`|  
|![Etiqueta seleccionada](../extensibility/ux-guidelines/media/0303-180-tagselected.png "0303-180_TagSelected")<br /><br /> **Selected**|Fondo|`Tag.SelectedBackground`|  
|![Etiqueta seleccionada](../extensibility/ux-guidelines/media/0303-180-tagselected.png "0303-180_TagSelected")<br /><br /> **Selected**|Primer plano (texto)|`Tag.SelectedBackgroundText`|  
  
#### <a name="glyph-close-icon"></a>Glifo (icono de cerrar)  
 **Valor predeterminado**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![&#40;de glifo&#41;](../extensibility/ux-guidelines/media/0303-181-tagglyph.png "0303-181_TagGlyph")<br /><br /> **Predeterminado (valor predeterminado de etiqueta)**|Fondo|N/D|  
|![&#40;de glifo&#41;](../extensibility/ux-guidelines/media/0303-181-tagglyph.png "0303-181_TagGlyph")<br /><br /> **Predeterminado (valor predeterminado de etiqueta)**|Primer plano (glifo)|`Tag.TagHoverGlyph`|  
  
 **Al mantener el puntero**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![&#40;de glifo&#41; al mantener el mouse](../extensibility/ux-guidelines/media/0303-182-tagglyphhover.png "0303-182_TagGlyphHover")<br /><br /> **Al mantener el puntero (valor predeterminado de etiqueta)**|Fondo|`Tag.TagHoverGlyphHoverBackground`|  
|![&#40;de glifo&#41; al mantener el mouse](../extensibility/ux-guidelines/media/0303-182-tagglyphhover.png "0303-182_TagGlyphHover")<br /><br /> **Al mantener el puntero (valor predeterminado de etiqueta)**|Primer plano (glifo)|`Tag.TagHoverGlyphHover`|  
|![&#40;de glifo&#41; al mantener el mouse](../extensibility/ux-guidelines/media/0303-182-tagglyphhover.png "0303-182_TagGlyphHover")<br /><br /> **Al mantener el puntero (valor predeterminado de etiqueta)**|Borde|`Tag.TagHoverGlyphHoverBorder`|  
  
 **Pressed**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![&#41; presionado &#40;de glifo de etiqueta](../extensibility/ux-guidelines/media/0303-183-tagglyphpressed.png "0303-183_TagGlyphPressed")<br /><br /> **Presionado (valor predeterminado de etiqueta)**|Fondo|`Tag.TagHoverGlyphPressedBackground`|  
|![&#41; presionado &#40;de glifo de etiqueta](../extensibility/ux-guidelines/media/0303-183-tagglyphpressed.png "0303-183_TagGlyphPressed")<br /><br /> **Presionado (valor predeterminado de etiqueta)**|Primer plano (glifo)|`Tag.TagHoverGlyphPressed`|  
|![&#41; presionado &#40;de glifo de etiqueta](../extensibility/ux-guidelines/media/0303-183-tagglyphpressed.png "0303-183_TagGlyphPressed")<br /><br /> **Presionado (valor predeterminado de etiqueta)**|Borde|`Tag.TagHoverGlyphPressedBorder`|  
  
 **Etiqueta seleccionada o valor predeterminado de glifo**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Etiqueta seleccionada](../extensibility/ux-guidelines/media/0303-184-tagselected.png "0303-184_TagSelected")<br /><br /> **Predeterminado (etiqueta seleccionada)**|Fondo|N/D|  
|![Etiqueta seleccionada](../extensibility/ux-guidelines/media/0303-184-tagselected.png "0303-184_TagSelected")<br /><br /> **Predeterminado (etiqueta seleccionada)**|Primer plano (glifo)|`Tag.TagSelectedGlyph`|  
  
 **Etiqueta seleccionada o al mantener el puntero sobre el glifo**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Etiqueta seleccionada al mantener el mouse](../extensibility/ux-guidelines/media/0303-185-tagselectedhover.png "0303-185_TagSelectedHover")<br /><br /> **Al mantener el puntero (etiqueta seleccionada)**|Fondo|`Tag.TagSelectedGlyphHoverBackground`|  
|![Etiqueta seleccionada al mantener el mouse](../extensibility/ux-guidelines/media/0303-185-tagselectedhover.png "0303-185_TagSelectedHover")<br /><br /> **Al mantener el puntero (etiqueta seleccionada)**|Primer plano (glifo)|`Tag.TagSelectedGlyphHover`|  
|![Etiqueta seleccionada al mantener el mouse](../extensibility/ux-guidelines/media/0303-185-tagselectedhover.png "0303-185_TagSelectedHover")<br /><br /> **Al mantener el puntero (etiqueta seleccionada)**|Borde|`Tag.TagSelectedGlyphHoverBorder`|  
  
 **Etiqueta seleccionada o glifo presionado**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Etiqueta seleccionada presionada](../extensibility/ux-guidelines/media/0303-186-tagselectedpressed.png "0303-186_TagSelectedPressed")<br /><br /> **Presionado (etiqueta seleccionada)**|Fondo|`Tag.TagSelectedGlyphPressedBackground`|  
|![Etiqueta seleccionada presionada](../extensibility/ux-guidelines/media/0303-186-tagselectedpressed.png "0303-186_TagSelectedPressed")<br /><br /> **Presionado (etiqueta seleccionada)**|Primer plano (glifo)|`Tag.TagSelectedGlyphPressed`|  
|![Etiqueta seleccionada presionada](../extensibility/ux-guidelines/media/0303-186-tagselectedpressed.png "0303-186_TagSelectedPressed")<br /><br /> **Presionado (etiqueta seleccionada)**|Borde|`Tag.TagSelectedGlyphPressedBorder`|  
  
### <a name="shell"></a>Shell  
  
#### <a name="background"></a>Fondo  
 El fondo del entorno consta de dos niveles. El nivel inferior es un color sólido que cubre todo el IDE. El nivel superior se encuentra debajo del área de comandos y entre los canales de ocultación automática de la ventana de herramientas en los extremos izquierdo y derecho del IDE. A partir de Visual Studio 2013, los niveles de fondo superior e inferior se establecen en el mismo color en los temas claro y oscuro.  
  
 ![Límite de fondo del shell](../extensibility/ux-guidelines/media/0303-187-shellbackgroundredline.png "0303-187_ShellBackgroundRedline")  
  
 Use…  
 para los lugares que quiere hacer coincidir con el fondo del entorno de Visual Studio.  
  
No use…  
- como relleno de lugares que no son superficies de fondo.  

- como fondo en el que quiere colocar elementos en primer plano.  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|Nivel inferior|Fondo|`Environment.EnvironmentBackground`|  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|Nivel superior|Fondo<br /><br /> *Los delimitadores de degradado se establecen en el mismo valor de color en los temas claro y oscuro de Visual Studio 2013.*|`Environment.EnvironmentBackgroundGradientBegin`|  
|Nivel superior|Fondo<br /><br /> *Los delimitadores de degradado se establecen en el mismo valor de color en los temas claro y oscuro de Visual Studio 2013.*|`Environment.EnvironmentBackgroundGradientEnd`|  
|Nivel superior|Fondo<br /><br /> *Los delimitadores de degradado se establecen en el mismo valor de color en los temas claro y oscuro de Visual Studio 2013.*|`Environment.EnvironmentBackgroundGradientMiddle1`|  
|Nivel superior|Fondo<br /><br /> *Los delimitadores de degradado se establecen en el mismo valor de color en los temas claro y oscuro de Visual Studio 2013.*|`Environment.EnvironmentBackgroundGradientMiddle2`|  
  
#### <a name="command-shelf"></a>Área de comandos  
 Para los fondos del área de comandos se usan dos conjuntos de nombres de token: un conjunto para la ubicación donde se coloca la barra de menús y uno para la ubicación donde se colocan las barras de comandos. Un grupo individual de la barra de comandos tiene sus propios valores de color de fondo, que se describen con más detalle en la sección "Barra de comandos". El texto de la barra de menús y la barra de comandos se describe en las secciones de barra de menús y barra de comandos, respectivamente.  
  
 ![Límite de shell de comandos](../extensibility/ux-guidelines/media/0303-188-commandshelfredline.png "0303-188_CommandShelfRedline")  
  
Use…  
- para las áreas donde se colocan menús o barras de herramientas.  

- con la combinación correcta de nombre de token en segundo plano o primer plano.  
  
  No use…  
  para áreas que no sean similares a un área de comandos.  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|Barra de menús|Fondo<br /><br /> *Los delimitadores de degradado se establecen en el mismo valor de color en los temas claro y oscuro de Visual Studio 2013.*|`Environment.CommandShelfHighlightGradientBegin`|  
|Barra de menús|Fondo<br /><br /> *Los delimitadores de degradado se establecen en el mismo valor de color en los temas claro y oscuro de Visual Studio 2013.*|`Environment.CommandShelfHighlightGradientMiddle`|  
|Barra de menús|Fondo<br /><br /> *Los delimitadores de degradado se establecen en el mismo valor de color en los temas claro y oscuro de Visual Studio 2013.*|`Environment.CommandShelfHighlightGradientEnd`|  
|Barra de comandos|Fondo<br /><br /> *Los delimitadores de degradado se establecen en el mismo valor de color en los temas claro y oscuro de Visual Studio 2013.*|`Environment.CommandShelfBackgroundGradientBegin`|  
|Barra de comandos|Fondo<br /><br /> *Los delimitadores de degradado se establecen en el mismo valor de color en los temas claro y oscuro de Visual Studio 2013.*|`Environment.CommandShelfBackgroundGradientMiddle`|  
|Barra de comandos|Fondo<br /><br /> *Los delimitadores de degradado se establecen en el mismo valor de color en los temas claro y oscuro de Visual Studio 2013.*|`Environment.CommandShelfBackgroundGradientEnd`|  
  
### <a name="toolbox"></a>Cuadro de herramientas  
 El cuadro de herramientas es una de las ventanas de herramientas comunes que se usa con más frecuencia en Visual Studio. Es esencialmente un control de árbol con un tema y un estilo especial aplicado.  
  
 ![Límite de cuadro de herramientas](../extensibility/ux-guidelines/media/0303-189-toolboxredline.png "0303-189_ToolboxRedline")  
  
 Use…  
 al diseñar una ventana de herramientas que desea que siempre sea coherente con el cuadro de herramientas del shell.  
  
 No use…  
 para cualquier elemento que no sea similar a la interfaz de usuario del cuadro de herramientas o si no está seguro de si la interfaz de usuario tendrá problemas si cambian los colores del cuadro de herramientas del shell.  
  
 **Valor predeterminado**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Nodo primario de cuadro de herramientas](../extensibility/ux-guidelines/media/0303-190-toolboxparentnode.png "0303-190_ToolboxParentNode")<br /><br /> **Nodo primario**|Fondo|`Environment.ToolboxContent`<br /><br /> Encabezados<br /><br /> `Environment.ToolWindowBackground`<br /><br /> Elementos individuales o ventana completa si no hay controles disponibles|  
|![Nodo secundario de cuadro de herramientas](../extensibility/ux-guidelines/media/0303-191-toolboxchildnode.png "0303-191_ToolboxChildNode")<br /><br /> **Nodo secundario**|Fondo|`Environment.ToolboxContent`<br /><br /> Encabezados<br /><br /> `Environment.ToolWindowBackground`<br /><br /> Elementos individuales o ventana completa si no hay controles disponibles|  
|![Nodo primario de cuadro de herramientas](../extensibility/ux-guidelines/media/0303-190-toolboxparentnode.png "0303-190_ToolboxParentNode")<br /><br /> **Nodo primario**|Borde|None|  
|![Nodo secundario de cuadro de herramientas](../extensibility/ux-guidelines/media/0303-191-toolboxchildnode.png "0303-191_ToolboxChildNode")<br /><br /> **Nodo secundario**|Borde|None|  
|![Nodo primario de cuadro de herramientas](../extensibility/ux-guidelines/media/0303-190-toolboxparentnode.png "0303-190_ToolboxParentNode")<br /><br /> **Nodo primario**|Primer plano (glifo)|`Environment.ToolboxContent`|  
|![Nodo secundario de cuadro de herramientas](../extensibility/ux-guidelines/media/0303-191-toolboxchildnode.png "0303-191_ToolboxChildNode")<br /><br /> **Nodo secundario**|Primer plano (glifo)|`Environment.ToolboxContent`|  
|![Nodo primario de cuadro de herramientas](../extensibility/ux-guidelines/media/0303-190-toolboxparentnode.png "0303-190_ToolboxParentNode")<br /><br /> **Nodo primario**|Primer plano (texto)|`Environment.ToolboxContent`|  
|![Nodo secundario de cuadro de herramientas](../extensibility/ux-guidelines/media/0303-191-toolboxchildnode.png "0303-191_ToolboxChildNode")<br /><br /> **Nodo secundario**|Primer plano (texto)|`Environment.ToolboxContent`|  
  
 **Al mantener el puntero**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Nodo secundario de cuadro de herramientas al mantener el mouse](../extensibility/ux-guidelines/media/0303-192-toolboxchildnodehover.png "0303-192_ToolboxChildNodeHover")<br /><br /> **Al mantener el puntero sobre el cuadro de herramientas en el nodo secundario**|Fondo|`Environment.ToolboxContentMouseOver`<br /><br /> Solo elementos individuales|  
|![Nodo secundario de cuadro de herramientas al mantener el mouse](../extensibility/ux-guidelines/media/0303-192-toolboxchildnodehover.png "0303-192_ToolboxChildNodeHover")<br /><br /> **Al mantener el puntero sobre el cuadro de herramientas en el nodo secundario**|Borde|None|  
|![Nodo secundario de cuadro de herramientas al mantener el mouse](../extensibility/ux-guidelines/media/0303-192-toolboxchildnodehover.png "0303-192_ToolboxChildNodeHover")<br /><br /> **Al mantener el puntero sobre el cuadro de herramientas en el nodo secundario**|Primer plano (texto)|`Environment.ToolboxContentMouseOver`<br /><br /> Solo elementos individuales|  
  
 **Selected**  
  
|Componente|Elemento|Nombre del token: Category.color|  
|---------------|-------------|--------------------------------|  
|![Nodo primario de cuadro de herramientas enfocado](../extensibility/ux-guidelines/media/0303-193-toolboxparentnodefocused.png "0303-193_ToolboxParentNodeFocused")<br /><br /> **Nodo primario con foco**|Fondo|`TreeView.SelectedItemActive`<br /><br /> De categoría [Tree view](../misc/shared-colors.md#BKMK_TreeView)|  
|![Nodo secundario de cuadro de herramientas enfocado](../extensibility/ux-guidelines/media/0303-194-toolboxchildnodefocused.png "0303-194_ToolboxChildNodeFocused")<br /><br /> **Nodo secundario con foco**|Fondo|`TreeView.SelectedItemActive`<br /><br /> De categoría [Tree view](../misc/shared-colors.md#BKMK_TreeView)|  
|![Nodo primario de cuadro de herramientas enfocado](../extensibility/ux-guidelines/media/0303-193-toolboxparentnodefocused.png "0303-193_ToolboxParentNodeFocused")<br /><br /> **Nodo primario con foco**|Borde|`TreeView.FocusVisualBorder`<br /><br /> De categoría [Tree view](../misc/shared-colors.md#BKMK_TreeView)|  
|![Nodo secundario de cuadro de herramientas enfocado](../extensibility/ux-guidelines/media/0303-194-toolboxchildnodefocused.png "0303-194_ToolboxChildNodeFocused")<br /><br /> **Nodo secundario con foco**|Borde|`TreeView.FocusVisualBorder`<br /><br /> De categoría [Tree view](../misc/shared-colors.md#BKMK_TreeView)|  
|![Nodo primario de cuadro de herramientas enfocado](../extensibility/ux-guidelines/media/0303-193-toolboxparentnodefocused.png "0303-193_ToolboxParentNodeFocused")<br /><br /> **Nodo primario con foco**|Primer plano (glifo)|`TreeView.SelectedItemActive`<br /><br /> De categoría [Tree view](../misc/shared-colors.md#BKMK_TreeView)|  
|![Nodo secundario de cuadro de herramientas enfocado](../extensibility/ux-guidelines/media/0303-194-toolboxchildnodefocused.png "0303-194_ToolboxChildNodeFocused")<br /><br /> **Nodo secundario con foco**|Primer plano (glifo)|`TreeView.SelectedItemActive`<br /><br /> De categoría [Tree view](../misc/shared-colors.md#BKMK_TreeView)|  
|![Nodo primario de cuadro de herramientas enfocado](../extensibility/ux-guidelines/media/0303-193-toolboxparentnodefocused.png "0303-193_ToolboxParentNodeFocused")<br /><br /> **Nodo primario con foco**|Primer plano (texto)|`TreeView.SelectedItemActive`<br /><br /> De categoría [Tree view](../misc/shared-colors.md#BKMK_TreeView)|  
|![Nodo secundario de cuadro de herramientas enfocado](../extensibility/ux-guidelines/media/0303-194-toolboxchildnodefocused.png "0303-194_ToolboxChildNodeFocused")<br /><br /> **Nodo secundario con foco**|Primer plano (texto)|`TreeView.SelectedItemActive`<br /><br /> De categoría [Tree view](../misc/shared-colors.md#BKMK_TreeView)|  
|![Nodo primario de cuadro de herramientas no enfocado](../extensibility/ux-guidelines/media/0303-195-toolboxparentnodeunfocused.png "0303-195_ToolboxParentNodeUnfocused")<br /><br /> **Nodo primario sin foco**|Fondo|`TreeView.SelectedItemInactive`<br /><br /> De categoría [Tree view](../misc/shared-colors.md#BKMK_TreeView)|  
|![Nodo secundario de cuadro de herramientas no enfocado](../extensibility/ux-guidelines/media/0303-196-toolboxchildnodeunfocused.png "0303-196_ToolboxChildNodeUnfocused")<br /><br /> **Nodo secundario sin foco**|Fondo|`TreeView.SelectedItemInactive`<br /><br /> De categoría [Tree view](../misc/shared-colors.md#BKMK_TreeView)|  
|![Nodo primario de cuadro de herramientas no enfocado](../extensibility/ux-guidelines/media/0303-195-toolboxparentnodeunfocused.png "0303-195_ToolboxParentNodeUnfocused")<br /><br /> **Nodo primario sin foco**|Borde|None|  
|![Nodo secundario de cuadro de herramientas no enfocado](../extensibility/ux-guidelines/media/0303-196-toolboxchildnodeunfocused.png "0303-196_ToolboxChildNodeUnfocused")<br /><br /> **Nodo secundario sin foco**|Borde|None|  
|![Nodo primario de cuadro de herramientas no enfocado](../extensibility/ux-guidelines/media/0303-195-toolboxparentnodeunfocused.png "0303-195_ToolboxParentNodeUnfocused")<br /><br /> **Nodo primario sin foco**|Primer plano (glifo)|`TreeView.SelectedItemInactive`<br /><br /> De categoría [Tree view](../misc/shared-colors.md#BKMK_TreeView)|  
|![Nodo secundario de cuadro de herramientas no enfocado](../extensibility/ux-guidelines/media/0303-196-toolboxchildnodeunfocused.png "0303-196_ToolboxChildNodeUnfocused")<br /><br /> **Nodo secundario sin foco**|Primer plano (glifo)|`TreeView.SelectedItemInactive`<br /><br /> De categoría [Tree view](../misc/shared-colors.md#BKMK_TreeView)|  
|![Nodo primario de cuadro de herramientas no enfocado](../extensibility/ux-guidelines/media/0303-195-toolboxparentnodeunfocused.png "0303-195_ToolboxParentNodeUnfocused")<br /><br /> **Nodo primario sin foco**|Primer plano (texto)|`TreeView.SelectedItemInactive`<br /><br /> De categoría [Tree view](../misc/shared-colors.md#BKMK_TreeView)|  
|![Nodo secundario de cuadro de herramientas no enfocado](../extensibility/ux-guidelines/media/0303-196-toolboxchildnodeunfocused.png "0303-196_ToolboxChildNodeUnfocused")<br /><br /> **Nodo secundario sin foco**|Primer plano (texto)|`TreeView.SelectedItemInactive`<br /><br /> De categoría [Tree view](../misc/shared-colors.md#BKMK_TreeView)|  
  
## <a name="color-value-reference"></a>Referencia de valor de color  
  
|Componente|Parte|Elemento|State|Claro|Oscuro|Azul|Contraste alto|
|---------|----|-------|-----|-----|----|----|----|  
|Líneas divisorias|||Predeterminado|FFEEEEF2|FF2D2D30|FFEEEEF2|ControlDark|  
|Glifo de expansión||Primer plano|Predeterminado|||||  
|Glifo de expansión||Primer plano|Al mantener el puntero|||||  
|Glifo de expansión||Fondo|Predeterminado|||||  
|Glifo de expansión||Fondo|Al mantener el puntero|||||  
|Glifo de expansión||Borde|Predeterminado|||||  
|Glifo de expansión||Borde|Al mantener el puntero|||||