---
title: "C&#243;mo: Ordenar datos en hojas de c&#225;lculo mediante programaci&#243;n"
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
  - "datos [desarrollo de Office en Visual Studio], ordenar en hojas de cálculo"
  - "ordenación de datos, hojas de cálculo"
  - "ordenar datos, en hojas de cálculo"
  - "hojas de cálculo, ordenar datos"
ms.assetid: 2fbc6e63-02ea-4624-8d6f-bed60e06c61e
caps.latest.revision: 56
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 55
---
# C&#243;mo: Ordenar datos en hojas de c&#225;lculo mediante programaci&#243;n
  Puede ordenar los datos contenidos en rangos de hojas de cálculo y listas en tiempo de ejecución.  El siguiente código ordena un rango con varias columnas denominado `Fruits` en función de los datos de la primera columna y, a continuación, en función de los datos de la segunda columna.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Ordenar datos en una personalización de nivel de documento  
  
#### Para ordenar datos en un control NamedRange  
  
1.  Llame al método <xref:Microsoft.Office.Tools.Excel.NamedRange.Sort%2A> del control <xref:Microsoft.Office.Tools.Excel.NamedRange>.  El siguiente ejemplo requiere un control <xref:Microsoft.Office.Tools.Excel.NamedRange> denominado `Fruits` en una hoja de cálculo.  Este código se debe colocar en una clase Sheet, no en la clase `ThisWorkbook`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#78](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#78)]
     [!code-vb[Trin_VstcoreExcelAutomation#78](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#78)]  
  
 Coloque el siguiente código en Sheet1.vb o Sheet1.cs para ordenar los datos de un control <xref:Microsoft.Office.Tools.Excel.ListObject>.  El código supone que tiene un control <xref:Microsoft.Office.Tools.Excel.ListObject> denominado `fruitList` en una hoja de cálculo denominada `Sheet1`.  
  
#### Para ordenar los datos de un control ListObject  
  
1.  Llame al método <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> de la propiedad <xref:Microsoft.Office.Tools.Excel.ListObject.Range%2A> de del control host <xref:Microsoft.Office.Tools.Excel.ListObject>.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#79](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#79)]
     [!code-vb[Trin_VstcoreExcelAutomation#79](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#79)]  
  
## Ordenar los datos de un complemento de VSTO  
  
#### Para ordenar los datos en un rango nativo  
  
1.  Llame al método <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> del control <xref:Microsoft.Office.Interop.Excel.Range> nativo de Excel.  El siguiente ejemplo requiere un control nativo de Excel denominado `Fruits` en una hoja de cálculo.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#23](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#23)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#23](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#23)]  
  
#### Para ordenar los datos de un control ListObject  
  
1.  Llame al método <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> de la propiedad <xref:Microsoft.Office.Tools.Excel.ListObject.Range%2A> del control <xref:Microsoft.Office.Interop.Excel.ListObject> nativo de Excel.  El siguiente ejemplo supone que tiene un control <xref:Microsoft.Office.Interop.Excel.ListObject> nativo de Excel denominado `fruitList` en la hoja de cálculo activa.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#24](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#24)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#24](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#24)]  
  
## Vea también  
 [Trabajar con hojas de cálculo](../vsto/working-with-worksheets.md)   
 [Cómo: Rellenar rangos automáticamente con datos que cambian de forma incremental mediante programación](../vsto/how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data.md)   
 [Cómo: Hacer referencia a rangos de hojas de cálculo en el código mediante programación](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [Cómo: Aplicar estilos a rangos de libros mediante programación](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [NamedRange &#40;Control&#41;](../vsto/namedrange-control.md)   
 [ListObject &#40;Control&#41;](../vsto/listobject-control.md)   
 [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  