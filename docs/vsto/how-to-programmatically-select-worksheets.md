---
title: "C&#243;mo: Seleccionar hojas de c&#225;lculo mediante programaci&#243;n"
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
  - "proyectos de Excel, seleccionar hojas de cálculo"
  - "hojas de cálculo, seleccionar"
ms.assetid: 9e7cdb11-e825-4c9f-abcd-d46fd20dc5e0
caps.latest.revision: 44
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 43
---
# C&#243;mo: Seleccionar hojas de c&#225;lculo mediante programaci&#243;n
  El método <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A> selecciona el objeto especificado, que mueve la selección del usuario al nuevo objeto.  Use el método <xref:Microsoft.Office.Tools.Excel.Worksheet.Activate%2A> si desea llevar el foco al objeto sin cambiar la selección del usuario.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Si desea seleccionar una hoja de cálculo existente en un complemento de VSTO o si la hoja de cálculo se creó en tiempo de ejecución en una personalización de nivel de documento, debe acceder a dicha hoja de cálculo mediante la colección <xref:Microsoft.Office.Interop.Excel.Sheets> de Excel del libro de Excel; en caso contrario, puede acceder al elemento de host <xref:Microsoft.Office.Tools.Excel.Worksheet> directamente.  
  
## Usar el elemento host Worksheet  
 En una personalización de nivel de documento, agregue el código siguiente a **Sheet1.vb** o **Sheet1.cs**.  
  
#### Para seleccionar la primera hoja de cálculo en un libro usando un elemento host  
  
1.  Llame al método <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A> de `Sheet1`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#19](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#19)]
     [!code-vb[Trin_VstcoreExcelAutomation#19](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#19)]  
  
## Usar la colección Sheets del libro de Excel  
 Acceda a la hoja de cálculo mediante la colección <xref:Microsoft.Office.Interop.Excel.Sheets> de Excel.  
  
#### Para seleccionar la primera hoja de cálculo de un libro mediante la colección Sheets del libro de Excel  
  
1.  Llame al método <xref:Microsoft.Office.Interop.Excel.Sheets.Select%2A> de la colección <xref:Microsoft.Office.Interop.Excel.Sheets> para seleccionar la primera hoja de cálculo del libro activo.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#20](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#20)]
     [!code-vb[Trin_VstcoreExcelAutomation#20](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#20)]  
  
## Vea también  
 [Trabajar con hojas de cálculo](../vsto/working-with-worksheets.md)   
 [Cómo: Imprimir hojas de cálculo mediante programación](../vsto/how-to-programmatically-print-worksheets.md)   
 [Cómo: Eliminar hojas de cálculo de libros mediante programación](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [Cómo: Ocultar hojas de cálculo mediante programación](../vsto/how-to-programmatically-hide-worksheets.md)   
 [Cómo: Proteger hojas de cálculo mediante programación](../vsto/how-to-programmatically-protect-worksheets.md)   
 [Elemento host Worksheet](../vsto/worksheet-host-item.md)   
 [Acceso global a objetos en los proyectos de Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Limitaciones de programación de elementos y controles Host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Información general sobre elementos y controles Host](../vsto/host-items-and-host-controls-overview.md)  
  
  