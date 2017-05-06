---
title: "C&#243;mo: Mostrar una cadena en la celda de una hoja de c&#225;lculo mediante programaci&#243;n"
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
  - "texto [desarrollo de Office en Visual Studio], agregar a hojas de cálculo"
  - "hojas de cálculo, mostrar texto en celdas"
ms.assetid: b19870ad-e132-49fd-994e-0a91710fa4c9
caps.latest.revision: 45
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 44
---
# C&#243;mo: Mostrar una cadena en la celda de una hoja de c&#225;lculo mediante programaci&#243;n
  En este ejemplo se ofrece una demostración de cómo se muestra texto en una celda mediante programación.  Para mostrar texto en una celda, utilice un control <xref:Microsoft.Office.Tools.Excel.NamedRange> o un objeto de rango de Excel nativo.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Usar un control NamedRange  
 En este ejemplo se utiliza un control <xref:Microsoft.Office.Tools.Excel.NamedRange> denominado `message`.  El control se debe agregar en tiempo de diseño a una personalización en el nivel del documento.  El siguiente código debe colocarse en una clase Sheet, no en la clase `ThisWorkbook`.  
  
#### Para mostrar texto en un control NamedRange  
  
1.  Establezca el valor del control <xref:Microsoft.Office.Tools.Excel.NamedRange> en **Hello World**.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#68](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#68)]
     [!code-vb[Trin_VstcoreExcelAutomation#68](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#68)]  
  
## Usar rangos de Excel nativos  
 En el código siguiente se crea un nuevo rango mediante programación y a continuación se le asigna un valor.  
  
#### Para mostrar texto en un rango de Excel  
  
1.  Recupere el rango en la celda **A1** de `Sheet1` y establezca el valor en **Hello World**.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#69](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#69)]
     [!code-vb[Trin_VstcoreExcelAutomation#69](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#69)]  
  
## Vea también  
 [Tutorial: Recopilar datos con Windows Forms](../vsto/walkthrough-collecting-data-using-a-windows-form.md)   
 [Solución de problemas de soluciones de Office](../vsto/troubleshooting-office-solutions.md)   
 [NamedRange &#40;Control&#41;](../vsto/namedrange-control.md)   
 [Acceso global a objetos en los proyectos de Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  