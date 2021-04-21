---
title: 'Cómo: Imprimir hojas de cálculo mediante programación'
description: Obtenga información sobre cómo puede usar Visual Studio para imprimir mediante programación cualquier hoja de cálculo en un libro de Microsoft Excel.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- printing [Office development in Visual Studio], worksheets
- worksheets, printing
- print preview, worksheets
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 129493f726967776aa669eb92f6e912ed9c1b11b
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827154"
---
# <a name="how-to-programmatically-print-worksheets"></a>Cómo: Imprimir hojas de cálculo mediante programación

Puede imprimir cualquier hoja de cálculo de un libro.

[!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="print-a-worksheet-in-a-document-level-customization"></a>Imprimir una hoja de cálculo en una personalización de nivel de documento

### <a name="to-print-a-worksheet"></a>Para imprimir una hoja de cálculo

1. Llame al método `PrintOut` de `Sheet1`, solicite dos copias y obtenga una vista previa del documento antes de imprimirlo.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet22":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet22":::

   El <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintPreview%2A> método permite mostrar el objeto especificado en la ventana Vista previa **de** impresión. El siguiente código supone que tiene un elemento host <xref:Microsoft.Office.Tools.Excel.Worksheet> denominado `Sheet1`.

### <a name="to-preview-a-page-before-printing"></a>Para obtener una vista previa de una página antes de imprimirla

1. Llame al método <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintPreview%2A> de la hoja de cálculo.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet23":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet23":::

## <a name="print-a-worksheet-in-a-vsto-add-in"></a>Imprimir una hoja de cálculo en un complemento de VSTO

### <a name="to-print-a-worksheet"></a>Para imprimir una hoja de cálculo

1. Llame al método <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintOut%2A> de la hoja de cálculo activa, solicite dos copias y obtenga una vista previa del documento antes de imprimirlo.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet14":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet14":::

   El <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> método permite mostrar el objeto especificado en la ventana Vista previa **de** impresión.

### <a name="to-preview-a-page-before-printing"></a>Para obtener una vista previa de una página antes de imprimirla

1. Llame al método <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> de la hoja de cálculo activa.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet15":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet15":::

## <a name="see-also"></a>Consulte también

- [Trabajar con hojas de cálculo](../vsto/working-with-worksheets.md)
- [Cómo: Comprobar la ortografía en hojas de cálculo mediante programación](../vsto/how-to-programmatically-check-spelling-in-worksheets.md)
- [Elemento host de hoja de cálculo](../vsto/worksheet-host-item.md)
- [Acceso global a objetos en proyectos de Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Parámetros opcionales en soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)
