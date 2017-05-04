---
title: "C&#243;mo: Copiar datos y formato de una hoja de c&#225;lculo al resto mediante programaci&#243;n | Microsoft Docs"
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
  - "copiar datos, desarrollo de Office en Visual Studio"
  - "datos [desarrollo de Office en Visual Studio], copiar de una hoja de cálculo al resto"
  - "formato [desarrollo de Office en Visual Studio]"
  - "hojas de cálculo, copiar datos"
ms.assetid: eed7dbaf-bdb5-4330-ba2e-5f3d50817eca
caps.latest.revision: 37
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 37
---
# C&#243;mo: Copiar datos y formato de una hoja de c&#225;lculo al resto mediante programaci&#243;n
  Puede copiar datos de un rango de una hoja en todas las demás hojas de un libro con el método <xref:Microsoft.Office.Interop.Excel.Worksheets.FillAcrossSheets%2A>.  Especifique un rango y si desea copiar datos, formato o ambos.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Ejemplo  
 [!code-csharp[Trin_VstcoreExcelAutomation#44](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#44)]
 [!code-vb[Trin_VstcoreExcelAutomation#44](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#44)]  
  
## Compilar el código  
 Este ejemplo requiere un rango denominado `rangeData` en una hoja de cálculo.  
  
## Vea también  
 [Trabajar con hojas de cálculo](../vsto/working-with-worksheets.md)   
 [Cómo: Agregar nuevas hojas de cálculo a libros mediante programación](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)   
 [Cómo: Cambiar el formato en filas de hojas de cálculo que contienen celdas seleccionadas mediante programación](../vsto/how-to-programmatically-change-formatting-in-worksheet-rows-containing-selected-cells.md)   
 [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  