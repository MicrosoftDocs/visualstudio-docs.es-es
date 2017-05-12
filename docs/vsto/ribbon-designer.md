---
title: "Dise&#241;ador de la cinta de opciones"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Designer_Microsoft.VisualStudio.Tools.Office.Ribbon.Design.RibbonDesigner"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "controles [desarrollo de Office en Visual Studio], cinta de opciones"
  - "Cinta de opciones personalizada"
  - "Cinta de opciones personalizada, acerca del diseñador de la cinta de opciones"
  - "personalizar la cinta de opciones"
  - "personalizar la cinta de opciones, acerca del diseñador de la cinta de opciones"
  - "diseñadores [desarrollo de Office en Visual Studio], cinta de opciones"
  - "propiedades de solo lectura"
  - "Cinta [desarrollo de Office en Visual Studio], tareas comunes"
  - "Cinta [desarrollo de Office en Visual Studio], controles"
  - "Cinta [desarrollo de Office en Visual Studio], personalizar"
  - "Cinta [desarrollo de Office en Visual Studio], teclas de método abreviado"
  - "Cinta [desarrollo de Office en Visual Studio], diseñador visual"
  - "Diseñador de la cinta de opciones [desarrollo de Office en Visual Studio]"
ms.assetid: 26617206-f4da-416f-a18a-d817b2d4872d
caps.latest.revision: 79
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 78
---
# Dise&#241;ador de la cinta de opciones
  El diseñador de la cinta de opciones es un lienzo de diseño visual.  Use el diseñador de la cinta de opciones para agregar pestañas, grupos y controles personalizados a la cinta de opciones de una aplicación de Microsoft Office.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
 Para abrir el diseñador de la cinta de opciones, agregue un elemento **Cinta \(diseñador visual\)** al proyecto.  A continuación, puede utilizar las herramientas de diseño para las tareas siguientes:  
  
-   [Realizar el diseño de la cinta de opciones](#DesigningRibbonLayout)  
  
-   [Controlar eventos y establecer propiedades de control](#HandleEventsSetProperties)  
  
-   [Agregar controles a la vista Backstage](#CustomizingMicrosoftOfficeButton)  
  
> [!NOTE]  
>  Hay algunas tareas que no puede realizar con el diseñador de la cinta de opciones.  Para obtener más información sobre estas tareas y cómo puede llevarlas a cabo, vea [Información general sobre la cinta de opciones](../vsto/ribbon-overview.md).  
  
 ![vínculo a vídeo](../vsto/media/playvideo.png "vínculo a vídeo") Dispone de una demostración en vídeo relacionada en [How Do I: Use the Ribbon Designer to Customize the Ribbon in Outlook?](http://go.microsoft.com/fwlink/?LinkID=130312).  
  
## Agregar un elemento Cinta \(diseñador visual\) a un proyecto  
 Para utilizar el diseñador de la cinta de opciones, agregue un nuevo elemento **Cinta \(diseñador visual\)** al proyecto.  Para obtener más información, vea [Cómo: Iniciarse en la personalización de la cinta de opciones](../vsto/how-to-get-started-customizing-the-ribbon.md).  
  
 Al agregar un nuevo elemento **Cinta \(diseñador visual\)**, Visual Studio agrega automáticamente los archivos siguientes al proyecto:  
  
-   Un archivo de código de cinta de opciones.  Este archivo tiene el nombre especificado para el elemento **Cinta \(diseñador visual\)** en el cuadro de diálogo **Agregar nuevo elemento**.  Agregue código a este archivo para controlar los eventos de la cinta de opciones.  
  
-   Un archivo de código de diseñador de la cinta de opciones.  Este archivo contiene código generado por el diseñador de la cinta de opciones y no debe editarse directamente.  
  
-   Un archivo de recursos.  Este archivo contiene los valores de propiedad de cada control de la cinta de opciones.  
  
 Si ya tiene un elemento **Cinta \(diseñador visual\)** de otro proyecto, puede reutilizarlo en su proyecto actual mediante el cuadro de diálogo **Agregar elemento existente**.  
  
##  <a name="DesigningRibbonLayout"></a> Diseñar una cinta de opciones  
 Hay tres maneras de abrir el diseñador de la cinta de opciones:  
  
-   En el **Explorador de soluciones**, haga doble clic en el archivo de código de la cinta de opciones.  
  
-   En el **Explorador de soluciones**, haga clic con el botón secundario en el archivo de código de la cinta de opciones y, a continuación, haga clic en **Ver diseñador**.  
  
-   En el **Explorador de soluciones**, seleccione el archivo de código de la cinta de opciones y, a continuación, haga clic en **Diseñador** en el menú **Ver**.  
  
 El diseñador de la cinta de opciones contiene una ficha y un grupo predeterminados.  Puede quitar la ficha y el grupo predeterminados del diseñador de la cinta de opciones.  Para quitar el grupo predeterminado, haga clic con el botón secundario en **Grupo1** y, a continuación, haga clic en **Eliminar**.  Para quitar la pestaña predeterminada, haga clic con el botón secundario en una área vacía de la superficie de diseño y, a continuación, haga clic en **Quitar ficha de cinta**.  
  
 También puede agregar pestañas, grupos y controles personalizados al diseñador de la Cinta.  Puede buscar estos controles en el **Cuadro de herramientas**, en el grupo **Controles de la cinta de opciones de Office**.  Hay tres maneras de agregar controles desde el grupo **Controles de la cinta de opciones de Office** al diseñador de la cinta de opciones:  
  
-   Arrastre un control hacia un área adecuada en el diseñador de la cinta de opciones.  
  
-   Haga clic en un control y, a continuación, haga clic en un área adecuada del diseñador de la cinta de opciones.  
  
-   Seleccione un área adecuada en el diseñador y, a continuación, haga doble clic en un control en el **Cuadro de herramientas**.  
  
### Flujo de trabajo del diseño de la cinta de opciones  
 Siga estos pasos básicos para realizar el diseño de la cinta de opciones:  
  
1.  [Agregar una pestaña personalizada a la Cinta](#AddTabToRibbon).  
  
2.  [Agregue grupos a la ficha](#AddGroupsToTab).  
  
3.  [Agregue controles a los grupos](#AddControlsToGroups).  
  
 Los controles sólo se pueden colocar en grupos; no puede arrastrar directamente un control a una ficha ni a la cinta de opciones.  Los grupos sólo se pueden colocar en fichas; no puede arrastrar directamente un grupo a una cinta de opciones.  
  
 Organice los controles arrastrándolos hacia las posiciones correctas.  También puede establecer las propiedades de un control mediante la ventana **Propiedades**.  
  
 No puede arrastrar controles de una ficha a otra en la cinta de opciones.  Si desea mover un control a otra ficha, debe utilizar el comando **Cortar** para quitar el control de una ficha y, a continuación, pegarlo en otra.  Si corta el control y lo pega, el controlador de eventos detiene el funcionamiento.  Puede volver a conectar el controlador de eventos en la ventana **Propiedades**.  Para obtener más información, vea [Propiedades &#40;ventana&#41;](../ide/reference/properties-window.md).  
  
###  <a name="AddTabToRibbon"></a> Agregar pestañas personalizadas a la Cinta.  
 Hay tres maneras de agregar una pestaña personalizada a la Cinta:  
  
-   Agregue una ficha desde el **Cuadro de herramientas**.  
  
-   Haga clic con el botón secundario en el diseñador de la cinta de opciones y, a continuación, haga clic en **Agregar ficha de cinta**.  
  
-   Abra el **Editor de la colección de fichas** y, a continuación, haga clic en **Agregar**.  
  
     Para abrir el **Editor de la colección de fichas**, en la ventana **Propiedades**, seleccione la propiedad **Fichas** y, a continuación, haga clic en el botón de puntos suspensivos ![Elipse del Diseñador de ASP.NET Mobile](../sharepoint/media/mwellipsis.png "Elipse del Diseñador de ASP.NET Mobile").  
  
 Después de agregar una ficha, puede agregar grupos para contener controles.  
  
#### Quitar pestañas personalizadas de la Cinta  
 Hay tres maneras de quitar una pestaña personalizada de la Cinta:  
  
-   Haga clic con el botón secundario en el diseñador y, a continuación, haga clic en **Quitar ficha de cinta**.  
  
-   En el panel **Comandos** de la ventana **Propiedades**, haga clic en **Quitar ficha de cinta**.  
  
-   Abra el **Editor de la colección de fichas**, seleccione la ficha y, a continuación, haga clic en **Quitar**.  
  
#### Cambiar la posición de una pestaña en la Cinta  
 Puede cambiar el orden de las pestañas personalizadas en una Cinta.  También puede colocar las pestañas personalizadas antes o después de una pestaña integrada en la Cinta.  Para obtener más información, vea [Cómo: Cambiar la posición de una pestaña en la cinta de opciones](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md).  
  
#### Personalizar las fichas integradas en la cinta de opciones  
 Una ficha integrada es una ficha que ya está en la cinta de opciones de una aplicación de Microsoft Office.  Por ejemplo, la ficha **Datos** es una ficha integrada en Excel.  
  
 Puede agregar grupos y controles a una ficha integrada.  De forma predeterminada, aparece un grupo personalizado como último grupo en una ficha integrada, aunque puede moverlo antes o después de cualquier grupo integrado en la ficha.  
  
 No puede quitar los grupos integrados.  
  
 Para obtener detalles sobre cómo personalizar una ficha integrada, vea [Cómo: Personalizar una pestaña integrada](../vsto/how-to-customize-a-built-in-tab.md).  
  
###  <a name="AddGroupsToTab"></a> Agregar grupos a una ficha  
 Los grupos organizan lógicamente los controles de la cinta de opciones.  Agregue grupos a las fichas.  Agregue todos los demás controles al grupo.  
  
###  <a name="AddControlsToGroups"></a> Agregar controles a grupos  
 Agregue uno o varios controles a un grupo.  En la tabla siguiente se describe cada control.  
  
|Control|Descripción|  
|-------------|-----------------|  
|**Box**|Contenedor que organiza los controles de un grupo.  Puede agregar cualquier control a un cuadro, excepto un separador, un grupo o una ficha.  Un cuadro puede ser horizontal o vertical.|  
|**Button**|Botón que inicia una acción.  Puede agregar un botón a un grupo, un grupo de botones, una lista desplegable, una galería, un menú o un botón de expansión.|  
|**ButtonGroup**|Grupo que contiene uno o varios botones, botones de alternancia, menús, botones de expansión y galerías.  Puede agregar un grupo de botones a un grupo o un menú.|  
|**CheckBox**|Cuadro que se selecciona o se borra para activar o desactivar una opción.|  
|**ComboBox**|Cuadro de edición con un cuadro de lista asociado.  Los usuarios pueden escribir o seleccionar su opción.  El cuadro muestra la selección actual.  Utilice la propiedad <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.Items%2A> para agregar y quitar elementos en tiempo de ejecución antes o después de cargar la cinta de opciones en la aplicación de Office.|  
|**DropDown**|Lista de elementos que el usuario puede seleccionar.  El usuario no puede escribir un nuevo elemento en una lista desplegable.<br /><br /> Utilice la propiedad <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.Items%2A> para agregar elementos a la lista.  Puede agregar y quitar elementos en tiempo de ejecución.<br /><br /> Utilice la propiedad <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.Buttons%2A> para agregar botones a la lista.  Sin embargo, no puede agregar ni quitar botones en tiempo de ejecución una vez cargada la cinta de opciones en la aplicación de Office.|  
|**EditBox**|Cuadro donde el usuario puede escribir texto.|  
|**Gallery**|Menú que presenta una matriz o cuadrícula de opciones visuales entre las que los usuarios pueden seleccionar.  Puede controlar el diseño de las selecciones en el menú.  Utilice las propiedades <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ColumnCount%2A> y <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.RowCount%2A> para especificar el número de filas y columnas que mostrarán los elementos y botones de la galería.|  
|**Etiqueta**|Texto que puede utilizar para identificar controles en la cinta de opciones.|  
|**Menú**|Lista desplegable que puede contener cualquiera de los controles siguientes:<br /><br /> -   Button<br />-   Check Box<br />-   Gallery<br />-   Menú<br />-   Split Button<br />-   Botón de alternancia<br />-   Separator<br /><br /> Para agregar un control a un menú en el diseñador de la cinta de opciones, haga clic en la flecha abajo del menú para exponer la superficie de diseño del menú.  A continuación, puede arrastrar los controles de la cinta de opciones desde el **Cuadro de herramientas** al menú.  Para organizar los controles, arrástrelos hacia las posiciones deseadas.<br /><br /> Para agregar controles a <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> después de cargar la cinta de opciones en la aplicación de Office, debe establecer la propiedad <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.Dynamic%2A> en **true** antes de cargar la cinta de opciones.  Para obtener información sobre cómo realizar esta acción, vea [Información general sobre el modelo de objetos para la cinta de opciones](../vsto/ribbon-object-model-overview.md).|  
|**Separator**|Barra delgada utilizada para separar elementos de una lista.  Cuando se agrega a un grupo, la barra es vertical.  Cuando se agrega a un menú, la barra es horizontal.|  
|**SplitButton**|Botón con un menú asociado.  Un botón de expansión puede contener cualquiera de los controles siguientes:<br /><br /> -   Button<br />-   Check Box<br />-   Gallery<br />-   Menú<br />-   Split Button<br />-   Botón de alternancia<br />-   Separator<br /><br /> Como el menú, el botón de expansión tiene su propia superficie de diseño.  Sin embargo, a diferencia de un menú, sólo puede actualizar los elementos de un botón de expansión antes de cargar la cinta de opciones en la aplicación de Office.  Para obtener información sobre cómo actualizar los elementos de un botón de expansión, vea [Información general sobre el modelo de objetos para la cinta de opciones](../vsto/ribbon-object-model-overview.md).|  
|**ToggleButton**|Botón que aparece presionado o sin presionar.|  
  
##  <a name="HandleEventsSetProperties"></a> Controlar eventos y establecer propiedades  
 El diseñador de la cinta de opciones permite establecer propiedades de control en tiempo de diseño utilizando la ventana **Propiedades**.  Además, la cinta de opciones expone un modelo de objetos fuertemente tipados que puede utilizar para obtener y establecer las propiedades de los controles de la cinta de opciones en tiempo de ejecución.  
  
 Puede hacer doble clic en cualquier control en el diseñador para abrir un controlador para el evento predeterminado del control.  Puede crear controladores para todos los demás eventos del control desde la ventana **Propiedades**.  
  
 Los eventos y las propiedades de la cinta de opciones se encuentran en el espacio de nombres <xref:Microsoft.Office.Tools.Ribbon>.  El elemento **Cinta \(diseñador visual\)** agrega automáticamente una referencia a este ensamblado en el proyecto e inserta la instrucción **using** o **Imports** adecuada en la parte superior del archivo de código de la cinta de opciones.  
  
 Para obtener información sobre el control de los eventos de la cinta de opciones y el establecimiento de las propiedades de los controles de la cinta de opciones en tiempo de ejecución, vea [Información general sobre el modelo de objetos para la cinta de opciones](../vsto/ribbon-object-model-overview.md).  
  
##  <a name="CustomizingMicrosoftOfficeButton"></a> Personalización de la vista Backstage  
 Puede usar el diseñador de la cinta de opciones para agregar controles al menú que se abre al hacer clic en la pestaña **Archivo**.  Este menú se denomina la vista Backstage.  
  
 No puede colocar controles antes o después de los controles integrados usando el diseñador de la cinta de opciones.  Un control integrado es un control que ya aparece en la vista Backstage.  Si desea colocar controles antes o después de los controles integrados, debe utilizar Cinta XML.  Para obtener más información sobre la **Cinta \(XML\)**, vea [XML de la cinta de opciones](../vsto/ribbon-xml.md).  Para obtener más información sobre la personalización de la vista Backstage, vea [Introducción a la vista Backstage de Office 2010 para desarrolladores](http://go.microsoft.com/fwlink/?LinkId=182189) y [Personalización de la vista Backstage de Office 2010 para desarrolladores](http://go.microsoft.com/fwlink/?LinkId=182188).  
  
 [!INCLUDE[appliesto_ribbon_2010](../vsto/includes/appliesto-ribbon-2010-md.md)]  
  
 Para obtener información sobre la adición de controles a la vista Backstage, vea [Cómo: Agregar controles en la vista Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md).  
  
##  <a name="Accessibility"></a> Accesibilidad en el diseñador de la cinta de opciones  
 Puede utilizar los métodos abreviados de teclado para mover controles en el diseñador de la cinta de opciones.  Algunos métodos abreviados de teclado se aplican a todos los controles y algunos sólo se aplican a los controles que tienen menús.  
  
 En la tabla siguiente se muestran los métodos abreviados de teclado que se aplican a todos los controles.  
  
|Acción|Método abreviado de teclado|  
|------------|---------------------------------|  
|Mover un control antes del control anterior en la lista.|CTRL\+FLECHA ARRIBA<br /><br /> CTRL\+FLECHA IZQUIERDA|  
|Mover un control después del control siguiente en la lista.|CTRL\+FLECHA ABAJO<br /><br /> CTRL\+FLECHA DERECHA|  
|Mover la selección de un control a otro en el mismo grupo.  En un panel desplegable, desplazarse entre el control primario y los controles del panel desplegable.|ARRIBA<br /><br /> ABAJO|  
|Recorrer en iteración hacia delante todos los controles.|TAB|  
|Recorrer en iteración hacia atrás todos los controles.|MAYÚS\+TAB|  
|Eliminar el control o conjunto de controles seleccionado.|SUPR|  
|Copiar los controles seleccionados.|CTRL\+C|  
|Cortar los controles seleccionados.|CTRL\+X|  
|Pegar controles desde el Portapapeles.|CTRL\+V|  
|Seleccionar el **Cuadro de herramientas**.|CTRL\+ALT\+X|  
|Seleccionar el componente primario.|ESC|  
  
 En la tabla siguiente se muestran los métodos abreviados de teclado que sólo se aplican al menú de Microsoft Office, <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>y <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>.  
  
|Acción|Método abreviado de teclado|  
|------------|---------------------------------|  
|Seleccionar el control primario si el panel desplegable está abierto y existe un control seleccionado en el panel desplegable.|IZQUIERDA|  
|Cerrar el panel desplegable si el panel desplegable está abierto y el control primario está seleccionado.|IZQUIERDA|  
|Abrir el panel desplegable.|DERECHA|  
|Seleccionar el primer control del panel desplegable si éste está abierto.|DERECHA|  
|Cerrar un panel desplegable.|ESC|  
  
## Vea también  
 [Información general sobre la cinta de opciones](../vsto/ribbon-overview.md)   
 [XML de la cinta de opciones](../vsto/ribbon-xml.md)   
 [Tutorial: Crear una pestaña personalizada usando el diseñador de la cinta de opciones](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Cómo: Exportar una cinta de opciones del diseñador de la cinta de opciones a XML de la cinta de opciones](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)   
 [Cómo: Iniciarse en la personalización de la cinta de opciones](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Obtener acceso a la cinta de opciones en tiempo de ejecución](../vsto/accessing-the-ribbon-at-run-time.md)  
  
  