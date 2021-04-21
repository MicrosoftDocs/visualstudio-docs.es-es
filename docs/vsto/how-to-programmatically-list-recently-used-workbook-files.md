---
title: 'Cómo: Enumerar mediante programación los archivos de libro usados recientemente'
description: Obtenga información sobre cómo puede enumerar mediante programación los archivos de libro de Microsoft Excel usados recientemente mediante Visual Studio.
ms.custom: SEO-VS-2020
titleSuffix: ''
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: ba7ca717af4330e8fb3c102b3a5fe5bf7d9162b6
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825334"
---
# <a name="how-to-programmatically-list-recently-used-workbook-files"></a>Cómo: Enumerar mediante programación los archivos de libro usados recientemente
  La propiedad devuelve una colección que contiene los nombres de todos los archivos que aparecen en la lista Microsoft Office Excel de <xref:Microsoft.Office.Interop.Excel._Application.RecentFiles%2A> archivos usados recientemente. La longitud de la lista varía en función del número de archivos que el usuario ha seleccionado conservar. Puede mostrar los resultados en un intervalo.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-list-recently-used-workbooks-in-a-range-object"></a>Para enumerar los libros usados recientemente en un objeto de intervalo

1. Recorrer en bucle la lista de archivos recientes y mostrar los nombres en las celdas relativas a un <xref:Microsoft.Office.Interop.Excel.Range> objeto .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet9":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet9":::

## <a name="see-also"></a>Consulte también
- [Trabajar con libros](../vsto/working-with-workbooks.md)
- [Control NamedRange](../vsto/namedrange-control.md)
- [Parámetros opcionales en soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)
