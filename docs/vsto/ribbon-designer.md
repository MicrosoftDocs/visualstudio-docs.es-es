---
title: Diseñador de la cinta de opciones
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- Designer_Microsoft.VisualStudio.Tools.Office.Ribbon.Design.RibbonDesigner
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom Ribbon, about Ribbon Designer
- controls [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], controls
- customizing the Ribbon, about Ribbon Designer
- Ribbon [Office development in Visual Studio], visual designer
- customizing the Ribbon
- custom Ribbon
- designers [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], customizing
- Ribbon [Office development in Visual Studio], common tasks
- Ribbon Designer [Office development in Visual Studio]
- read-only properties
- Ribbon [Office development in Visual Studio], shortcut keys
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8cc47445f9d2024f5d8a83c8f376bc0299b8ea4e
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60103646"
---
# <a name="ribbon-designer"></a>Diseñador de la cinta de opciones
  El Diseñador de cinta es un lienzo de diseño visual. Usar el Diseñador de cinta de opciones para agregar pestañas personalizadas, grupos y controles a la cinta de opciones de una aplicación de Microsoft Office.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

 Para abrir el Diseñador de cinta, agregue un **cinta (diseñador Visual)** a su proyecto. A continuación, puede usar las herramientas de diseño para las siguientes tareas:

- [Diseño de la cinta de opciones](#DesigningRibbonLayout)

- [Controlar eventos y establecer las propiedades del control](#HandleEventsSetProperties)

- [Agregar controles a la vista Backstage](#CustomizingMicrosoftOfficeButton)

> [!NOTE]
>  Hay algunas tareas que no se puede realizar mediante el Diseñador de cinta de opciones. Para obtener más información sobre estas tareas y cómo puede llevarlas a cabo, consulte [información general de la cinta de opciones](../vsto/ribbon-overview.md).

 ![vínculo a vídeo](../vsto/media/playvideo.gif "vínculo al vídeo") para una demostración en vídeo relacionada, vea [¿cómo lo hago?: ¿Usar el Diseñador de cinta para personalizar la cinta de opciones en Outlook? ](http://go.microsoft.com/fwlink/?LinkID=130312).

## <a name="add-a-ribbon-visual-designer-item-to-a-project"></a>Agregar un elemento cinta (diseñador Visual) a un proyecto
 Para usar el Diseñador de cinta, agregue un nuevo **cinta (diseñador Visual)** a su proyecto. Para obtener más información, vea [Cómo: Introducción a la personalización de la cinta de opciones](../vsto/how-to-get-started-customizing-the-ribbon.md).

 Cuando se agrega un nuevo **cinta (diseñador Visual)** producto, Visual Studio agrega automáticamente los siguientes archivos al proyecto:

- Un archivo de código de la cinta de opciones. Este archivo tiene el nombre que especifique para la **cinta (diseñador Visual)** de elemento en el **Agregar nuevo elemento** cuadro de diálogo. Agregue código para controlar los eventos de la cinta de opciones para este archivo.

- Un archivo de código del Diseñador de cinta. Este archivo contiene código generado por el Diseñador de cinta y no debe editarse directamente.

- Un archivo de recursos. Este archivo contiene los valores de propiedad de cada control en la cinta de opciones.

  Si ya tiene un **cinta (diseñador Visual)** elemento de otro proyecto, puede reutilizarlo en su proyecto actual mediante el uso de la **Agregar elemento existente** cuadro de diálogo.

## <a name="DesigningRibbonLayout"></a> Diseñar una cinta de opciones
 Hay tres maneras de abrir el Diseñador de cinta:

- En **el Explorador de soluciones**, haga doble clic en el archivo de código de la cinta de opciones.

- En **el Explorador de soluciones**, haga clic en el archivo de código de la cinta de opciones y, a continuación, haga clic en **Diseñador de vistas**.

- En **el Explorador de soluciones**, seleccione el archivo de código de la cinta de opciones y, a continuación, haga clic en **diseñador** en el **vista** menú.

  El Diseñador de cinta de opciones contiene una ficha predeterminada y un grupo. Puede quitar la ficha predeterminada y el grupo desde el Diseñador de cinta de opciones. Para quitar el grupo predeterminado, haga clic en **Group1**y, a continuación, haga clic en **eliminar**. Para quitar la ficha predeterminada, haga clic en un área vacía de la superficie de diseño y, a continuación, haga clic en **Quitar ficha de cinta**.

  También puede agregar pestañas personalizadas, grupos y controles en el Diseñador de cinta. Puede encontrar estos controles en el **cuadro de herramientas**, en el **controles de la cinta de Office** grupo. Hay tres maneras de agregar controles desde el **controles de la cinta de Office** grupo en el Diseñador de cinta:

- Arrastre un control a un área adecuada en el Diseñador de cinta.

- Haga clic en un control y, a continuación, haga clic en un área adecuada en el Diseñador de cinta.

- Seleccione un área adecuada en el diseñador y, a continuación, haga doble clic en un control en el **cuadro de herramientas**.

### <a name="ribbon-design-workflow"></a>Flujo de trabajo de diseño de cinta de opciones
 Siga estos pasos básicos para definir el diseño de la cinta de opciones:

1. [Agregar una pestaña personalizada a la cinta de opciones](#AddTabToRibbon).

2. [Agregar grupos a la ficha](#AddGroupsToTab).

3. [Agregar controles a los grupos](#AddControlsToGroups).

   Los controles se pueden colocar solo en grupos; no se puede arrastrar un control directamente en una pestaña o en la cinta de opciones. Los grupos se pueden colocar solo en fichas; no puede arrastrar un grupo directamente a una cinta de opciones.

   Organizar los controles arrastrándolos hacia las posiciones correctas. Puede establecer las propiedades de un control mediante la **propiedades** ventana.

   No se puede arrastrar controles de una pestaña a otra en la cinta de opciones. Si desea mover un control a otra ficha, debe usar el **cortar** comando para quitar el control de una ficha y, a continuación, pegarlo en otra pestaña. Si corta el control y lo pega, el controlador de eventos deja de funcionar. Puede volver a conectar el controlador de eventos en el **propiedades** ventana. Para obtener más información, consulte [ventana propiedades](../ide/reference/properties-window.md).

### <a name="AddTabToRibbon"></a> Agregar pestañas personalizadas a la cinta de opciones
 Hay tres maneras de agregar una pestaña personalizada a la cinta de opciones:

- Agregar una pestaña de la **cuadro de herramientas**.

- Haga clic en el Diseñador de cinta y, a continuación, haga clic en **Agregar ficha de cinta**.

- Abra el **pestaña Editor de la colección**y, a continuación, haga clic en **agregar**.

   Para abrir el **pestaña Editor de la colección**, en el **propiedades** ventana, seleccione el **pestañas** propiedad y, a continuación, haga clic en el botón de puntos suspensivos ![ASP.NET Mobile Elipse diseñador](../sharepoint/media/mwellipsis.gif "elipse del Diseñador de ASP.NET Mobile").

  Después de agregar una pestaña, puede agregar grupos para contener controles.

#### <a name="remove-custom-tabs-from-the-ribbon"></a>Quitar pestañas personalizadas de la cinta de opciones
 Hay tres formas de quitar una pestaña personalizada de la cinta de opciones:

- Haga clic en el diseñador y, a continuación, haga clic en **Quitar ficha de cinta**.

- En el **comandos** panel de la **propiedades** ventana, haga clic en **Quitar ficha de cinta**.

- Abra el **pestaña Editor de la colección**, seleccione la ficha y, a continuación, haga clic en **quitar**.

#### <a name="change-the-position-of-a-tab-on-the-ribbon"></a>Cambiar la posición de una pestaña en la cinta de opciones
 Puede cambiar el orden de las pestañas personalizadas en una cinta de opciones. También puede colocar las pestañas personalizadas antes o después de una pestaña integrada en la cinta de opciones. Para obtener más información, vea [Cómo: Cambiar la posición de una pestaña en la cinta de opciones](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md).

#### <a name="customize-built-in-tabs-on-the-ribbon"></a>Personalizar las fichas integradas de la cinta de opciones
 Una pestaña integrada es una ficha que ya está en la cinta de opciones de una aplicación de Microsoft Office. Por ejemplo, el **datos** ficha es una pestaña integrada en Excel.

 Puede agregar grupos y controles a una pestaña integrada. De forma predeterminada, un grupo personalizado aparece como el último grupo en una ficha integrada, aunque puede moverlo antes o después de cualquier grupo integrado en la pestaña.

 No se puede quitar grupos integrados.

 Para obtener más información sobre cómo personalizar una pestaña integrada, vea [Cómo: Personalizar una pestaña integrada](../vsto/how-to-customize-a-built-in-tab.md).

### <a name="AddGroupsToTab"></a> Agregar grupos a una ficha
 Los grupos organizan lógicamente los controles en la cinta de opciones. Agregar grupos de pestañas. Agregar todos los demás controles al grupo.

### <a name="AddControlsToGroups"></a> Agregar controles a grupos
 Agregue uno o más controles a un grupo. En la tabla siguiente se describe cada control.

|Control|Descripción|
|-------------|-----------------|
|**Box**|Un contenedor que organiza los controles de un grupo. Puede agregar cualquier control a un cuadro, excepto un separador, un grupo o una pestaña. Un cuadro puede ser horizontal o vertical.|
|**Button**|Un botón que inicia una acción. Puede agregar un botón a un grupo, un grupo de botones, una lista desplegable, una galería, un menú o un botón de expansión.|
|**ButtonGroup**|Un grupo que contiene uno o varios botones, botones de alternancia, menús, botones de expansión y galerías. Puede agregar un grupo de botones a un grupo o un menú.|
|**CheckBox**|Un cuadro que está activado o desactivado para activar o desactivar una opción.|
|**ComboBox**|Un cuadro de edición con un cuadro de lista asociado. Los usuarios pueden escribir o seleccionar su opción. El cuadro muestra la selección actual. Use el <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.Items%2A> propiedad para agregar y quitar elementos en tiempo de ejecución antes o después de carga la cinta de opciones en la aplicación de Office.|
|**DropDown**|Una lista de elementos que el usuario puede seleccionar. El usuario no puede escribir un nuevo elemento en una lista desplegable.<br /><br /> Use el <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.Items%2A> propiedad para agregar elementos a la lista. Puede agregar y quitar elementos en tiempo de ejecución.<br /><br /> Use el <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.Buttons%2A> propiedad para agregar botones a la lista. Sin embargo, no puede agregar y quitar botones en tiempo de ejecución después de carga la cinta de opciones en la aplicación de Office.|
|**EditBox**|Un cuadro en el que el usuario puede escribir texto.|
|**Galería**|Un menú que presenta una matriz o cuadrícula de opciones visuales las desde el que los usuarios pueden seleccionar. Puede controlar el diseño de las selecciones en el menú. Use la <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ColumnCount%2A> y <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.RowCount%2A> propiedades para especificar el número de filas y columnas que se mostrarán los elementos y botones de la galería.|
|**Label**|Texto que puede usar para identificar controles en la cinta de opciones.|
|**Menu**|Una lista desplegable que puede contener ninguno de los siguientes controles:<br /><br /> : Botón<br />: Casilla de verificación<br />-Galería<br />-Menú<br />: Botón de expansión<br />: Botón de alternancia<br />: Separador<br /><br /> Para agregar un control a un menú en el Diseñador de cinta, haga clic en la flecha hacia abajo en el menú para exponer la superficie de diseño de menú. A continuación, puede arrastrar los controles de cinta de opciones desde el **cuadro de herramientas** en el menú. Para organizar los controles, arrástrelos hacia las posiciones deseadas.<br /><br /> Para agregar controles a la <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> después de carga la cinta de opciones en la aplicación de Office, debe establecer el <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.Dynamic%2A> propiedad **true** antes de que se cargue la cinta de opciones. Para obtener información acerca de cómo hacerlo, consulte [información general sobre el modelo de objetos de cinta de opciones](../vsto/ribbon-object-model-overview.md).|
|**Separator**|Barra delgada utilizada para separar elementos de una lista. Cuando se agregan a un grupo, la barra es vertical. Cuando se agrega a un menú, la barra es horizontal.|
|**SplitButton**|Un botón con un menú asociado. Un botón de expansión puede contener ninguno de los siguientes controles:<br /><br /> : Botón<br />: Casilla de verificación<br />-Galería<br />-Menú<br />: Botón de expansión<br />: Botón de alternancia<br />: Separador<br /><br /> Al igual que el menú, el botón de expansión tiene su propia superficie de diseño. Sin embargo, a diferencia de un menú, puede actualizar solo los elementos de un botón de expansión antes de carga la cinta de opciones en la aplicación de Office. Para obtener información acerca de cómo actualizar los elementos de un botón de expansión, vea [información general sobre el modelo de objetos de cinta de opciones](../vsto/ribbon-object-model-overview.md).|
|**ToggleButton**|Un botón que aparece o no presionado.|

## <a name="HandleEventsSetProperties"></a> Controlar eventos y establecer las propiedades
 El Diseñador de cinta de opciones le permite establecer las propiedades del control en tiempo de diseño mediante el **propiedades** ventana. Además, la cinta de opciones expone un modelo de objetos fuertemente tipados que puede usar para obtener y establecer las propiedades de controles de cinta de opciones en tiempo de ejecución.

 Hacer doble clic en cualquier control en el diseñador para abrir un controlador de eventos para el evento predeterminado del control. Puede crear controladores de eventos para todos los demás eventos de control mediante la **propiedades** ventana.

 Propiedades y eventos de la cinta de opciones se encuentran en el <xref:Microsoft.Office.Tools.Ribbon> espacio de nombres. El **cinta (diseñador Visual)** elemento agrega automáticamente una referencia a este ensamblado en el proyecto e inserta adecuado **mediante** o **importaciones** instrucción en la parte superior la cinta de opciones archivo de código.

 Para obtener información sobre cómo controlar eventos de la cinta de opciones y establecer las propiedades de controles de cinta de opciones en tiempo de ejecución, vea [información general sobre el modelo de objetos de cinta de opciones](../vsto/ribbon-object-model-overview.md).

## <a name="CustomizingMicrosoftOfficeButton"></a> Personalizar la vista Backstage
 Puede usar el Diseñador de cinta para agregar controles al menú que se abre al hacer clic en el **archivo** ficha. Este menú se llama a la vista Backstage.

 No se puede colocar controles antes o después de los controles integrados usando el Diseñador de cinta de opciones. Un control integrado es un control que ya aparece en la vista Backstage. Si desea colocar controles antes o después de los controles integrados, debe usar XML de cinta de opciones. Para obtener más información acerca de **cinta (XML)**, consulte [Ribbon XML](../vsto/ribbon-xml.md). Para obtener más información acerca de cómo personalizar la vista Backstage, consulte [Introducción a la vista Backstage de Office 2010 para desarrolladores](http://go.microsoft.com/fwlink/?LinkId=182189) y [personalizar la vista Backstage de Office 2010 para desarrolladores](http://go.microsoft.com/fwlink/?LinkId=182188).

 [!INCLUDE[appliesto_ribbon_2010](../vsto/includes/appliesto-ribbon-2010-md.md)]

 Para obtener información sobre cómo agregar controles a la vista Backstage, vea [Cómo: Agregar controles a la vista Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md).

## <a name="Accessibility"></a> Accesibilidad en el Diseñador de cinta
 Puede usar métodos abreviados de teclado para mover controles en el Diseñador de cinta. Algunos métodos abreviados de teclado se aplican a todos los controles y algunas se aplican sólo a los controles que tienen menús.

 Métodos abreviados de teclado que se aplican a todos los controles se muestran en la tabla siguiente.

|Acción|Método abreviado de teclado|
|------------|-----------------------|
|Mover un control antes de que el control anterior en la lista.|**CTRL**+**seguridad**<br /><br /> **CTRL**+**izquierda**|
|Mover un control después del control en la lista siguiente.|**CTRL**+**hacia abajo**<br /><br /> **CTRL**+**derecha**|
|Mover la selección de un control a otro en el mismo grupo. Para un panel desplegable, desplazarse entre el control primario y los controles en el panel de lista desplegable.|**Arriba**<br /><br /> **Abajo**|
|Recorrer en iteración hacia delante todos los controles.|**Tabulación**|
|Recorrer en iteración hacia atrás todos los controles.|**Mayús**+**Tabulador**|
|Elimine el control seleccionado o el conjunto de controles.|**Eliminar**|
|Copie los controles seleccionados.|**Ctrl**+**C**|
|Cortar los controles seleccionados.|**Ctrl**+**X**|
|Pegar controles desde el Portapapeles.|**Ctrl**+**V**|
|Seleccione el **cuadro de herramientas**.|**Ctrl**+**Alt**+**X**|
|Seleccione el componente primario.|**Esc**|

 Métodos abreviados de teclado que se aplican solo al menú de Microsoft Office, <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>, y <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton> se muestran en la tabla siguiente.

|Acción|Método abreviado de teclado|
|------------|-----------------------|
|Seleccione el control primario si el panel desplegable está abierto y hay un control seleccionado en el panel de lista desplegable.|**Izquierda**|
|Cierre el panel desplegable si el panel desplegable está abierto y se selecciona el control primario.|**Izquierda**|
|Abra el panel de lista desplegable.|**Derecha**|
|Seleccione el primer control en el panel desplegable si el panel desplegable está abierto.|**Derecha**|
|Cerrar un panel desplegable.|**Esc**|

## <a name="see-also"></a>Vea también

- [Información general de la cinta de opciones](../vsto/ribbon-overview.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [Tutorial: Crear una pestaña personalizada usando el Diseñador de cinta de opciones](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Cómo: Exportar una cinta desde el Diseñador de cinta al XML de cinta](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)
- [Cómo: Introducción a la personalización de la cinta de opciones](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Obtener acceso a la cinta de opciones en tiempo de ejecución](../vsto/accessing-the-ribbon-at-run-time.md)
