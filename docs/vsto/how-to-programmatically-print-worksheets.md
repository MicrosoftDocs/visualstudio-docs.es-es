---
title: "C&#243;mo: Imprimir hojas de c&#225;lculo mediante programaci&#243;n"
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
  - "vista previa de impresión, hojas de cálculo"
  - "impresión [desarrollo de Office en Visual Studio], hojas de cálculo"
  - "hojas de cálculo, imprimir"
ms.assetid: 312bfcd7-0a74-421c-b42e-df71a06b7bdf
caps.latest.revision: 46
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 45
---
# C&#243;mo: Imprimir hojas de c&#225;lculo mediante programaci&#243;n
  Puede imprimir cualquier hoja de cálculo de un libro.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Imprimir una hoja de cálculo en una personalización de nivel de documento  
  
#### Para imprimir una hoja de cálculo  
  
1.  Llame al método <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintOut%2A> de `Sheet1`, solicite dos copias y obtenga una vista previa del documento antes de imprimirlo.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#22](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#22)]
     [!code-vb[Trin_VstcoreExcelAutomation#22](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#22)]  
  
 El método <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintPreview%2A> le permite mostrar el objeto especificado en la ventana **Vista previa de impresión**.  El siguiente código supone que tiene un elemento host <xref:Microsoft.Office.Tools.Excel.Worksheet> denominado `Sheet1`.  
  
#### Para obtener una vista previa de una página antes de imprimirla  
  
1.  Llame al método <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintPreview%2A> de la hoja de cálculo.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#23](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#23)]
     [!code-vb[Trin_VstcoreExcelAutomation#23](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#23)]  
  
## Imprimir una hoja de cálculo en un complemento de VSTO  
  
#### Para imprimir una hoja de cálculo  
  
1.  Llame al método <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintOut%2A> de la hoja de cálculo activa, solicite dos copias y obtenga una vista previa del documento antes de imprimirlo.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#14](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#14)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#14](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#14)]  
  
 El método <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> le permite mostrar el objeto especificado en la ventana **Vista previa de impresión**.  
  
#### Para obtener una vista previa de una página antes de imprimirla  
  
1.  Llame al método <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> de la hoja de cálculo activa.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#15](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#15)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#15](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#15)]  
  
## Vea también  
 [Trabajar con hojas de cálculo](../vsto/working-with-worksheets.md)   
 [Cómo: Revisar la ortografía en hojas de cálculo mediante programación](../vsto/how-to-programmatically-check-spelling-in-worksheets.md)   
 [Elemento host Worksheet](../vsto/worksheet-host-item.md)   
 [Acceso global a objetos en los proyectos de Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  