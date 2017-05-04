---
title: "C&#243;mo: Mostrar los archivos de libro usados recientemente mediante programaci&#243;n | Microsoft Docs"
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
  - "Excel [desarrollo de Office en Visual Studio], enumeración de los archivos utilizados recientemente"
  - "enumeración de los archivos recientes, Excel"
  - "RecentFiles (propiedad)"
  - "libros, mostrar los utilizados recientemente"
ms.assetid: 210a3753-4845-4875-b34a-a30d3a1299b3
caps.latest.revision: 42
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 42
---
# C&#243;mo: Mostrar los archivos de libro usados recientemente mediante programaci&#243;n
  La propiedad <xref:Microsoft.Office.Interop.Excel._Application.RecentFiles%2A> devuelve una colección de cadenas que contiene los nombres de todos los archivos que aparecen en la lista de los archivos utilizados recientemente del menú Archivo de Microsoft Office Excel 2003.  La longitud de la lista varía en función del número de archivos que haya seleccionado el usuario para que se conserven.  Puede mostrar los resultados en un rango.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### Para mostrar en un control de rango la lista de los libros utilizados recientemente  
  
1.  Examine la lista de archivos recientes y muestre los nombres en celdas relativas a un objeto <xref:Microsoft.Office.Interop.Excel.Range>.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#9](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#9)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#9](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#9)]  
  
## Vea también  
 [Trabajar con libros](../vsto/working-with-workbooks.md)   
 [NamedRange &#40;Control&#41;](../vsto/namedrange-control.md)   
 [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  