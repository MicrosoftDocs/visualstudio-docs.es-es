---
title: 'Cómo: Seleccionar hojas de cálculo mediante programación'
description: Use Visual Studio para seleccionar hojas de cálculo de Microsoft Excel mediante programación con el elemento host de la hoja de cálculo o la colección de hojas del libro de Excel.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, selecting
- Excel projects, selecting worksheets
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 04f410292fff686e7604e917e6c3fa7002c65273
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826257"
---
# <a name="how-to-programmatically-select-worksheets"></a>Cómo: Seleccionar hojas de cálculo mediante programación
  El método <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A> selecciona el objeto especificado, que mueve la selección del usuario al nuevo objeto. Use el método <xref:Microsoft.Office.Tools.Excel.Worksheet.Activate%2A> si desea llevar el foco al objeto sin cambiar la selección del usuario.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Si desea seleccionar una hoja de cálculo existente en un complemento de VSTO o si la hoja de cálculo se creó en tiempo de ejecución en una personalización de nivel de documento, debe acceder a ella mediante la colección de Excel del libro de Excel; de lo contrario, puede acceder al elemento <xref:Microsoft.Office.Interop.Excel.Sheets> <xref:Microsoft.Office.Tools.Excel.Worksheet> host directamente.

## <a name="use-the-worksheet-host-item"></a>Uso del elemento host de la hoja de cálculo
 En una personalización de nivel de documento, agregue el código siguiente a *Sheet1.vb* o *Sheet1.cs.*

### <a name="to-select-the-first-worksheet-in-a-workbook-using-a-host-item"></a>Para seleccionar la primera hoja de cálculo en un libro usando un elemento host

1. Llame al método <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A> de `Sheet1`.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet19":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet19":::

## <a name="use-the-sheets-collection-of-the-excel-workbook"></a>Uso de la colección de hojas del libro de Excel
 Acceda a la hoja de cálculo mediante la colección <xref:Microsoft.Office.Interop.Excel.Sheets> de Excel.

### <a name="to-select-the-first-worksheet-in-a-workbook-using-the-sheets-collection-of-the-excel-workbook"></a>Para seleccionar la primera hoja de cálculo de un libro mediante la colección Sheets del libro de Excel

1. Llame al método <xref:Microsoft.Office.Interop.Excel.Sheets.Select%2A> de la colección <xref:Microsoft.Office.Interop.Excel.Sheets> para seleccionar la primera hoja de cálculo del libro activo.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet20":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet20":::

## <a name="see-also"></a>Consulte también
- [Trabajar con hojas de cálculo](../vsto/working-with-worksheets.md)
- [Cómo: Imprimir hojas de cálculo mediante programación](../vsto/how-to-programmatically-print-worksheets.md)
- [Cómo: Eliminar hojas de cálculo de libros mediante programación](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)
- [Cómo: Ocultar hojas de cálculo mediante programación](../vsto/how-to-programmatically-hide-worksheets.md)
- [Cómo: Proteger hojas de cálculo mediante programación](../vsto/how-to-programmatically-protect-worksheets.md)
- [Elemento host de hoja de cálculo](../vsto/worksheet-host-item.md)
- [Acceso global a objetos en proyectos de Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Limitaciones mediante programación de elementos host y controles host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Parámetros opcionales en soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)
- [Introducción a los elementos host y los controles host](../vsto/host-items-and-host-controls-overview.md)
