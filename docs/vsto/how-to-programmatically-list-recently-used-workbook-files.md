---
title: 'Cómo: mostrar los archivos de libro usados recientemente mediante programación'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, listing recently used
- RecentFiles property
- Excel [Office development in Visual Studio], recently used files listing
- recent file list, Excel
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4f4f34a8ed848d548b2e23d3f9a3cf3c603c7cad
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85541367"
---
# <a name="how-to-programmatically-list-recently-used-workbook-files"></a>Cómo: mostrar los archivos de libro usados recientemente mediante programación
  La <xref:Microsoft.Office.Interop.Excel._Application.RecentFiles%2A> propiedad devuelve una colección que contiene los nombres de todos los archivos que aparecen en la Microsoft Office lista de Excel de archivos usados recientemente. La longitud de la lista varía en función del número de archivos que el usuario haya seleccionado para conservar. Puede mostrar los resultados en un intervalo.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-list-recently-used-workbooks-in-a-range-object"></a>Para enumerar los libros usados recientemente en un objeto Range

1. Recorrer en iteración la lista de archivos recientes y mostrar los nombres en celdas relativas a un <xref:Microsoft.Office.Interop.Excel.Range> objeto.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#9](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#9)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#9](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#9)]

## <a name="see-also"></a>Consulte también
- [Trabajar con libros](../vsto/working-with-workbooks.md)
- [NamedRange (control)](../vsto/namedrange-control.md)
- [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)
