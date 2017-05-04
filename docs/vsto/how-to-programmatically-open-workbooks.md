---
title: "C&#243;mo: Abrir libros mediante programaci&#243;n | Microsoft Docs"
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
  - "Excel [desarrollo de Office en Visual Studio], abrir libros"
  - "libros, abrir"
ms.assetid: 06c0ac87-a2c6-4cc1-87be-39be0cb81c71
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 36
---
# C&#243;mo: Abrir libros mediante programaci&#243;n
  La colección <xref:Microsoft.Office.Interop.Excel.Workbooks> permite trabajar con todos los libros abiertos, así como abrir libros en Microsoft Office Excel.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### Para abrir un libro existente  
  
1.  Utilice el método <xref:Microsoft.Office.Interop.Excel.Workbooks.Open%2A> de la colección <xref:Microsoft.Office.Interop.Excel.Workbooks>, pasando la ruta de acceso al libro.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#2)]
     [!code-vb[Trin_VstcoreExcelAutomation#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#2)]  
  
## Compilar el código  
 Este ejemplo de código requiere lo siguiente:  
  
-   Un libro denominado `YourWorkbook.xls` en un directorio llamado `Test` de la unidad C.  
  
## Vea también  
 [Trabajar con libros](../vsto/working-with-workbooks.md)   
 [Cómo: Abrir archivos de texto como libros mediante programación](../vsto/how-to-programmatically-open-text-files-as-workbooks.md)   
 [Cómo: Crear nuevos libros mediante programación](../vsto/how-to-programmatically-create-new-workbooks.md)   
 [Cómo: Guardar libros mediante programación](../vsto/how-to-programmatically-save-workbooks.md)   
 [Cómo: Cerrar libros mediante programación](../vsto/how-to-programmatically-close-workbooks.md)   
 [Limitaciones de programación de elementos y controles Host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Información general sobre elementos y controles Host](../vsto/host-items-and-host-controls-overview.md)  
  
  