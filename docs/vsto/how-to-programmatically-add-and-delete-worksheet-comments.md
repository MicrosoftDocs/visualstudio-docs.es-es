---
title: "C&#243;mo: Agregar y eliminar comentarios en una hoja de c&#225;lculo mediante programaci&#243;n | Microsoft Docs"
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
  - "intervalos, comentarios"
  - "hojas de cálculo, comentarios"
  - "comentarios, hojas de cálculo"
ms.assetid: 3408ce22-a7b7-4e2b-bfc1-dc24d679ee73
caps.latest.revision: 53
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 52
---
# C&#243;mo: Agregar y eliminar comentarios en una hoja de c&#225;lculo mediante programaci&#243;n
  Puede agregar y eliminar comentarios en las hojas de cálculo de Microsoft Office Excel mediante programación. Los comentarios solo se pueden agregar a celdas individuales y no a intervalos de varias celdas.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Agregar y eliminar comentarios en un proyecto de nivel de documento  
 En los ejemplos siguientes, se da por hecho que hay un control <xref:Microsoft.Office.Tools.Excel.NamedRange> de una sola celda denominado `dateComment` en una hoja de cálculo denominada `Sheet1`.  
  
#### Agregar un nuevo comentario a un intervalo con nombre  
  
1.  Llame al método <xref:Microsoft.Office.Tools.Excel.NamedRange.AddComment%2A> del control <xref:Microsoft.Office.Tools.Excel.NamedRange> y escriba el texto del comentario. Este código se debe colocar en la clase `Sheet1`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#30](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#30)]
     [!code-vb[Trin_VstcoreExcelAutomation#30](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#30)]  
  
#### Eliminar un comentario de un intervalo con nombre  
  
1.  Compruebe si en el intervalo hay un comentario y elimínelo. Este código se debe colocar en la clase `Sheet1`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#29](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#29)]
     [!code-vb[Trin_VstcoreExcelAutomation#29](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#29)]  
  
## Agregar y eliminar un comentario en un proyecto de complemento VSTO  
 En los ejemplos siguientes, se da por hecho que hay una sola celda <xref:Microsoft.Office.Interop.Excel.Range> denominada `dateComment` en una hoja de cálculo.  
  
#### Agregar un nuevo comentario a un intervalo de Excel  
  
1.  Llame al método <xref:Microsoft.Office.Interop.Excel.Range.AddComment%2A> de <xref:Microsoft.Office.Interop.Excel.Range> y escriba el texto del comentario.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#20](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#20)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#20](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#20)]  
  
#### Eliminar un comentario de un intervalo de Excel  
  
1.  Compruebe si en el intervalo hay un comentario y elimínelo.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#19](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#19)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#19](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#19)]  
  
## Vea también  
 [Trabajar con hojas de cálculo](../vsto/working-with-worksheets.md)   
 [Cómo: Mostrar los comentarios de las hojas de cálculo mediante programación](../vsto/how-to-programmatically-display-worksheet-comments.md)   
 [NamedRange &#40;Control&#41;](../vsto/namedrange-control.md)  
  
  