---
title: "C&#243;mo: Agregar texto y formato a celdas de tablas de Word mediante programaci&#243;n"
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
  - "celdas, agregar texto y formato"
  - "formato [desarrollo de Office en Visual Studio]"
  - "tablas [desarrollo de Office en Visual Studio], agregar texto y formato"
  - "texto [desarrollo de Office en Visual Studio], agregar a las tablas de Word"
ms.assetid: 3df6492a-dc9c-43ac-8fc3-0f944edd88b2
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 39
---
# C&#243;mo: Agregar texto y formato a celdas de tablas de Word mediante programaci&#243;n
  Cada tabla consta de una colección de celdas.  Cada objeto <xref:Microsoft.Office.Interop.Word.Cell> individual representa una celda de la tabla.  Se hace referencia a cada celda mediante su ubicación en la tabla.  Este ejemplo hace referencia a la celda ubicada en la primera fila y la primera columna de la tabla, le añade texto y le aplica formato.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### Para agregar texto y formato a celdas  
  
1.  Haga referencia a la celda por su ubicación en la tabla, agregue texto a la celda y aplique el formato.  
  
     El siguiente ejemplo de código se puede usar en una personalización de nivel de documento.  Para usar este ejemplo, ejecútelo desde la clase `ThisDocument` del proyecto.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#97](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#97)]
     [!code-vb[Trin_VstcoreWordAutomation#97](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#97)]  
  
     El siguiente ejemplo de código se puede usar en un complemento de VSTO.  En este ejemplo se usa el documento activo.  Para usar este ejemplo, ejecútelo desde la clase `ThisAddIn` del proyecto.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#97](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#97)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#97](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#97)]  
  
## Vea también  
 [Cómo: Crear tablas de Word mediante programación](../vsto/how-to-programmatically-create-word-tables.md)   
 [Cómo: Agregar filas y columnas a tablas de Word mediante programación](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md)   
 [Cómo: Rellenar tablas de Word con propiedades de documento mediante programación](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)  
  
  