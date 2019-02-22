---
title: Filtrar Ocultar mediante programación las hojas de cálculo
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- hidden worksheets
- worksheets, hiding
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6fe1ebb3316acfc53ac29ea734413cc0cf2cb15e
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56638561"
---
# <a name="how-to-programmatically-hide-worksheets"></a>Procedimiento Ocultar mediante programación las hojas de cálculo
  Puede mostrar u ocultar las hojas de cálculo de un libro. Para ocultar una hoja de cálculo, use el elemento host de la hoja de cálculo o acceda a ella mediante la colección “Sheets” del libro.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-the-worksheet-host-item"></a>Utilice el elemento host worksheet
 Si la hoja de cálculo se agregó durante el diseño de una personalización de nivel de documento, use la propiedad <xref:Microsoft.Office.Tools.Excel.Worksheet.Visible%2A> para ocultar la hoja de cálculo especificada.

### <a name="to-hide-a-worksheet-using-a-worksheet-host-item"></a>Ocultar una hoja de cálculo mediante un elemento host de hoja de cálculo

1.  Establezca la propiedad <xref:Microsoft.Office.Tools.Excel.Worksheet.Visible%2A> del elemento host `Sheet1` en el valor de la enumeración <xref:Microsoft.Office.Interop.Excel.XlSheetVisibility.xlSheetHidden> .

     [!code-csharp[Trin_VstcoreExcelAutomation#25](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#25)]
     [!code-vb[Trin_VstcoreExcelAutomation#25](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#25)]

## <a name="use-the-sheets-collection-of-the-excel-workbook"></a>Usar la colección Sheets del libro de Excel
 Acceda a las hojas de cálculo a través de la colección <xref:Microsoft.Office.Interop.Excel.Sheets> de Microsoft Office Excel en los siguientes casos:

-   Desea ocultar una hoja de cálculo en un complemento de VSTO.

-   Si la hoja de cálculo que desea ocultar se creó en tiempo de ejecución en una personalización de nivel de documento.

### <a name="to-hide-a-worksheet-using-the-sheets-collection-of-the-excel-workbook"></a>Ocultar una hoja de cálculo mediante la colección “Sheets” del libro de Excel

1.  Establezca la propiedad <xref:Microsoft.Office.Interop.Excel.Worksheets.Visible%2A> de la hoja de cálculo en el valor de enumeración <xref:Microsoft.Office.Interop.Excel.XlSheetVisibility.xlSheetHidden> .

     [!code-csharp[Trin_VstcoreExcelAutomation#26](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#26)]
     [!code-vb[Trin_VstcoreExcelAutomation#26](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#26)]

## <a name="see-also"></a>Vea también
- [Trabajar con hojas de cálculo](../vsto/working-with-worksheets.md)
- [Cómo: Eliminar hojas de cálculo de libros mediante programación](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)
- [Cómo: Mover hojas de cálculo dentro de los libros de programación](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)
- [Cómo: Proteger mediante programación las hojas de cálculo](../vsto/how-to-programmatically-protect-worksheets.md)
- [Elementos host y la información general sobre controles de host](../vsto/host-items-and-host-controls-overview.md)
- [Acceso global a objetos en los proyectos de Office](../vsto/global-access-to-objects-in-office-projects.md)
