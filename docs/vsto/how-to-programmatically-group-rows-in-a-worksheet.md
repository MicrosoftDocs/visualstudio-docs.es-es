---
title: "C&#243;mo: Agrupar filas de una hoja de c&#225;lculo mediante programaci&#243;n"
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
  - "columnas [desarrollo de Office en Visual Studio], desagrupar"
  - "grupos"
  - "grupos [desarrollo de Office en Visual Studio], borrar en hojas de cálculo"
  - "grupos, crear en las hojas de cálculo"
  - "intervalos, crear grupos"
  - "filas [desarrollo de Office en Visual Studio], desagrupar"
  - "hojas de cálculo, borrar grupos"
  - "hojas de cálculo, crear grupos"
  - "hojas de cálculo, desagrupar filas y columnas"
ms.assetid: 48037dca-35a2-4df2-918b-6a9f568fae91
caps.latest.revision: 46
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 45
---
# C&#243;mo: Agrupar filas de una hoja de c&#225;lculo mediante programaci&#243;n
  Puede agrupar una o más filas enteras.  Para crear un grupo en una hoja de cálculo, utilice un control <xref:Microsoft.Office.Tools.Excel.NamedRange> o un objeto nativo de rango de Excel.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Usar un control NamedRange  
 Si agrega en tiempo de diseño un control <xref:Microsoft.Office.Tools.Excel.NamedRange> a un proyecto en el nivel del documento, puede utilizar el control para crear mediante programación un grupo.  En el siguiente ejemplo se supone que hay tres controles <xref:Microsoft.Office.Tools.Excel.NamedRange> denominados `data2001`, `data2002` y `dataAll` en la misma hoja de cálculo.  Cada rango con nombre hace referencia a una fila entera de la hoja de cálculo.  
  
#### Para crear un grupo de controles NamedRange en una hoja de cálculo  
  
1.  Agrupe tres rangos con nombre mediante llamadas al método <xref:Microsoft.Office.Tools.Excel.NamedRange.Group%2A> de cada rango.  Este código debe colocarse en una clase Sheet, no en la clase `ThisWorkbook`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#32](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#32)]
     [!code-vb[Trin_VstcoreExcelAutomation#32](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#32)]  
  
    > [!NOTE]  
    >  Para desagrupar las filas, llame al método <xref:Microsoft.Office.Tools.Excel.NamedRange.Ungroup%2A>.  
  
## Usar rangos de Excel nativos  
 En el ejemplo de código se supone que hay tres rangos de Excel denominados `data2001`, `data2002` y `dataAll` en una hoja de cálculo.  
  
#### Para crear un grupo de rangos de Excel en una hoja de cálculo  
  
1.  Agrupe tres rangos con nombre mediante llamadas al método <xref:Microsoft.Office.Interop.Excel.Range.Group%2A> de cada rango.  En el siguiente ejemplo se supone que hay tres controles <xref:Microsoft.Office.Interop.Excel.Range> denominados `data2001`, `data2002` y `dataAll` en la misma hoja de cálculo.  Cada rango con nombre hace referencia a una fila entera de la hoja de cálculo.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#33](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#33)]
     [!code-vb[Trin_VstcoreExcelAutomation#33](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#33)]  
  
    > [!NOTE]  
    >  Para desagrupar las filas, llame al método <xref:Microsoft.Office.Interop.Excel.Range.Ungroup%2A>.  
  
## Vea también  
 [Trabajar con hojas de cálculo](../vsto/working-with-worksheets.md)   
 [NamedRange &#40;Control&#41;](../vsto/namedrange-control.md)   
 [Cómo: Agregar controles NamedRange a hojas de cálculo](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  