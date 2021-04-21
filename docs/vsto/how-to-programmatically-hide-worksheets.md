---
title: 'Cómo: Ocultar hojas de cálculo mediante programación'
description: Obtenga información sobre cómo puede mostrar u ocultar mediante programación cualquier hoja de cálculo en un libro de Microsoft Excel mediante el elemento host de la hoja de cálculo.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- hidden worksheets
- worksheets, hiding
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b859ea468db86d57347553f9fd10b44fea99026b
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826478"
---
# <a name="how-to-programmatically-hide-worksheets"></a>Cómo: Ocultar hojas de cálculo mediante programación
  Puede mostrar u ocultar las hojas de cálculo de un libro. Para ocultar una hoja de cálculo, use el elemento host de la hoja de cálculo o acceda a ella mediante la colección “Sheets” del libro.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-the-worksheet-host-item"></a>Usar el elemento host de la hoja de cálculo
 Si la hoja de cálculo se agregó durante el diseño de una personalización de nivel de documento, use la propiedad <xref:Microsoft.Office.Tools.Excel.Worksheet.Visible%2A> para ocultar la hoja de cálculo especificada.

### <a name="to-hide-a-worksheet-using-a-worksheet-host-item"></a>Ocultar una hoja de cálculo mediante un elemento host de hoja de cálculo

1. Establezca la propiedad <xref:Microsoft.Office.Tools.Excel.Worksheet.Visible%2A> del elemento host `Sheet1` en el valor de la enumeración <xref:Microsoft.Office.Interop.Excel.XlSheetVisibility.xlSheetHidden> .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet25":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet25":::

## <a name="use-the-sheets-collection-of-the-excel-workbook"></a>Usar la colección Sheets del libro de Excel
 Acceda a las hojas de cálculo a través de la colección <xref:Microsoft.Office.Interop.Excel.Sheets> de Microsoft Office Excel en los siguientes casos:

- Quiere ocultar una hoja de cálculo en un complemento de VSTO.

- Si la hoja de cálculo que desea ocultar se creó en tiempo de ejecución en una personalización de nivel de documento.

### <a name="to-hide-a-worksheet-using-the-sheets-collection-of-the-excel-workbook"></a>Ocultar una hoja de cálculo mediante la colección “Sheets” del libro de Excel

1. Establezca la propiedad <xref:Microsoft.Office.Interop.Excel.Worksheets.Visible%2A> de la hoja de cálculo en el valor de enumeración <xref:Microsoft.Office.Interop.Excel.XlSheetVisibility.xlSheetHidden> .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet26":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet26":::

## <a name="see-also"></a>Consulte también
- [Trabajar con hojas de cálculo](../vsto/working-with-worksheets.md)
- [Cómo: Eliminar hojas de cálculo de libros mediante programación](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)
- [Cómo: Mover hojas de cálculo dentro de libros mediante programación](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)
- [Cómo: Proteger hojas de cálculo mediante programación](../vsto/how-to-programmatically-protect-worksheets.md)
- [Introducción a los elementos host y los controles host](../vsto/host-items-and-host-controls-overview.md)
- [Acceso global a objetos en proyectos de Office](../vsto/global-access-to-objects-in-office-projects.md)
