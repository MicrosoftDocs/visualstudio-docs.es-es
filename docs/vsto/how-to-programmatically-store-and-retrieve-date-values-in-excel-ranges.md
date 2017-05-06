---
title: "C&#243;mo: Almacenar y recuperar valores de fecha en rangos de Excel mediante programaci&#243;n"
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
  - "valores de fecha"
  - "valores de fecha, almacenar en rangos de Excel"
  - "fechas, recuperar de rangos de Excel"
  - "fechas, almacenar en rangos de Excel"
  - "Excel [desarrollo de Office en Visual Studio], recuperar valores de datos de rangos"
  - "Excel [desarrollo de Office en Visual Studio], almacenar valores de datos en rangos"
  - "intervalos, recuperar valores de datos"
  - "intervalos, almacenar valores de datos"
ms.assetid: e1cdd262-0356-4499-8bc5-e730f74235a2
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 39
---
# C&#243;mo: Almacenar y recuperar valores de fecha en rangos de Excel mediante programaci&#243;n
  Puede almacenar y recuperar valores de un control <xref:Microsoft.Office.Tools.Excel.NamedRange> o de objeto de rango de Excel nativo.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Si almacena un valor de fecha igual o anterior a 1\/1\/1900 en un intervalo con las herramientas de desarrollo de Office en Visual Studio, dicho valor se almacena con formato de automatización OLE \(OA\).  Debe utilizar el método <xref:System.DateTime.FromOADate%2A> para recuperar el valor de fechas de automatización OLE \(OA\).  Si la fecha es anterior a 1\/1\/1900, se almacena como una cadena.  
  
> [!NOTE]  
>  Las fechas de Excel difieren de las fechas con formato de automatización OLE en los dos primeros meses de 1900.  También existen diferencias si se activa la opción **Sistema de fechas de 1904**.  Los siguientes ejemplos de código no tratan estas diferencias.  
  
## Usar un control NamedRange  
  
-   Se trata de un ejemplo para personalizaciones en el nivel del documento.  El siguiente código debe colocarse en una clase Sheet, no en la clase `ThisWorkbook`.  
  
#### Para almacenar un valor de fecha en un rango con nombre  
  
1.  Cree un control <xref:Microsoft.Office.Tools.Excel.NamedRange> en la celda **A1**.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#50](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#50)]
     [!code-vb[Trin_VstcoreExcelAutomation#50](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#50)]  
  
2.  Establezca la fecha actual como valor de `NamedRange1`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#51](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#51)]
     [!code-vb[Trin_VstcoreExcelAutomation#51](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#51)]  
  
#### Para recuperar un valor de fecha de un rango con nombre  
  
1.  Recupere el valor de fecha de `NamedRange1`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#52](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#52)]
     [!code-vb[Trin_VstcoreExcelAutomation#52](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#52)]  
  
## Usar rangos de Excel nativos  
  
#### Para almacenar un valor de fecha en un objeto de rango de Excel nativo  
  
1.  Cree un <xref:Microsoft.Office.Interop.Excel.Range> que represente la **A1**.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#25](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#25)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#25](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#25)]  
  
2.  Establezca la fecha actual como valor de `rng`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#26](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#26)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#26](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#26)]  
  
#### Para recuperar un valor de fecha de un objeto de rango de Excel nativo  
  
1.  Recupere el valor de fecha de `rng`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#27](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#27)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#27](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#27)]  
  
## Vea también  
 [Trabajar con rangos](../vsto/working-with-ranges.md)   
 [Información general sobre el modelo de objetos de Excel](../vsto/excel-object-model-overview.md)   
 [NamedRange &#40;Control&#41;](../vsto/namedrange-control.md)   
 [Cómo: Hacer referencia a rangos de hojas de cálculo en el código mediante programación](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [Cómo: Agregar controles NamedRange a hojas de cálculo](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  