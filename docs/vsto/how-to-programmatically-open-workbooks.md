---
title: 'Cómo: abrir libros mediante programación'
description: Obtenga información sobre cómo puede usar Visual Studio para abrir mediante programación un libro de Microsoft Excel o trabajar con un libro existente.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, opening
- Excel [Office development in Visual Studio], opening workbooks
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f7de4072df177bd9a7c6ae23bf59e44e50d56e32
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2020
ms.locfileid: "97523894"
---
# <a name="how-to-programmatically-open-workbooks"></a>Cómo: abrir libros mediante programación
  La <xref:Microsoft.Office.Interop.Excel.Workbooks> colección de Microsoft Office Excel permite trabajar con todos los libros abiertos y abrir los libros.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-open-an-existing-workbook"></a>Para abrir un libro existente

1. Use el <xref:Microsoft.Office.Interop.Excel.Workbooks.Open%2A> método de la <xref:Microsoft.Office.Interop.Excel.Workbooks> colección, pasando la ruta de acceso al libro.

     [!code-csharp[Trin_VstcoreExcelAutomation#2](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#2)]
     [!code-vb[Trin_VstcoreExcelAutomation#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#2)]

## <a name="compile-the-code"></a>Compilar el código
 Para este ejemplo de código se necesita lo siguiente:

- Un libro denominado `YourWorkbook.xls` debe existir en un directorio denominado `Test` en la unidad C.

## <a name="see-also"></a>Consulte también
- [Trabajar con libros](../vsto/working-with-workbooks.md)
- [Cómo: abrir archivos de texto como libros mediante programación](../vsto/how-to-programmatically-open-text-files-as-workbooks.md)
- [Cómo: crear nuevos libros mediante programación](../vsto/how-to-programmatically-create-new-workbooks.md)
- [Cómo: guardar libros mediante programación](../vsto/how-to-programmatically-save-workbooks.md)
- [Cómo: cerrar libros mediante programación](../vsto/how-to-programmatically-close-workbooks.md)
- [Limitaciones de programación de elementos y controles host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)
- [Información general sobre elementos y controles host](../vsto/host-items-and-host-controls-overview.md)
