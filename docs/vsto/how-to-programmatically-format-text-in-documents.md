---
title: "C&#243;mo: Dar formato al texto en documentos mediante programaci&#243;n"
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
  - "formato [desarrollo de Office en Visual Studio]"
  - "documentos [desarrollo de Office en Visual Studio], formato de texto"
  - "texto [desarrollo de Office en Visual Studio], formato en documentos"
ms.assetid: 0a84893b-5ccc-4515-a2dc-95773ee8eaba
caps.latest.revision: 42
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 41
---
# C&#243;mo: Dar formato al texto en documentos mediante programaci&#243;n
  Puede utilizar el objeto <xref:Microsoft.Office.Interop.Word.Range> para dar formato al texto de un documento de Microsoft Office Word.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 En el siguiente ejemplo se selecciona el primer párrafo del documento y se cambia el tamaño de la fuente, el nombre de la fuente y la alineación. A continuación, se selecciona el intervalo y se muestra un cuadro de mensaje para hacer una pausa antes de ejecutar la siguiente sección de código. La siguiente sección llama tres veces al método Undo del elemento host <xref:Microsoft.Office.Tools.Word.Document> \(para una personalización de nivel de documento\) o la clase <xref:Microsoft.Office.Interop.Word.Document> \(para un complemento de VSTO\). Aplica el estilo Sangría normal y muestra un cuadro de mensaje para pausar el código. A continuación, el código llama una vez al método <xref:Microsoft.Office.Tools.Word.Document.Undo%2A> y muestra un cuadro de mensaje.  
  
## Ejemplo de personalización de nivel de documento  
  
#### Para dar formato a un texto mediante una personalización de nivel de documento  
  
1.  El siguiente ejemplo se puede usar en una personalización de nivel de documento. Para usar este código, ejecútelo desde la clase `ThisDocument` del proyecto.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#62](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#62)]
     [!code-vb[Trin_VstcoreWordAutomation#62](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#62)]  
  
## Ejemplo para complemento de VSTO  
  
#### Para dar formato al texto mediante un complemento de VSTO  
  
1.  El siguiente ejemplo se puede usar en un complemento de VSTO. En este ejemplo se usa el documento activo. Para usar este código, ejecútelo desde la clase `ThisAddIn` del proyecto.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#62](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#62)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#62](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#62)]  
  
## Vea también  
 [Cómo: Definir y seleccionar intervalos en documentos mediante programación](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Cómo: Insertar texto en documentos de Word mediante programación](../vsto/how-to-programmatically-insert-text-into-word-documents.md)   
 [Cómo: Buscar y reemplazar texto en documentos mediante programación](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)  
  
  