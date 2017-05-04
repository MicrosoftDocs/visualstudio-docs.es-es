---
title: "C&#243;mo: Recuperar los caracteres inicial y final de los intervalos mediante programaci&#243;n | Microsoft Docs"
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
  - "intervalos, recuperar los caracteres iniciales y finales"
  - "caracteres finales"
  - "caracteres iniciales"
  - "documentos [desarrollo de Office en Visual Studio], recuperar intervalos"
ms.assetid: 734c630c-abc9-491d-94b6-429d1fc7a4cc
caps.latest.revision: 37
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 36
---
# C&#243;mo: Recuperar los caracteres inicial y final de los intervalos mediante programaci&#243;n
  En este ejemplo se muestra cómo se pueden recuperar las posiciones de los caracteres de inicio y fin de un intervalo.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### Recuperar los caracteres inicial y final de un intervalo en una personalización de nivel de documento  
  
1.  Obtenga los valores de las propiedades <xref:Microsoft.Office.Interop.Word.Range.Start%2A> y <xref:Microsoft.Office.Interop.Word.Range.End%2A> del objeto <xref:Microsoft.Office.Interop.Word.Range>. En el ejemplo de código siguiente se obtienen las posiciones de inicio y fin de la segunda frase del documento. Para usar este ejemplo de código, ejecútelo desde la clase `ThisDocument` del proyecto.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#25](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#25)]
     [!code-vb[Trin_VstcoreWordAutomation#25](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#25)]  
  
### Recuperar los caracteres inicial y final de un intervalo en un complemento VSTO  
  
1.  Obtenga los valores de las propiedades <xref:Microsoft.Office.Interop.Word.Range.Start%2A> y <xref:Microsoft.Office.Interop.Word.Range.End%2A> del objeto <xref:Microsoft.Office.Interop.Word.Range>. En el ejemplo de código siguiente se obtienen las posiciones de inicio y fin de la segunda frase del documento activo. Para usar este ejemplo de código, ejecútelo desde la clase `ThisAddIn` del proyecto.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#25](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#25)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#25](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#25)]  
  
## Vea también  
 [Cómo: Definir y seleccionar intervalos en documentos mediante programación](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Cómo: ampliar rangos en documentos mediante programación](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [Cómo: Restablecer intervalos en documentos de Word mediante programación](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [Cómo: Contraer intervalos o selecciones en documentos mediante programación](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)   
 [Cómo: Excluir marcas de párrafo al crear intervalos mediante programación](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)   
 [Cómo: Calcular un recuento de caracteres en documentos mediante programación](../vsto/how-to-programmatically-count-characters-in-documents.md)  
  
  