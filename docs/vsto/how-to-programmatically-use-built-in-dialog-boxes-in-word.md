---
title: "C&#243;mo: Usar cuadros de di&#225;logo integrados en Word mediante programaci&#243;n | Microsoft Docs"
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
  - "Word [desarrollo de Office en Visual Studio], cuadros de diálogo"
  - "cuadros de diálogo, Word"
ms.assetid: 0c7e4338-dead-4444-868b-3b0212368455
caps.latest.revision: 54
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 53
---
# C&#243;mo: Usar cuadros de di&#225;logo integrados en Word mediante programaci&#243;n
  Cuando se trabaja con Microsoft Office Word, a veces hay que presentar cuadros de diálogo para que el usuario especifique información.  Aunque puede crear sus propios cuadros de diálogo, también puede usar los cuadros de diálogo integrados en Word, que se exponen en la colección <xref:Microsoft.Office.Interop.Word.Dialogs> del objeto <xref:Microsoft.Office.Interop.Word.Application>.  Tiene a su disposición más de 200 cuadros de diálogo integrados, que se representan como enumeraciones.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## Mostrar cuadros de diálogo  
 Para mostrar un cuadro de diálogo, use uno de los valores de la enumeración <xref:Microsoft.Office.Interop.Word.WdWordDialog> para crear un objeto <xref:Microsoft.Office.Interop.Word.Dialog> que represente el cuadro de diálogo que desea mostrar.  A continuación, llame al método <xref:Microsoft.Office.Interop.Word.Dialog.Show%2A> del objeto <xref:Microsoft.Office.Interop.Word.Dialog>.  
  
 En el ejemplo de código siguiente se muestra cómo presentar el cuadro de diálogo **Abrir archivo**.  Para usar este ejemplo, ejecútelo desde la clase `ThisDocument` o `ThisAddIn` del proyecto.  
  
 [!code-csharp[Trin_VstcoreWordAutomation#100](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#100)]
 [!code-vb[Trin_VstcoreWordAutomation#100](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#100)]  
  
### Obtener acceso a miembros de cuadro de diálogo que están disponibles a través del enlace en tiempo de ejecución  
 Algunas propiedades y métodos de los cuadros de diálogo de Word solo están disponibles a través del enlace en tiempo de ejecución.  En proyectos de Visual Basic donde **Option Strict** on, deberá utilizar la reflexión para tener acceso a estos miembros.  Para obtener más información, vea [Enlace en tiempo de ejecución en las soluciones de Office](../vsto/late-binding-in-office-solutions.md).  
  
 El ejemplo de código siguiente se muestra cómo utilizar la propiedad de **Name** del cuadro de diálogo **Abrir archivo** en los proyectos de Visual Basic donde o en proyectos de Visual c\# **Option Strict** destinados [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)].  Para usar este ejemplo, ejecútelo desde la clase `ThisDocument` o `ThisAddIn` del proyecto.  
  
 [!code-csharp[Trin_VstcoreWordAutomation#122](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#122)]
 [!code-vb[Trin_VstcoreWordAutomation#122](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#122)]  
  
 El ejemplo de código siguiente muestra cómo utilizar la reflexión para tener acceso a la propiedad de **Name** del cuadro de diálogo **Abrir archivo** en los proyectos de Visual Basic donde **Option Strict** on.  Para usar este ejemplo, ejecútelo desde la clase `ThisDocument` o `ThisAddIn` del proyecto.  
  
 [!code-vb[Trin_VstcoreWordAutomation#102](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#102)]  
  
## Vea también  
 [Cómo: Usar cuadros de diálogo de Word en modo oculto mediante programación](../vsto/how-to-programmatically-use-word-dialog-boxes-in-hidden-mode.md)   
 [Información general acerca del modelo de objetos de Word](../vsto/word-object-model-overview.md)   
 [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Option Strict &#40;Instrucción&#41;](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [Reflexión &#40;C&#35; y Visual Basic&#41;](http://msdn.microsoft.com/library/5d1d1bcf-08de-4d0b-97a8-912d17c00f26)  
  
  