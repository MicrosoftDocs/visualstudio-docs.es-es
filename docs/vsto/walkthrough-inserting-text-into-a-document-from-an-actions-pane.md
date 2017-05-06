---
title: "Tutorial: Insertar texto en un documento de un panel de acciones"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "paneles de acciones [desarrollo de Office en Visual Studio], agregar controles"
  - "paneles de acciones [desarrollo de Office en Visual Studio], crear en Word"
  - "documentos inteligentes [desarrollo de Office en Visual Studio], agregar controles"
  - "documentos inteligentes [desarrollo de Office en Visual Studio], crear en Word"
ms.assetid: fd14c896-5737-4a20-94f7-6064b67112c5
caps.latest.revision: 70
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 69
---
# Tutorial: Insertar texto en un documento de un panel de acciones
  En este tutorial se muestra el modo de crear un panel de acciones en un documento de Microsoft Office Word.  El panel de acciones contiene dos controles que recopilan datos y, a continuación, envían el texto al documento.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 En este tutorial se muestran las tareas siguientes:  
  
-   Diseñar una interfaz con los controles de formularios Windows Forms en un control del panel de acciones.  
  
-   Mostrar el panel de acciones cuando se abra la aplicación.  
  
> [!NOTE]  
>  Es posible que su equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones.  La edición de Visual Studio que tenga y la configuración que esté usando determinan estos elementos.  Para obtener más información, vea [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/es-es/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] o [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
## Crear el proyecto  
 El primer paso es crear el proyecto de documento de Word.  
  
#### Para crear un nuevo proyecto  
  
1.  Cree un proyecto de documento de Word con el nombre Mi panel de acciones básico.  En el asistente, seleccione **Crear un nuevo documento**.  Para obtener más información, vea [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio abre el nuevo documento de Word en el diseñador y agrega el proyecto **Mi panel de acciones básico** al **Explorador de soluciones**.  
  
## Agregar texto y marcadores al documento  
 El panel de acciones enviará el texto a los marcadores del documento.  Para diseñar el documento, escriba algún texto para crear un formulario básico.  
  
#### Para agregar texto al documento  
  
1.  Escriba el texto siguiente en el documento de Word:  
  
     21 de marzo de 2008  
  
     Nombre  
  
     Dirección  
  
     Este es un ejemplo de un panel de acciones básico en Word.  
  
 Puede agregar un control <xref:Microsoft.Office.Tools.Word.Bookmark> al documento si lo arrastra desde el **Cuadro de herramientas** de Visual Studio o si utiliza el cuadro de diálogo **Marcador** de Word.  
  
#### Para agregar un control para marcador al documento  
  
1.  Desde la ficha **Controles de Word** del **Cuadro de herramientas**, arrastre un control <xref:Microsoft.Office.Tools.Word.Bookmark> al documento.  
  
     Aparece el cuadro de diálogo **Agregar control de marcador**.  
  
2.  Seleccione la palabra **Nombre**, sin seleccionar la marca de párrafo, y haga clic en **Aceptar**.  
  
    > [!NOTE]  
    >  La marca de párrafo debe estar fuera del marcador.  Si no se ven las marcas de párrafo en el documento, haga clic en el menú **Herramientas**, elija **Herramientas de Microsoft Office Word** y, a continuación, haga clic en **Opciones**.  Haga clic en la ficha **Ver** y active la casilla **Marcas de párrafo** en la sección **Marcas de formato** del cuadro de diálogo **Opciones**.  
  
3.  En la ventana **Propiedades**, cambie la propiedad **Nombre** de **Bookmark1** a **showName**.  
  
4.  Seleccione la palabra **Dirección**, sin seleccionar la marca de párrafo.  
  
5.  En la pestaña **Insertar** de la cinta de opciones, en el grupo **Vínculos**, haga clic en **Marcador**.  
  
6.  En el cuadro de diálogo **Marcador**, escriba **showAddress** en el cuadro **Nombre de marcador** y haga clic en **Agregar**.  
  
## Agregar controles al panel de acciones  
 Para diseñar la interfaz del panel de acciones, agregue un control del panel de acciones al proyecto y, a continuación, agregue controles de formularios Windows Forms al control del panel de acciones.  
  
#### Para agregar un control del panel de acciones  
  
1.  Seleccione el proyecto **Mi panel de acciones básico** en el **Explorador de soluciones**.  
  
2.  En el menú **Proyecto**, haga clic en **Agregar nuevo elemento**.  
  
3.  En el cuadro de diálogo **Agregar nuevo elemento**, haga clic en **Control del panel de acciones**, asígnele el nombre **InsertTextControl** y haga clic en **Agregar**.  
  
#### Para agregar controles Windows Form al control del panel de acciones  
  
1.  Si el control del panel de acciones no está visible en el diseñador, haga doble clic en **InsertTextControl**.  
  
2.  En la ficha **Controles comunes** del **Cuadro de herramientas**, arrastre un control **Label** hasta el control del panel de acciones.  
  
3.  Cambie la propiedad **Text** del control Label a **Name**.  
  
4.  Agregue un control **Textbox** al control del panel de acciones y cambie las siguientes propiedades.  
  
    |Propiedad|Valor|  
    |---------------|-----------|  
    |**Nombre**|**getName**|  
    |**Size**|**130, 20**|  
  
5.  Agregue un segundo control **Label** al control del panel de acciones y cambie la propiedad **Text** a **Address**.  
  
6.  Agregue un segundo control **Textbox** al control del panel de acciones y cambie las siguientes propiedades.  
  
    |Propiedad|Valor|  
    |---------------|-----------|  
    |**Nombre**|**getAddress**|  
    |**AcceptsReturn**|**True**|  
    |**Multiline**|**True**|  
    |**Size**|**130, 40**|  
  
7.  Agregue un control **Button** al control del panel de acciones y cambie las siguientes propiedades.  
  
    |Propiedad|Valor|  
    |---------------|-----------|  
    |**Nombre**|**addText**|  
    |**Texto**|**Insert**|  
  
## Agregar código al texto Insertar en el documento  
 En el panel de acciones, escriba código que inserte el texto de los cuadros de texto en los controles <xref:Microsoft.Office.Tools.Word.Bookmark> adecuados del documento.  Puede utilizar la clase `Globals` para tener acceso a los controles del documento desde los controles del panel de acciones.  Para obtener más información, vea [Acceso global a objetos en los proyectos de Office](../vsto/global-access-to-objects-in-office-projects.md).  
  
#### Para insertar texto del panel de acciones en un marcador del documento  
  
1.  Agregue el siguiente código al controlador de eventos <xref:System.Windows.Forms.Control.Click> del botón **addText**.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#8](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/InsertTextControl.cs#8)]
     [!code-vb[Trin_VstcoreActionsPaneWord#8](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/InsertTextControl.vb#8)]  
  
2.  En C\#, debe agregar un controlador de eventos para el clic de botón.  Puede colocar este código en el constructor `InsertTextControl`, después de la llamada a `IntializeComponent`.  Para obtener más información sobre cómo crear controladores de eventos, vea [Cómo: Crear controladores de eventos en proyectos de Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#9](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/InsertTextControl.cs#9)]  
  
## Agregar código para mostrar el panel de acciones  
 Para mostrar el panel de acciones, agregue el control que ha creado a la colección de controles.  
  
#### Para mostrar el panel de acciones  
  
1.  Cree una nueva instancia del control del panel de acciones en la clase `ThisDocument`.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#10)]
     [!code-vb[Trin_VstcoreActionsPaneWord#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#10)]  
  
2.  Agregue el código siguiente al controlador de eventos <xref:Microsoft.Office.Tools.Word.Document.Startup> de la clase `ThisDocument`.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#11)]
     [!code-vb[Trin_VstcoreActionsPaneWord#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#11)]  
  
## Probar la aplicación  
 Pruebe el documento para comprobar que el panel de acciones se abre cuando se abre el documento y que el texto escrito en los cuadros de texto se inserta en los marcadores cuando se hace clic en el botón.  
  
#### Para probar el documento  
  
1.  Presione F5 para ejecutar el proyecto.  
  
2.  Confirme que el panel de acciones está visible.  
  
3.  Escriba su nombre y dirección en los cuadros de texto del panel de acciones y haga clic en **Insertar**.  
  
## Pasos siguientes  
 Éstas son algunas de las tareas que pueden venir a continuación:  
  
-   Crear un panel de acciones en Excel.  Para obtener más información, vea [How to: Add an Actions Pane to Excel Workbooks](http://msdn.microsoft.com/es-es/62abfce6-e44f-419d-85d8-26bf59f33872).  
  
-   Enlazar datos a controles en un panel de acciones.  Para obtener más información, vea [Tutorial: Enlazar datos a controles en un panel de acciones de Word](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md).  
  
## Vea también  
 [Información general sobre paneles de acciones](../vsto/actions-pane-overview.md)   
 [Cómo: Agregar un panel de acciones a documentos de Word o libros de Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [How to: Add an Actions Pane to Excel Workbooks](http://msdn.microsoft.com/es-es/62abfce6-e44f-419d-85d8-26bf59f33872)   
 [Cómo: Administrar el diseño de controles en paneles de acciones](../vsto/how-to-manage-control-layout-on-actions-panes.md)   
 [Bookmark &#40;Control&#41;](../vsto/bookmark-control.md)  
  
  