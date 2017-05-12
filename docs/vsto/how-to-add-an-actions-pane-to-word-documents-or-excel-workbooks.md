---
title: "C&#243;mo: Agregar un panel de acciones a documentos de Word o libros de Excel"
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
ms.assetid: cea3c2b6-9364-4134-b812-50888ad8bd76
caps.latest.revision: 63
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 62
---
# C&#243;mo: Agregar un panel de acciones a documentos de Word o libros de Excel
  Para agregar un panel de acciones a un documento de Microsoft Office Word o un libro de Microsoft Excel, primero cree un control de usuario de formularios Windows Forms.  A continuación, agregue el control de usuario a la propiedad <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> de campo `ThisDocument.ActionsPane` \(palabra\) o campo `ThisWorkbook.ActionsPane` \(Excel\) en el proyecto.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
> [!NOTE]  
>  Es posible que su equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones.  La edición de Visual Studio que tenga y la configuración que esté usando determinan estos elementos.  Para obtener más información, vea [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/es-es/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Crear el control de usuario  
 El siguiente procedimiento muestra cómo crear un control de usuario en un proyecto de word o excel.  También agrega al control de usuario un botón que escribe texto en el documento o el libro cuando se haga clic en.  
  
#### Para crear el control de usuario  
  
1.  Abra el proyecto de nivel de documento de word o de Excel en Visual Studio.  
  
2.  En el menú **Proyecto**, haga clic en **Agregar nuevo elemento**.  
  
3.  En el cuadro de diálogo **Agregar nuevo elemento**, seleccione **Control del panel de acciones**, denomínelo **HelloControl** y, a continuación, haga clic en **Agregar**.  
  
    > [!NOTE]  
    >  Alternativamente, puede agregar un elemento **Control de usuario** a su proyecto.  Las clases generadas por los elementos **Control del panel de acciones** y **Control de usuario** son equivalentes desde el punto de vista funcional.  
  
4.  En la pestaña **Windows Forms** del **Cuadro de herramientas**, arrastre un control **Button** hasta el control.  
  
    > [!NOTE]  
    >  Si el control no está visible en el diseñador, haga doble clic en **HelloControl** en el **Explorador de soluciones**.  
  
5.  Agregue código al controlador de eventos <xref:System.Windows.Forms.Control.Click> del botón.  El ejemplo siguiente se muestra el código para un documento de Microsoft Office Word.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#12](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/HelloControl.cs#12)]
     [!code-vb[Trin_VstcoreActionsPaneWord#12](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/HelloControl.vb#12)]  
  
6.  En C\#, debe agregar un controlador de eventos para el clic de botón.  Puede colocar este código en el constructor `HelloControl`, después de la llamada a `IntializeComponent`.  
  
     Para obtener información acerca de cómo crear controladores de eventos, vea [Cómo: Crear controladores de eventos en proyectos de Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#13](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/HelloControl.cs#13)]  
  
## Agregar el control de usuario al panel de acciones  
 Para mostrar el panel de acciones, agregue el control de usuario a la propiedad <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> de campo `ThisDocument.ActionsPane` \(palabra\) o campo `ThisWorkbook.ActionsPane` \(Excel\).  
  
#### Para agregar el control de usuario al panel de acciones  
  
1.  Agregue el código siguiente a la clase `ThisDocument` o `ThisWorkbook` como una declaración de nivel de clase \(no agregue este código a un método\).  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#14](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#14)]
     [!code-vb[Trin_VstcoreActionsPaneWord#14](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#14)]  
  
2.  Agregue el código siguiente al controlador de eventos `ThisDocument_Startup` de la clase `ThisDocument` o al controlador de eventos `ThisWorkbook_Startup` de la clase `ThisWorkbook` .  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#15](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#15)]
     [!code-vb[Trin_VstcoreActionsPaneWord#15](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#15)]  
  
## Vea también  
 [Información general sobre paneles de acciones](../vsto/actions-pane-overview.md)   
 [Tutorial: Insertar texto en un documento de un panel de acciones](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)   
 [Cómo: Administrar el diseño de controles en paneles de acciones](../vsto/how-to-manage-control-layout-on-actions-panes.md)   
 [Tutorial: Insertar texto en un documento de un panel de acciones](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)  
  
  