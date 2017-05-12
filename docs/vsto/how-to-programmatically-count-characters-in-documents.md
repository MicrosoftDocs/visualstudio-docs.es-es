---
title: "C&#243;mo: Calcular un recuento de caracteres en documentos mediante programaci&#243;n"
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
  - "caracteres, contar en documentos"
  - "contar los caracteres de los documentos"
  - "documentos de Office [desarrollo de Office en Visual Studio], contar caracteres"
ms.assetid: ab64fe87-896a-4b56-bdf8-91c4326b540e
caps.latest.revision: 37
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 36
---
# C&#243;mo: Calcular un recuento de caracteres en documentos mediante programaci&#243;n
  El primer carácter de un documento está en la posición de carácter 0, que representa el punto de inserción. La última posición de carácter es igual al número total de caracteres del documento. Puede determinar el número de caracteres de un documento mediante la propiedad <xref:Microsoft.Office.Interop.Word.Characters.Count%2A> de la colección <xref:Microsoft.Office.Interop.Word.Characters>.  
  
 Se cuentan todos los caracteres en el documento, incluidos los espacios, las marcas de párrafo y otros caracteres que normalmente están ocultos. Incluso un nuevo documento en blanco devuelve un recuento de caracteres porque contiene una marca de párrafo.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### Para mostrar el número de caracteres en una personalización de nivel de documento  
  
1.  Seleccione todo el documento.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#98](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#98)]
     [!code-vb[Trin_VstcoreWordAutomation#98](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#98)]  
  
2.  Muestre el número de caracteres del documento en un cuadro de mensaje.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#99](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#99)]
     [!code-vb[Trin_VstcoreWordAutomation#99](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#99)]  
  
### Para mostrar el número de caracteres en un complemento de VSTO  
  
1.  Seleccione todo el documento. El siguiente ejemplo selecciona el documento activo.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#98](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#98)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#98](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#98)]  
  
2.  Muestre el número de caracteres del documento en un cuadro de mensaje.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#99](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#99)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#99](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#99)]  
  
## Vea también  
 [Cómo: Recuperar los caracteres inicial y final de los intervalos mediante programación](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)   
 [Cómo: Definir y seleccionar intervalos en documentos mediante programación](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)  
  
  