---
title: "C&#243;mo: Cerrar documentos de Visio mediante programaci&#243;n"
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
  - "documentos [desarrollo de Office en Visual Studio], cerrar documentos de Visio"
  - "Visio [desarrollo de Office en Visual Studio], cerrar documentos de Visio"
ms.assetid: 59c0e215-a4c1-4b39-a491-37534f172705
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# C&#243;mo: Cerrar documentos de Visio mediante programaci&#243;n
  Puede cerrar el documento de Microsoft Office Visio activo con el método Microsoft.Office.Interop.Visio.Document.Close.  
  
 Para obtener información más detallada sobre este método, vea la documentación de referencia de VBA del método [Microsoft.Office.Interop.Visio.Document.Close](HV10070225).  
  
## Cerrar el documento activo  
  
#### Para cerrar el documento activo  
  
-   Llame al método Microsoft.Office.Interop.Visio.Document.Close para cerrar el documento activo.  
  
     Para usar el ejemplo de código siguiente, ejecútelo en la clase `ThisAddIn` de un proyecto de complemento de VSTO para Visio.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#7)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#7)]  
  
## Vea también  
 [Soluciones de Visio](../vsto/visio-solutions.md)   
 [Información general sobre el modelo de objetos de Visio](../vsto/visio-object-model-overview.md)   
 [Cómo: Crear nuevos documentos de Visio mediante programación](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [Cómo: Abrir documentos de Visio mediante programación](../vsto/how-to-programmatically-open-visio-documents.md)   
 [Cómo: Guardar documentos de Visio mediante programación](../vsto/how-to-programmatically-save-visio-documents.md)   
 [Cómo: Imprimir documentos de Visio mediante programación](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  