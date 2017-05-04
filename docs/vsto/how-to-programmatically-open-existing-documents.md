---
title: "C&#243;mo: Abrir documentos existentes mediante programaci&#243;n | Microsoft Docs"
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
  - "documentos [desarrollo de Office en Visual Studio], abrir"
  - "Word [desarrollo de Office en Visual Studio], abrir documentos"
ms.assetid: 08f7fe4b-d96d-4a0c-b32a-aa7fd7992316
caps.latest.revision: 44
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 43
---
# C&#243;mo: Abrir documentos existentes mediante programaci&#243;n
  El método <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> abre el documento existente de Microsoft Office Word especificado por una ruta de acceso completa y el nombre de archivo.  Este método devuelve un objeto <xref:Microsoft.Office.Interop.Word.Document> que representa el documento abierto.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### Para abrir un documento  
  
-   Llame al método <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> de la colección <xref:Microsoft.Office.Interop.Word.Documents> y proporcione una ruta de acceso al documento.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#5)]
     [!code-vb[Trin_VstcoreWordAutomation#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#5)]  
  
### Para abrir un documento en modo de sólo lectura  
  
-   Llame al método <xref:Microsoft.Office.Interop.Word.Documents.Open%2A>, proporcione una ruta de acceso al documento y establezca el argumento *ReadOnly* en **True** en la llamada al método.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#6)]
     [!code-vb[Trin_VstcoreWordAutomation#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#6)]  
  
## Compilar el código  
 Este ejemplo de código requiere lo siguiente:  
  
-   Debe haber un documento denominado NewDocument.doc en un directorio denominado Test en la unidad C.  
  
## Vea también  
 [Cómo: Crear nuevos documentos mediante programación](../vsto/how-to-programmatically-create-new-documents.md)   
 [Cómo: Cerrar documentos mediante programación](../vsto/how-to-programmatically-close-documents.md)   
 [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  