---
title: "C&#243;mo: Mostrar todas las hojas de c&#225;lculo de un libro mediante programaci&#243;n"
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
  - "libros, mostrar hojas de cálculo"
  - "hojas de cálculo, mostrar"
ms.assetid: 38b63d1d-6047-44e8-b089-c576c6179e4a
caps.latest.revision: 46
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 45
---
# C&#243;mo: Mostrar todas las hojas de c&#225;lculo de un libro mediante programaci&#243;n
  La clase <xref:Microsoft.Office.Interop.Excel.Workbook> proporciona un objeto <xref:Microsoft.Office.Interop.Excel.Worksheets>.  Este objeto contiene una colección de todos los objetos <xref:Microsoft.Office.Interop.Excel.Worksheet> del libro.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### Para hacer una lista de todas las hojas de cálculo existentes en un libro en una personalización en el nivel del documento  
  
1.  Recorra en iteración la colección <xref:Microsoft.Office.Interop.Excel.Worksheets> y envíe el nombre de cada una de las hojas a un desplazamiento de celda desde un control <xref:Microsoft.Office.Tools.Excel.NamedRange>.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#21](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#21)]
     [!code-vb[Trin_VstcoreExcelAutomation#21](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#21)]  
  
### Para hacer una lista de todas las hojas de cálculo existentes en un libro en un complemento de VSTO  
  
1.  Recorra en iteración la colección <xref:Microsoft.Office.Interop.Excel.Worksheets> y envíe el nombre de cada una de las hojas a un desplazamiento de celda desde un objeto <xref:Microsoft.Office.Interop.Excel.Range>.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#13](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#13)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#13](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#13)]  
  
## Vea también  
 [Trabajar con hojas de cálculo](../vsto/working-with-worksheets.md)   
 [Cómo: Agregar nuevas hojas de cálculo a libros mediante programación](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)   
 [Cómo: Mover hojas de cálculo dentro de libros mediante programación](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)   
 [Acceso global a objetos en los proyectos de Office](../vsto/global-access-to-objects-in-office-projects.md)  
  
  