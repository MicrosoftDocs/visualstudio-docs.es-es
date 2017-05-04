---
title: "C&#243;mo: Cerrar libros mediante programaci&#243;n | Microsoft Docs"
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
  - "libros, cerrar"
  - "Excel [desarrollo de Office en Visual Studio], cerrar libros"
ms.assetid: 50709caf-2ad8-4843-987c-9a34c8c1e4fe
caps.latest.revision: 52
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 51
---
# C&#243;mo: Cerrar libros mediante programaci&#243;n
  Puede cerrar el libro activo o especificar el libro que se va a cerrar.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Cerrar el libro activo  
 Hay dos procedimientos para cerrar el libro activo: uno para las personalizaciones de nivel de documento y uno para los complementos de VSTO.  
  
#### Para cerrar el libro activo en una personalización de nivel de documento  
  
1.  Llame al método <xref:Microsoft.Office.Tools.Excel.Workbook.Close%2A> para cerrar el libro asociado a la personalización. Para usar el ejemplo de código siguiente, ejecútelo en la clase `Sheet1` en un proyecto de nivel de documento para Excel.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#3)]
     [!code-vb[Trin_VstcoreExcelAutomation#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#3)]  
  
#### Para cerrar el libro activo en un complemento de VSTO  
  
1.  Llame al método <xref:Microsoft.Office.Interop.Excel._Workbook.Close%2A> para cerrar el libro activo. Para usar el ejemplo de código siguiente, ejecútelo en la clase `ThisAddIn` en un proyecto de complemento VSTO para Excel.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#1)]  
  
## Cerrar un libro que se especifica por el nombre  
 El modo de cerrar un libro que se especifica según el nombre, es el mismo para los complementos VSTO y para las personalizaciones de nivel de documento.  
  
#### Para cerrar un libro que se especifica por el nombre  
  
1.  Especifique el nombre del libro como argumento para la colección <xref:Microsoft.Office.Interop.Excel.Workbooks>. En el siguiente ejemplo de código, se supone que un libro denominado **NewWorkbook** está abierto en Excel.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#2)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#2)]  
  
## Vea también  
 [Trabajar con libros](../vsto/working-with-workbooks.md)   
 [Cómo: Guardar libros mediante programación](../vsto/how-to-programmatically-save-workbooks.md)   
 [Cómo: Abrir libros mediante programación](../vsto/how-to-programmatically-open-workbooks.md)   
 [Limitaciones de programación de elementos y controles Host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Información general sobre elementos y controles Host](../vsto/host-items-and-host-controls-overview.md)  
  
  