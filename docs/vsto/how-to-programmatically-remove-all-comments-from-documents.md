---
title: "C&#243;mo: Quitar todos los comentarios de documentos mediante programaci&#243;n"
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
  - "documentos [desarrollo de Office en Visual Studio], quitar comentarios"
  - "comentarios, quitar de documentos"
ms.assetid: 920de39a-3b6d-4682-bca6-f4b4dedda1ac
caps.latest.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 23
---
# C&#243;mo: Quitar todos los comentarios de documentos mediante programaci&#243;n
  Use el método DeleteAllComments para quitar todos los comentarios de un documento de Microsoft Office Word.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### Para quitar todos los comentarios de un documento que forma parte de una personalización de nivel de documento  
  
1.  Llame al método <xref:Microsoft.Office.Tools.Word.Document.DeleteAllComments%2A> de la clase `ThisDocument` en su proyecto. Para usar este ejemplo de código, ejecútelo desde la clase `ThisDocument`.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#119](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#119)]
     [!code-vb[Trin_VstcoreWordAutomation#119](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#119)]  
  
### Para quitar todos los comentarios de un documento mediante un complemento de VSTO  
  
1.  Llame al método <xref:Microsoft.Office.Interop.Word._Document.DeleteAllComments%2A> del <xref:Microsoft.Office.Interop.Word.Document> del que quiere quitar los comentarios.  
  
     El ejemplo de código siguiente quita todos los comentarios del documento activo. Para usar este ejemplo de código, ejecútelo desde la clase `ThisAddIn` del proyecto.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#119](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#119)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#119](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#119)]  
  
## Vea también  
 [Cómo: Agregar comentarios al texto en documentos mediante programación](../vsto/how-to-programmatically-add-comments-to-text-in-documents.md)   
 [Elemento host Document](../vsto/document-host-item.md)  
  
  