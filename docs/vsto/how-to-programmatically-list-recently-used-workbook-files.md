---
title: "Cómo: mediante programación lista de archivos usados recientemente libro | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, listing recently used
- RecentFiles property
- Excel [Office development in Visual Studio], recently used files listing
- recent file list, Excel
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: e8a64f8a934e8cd7cdbbed11a87d15e795d19d0f
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-list-recently-used-workbook-files"></a>Cómo: Mostrar los archivos de libro usados recientemente mediante programación
  El <xref:Microsoft.Office.Interop.Excel._Application.RecentFiles%2A> propiedad devuelve una colección que contiene los nombres de todos los archivos que aparecen en la lista de Microsoft Office Excel de archivos usados recientemente. La longitud de la lista varía dependiendo del número de archivos que el usuario ha seleccionado para conservar. Puede mostrar los resultados en un intervalo.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### <a name="to-list-recently-used-workbooks-in-a-range-object"></a>Para obtener una lista de recientemente los libros utilizados en un objeto range  
  
1.  Recorrer la lista de archivos recientes y muestre los nombres en celdas relativo a un <xref:Microsoft.Office.Interop.Excel.Range> objeto.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#9](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#9)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#9](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#9)]  
  
## <a name="see-also"></a>Vea también  
 [Trabajar con libros](../vsto/working-with-workbooks.md)   
 [NamedRange (Control)](../vsto/namedrange-control.md)   
 [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  