---
title: "C&#243;mo: Ejecutar c&#225;lculos de Excel mediante programaci&#243;n | Microsoft Docs"
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
  - "cálculos, ejecutar en Excel"
  - "Excel [desarrollo de Office en Visual Studio], ejecutar cálculos mediante programación"
  - "intervalos, ejecutar cálculos"
  - "libros, ejecutar cálculos"
ms.assetid: 0bf30d93-8620-43ad-bfb8-f45bf3b5461f
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 38
---
# C&#243;mo: Ejecutar c&#225;lculos de Excel mediante programaci&#243;n
  Se usa un proceso similar para ejecutar los cálculos en un control <xref:Microsoft.Office.Tools.Excel.NamedRange> o en un objeto nativo de rango de Excel.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Ejecutar cálculos en un control NamedRange  
 En el ejemplo siguiente se crea un control <xref:Microsoft.Office.Tools.Excel.NamedRange> en la celda A1 y, a continuación, se calcula la celda.  Este código debe colocarse en una clase Sheet, no en la clase `ThisWorkbook`.  
  
#### Para ejecutar cálculos en un control NamedRange  
  
1.  Cree el rango con nombre.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#75](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#75)]
     [!code-vb[Trin_VstcoreExcelAutomation#75](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#75)]  
  
2.  Llame al método <xref:Microsoft.Office.Tools.Excel.NamedRange.Calculate%2A> del rango especificado.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#76](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#76)]
     [!code-vb[Trin_VstcoreExcelAutomation#76](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#76)]  
  
## Ejecutar cálculos en un rango nativo de Excel  
  
#### Para ejecutar cálculos en un rango nativo de Excel  
  
1.  Cree el rango con nombre.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#30](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#30)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#30](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#30)]  
  
2.  Llame al método <xref:Microsoft.Office.Interop.Excel.Range.Calculate%2A> del rango especificado.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#31](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#31)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#31](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#31)]  
  
## Vea también  
 [Trabajar con rangos](../vsto/working-with-ranges.md)   
 [NamedRange &#40;Control&#41;](../vsto/namedrange-control.md)   
 [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  