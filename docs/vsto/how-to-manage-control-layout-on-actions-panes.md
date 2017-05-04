---
title: "C&#243;mo: Administrar el dise&#241;o de controles en paneles de acciones | Microsoft Docs"
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
  - "paneles de acciones [desarrollo de Office en Visual Studio], diseño de controles"
  - "controles [desarrollo de Office en Visual Studio], diseño en paneles de acciones"
  - "documentos inteligentes [desarrollo de Office en Visual Studio], diseño de controles"
ms.assetid: 857550d0-b9c0-4d2f-a947-dd955bcf2823
caps.latest.revision: 59
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 55
---
# C&#243;mo: Administrar el dise&#241;o de controles en paneles de acciones
  Los paneles de acciones se acoplan de manera predeterminada a la derecha de los documentos y hojas de cálculo. No obstante, también se pueden acoplar a la izquierda o en la parte superior o inferior.  Si se van a utilizar varios controles de usuario, se puede escribir código para apilarlos correctamente en el panel de acciones.  Para obtener más información, vea [Información general sobre paneles de acciones](../vsto/actions-pane-overview.md).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 El orden de pila de los controles dependerá de si el panel de acciones está acoplado vertical u horizontalmente.  
  
> [!NOTE]  
>  Es posible configurar los controles para cambiar de tamaño con el panel de acciones en caso de que el usuario decida cambiarlo en tiempo de ejecución.  Para ello, se puede utilizar la propiedad <xref:System.Windows.Forms.Control.Anchor%2A> de un control de formularios Windows Forms para acoplar los controles al panel de acciones.  Para obtener más información, vea [Cómo: Delimitar controles en formularios Windows Forms](../Topic/How%20to:%20Anchor%20Controls%20on%20Windows%20Forms.md).  
  
> [!NOTE]  
>  Es posible que su equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones.  La edición de Visual Studio que tenga y la configuración que esté usando determinan estos elementos.  Para obtener más información, vea [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/es-es/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Para establecer el orden de pila de los controles del panel de acciones  
  
1.  Abra un proyecto de nivel de documento para Microsoft Office Word que incluya un panel de acciones con varios controles de usuario o controles de panel de acciones anidados.  Para obtener más información, vea [Cómo: Agregar un panel de acciones a documentos de Word o libros de Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md).  
  
2.  En el **Explorador de soluciones**, haga clic con el botón secundario en **ThisDocument.vb** o en **ThisDocument.cs** y, a continuación, haga clic en **Ver código**.  
  
3.  En el controlador de eventos <xref:Microsoft.Office.Tools.ActionsPane.OrientationChanged> del panel de acciones, compruebe si la orientación del panel es horizontal.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#30](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#30)]
     [!code-vb[Trin_VstcoreActionsPaneWord#30](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#30)]  
  
4.  Si la orientación fuera horizontal, apile los controles del panel de acciones desde la izquierda; de lo contrario, apílelos desde arriba.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#31](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#31)]
     [!code-vb[Trin_VstcoreActionsPaneWord#31](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#31)]  
  
5.  En C\#, debe agregar un controlador de eventos para `ActionsPane` al controlador de eventos <xref:Microsoft.Office.Tools.Word.Document.Startup>.  Para obtener más información sobre cómo crear controladores de eventos, vea [Cómo: Crear controladores de eventos en proyectos de Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#32](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#32)]  
  
6.  Ejecute el proyecto y compruebe que los controles del panel de acciones se apilan de izquierda a derecha cuando el panel está acoplado en la parte superior del documento y que se apilan de arriba abajo cuando está en la parte derecha.  
  
## Ejemplo  
 [!code-csharp[Trin_VstcoreActionsPaneWord#29](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#29)]
 [!code-vb[Trin_VstcoreActionsPaneWord#29](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#29)]  
  
## Compilar el código  
 Para este ejemplo se necesita:  
  
-   Un proyecto de nivel de documento de Word con un panel de acciones que contiene varios controles de usuario o controles de panel de acciones anidados.  
  
## Vea también  
 [Información general sobre paneles de acciones](../vsto/actions-pane-overview.md)   
 [Cómo: Agregar un panel de acciones a documentos de Word o libros de Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Cómo: Agregar un panel de acciones a documentos de Word o libros de Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Tutorial: Insertar texto en un documento de un panel de acciones](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)   
 [Tutorial: Insertar texto en un documento de un panel de acciones](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)  
  
  