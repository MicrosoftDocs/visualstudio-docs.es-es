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
ms.openlocfilehash: e1c2941b0c088a832540fd3380c993fe2c380b44
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985624"
---
# <a name="ribbon-designer"></a>Diseñador de la cinta de opciones
  El diseñador de la cinta de opciones es un lienzo de diseño visual. Use el diseñador de la cinta de opciones para agregar pestañas, grupos y controles personalizados a la cinta de opciones de una aplicación Microsoft Office.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

 Para abrir el diseñador de la cinta de opciones, agregue un elemento **cinta (diseñador visual)** al proyecto. A continuación, puede usar las herramientas de diseño de para las siguientes tareas:

- [Diseñar el diseño de la cinta de opciones](#DesigningRibbonLayout)

- [Controlar eventos y establecer propiedades de control](#HandleEventsSetProperties)

- [Agregar controles a la vista backstage](#CustomizingMicrosoftOfficeButton)

> [!NOTE]
> Hay algunas tareas que no puede realizar mediante el diseñador de la cinta de opciones. Para obtener más información acerca de estas tareas y cómo puede llevarlas a cabo, consulte [información general de la cinta](../vsto/ribbon-overview.md)de opciones.

## <a name="add-a-ribbon-visual-designer-item-to-a-project"></a>Agregar un elemento cinta (diseñador visual) a un proyecto
 Para usar el diseñador de la cinta de opciones, agregue un nuevo elemento **cinta (diseñador visual)** al proyecto. Para obtener más información, vea [Cómo: Introducción a la personalización de la cinta de opciones](../vsto/how-to-get-started-customizing-the-ribbon.md).

 Al agregar un nuevo elemento **cinta (diseñador visual)** , Visual Studio agrega automáticamente los siguientes archivos al proyecto:

- Un archivo de código de la cinta de opciones. Este archivo tiene el nombre que especificó para el elemento **cinta (diseñador visual)** en el cuadro de diálogo **Agregar nuevo elemento** . Agregue código para controlar los eventos de la cinta de opciones a este archivo.

- Un archivo de código del diseñador de la cinta. Este archivo contiene código generado por el diseñador de la cinta de opciones y no debe editarse directamente.

- Un archivo de recursos. Este archivo contiene los valores de propiedad de cada control de la cinta de opciones.

  Si ya tiene un elemento **cinta (diseñador visual)** de otro proyecto, puede volver a usarlo en el proyecto actual mediante el cuadro de diálogo **Agregar elemento existente** .

## <a name="DesigningRibbonLayout"></a>Diseñar una cinta de opciones
 Hay tres maneras de abrir el diseñador de la cinta de opciones:

- En **Explorador de soluciones**, haga doble clic en el archivo de código de la cinta de opciones.

- En **Explorador de soluciones**, haga clic con el botón secundario en el archivo de código de la cinta y, a continuación, haga clic en **Ver diseñador**.

- En **Explorador de soluciones**, seleccione el archivo de código de la cinta de opciones y, a continuación, haga clic en **Diseñador** en el menú **Ver** .

  El diseñador de la cinta de opciones contiene una ficha y un grupo predeterminados. Puede quitar la pestaña y el grupo predeterminados del diseñador de la cinta de opciones. Para quitar el grupo predeterminado, haga clic con el botón secundario en **Grupo1**y, a continuación, haga clic en **eliminar**. Para quitar la pestaña predeterminada, haga clic con el botón secundario en un área vacía de la superficie de diseño y, a continuación, haga clic en **quitar la pestaña de la cinta**.

  También puede Agregar pestañas, grupos y controles personalizados al diseñador de la cinta de opciones. Puede encontrar estos controles en el **cuadro de herramientas**, en el grupo controles de la cinta de opciones de **Office** . Hay tres maneras de agregar controles desde el grupo **controles** de la cinta de opciones de Office al diseñador de la cinta de opciones:

- Arrastre un control a un área adecuada en el diseñador de la cinta de opciones.

- Haga clic en un control y, a continuación, haga clic en un área adecuada en el diseñador de la cinta de opciones.

- Seleccione un área adecuada en el diseñador y, a continuación, haga doble clic en un control en el **cuadro de herramientas**.

### <a name="ribbon-design-workflow"></a>Flujo de trabajo de diseño de cinta
 Siga estos pasos básicos para diseñar el diseño de la cinta de opciones:

1. [Agregue una pestaña personalizada a la cinta](#AddTabToRibbon)de opciones.

2. [Agregue grupos a la pestaña](#AddGroupsToTab).

3. [Agregue controles a los grupos](#AddControlsToGroups).

   Los controles solo se pueden quitar en grupos; no se puede arrastrar un control directamente a una pestaña o a la cinta de opciones. Los grupos solo se pueden quitar en pestañas; no se puede arrastrar un grupo directamente a una cinta de opciones.

   Organice los controles arrastrándolos a las posiciones correctas. Puede establecer las propiedades de un control mediante la ventana **propiedades** .

   No se pueden arrastrar controles de una pestaña a otra en la cinta de opciones. Si desea trasladar un control a otra pestaña, debe usar el comando **cortar** para quitar el control de una pestaña y, a continuación, pegar el control en otra pestaña. Si corta el control y lo pega, el controlador de eventos deja de funcionar. Puede volver a conectar el controlador de eventos en la ventana **propiedades** . Para obtener más información, vea [ventana Propiedades](../ide/reference/properties-window.md).

### <a name="AddTabToRibbon"></a>Agregar pestañas personalizadas a la cinta de opciones
 Hay tres maneras de agregar una pestaña personalizada a la cinta de opciones:

- Agregue una pestaña desde el **cuadro de herramientas**.

- Haga clic con el botón secundario en el diseñador de la cinta y, a continuación, haga clic en **Agregar pestaña de cinta**.

- Abra el **Editor de la colección de pestañas**y haga clic en **Agregar**.

   Para abrir el **Editor de la colección de pestañas**, en la ventana **propiedades** , seleccione la propiedad **Tabs** y, a continuación, haga clic en el botón de puntos suspensivos ASP.net de la ![elipse de Mobile Designer](../sharepoint/media/mwellipsis.gif "Elipse del Diseñador de ASP.NET Mobile").

  Después de agregar una pestaña, puede agregar grupos para que contengan controles.

#### <a name="remove-custom-tabs-from-the-ribbon"></a>Quitar pestañas personalizadas de la cinta de opciones
 Hay tres maneras de quitar una pestaña personalizada de la cinta de opciones:

- Haga clic con el botón secundario en el diseñador y, a continuación, haga clic en **quitar ficha de cinta**.

- En el panel **comandos** de la ventana **propiedades** , haga clic en **quitar ficha de cinta**.

- Abra el **Editor de la colección de pestañas**, seleccione la pestaña y, a continuación, haga clic en **quitar**.

#### <a name="change-the-position-of-a-tab-on-the-ribbon"></a>Cambiar la posición de una pestaña en la cinta de opciones
 Puede cambiar el orden de las pestañas personalizadas en una cinta de opciones. También puede colocar las pestañas personalizadas antes o después de una pestaña integrada en la cinta de opciones. Para obtener más información, vea [Cómo: cambiar la posición de una pestaña en la cinta de opciones](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md).

#### <a name="customize-built-in-tabs-on-the-ribbon"></a>Personalizar pestañas integradas en la cinta de opciones
 Una pestaña integrada es una pestaña que ya está en la cinta de opciones de una aplicación Microsoft Office. Por ejemplo, la pestaña **datos** es una pestaña integrada en Excel.

 Puede agregar grupos y controles a una pestaña integrada. De forma predeterminada, un grupo personalizado aparece como el último grupo en una pestaña integrada, aunque puede moverse antes o después de cualquier grupo integrado en la pestaña.

 No se pueden quitar los grupos integrados.

 Para obtener más información sobre cómo personalizar una pestaña integrada, consulte [Cómo: personalizar una pestaña integrada](../vsto/how-to-customize-a-built-in-tab.md).

### <a name="AddGroupsToTab"></a>Agregar grupos a una pestaña
 Los grupos organizan lógicamente los controles en la cinta de opciones. Agregar grupos a pestañas. Agregue todos los demás controles al grupo.

### <a name="AddControlsToGroups"></a>Agregar controles a grupos
 Agregue uno o varios controles a un grupo. En la tabla siguiente se describe cada control.

|Control|Descripción|
|-------------|-----------------|
|**Box**|Contenedor que organiza los controles de un grupo. Puede agregar cualquier control a un cuadro excepto un separador, un grupo o una pestaña. Un cuadro puede ser horizontal o vertical.|
|**Button**|Un botón que inicia una acción. Puede Agregar un botón a un grupo, un grupo de botones, una lista desplegable, una galería, un menú o un botón de expansión.|
|**ButtonGroup**|Un grupo que contiene uno o varios botones, botones de alternancia, menús, botones de expansión y galerías. Puede Agregar un grupo de botones a un grupo o un menú.|
|**CheckBox**|Cuadro que se selecciona o se desactiva para activar o desactivar una opción.|
|**ComboBox**|Cuadro de edición con un cuadro de lista asociado. Los usuarios pueden escribir o seleccionar su elección. El cuadro muestra la selección actual. Utilice la propiedad <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.Items%2A> para agregar y quitar elementos en tiempo de ejecución antes o después de cargar la cinta de opciones en la aplicación de Office.|
|**Plegable**|Una lista de elementos que el usuario puede seleccionar. El usuario no puede escribir un nuevo elemento en una lista desplegable.<br /><br /> Use la propiedad <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.Items%2A> para agregar elementos a la lista. Puede Agregar y quitar elementos en tiempo de ejecución.<br /><br /> Use la propiedad <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.Buttons%2A> para agregar botones a la lista. Sin embargo, no puede agregar ni quitar botones en tiempo de ejecución después de cargar la cinta de opciones en la aplicación de Office.|
|**EditBox**|Cuadro en el que el usuario puede escribir texto.|
|**Galería**|Menú que presenta una matriz o cuadrícula de opciones visuales desde las que los usuarios pueden seleccionar. Puede controlar el diseño de las selecciones en el menú. Use las propiedades <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ColumnCount%2A> y <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.RowCount%2A> para especificar el número de filas y columnas que mostrarán los elementos y botones de la galería.|
|**Etiqueta**|Texto que puede usar para identificar controles en la cinta de opciones.|
|**Menu**|Lista desplegable que puede contener cualquiera de los controles siguientes:<br /><br /> -Botón<br />-Casilla<br />-Galería<br />-Menú<br />-Botón de expansión<br />-Botón de alternancia<br />-Separador<br /><br /> Para agregar un control a un menú en el diseñador de la cinta de opciones, haga clic en la flecha hacia abajo del menú para exponer la superficie de diseño del menú. A continuación, puede arrastrar los controles de la cinta de opciones desde el **cuadro de herramientas** hasta el menú. Para organizar los controles, arrástrelos hasta las posiciones deseadas.<br /><br /> Para agregar controles al <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> después de cargar la cinta de opciones en la aplicación de Office, debe establecer la propiedad <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.Dynamic%2A> en **true** antes de que se cargue la cinta de opciones. Para obtener información sobre cómo hacerlo, vea [información general sobre el modelo de objetos de la cinta](../vsto/ribbon-object-model-overview.md).|
|**Separator**|Barra fina utilizada para separar los elementos de una lista. Cuando se agrega a un grupo, la barra es vertical. Cuando se agrega a un menú, la barra es horizontal.|
|**SplitButton**|Botón con un menú asociado. Un botón de expansión puede contener cualquiera de los controles siguientes:<br /><br /> -Botón<br />-Casilla<br />-Galería<br />-Menú<br />-Botón de expansión<br />-Botón de alternancia<br />-Separador<br /><br /> Al igual que el menú, el botón de expansión tiene su propia superficie de diseño. Sin embargo, a diferencia de un menú, solo puede actualizar los elementos de un botón de expansión antes de que se cargue la cinta de opciones en la aplicación de Office. Para obtener información sobre cómo actualizar los elementos de un botón de expansión, vea [información general sobre el modelo de objetos de la cinta](../vsto/ribbon-object-model-overview.md).|
|**ToggleButton**|Botón que aparece presionado o no presionado.|

## <a name="HandleEventsSetProperties"></a>Controlar eventos y establecer propiedades
 El diseñador de la cinta de opciones le permite establecer las propiedades del control en tiempo de diseño mediante la ventana **propiedades** . Además, la cinta de opciones expone un modelo de objetos fuertemente tipados que se puede usar para obtener y establecer las propiedades de los controles de la cinta de opciones en tiempo de ejecución.

 Puede hacer doble clic en cualquier control del diseñador para abrir un controlador de eventos para el evento predeterminado del control. Puede crear controladores de eventos para todos los demás eventos de control mediante la ventana **propiedades** .

 Los eventos y las propiedades de la cinta de opciones se encuentran en el espacio de nombres <xref:Microsoft.Office.Tools.Ribbon>. El elemento **cinta (diseñador visual)** agrega automáticamente una referencia a este ensamblado en el proyecto e inserta la instrucción **using** o **Imports** correspondiente en la parte superior del archivo de código de la cinta de opciones.

 Para obtener información sobre cómo controlar los eventos de la cinta y establecer las propiedades de los controles de la cinta de opciones en tiempo de ejecución, vea [información general sobre el modelo de objetos Ribbon](../vsto/ribbon-object-model-overview.md).

## <a name="CustomizingMicrosoftOfficeButton"></a>Personalizar la vista backstage
 Puede usar el diseñador de la cinta de opciones para agregar controles al menú que se abre al hacer clic en la pestaña **archivo** . Este menú se denomina vista backstage.

 No se pueden colocar controles antes o después de los controles integrados mediante el diseñador de la cinta de opciones. Un control integrado es un control que ya aparece en la vista backstage. Si desea colocar los controles antes o después de los controles integrados, debe usar el XML de la cinta de opciones. Para obtener más información acerca de **la cinta (XML)** , vea [XML de la cinta](../vsto/ribbon-xml.md). Para obtener más información sobre cómo personalizar la vista backstage, vea [Introducción a la vista backstage de office 2010 para desarrolladores](/previous-versions/office/developer/office-2010/ee691833(v=office.14)) y [Personalización de la vista backstage de Office 2010 para desarrolladores](/previous-versions/office/developer/office-2010/ee815851(v=office.14)).

 [!INCLUDE[appliesto_ribbon_2010](../vsto/includes/appliesto-ribbon-2010-md.md)]

 Para obtener información sobre cómo agregar controles a la vista backstage, vea [Cómo: agregar controles a la vista Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md).

## <a name="Accessibility"></a>Accesibilidad en el diseñador de la cinta de opciones
 Puede usar métodos abreviados de teclado para trasladar controles en el diseñador de la cinta de opciones. Algunos métodos abreviados de teclado se aplican a todos los controles y algunos solo se aplican a los controles que tienen menús.

 En la tabla siguiente se muestran los métodos abreviados de teclado que se aplican a todos los controles.

|Acción|Método abreviado de teclado|
|------------|-----------------------|
|Mueva un control antes del control anterior en la lista.|**Ctrl**+**arriba**<br /><br /> **Ctrl**+**izquierda**|
|Mueve un control después del siguiente control de la lista.|**Ctrl**+**abajo**<br /><br /> **Ctrl**+**derecha**|
|Mueva la selección de un control a otro en el mismo grupo. En un panel desplegable, desplazarse entre el control primario y los controles del panel desplegable.|**Los**<br /><br /> **Vertical**|
|Recorrer en iteración hacia delante todos los controles.|**Tabulación**|
|Iterar hacia atrás a través de todos los controles.|**Mayús**+**Tabulador**|
|Eliminar el control o conjunto de controles seleccionado.|**Eliminar**|
|Copiar los controles seleccionados.|**Ctrl**+**C**|
|Cortar los controles seleccionados.|**Ctrl**+**X**|
|Pegar controles del portapapeles.|**Ctrl**+**V**|
|Seleccione el **cuadro de herramientas**.|**Ctrl**+**Alt**+**X**|
|Seleccione el componente primario.|**Esc**|

 En la tabla siguiente se muestran los métodos abreviados de teclado que se aplican solo al menú Microsoft Office, <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>y <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>.

|Acción|Método abreviado de teclado|
|------------|-----------------------|
|Seleccione el control primario si el panel desplegable está abierto y hay un control seleccionado en el panel desplegable.|**Izquierda**|
|Cierre el panel desplegable si el panel desplegable está abierto y está seleccionado control primario.|**Izquierda**|
|Abra el panel desplegable.|**Derecha**|
|Seleccione el primer control del panel desplegable si el panel desplegable está abierto.|**Derecha**|
|Cerrar un panel desplegable.|**Esc**|

## <a name="see-also"></a>Vea también

- [Información general sobre la cinta](../vsto/ribbon-overview.md)
- [XML de la cinta](../vsto/ribbon-xml.md)
- [Tutorial: crear una pestaña personalizada mediante el diseñador de la cinta de opciones](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Cómo: exportar una cinta de opciones del diseñador de la cinta de opciones a XML de la cinta](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)
- [Cómo: Introducción a la personalización de la cinta de opciones](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Obtener acceso a la cinta de opciones en tiempo de ejecución](../vsto/accessing-the-ribbon-at-run-time.md)
