---
title: "C&#243;mo: Usar cuadros de di&#225;logo de Word en modo oculto mediante programaci&#243;n | Microsoft Docs"
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
  - "cuadros de diálogo, modo oculto en Word"
  - "cuadros de diálogo en modo oculto"
  - "Word [desarrollo de Office en Visual Studio], cuadros de diálogo"
ms.assetid: a5619325-8b54-41f1-becb-3f6eae7e4a6b
caps.latest.revision: 48
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 47
---
# C&#243;mo: Usar cuadros de di&#225;logo de Word en modo oculto mediante programaci&#243;n
  Puede realizar operaciones complejas con una llamada al método invocando los cuadros de diálogo integrados en Microsoft Office Word sin mostrarlos al usuario.  Puede hacerlo utilizando el método <xref:Microsoft.Office.Interop.Word.Dialog.Execute%2A> del objeto <xref:Microsoft.Office.Interop.Word.Dialog> sin llamar al método <xref:Microsoft.Office.Interop.Word.Dialog.Display%2A>.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## Ejemplos  
 En los siguientes ejemplos de código se muestra cómo usar el cuadro de diálogo **Configurar página** en modo oculto para establecer varias propiedades de configuración de página sin datos proporcionados por el usuario.  En los ejemplos se usa un objeto <xref:Microsoft.Office.Interop.Word.Dialog> para configurar un tamaño de página personalizado.  Los valores específicos de la configuración de página, como el margen superior, el margen inferior, etc., están disponibles como propiedades del objeto <xref:Microsoft.Office.Interop.Word.Dialog> enlazadas en tiempo de ejecución.  Word crea estas propiedades dinámicamente, en tiempo de ejecución.  
  
 En el siguiente ejemplo se muestra cómo realizar esta tarea en proyectos de Visual Basic donde **Option Strict** está desactivada y en los proyectos de Visual C\# destinados a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)].  En estos proyectos, puede usar las características de enlace en tiempo de ejecución en los compiladores de Visual C\# y Visual Basic.  Para usar este ejemplo, ejecútelo desde la clase `ThisDocument` o `ThisAddIn` del proyecto.  
  
 [!code-csharp[Trin_VstcoreWordAutomation#123](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#123)]
 [!code-vb[Trin_VstcoreWordAutomation#123](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#123)]  
  
 El siguiente ejemplo se muestra cómo realizar esta tarea en proyectos de Visual Basic donde **Option Strict** en.  En estos proyectos, debe usar la reflexión para tener acceso a las propiedades enlazadas en tiempo de ejecución.  Para usar este ejemplo, ejecútelo desde la clase `ThisDocument` o `ThisAddIn` del proyecto.  
  
 [!code-vb[Trin_VstcoreWordAutomation#104](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#104)]  
  
## Vea también  
 [Cómo: Usar cuadros de diálogo integrados en Word mediante programación](../vsto/how-to-programmatically-use-built-in-dialog-boxes-in-word.md)   
 [Información general acerca del modelo de objetos de Word](../vsto/word-object-model-overview.md)   
 [Enlace en tiempo de ejecución en las soluciones de Office](../vsto/late-binding-in-office-solutions.md)   
 [Reflexión &#40;C&#35; y Visual Basic&#41;](../Topic/Reflection%20(C%23%20and%20Visual%20Basic).md)  
  
  