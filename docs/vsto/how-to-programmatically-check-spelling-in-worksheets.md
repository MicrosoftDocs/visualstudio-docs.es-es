---
title: "C&#243;mo: Revisar la ortograf&#237;a en hojas de c&#225;lculo mediante programaci&#243;n | Microsoft Docs"
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
  - "revisión ortográfica"
  - "corrector ortográfico, hojas de cálculo"
  - "hojas de cálculo, revisar la ortografía"
  - "corrector ortográfico, revisar ortografía en hojas de cálculo"
ms.assetid: 16367c5d-2075-4174-bb87-dfc59f02c84c
caps.latest.revision: 53
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 52
---
# C&#243;mo: Revisar la ortograf&#237;a en hojas de c&#225;lculo mediante programaci&#243;n
  Puede comprobar la ortografía en una hoja de cálculo mediante programación. El cuadro de diálogo **Ortografía** aparece automáticamente si hay palabras mal escritas en la hoja de cálculo.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### Para revisar la ortografía en una hoja de cálculo en una personalización de nivel de documento  
  
1.  Llame al método <xref:Microsoft.Office.Tools.Excel.Worksheet.CheckSpelling%2A> de la hoja de cálculo.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#45](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#45)]
     [!code-vb[Trin_VstcoreExcelAutomation#45](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#45)]  
  
### Para revisar la ortografía en una hoja de cálculo en un complemento VSTO  
  
1.  Llame al método <xref:Microsoft.Office.Interop.Excel._Worksheet.CheckSpelling%2A> de la hoja de cálculo activa.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#22](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#22)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#22](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#22)]  
  
## Vea también  
 [Trabajar con hojas de cálculo](../vsto/working-with-worksheets.md)   
 [Cómo: Ejecutar cálculos de Excel mediante programación](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md)   
 [NamedRange &#40;Control&#41;](../vsto/namedrange-control.md)   
 [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  