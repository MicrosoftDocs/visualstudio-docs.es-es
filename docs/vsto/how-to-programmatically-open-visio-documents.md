---
title: "C&#243;mo: Abrir documentos de Visio mediante programaci&#243;n | Microsoft Docs"
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
  - "documentos [desarrollo de Office en Visual Studio], abrir documentos de Visio"
  - "Visio [desarrollo de Office en Visual Studio], abrir documentos de Visio"
ms.assetid: bddb820c-bde7-4d21-a0b3-6d1968baccab
caps.latest.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# C&#243;mo: Abrir documentos de Visio mediante programaci&#243;n
  Existen dos métodos para abrir documentos existentes de Microsoft Office Visio: Open y OpenEx. El método OpenEx es idéntico al método Open, excepto en que proporciona argumentos en los que el llamador puede especificar cómo se abre el documento.  
  
 Para obtener detalles sobre el modelo de objetos, consulte la documentación de referencia de VBA para el método [Microsoft.Office.Interop.Visio.Documents.Open](HV10070351) y el método [Microsoft.Office.Interop.Visio.Documents.OpenEx](HV10071456).  
  
## Apertura de un documento de Visio  
  
#### Para abrir un documento de Visio  
  
-   Llame al método Microsoft.Office.Interop.Visio.Documents.Open y facilite la ruta de acceso completa del documento de Visio.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#5)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#5)]  
  
## Apertura de un documento de Visio con argumentos especificados  
  
#### Para abrir un documento de Visio como de solo lectura y acoplado  
  
-   Llame al método Microsoft.Office.Interop.Visio.Documents.OpenEx, facilite la ruta de acceso completa del documento de Visio e incluya los argumentos que desea utilizar; en este caso, Docked y Read\-only.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#6)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#6)]  
  
## Compilar el código  
 Para este ejemplo de código se necesita lo siguiente:  
  
-   Un documento de Visio denominado `myDrawing.vsd` que debe encontrarse en un directorio llamado `Test` en la carpeta Mis documentos \(en Windows XP y versiones anteriores\) o en la carpeta Documentos \(en Windows Vista\).  
  
## Vea también  
 [Soluciones de Visio](../vsto/visio-solutions.md)   
 [Información general sobre el modelo de objetos de Visio](../vsto/visio-object-model-overview.md)   
 [Cómo: Crear nuevos documentos de Visio mediante programación](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [Cómo: Cerrar documentos de Visio mediante programación](../vsto/how-to-programmatically-close-visio-documents.md)   
 [Cómo: Guardar documentos de Visio mediante programación](../vsto/how-to-programmatically-save-visio-documents.md)   
 [Cómo: Imprimir documentos de Visio mediante programación](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  