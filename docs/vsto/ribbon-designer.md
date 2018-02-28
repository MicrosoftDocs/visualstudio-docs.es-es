---
title: "El Diseñador de la cinta de opciones | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
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
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: cab4a223f8e2d33185f37bc6ad90397ace1d56e1
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="ribbon-designer"></a>Diseñador de la cinta de opciones
  El Diseñador de la cinta de opciones es un lienzo de diseño visual. Use el Diseñador de la cinta de opciones para agregar pestañas personalizadas, grupos y controles a la cinta de opciones de una aplicación de Microsoft Office.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
 Para abrir el Diseñador de la cinta de opciones, agregue un **cinta (diseñador Visual)** elemento al proyecto. A continuación, puede usar las herramientas de diseño para las siguientes tareas:  
  
-   [Diseño de la cinta de opciones](#DesigningRibbonLayout)  
  
-   [Controlar eventos y establecer las propiedades de control](#HandleEventsSetProperties)  
  
-   [Agregar controles a la vista Backstage](#CustomizingMicrosoftOfficeButton)  
  
> [!NOTE]  
>  Hay algunas tareas que no se puede realizar mediante el Diseñador de la cinta de opciones. Para obtener más información sobre estas tareas y cómo se puede realizar, vea [información general de la cinta de opciones](../vsto/ribbon-overview.md).  
  
 ![vínculo a vídeo](../vsto/media/playvideo.gif "vínculo a vídeo") para una demostración en vídeo relacionada, vea [Cómo: usar el Diseñador de la cinta de opciones para personalizar la cinta de opciones en Outlook?](http://go.microsoft.com/fwlink/?LinkID=130312).  
  
## <a name="adding-a-ribbon-visual-designer-item-to-a-project"></a>Agregar un elemento cinta (diseñador Visual) a un proyecto  
 Para utilizar el Diseñador de la cinta de opciones, agregue un nuevo **cinta (diseñador Visual)** elemento al proyecto. Para obtener más información, consulte [How to: Get Started Customizing the Ribbon](../vsto/how-to-get-started-customizing-the-ribbon.md).  
  
 Cuando se agrega un nuevo **cinta (diseñador Visual)** elemento, Visual Studio agrega automáticamente los siguientes archivos al proyecto:  
  
-   Un archivo de código de la cinta de opciones. Este archivo tiene el nombre que especifique para la **cinta (diseñador Visual)** de elemento en el **Agregar nuevo elemento** cuadro de diálogo. Agregue código para controlar los eventos de la cinta de opciones en este archivo.  
  
-   Un archivo de código del Diseñador de la cinta. Este archivo contiene código generado por el Diseñador de la cinta de opciones y no debe editarse directamente.  
  
-   Un archivo de recursos. Este archivo contiene los valores de propiedad de cada control en la cinta de opciones.  
  
 Si ya tiene un **cinta (diseñador Visual)** elemento desde otro proyecto, puede volver a usarla en el proyecto actual mediante el uso de la **Agregar elemento existente** cuadro de diálogo.  
  
##  <a name="DesigningRibbonLayout"></a>Diseñar una cinta de opciones  
 Hay tres maneras de abrir el Diseñador de la cinta de opciones:  
  
-   En **el Explorador de soluciones**, haga doble clic en el archivo de código de la cinta de opciones.  
  
-   En **el Explorador de soluciones**, haga clic en el archivo de código de la cinta de opciones y, a continuación, haga clic en **Diseñador de vistas**.  
  
-   En **el Explorador de soluciones**, seleccione el archivo de código de la cinta de opciones y, a continuación, haga clic en **diseñador** en el **vista** menú.  
  
 El Diseñador de la cinta de opciones contiene una ficha predeterminada y un grupo. Puede quitar la ficha predeterminada y el grupo desde el Diseñador de la cinta de opciones. Para quitar el grupo predeterminado, haga clic en **Group1**y, a continuación, haga clic en **eliminar**. Para quitar la ficha predeterminada, haga clic en un área vacía de la superficie de diseño y, a continuación, haga clic en **Quitar ficha de la cinta de opciones**.  
  
 También puede agregar pestañas personalizadas, grupos y controles en el Diseñador de la cinta de opciones. Puede encontrar estos controles en la **cuadro de herramientas**, en la **controles de la cinta de Office** grupo. Hay tres maneras de agregar controles desde el **controles de la cinta de Office** grupo hasta el Diseñador de la cinta de opciones:  
  
-   Arrastre un control a un área apropiada en el Diseñador de la cinta de opciones.  
  
-   Haga clic en un control y, a continuación, haga clic en un área apropiada en el Diseñador de la cinta de opciones.  
  
-   Seleccione un área apropiada en el diseñador y, a continuación, haga doble clic en un control en el **cuadro de herramientas**.  
  
### <a name="ribbon-design-workflow"></a>Flujo de trabajo de diseño de la cinta de opciones  
 Siga estos pasos básicos para crear el diseño de la cinta de opciones:  
  
1.  [Agregar una pestaña personalizada a la cinta de opciones](#AddTabToRibbon).  
  
2.  [Agregar grupos a la ficha](#AddGroupsToTab).  
  
3.  [Agregar controles a los grupos](#AddControlsToGroups).  
  
 Se pueden quitar controles únicamente en grupos; no se puede arrastrar un control directamente a una pestaña o a la cinta de opciones. Se pueden quitar grupos sólo en pestañas; no puede arrastrar un grupo directamente a una cinta de opciones.  
  
 Organizar los controles arrastrándolos hacia las posiciones correctas. Puede establecer las propiedades de un control mediante la **propiedades** ventana.  
  
 No se puede arrastrar controles de una pestaña a otra en la cinta de opciones. Si desea mover un control a otra ficha, debe utilizar el **cortar** comando para quitar el control de una pestaña y, a continuación, pegarlo en otra ficha. Si corta el control y pegarlo, el controlador de eventos deja de funcionar. Puede volver a conectar el controlador de eventos en el **propiedades** ventana. Para obtener más información, consulte [ventana propiedades](/visualstudio/ide/reference/properties-window).  
  
###  <a name="AddTabToRibbon"></a>Agregar pestañas personalizadas a la cinta de opciones  
 Hay tres maneras de agregar una pestaña personalizada a la cinta de opciones:  
  
-   Agregar una pestaña de la **cuadro de herramientas**.  
  
-   Haga clic en el Diseñador de la cinta de opciones y, a continuación, haga clic en **Agregar pestaña de cinta de opciones**.  
  
-   Abra la **Editor de la colección de ficha**y, a continuación, haga clic en **agregar**.  
  
     Para abrir el **Editor de la colección de ficha**, en la **propiedades** ventana, seleccione la **pestañas** propiedad y, a continuación, haga clic en el botón de puntos suspensivos ![ASP.NET Mobile Elipse diseñador](../sharepoint/media/mwellipsis.gif "elipse del Diseñador de ASP.NET Mobile").  
  
 Después de agregar una pestaña, puede agregar grupos para que contenga controles.  
  
#### <a name="removing-custom-tabs-from-the-ribbon"></a>Quitar pestañas personalizadas de la cinta de opciones  
 Hay tres maneras de quitar una pestaña personalizada de la cinta de opciones:  
  
-   Haga clic en el diseñador y, a continuación, haga clic en **Quitar ficha de la cinta de opciones**.  
  
-   En el **comandos** panel de la **propiedades** ventana, haga clic en **Quitar ficha de la cinta de opciones**.  
  
-   Abra la **Editor de la colección de ficha**, seleccione la ficha y, a continuación, haga clic en **quitar**.  
  
#### <a name="changing-the-position-of-a-tab-on-the-ribbon"></a>Cambiar la posición de una pestaña en la cinta de opciones  
 Puede cambiar el orden de las fichas personalizadas en una cinta de opciones. También puede colocar pestañas personalizadas antes o después de una pestaña integrada en la cinta de opciones. Para obtener más información, consulte [Cómo: cambiar la posición de una pestaña en la cinta de opciones](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md).  
  
#### <a name="customizing-built-in-tabs-on-the-ribbon"></a>Personalizar las fichas integradas en la cinta de opciones  
 Una pestaña integrada es una pestaña que ya está en la cinta de opciones de una aplicación de Microsoft Office. Por ejemplo, el **datos** ficha es una pestaña integrada en Excel.  
  
 Puede agregar grupos y controles a una pestaña integrada. De forma predeterminada, aparece un grupo personalizado como último grupo en una pestaña integrada, aunque puede moverlo antes o después de cualquier grupo integrado en la pestaña.  
  
 No se puede quitar grupos integrados.  
  
 Para obtener más información sobre cómo personalizar una pestaña integrada, vea [Cómo: personalizar una pestaña integrada](../vsto/how-to-customize-a-built-in-tab.md).  
  
###  <a name="AddGroupsToTab"></a>Agregar grupos a una ficha  
 Los grupos organizan lógicamente los controles en la cinta de opciones. Agregar grupos a las fichas. Agregue todos los demás controles al grupo.  
  
###  <a name="AddControlsToGroups"></a>Agregar controles a grupos  
 Agregar uno o más controles a un grupo. En la tabla siguiente describe cada control.  
  
|Control|Descripción|  
|-------------|-----------------|  
|**Cuadro de**|Un contenedor que organiza los controles en un grupo. Puede agregar cualquier control a un cuadro, excepto un separador, un grupo o una tabulación. Un cuadro puede ser horizontal o vertical.|  
|**Button**|Un botón que inicia una acción. Puede agregar un botón a un grupo, un grupo de botones, una lista desplegable, una galería, un menú o un botón de expansión.|  
|**Grupo de botones**|Un grupo que contiene uno o varios botones, botones de alternancia, menús, botones de división y galerías. Puede agregar un grupo de botones a un grupo o un menú.|  
|**CheckBox**|Un cuadro que se selecciona o se borra para activar o desactivar una opción.|  
|**ComboBox**|Un cuadro de edición con un cuadro de lista adjuntado. Los usuarios pueden escribir o seleccionar su elección. El cuadro muestra la selección actual. Use la <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.Items%2A> propiedad para agregar y quitar elementos en tiempo de ejecución antes o después de carga la cinta de opciones en la aplicación de Office.|  
|**Lista desplegable**|Una lista de elementos que el usuario puede seleccionar. El usuario no es posible escribir un nuevo elemento en una lista desplegable.<br /><br /> Use la <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.Items%2A> propiedad para agregar elementos a la lista. Puede agregar y quitar elementos en tiempo de ejecución.<br /><br /> Use la <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.Buttons%2A> propiedad para agregar botones a la lista. Sin embargo, no se puede agregar y quitar botones en tiempo de ejecución después de carga la cinta de opciones en la aplicación de Office.|  
|**Cuadro de edición**|Un cuadro en el que el usuario puede escribir texto.|  
|**Galería**|Un menú que presenta una matriz o cuadrícula de opciones visuales de que los usuarios pueden seleccionar. Puede controlar el diseño de las selecciones en el menú. Use la <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ColumnCount%2A> y <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.RowCount%2A> propiedades para especificar el número de filas y columnas que se mostrarán los elementos y botones de la galería.|  
|**Label**|Texto que puede usar para identificar los controles en la cinta de opciones.|  
|**Menu**|Una lista desplegable que puede contener cualquiera de los siguientes controles:<br /><br /> -Botón<br />: Casilla de verificación<br />-Galería<br />-Menú<br />: Botón de expansión<br />: Botón de alternancia<br />-Separador<br /><br /> Para agregar un control a un menú en el Diseñador de la cinta de opciones, haga clic en la flecha hacia abajo en el menú para exponer la superficie de diseño del menú. A continuación, puede arrastrar los controles de cinta de opciones desde el **cuadro de herramientas** en el menú. Para organizar los controles, arrástrelos hasta la posición deseada.<br /><br /> Para agregar controles a la <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> después de carga la cinta de opciones en la aplicación de Office, debe establecer el <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.Dynamic%2A> propiedad **true** antes de que se cargue la cinta de opciones. Para obtener información acerca de cómo hacerlo, consulte [información general sobre el modelo de objetos de la cinta de opciones](../vsto/ribbon-object-model-overview.md).|  
|**Separator**|Barra delgada utilizada para separar elementos de una lista. Cuando se agrega a un grupo, la barra es vertical. Cuando se agrega a un menú, la barra es horizontal.|  
|**SplitButton**|Un botón con un menú asociado. Un botón de división puede contener cualquiera de los siguientes controles:<br /><br /> -Botón<br />: Casilla de verificación<br />-Galería<br />-Menú<br />: Botón de expansión<br />: Botón de alternancia<br />-Separador<br /><br /> Al igual que el menú, el botón de expansión tiene su propia superficie de diseño. Sin embargo, a diferencia de un menú, puede actualizar solo los elementos de un botón de división antes de carga la cinta de opciones en la aplicación de Office. Para obtener información sobre cómo actualizar los elementos de un botón de expansión, consulte [información general sobre el modelo de objetos de la cinta de opciones](../vsto/ribbon-object-model-overview.md).|  
|**ToggleButton**|Un botón que aparece o no presionado.|  
  
##  <a name="HandleEventsSetProperties"></a>Control de eventos y establecer propiedades  
 El Diseñador de la cinta de opciones le permite establecer propiedades de control en tiempo de diseño mediante la **propiedades** ventana. Además, la cinta de opciones expone un modelo de objetos fuertemente tipado que puede usar para obtener y establecer las propiedades de controles de cinta de opciones en tiempo de ejecución.  
  
 Hacer doble clic en cualquier control en el diseñador para abrir un controlador de eventos para el evento predeterminado del control. Puede crear controladores de eventos para todos los demás eventos de control mediante la **propiedades** ventana.  
  
 Propiedades y eventos de la cinta de opciones se encuentran en el <xref:Microsoft.Office.Tools.Ribbon> espacio de nombres. El **cinta (diseñador Visual)** elemento agrega automáticamente una referencia a este ensamblado en el proyecto e inserta la correspondiente **con** o **importaciones** instrucción en la parte superior la cinta de opciones archivo de código.  
  
 Para obtener información sobre el control de eventos de la cinta de opciones y la configuración de las propiedades de controles de cinta de opciones en tiempo de ejecución, consulte [información general sobre el modelo de objetos de la cinta de opciones](../vsto/ribbon-object-model-overview.md).  
  
##  <a name="CustomizingMicrosoftOfficeButton"></a>Personalizar la vista Backstage  
 Puede utilizar el Diseñador de la cinta de opciones para agregar controles al menú que se abre al hacer clic en el **archivo** ficha. Este menú se denomina vista Backstage.  
  
 No se puede colocar controles antes o después de los controles integrados mediante el Diseñador de la cinta de opciones. Un control integrado es un control que ya aparece en la vista Backstage. Si desea colocar controles antes o después de los controles integrados, debe usar XML de cinta de opciones. Para obtener más información acerca de **cinta (XML)**, consulte [XML de cinta de opciones](../vsto/ribbon-xml.md). Para obtener más información acerca de cómo personalizar la vista Backstage, consulte [Introducción a Office 2010 Backstage View for Developers](http://go.microsoft.com/fwlink/?LinkId=182189) y [personalizar Office 2010 Backstage View for Developers](http://go.microsoft.com/fwlink/?LinkId=182188).  
  
 [!INCLUDE[appliesto_ribbon_2010](../vsto/includes/appliesto-ribbon-2010-md.md)]  
  
 Para obtener información sobre cómo agregar controles a la vista Backstage, consulte [Cómo: agregar controles a la vista Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md).  
  
##  <a name="Accessibility"></a>Accesibilidad en el Diseñador de la cinta de opciones  
 Puede utilizar métodos abreviados de teclado para mover los controles en el Diseñador de la cinta de opciones. Algunos métodos abreviados de teclado se aplican a todos los controles y algunas se aplican sólo a los controles que tienen menús.  
  
 Métodos abreviados de teclado que se aplican a todos los controles se muestran en la tabla siguiente.  
  
|Acción|Método abreviado de teclado|  
|------------|-----------------------|  
|Mover un control antes de que el control anterior en la lista.|CTRL+FLECHA ARRIBA<br /><br /> CTRL+FLECHA IZQUIERDA|  
|Mover un control después del control siguiente en la lista.|CTRL+FLECHA ABAJO<br /><br /> CTRL+FLECHA DERECHA|  
|Mover la selección de un control a otro en el mismo grupo. En un panel desplegable, desplazarse entre el control primario y los controles en el panel de la lista desplegable.|ARRIBA<br /><br /> ABAJO|  
|Iterar hacia delante a través de todos los controles.|TAB|  
|Recorrer en iteración todos los controles hacia atrás.|MAYÚS+TAB|  
|Elimine el control seleccionado o un conjunto de controles.|SUPRIMIR|  
|Copie los controles seleccionados.|CTRL+C|  
|Cortar los controles seleccionados.|CTRL+X|  
|Pegar controles desde el Portapapeles.|CTRL+V|  
|Seleccione el **cuadro de herramientas**.|CTRL+ALT+X|  
|Seleccione el componente primario.|ESC|  
  
 Métodos abreviados de teclado que se aplican sólo en el menú de Microsoft Office, <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>, y <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton> se muestran en la tabla siguiente.  
  
|Acción|Método abreviado de teclado|  
|------------|-----------------------|  
|Seleccione el control primario si el panel desplegable está abierto y no hay un control seleccionado en el panel de lista desplegable.|IZQUIERDA|  
|Cierre el panel de lista desplegable si el panel desplegable está abierto y se selecciona el control primario.|IZQUIERDA|  
|Abra el panel de lista desplegable.|DERECHA|  
|Si se abre el panel de lista desplegable, seleccione el primer control en el panel de lista desplegable.|DERECHA|  
|Cerrar un panel de lista desplegable.|ESC|  
  
## <a name="see-also"></a>Vea también  
 [Información general de la cinta de opciones](../vsto/ribbon-overview.md)   
 [XML de la cinta de opciones](../vsto/ribbon-xml.md)   
 [Tutorial: Crear una pestaña personalizada usando el Diseñador de la cinta de opciones](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Cómo: exportar una cinta de opciones desde el Diseñador de la cinta de opciones a XML de la cinta de opciones](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)   
 [Cómo: empezar a personalizar la cinta de opciones](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Obtener acceso a la cinta en tiempo de ejecución](../vsto/accessing-the-ribbon-at-run-time.md)  
  
  