---
title: Procedimiento Lista de usados recientemente mediante programación los archivos de libro
ms.date: 02/02/2017
ms.topic: conceptual
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: 850dc26b9a5f270b3806d9623795535d34cf8f4b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53989638"
---
# <a name="how-to-programmatically-list-recently-used-workbook-files"></a>Procedimiento Lista de usados recientemente mediante programación los archivos de libro
  El <xref:Microsoft.Office.Interop.Excel._Application.RecentFiles%2A> propiedad devuelve una colección que contiene los nombres de todos los archivos que aparecen en la lista de Microsoft Office Excel de archivos usados recientemente. La longitud de la lista varía según el número de archivos que el usuario ha seleccionado para conservar. Puede mostrar los resultados en un intervalo.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="to-list-recently-used-workbooks-in-a-range-object"></a>Para obtener una lista recientemente de los libros utilizados en un objeto range  
  
1.  Recorra en iteración la lista de archivos recientes y mostrar los nombres de las celdas relativo a un <xref:Microsoft.Office.Interop.Excel.Range> objeto.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#9](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#9)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#9](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#9)]  
  
## <a name="see-also"></a>Vea también  
 [Trabajar con libros](../vsto/working-with-workbooks.md)   
 [NamedRange (control)](../vsto/namedrange-control.md)   
 [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)  
