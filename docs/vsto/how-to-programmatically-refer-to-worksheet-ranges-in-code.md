---
title: "C&#243;mo: Hacer referencia a rangos de hojas de c&#225;lculo en el c&#243;digo mediante programaci&#243;n"
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
  - "Excel [desarrollo de Office en Visual Studio], hacer referencia a rangos de hojas de cálculo"
  - "intervalos, hacer referencia"
  - "hacer referencia a rangos de hojas de cálculo"
  - "hojas de cálculo, hacer referencia a rangos"
ms.assetid: 113633b8-426a-4d02-b6b8-d459d1f110ea
caps.latest.revision: 46
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 46
---
# C&#243;mo: Hacer referencia a rangos de hojas de c&#225;lculo en el c&#243;digo mediante programaci&#243;n
  Se utiliza un proceso similar para hacer referencia al contenido de un control <xref:Microsoft.Office.Tools.Excel.NamedRange> o a un objeto de rango de Excel nativo.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Usar un control NamedRange  
 En el ejemplo siguiente se agrega un control <xref:Microsoft.Office.Tools.Excel.NamedRange> a una hoja de cálculo y, a continuación, se agrega texto a la celda del rango.  
  
#### Para hacer referencia a un control NamedRange  
  
1.  Asigne una cadena a la propiedad <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> del control <xref:Microsoft.Office.Tools.Excel.NamedRange>.  Este código debe colocarse en una clase Sheet, no en la clase `ThisWorkbook`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#46](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#46)]
     [!code-vb[Trin_VstcoreExcelAutomation#46](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#46)]  
  
## Usar rangos de Excel nativos  
 En el ejemplo siguiente se agrega un rango de Excel nativo a una hoja de cálculo y, a continuación, se agrega texto a la celda del rango.  
  
#### Para hacer referencia a un objeto de rango nativo  
  
1.  Asigne una cadena a la propiedad <xref:Microsoft.Office.Interop.Excel.Range.Value2%2A> del rango.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#47](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#47)]
     [!code-vb[Trin_VstcoreExcelAutomation#47](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#47)]  
  
## Vea también  
 [Trabajar con rangos](../vsto/working-with-ranges.md)   
 [Cómo: Revisar la ortografía en hojas de cálculo mediante programación](../vsto/how-to-programmatically-check-spelling-in-worksheets.md)   
 [Cómo: Aplicar estilos a rangos de libros mediante programación](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [Cómo: Rellenar rangos automáticamente con datos que cambian de forma incremental mediante programación](../vsto/how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data.md)   
 [Cómo: Buscar texto en rangos de hojas de cálculo mediante programación](../vsto/how-to-programmatically-search-for-text-in-worksheet-ranges.md)   
 [NamedRange &#40;Control&#41;](../vsto/namedrange-control.md)   
 [Información general sobre elementos y controles Host](../vsto/host-items-and-host-controls-overview.md)   
 [Limitaciones de programación de elementos y controles Host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  