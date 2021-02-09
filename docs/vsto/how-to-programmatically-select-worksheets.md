---
title: 'Cómo: seleccionar hojas de cálculo mediante programación'
description: Use Visual Studio para seleccionar las hojas de cálculo de Microsoft Excel mediante programación con el elemento host de la hoja de cálculo o la colección de hojas del libro de Excel.
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
ms.openlocfilehash: 8a58c4cc53597714eb65010c2fdbb423dd20a35a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99899392"
---
# <a name="how-to-programmatically-select-worksheets"></a>Cómo: seleccionar hojas de cálculo mediante programación
  El método <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A> selecciona el objeto especificado, que mueve la selección del usuario al nuevo objeto. Use el método <xref:Microsoft.Office.Tools.Excel.Worksheet.Activate%2A> si desea llevar el foco al objeto sin cambiar la selección del usuario.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Si desea seleccionar una hoja de cálculo existente en un complemento de VSTO o si la hoja de cálculo se creó en tiempo de ejecución en una personalización de nivel de documento, debe tener acceso a ella mediante la <xref:Microsoft.Office.Interop.Excel.Sheets> colección de Excel del libro de Excel; de lo contrario, puede tener acceso <xref:Microsoft.Office.Tools.Excel.Worksheet> directamente al elemento host.

## <a name="use-the-worksheet-host-item"></a>Usar el elemento host Worksheet
 En una personalización de nivel de documento, agregue el código siguiente a *Sheet1. VB* o *Sheet1.CS*.

### <a name="to-select-the-first-worksheet-in-a-workbook-using-a-host-item"></a>Para seleccionar la primera hoja de cálculo en un libro usando un elemento host

1. Llame al método <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A> de `Sheet1`.

     [!code-csharp[Trin_VstcoreExcelAutomation#19](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#19)]
     [!code-vb[Trin_VstcoreExcelAutomation#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#19)]

## <a name="use-the-sheets-collection-of-the-excel-workbook"></a>Usar la colección sheets del libro de Excel
 Acceda a la hoja de cálculo mediante la colección <xref:Microsoft.Office.Interop.Excel.Sheets> de Excel.

### <a name="to-select-the-first-worksheet-in-a-workbook-using-the-sheets-collection-of-the-excel-workbook"></a>Para seleccionar la primera hoja de cálculo de un libro mediante la colección Sheets del libro de Excel

1. Llame al método <xref:Microsoft.Office.Interop.Excel.Sheets.Select%2A> de la colección <xref:Microsoft.Office.Interop.Excel.Sheets> para seleccionar la primera hoja de cálculo del libro activo.

     [!code-csharp[Trin_VstcoreExcelAutomation#20](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#20)]
     [!code-vb[Trin_VstcoreExcelAutomation#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#20)]

## <a name="see-also"></a>Vea también
- [Trabajar con hojas de cálculo](../vsto/working-with-worksheets.md)
- [Cómo: imprimir hojas de cálculo mediante programación](../vsto/how-to-programmatically-print-worksheets.md)
- [Cómo: eliminar hojas de cálculo de libros mediante programación](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)
- [Cómo: ocultar hojas de cálculo mediante programación](../vsto/how-to-programmatically-hide-worksheets.md)
- [Cómo: proteger hojas de cálculo mediante programación](../vsto/how-to-programmatically-protect-worksheets.md)
- [Elemento host de hoja de cálculo](../vsto/worksheet-host-item.md)
- [Acceso global a objetos en proyectos de Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Limitaciones de programación de elementos y controles host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)
- [Información general sobre elementos y controles host](../vsto/host-items-and-host-controls-overview.md)
