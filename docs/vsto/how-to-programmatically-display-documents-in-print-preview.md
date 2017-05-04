---
title: "C&#243;mo: Mostrar documentos en Vista previa de impresi&#243;n mediante programaci&#243;n | Microsoft Docs"
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
  - "Word [desarrollo de Office en Visual Studio], mostrar documentos en vista previa de impresión"
  - "documentos [desarrollo de Office en Visual Studio], mostrar en vista previa de impresión"
ms.assetid: 96c7faea-9c5c-42b4-a009-08894a6d15c9
caps.latest.revision: 39
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 38
---
# C&#243;mo: Mostrar documentos en Vista previa de impresi&#243;n mediante programaci&#243;n
  Si una solución genera un informe, tal vez sea conveniente presentarlo al usuario en el modo Vista previa de impresión.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## Procedimientos para las personalizaciones de nivel de documento  
  
#### Para mostrar un documento en vista previa de impresión llamando al método PrintPreview  
  
1.  Llame al método <xref:Microsoft.Office.Tools.Word.Document.PrintPreview%2A> de la clase <xref:Microsoft.Office.Tools.Word.Document>. Para usar este ejemplo de código, ejecútelo desde la clase `ThisDocument` del proyecto.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#13](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#13)]
     [!code-vb[Trin_VstcoreWordAutomation#13](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#13)]  
  
#### Para mostrar un documento en vista previa de impresión llamando al método PrintPreview  
  
1.  Establezca la propiedad <xref:Microsoft.Office.Interop.Word._Application.PrintPreview%2A> del objeto <xref:Microsoft.Office.Interop.Word.Application> en **true**.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#14](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#14)]
     [!code-vb[Trin_VstcoreWordAutomation#14](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#14)]  
  
## Procedimientos para los complementos de VSTO  
  
#### Para mostrar un documento en vista previa de impresión llamando al método PrintPreview  
  
1.  Llame al método <xref:Microsoft.Office.Interop.Word._Document.PrintPreview%2A> del objeto <xref:Microsoft.Office.Interop.Word.Document> del que quiere obtener una vista previa. Para usar este ejemplo de código, ejecútelo desde la clase `ThisAddIn` del proyecto.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#13](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#13)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#13](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#13)]  
  
#### Para mostrar un documento en vista previa de impresión llamando al método PrintPreview  
  
1.  Establezca la propiedad <xref:Microsoft.Office.Interop.Word._Application.PrintPreview%2A> del objeto <xref:Microsoft.Office.Interop.Word.Application> en **true**.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#14](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#14)]
     [!code-vb[Trin_VstcoreWordAutomation#14](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#14)]  
  
## Vea también  
 [Cómo: Imprimir documentos mediante programación](../vsto/how-to-programmatically-print-documents.md)   
 [Cómo: Abrir documentos existentes mediante programación](../vsto/how-to-programmatically-open-existing-documents.md)   
 [Cómo: Crear nuevos documentos mediante programación](../vsto/how-to-programmatically-create-new-documents.md)  
  
  