---
title: 'Cómo: Agregar y eliminar comentarios de hojas de cálculo mediante programación'
description: Obtenga información sobre cómo puede agregar y eliminar comentarios mediante programación en Microsoft Office hojas de cálculo de Excel. Solo puede agregar comentarios a celdas únicas, no a intervalos de varias celdas.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, comments
- worksheets, comments
- comments, worksheets
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 20b718be3bec6cac3ee6c0b0985fa6efca867189
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826946"
---
# <a name="how-to-programmatically-add-and-delete-worksheet-comments"></a>Cómo: Agregar y eliminar comentarios de hojas de cálculo mediante programación
  Puede agregar y eliminar comentarios en las hojas de cálculo de Microsoft Office Excel mediante programación. Los comentarios solo se pueden agregar a celdas individuales y no a intervalos de varias celdas.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="add-and-delete-a-comment-in-a-document-level-project"></a>Agregar y eliminar un comentario en un proyecto de nivel de documento
 En los ejemplos siguientes, se da por hecho que hay un control <xref:Microsoft.Office.Tools.Excel.NamedRange> de una sola celda denominado `dateComment` en una hoja de cálculo denominada `Sheet1`.

### <a name="to-add-a-new-comment-to-a-named-range"></a>Agregar un nuevo comentario a un intervalo con nombre

1. Llame al método <xref:Microsoft.Office.Tools.Excel.NamedRange.AddComment%2A> del control <xref:Microsoft.Office.Tools.Excel.NamedRange> y escriba el texto del comentario. Este código se debe colocar en la clase `Sheet1` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet30":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet30":::

#### <a name="to-delete-a-comment-from-a-named-range"></a>Eliminar un comentario de un intervalo con nombre

1. Compruebe si en el intervalo hay un comentario y elimínelo. Este código se debe colocar en la clase `Sheet1` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet29":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet29":::

## <a name="add-and-delete-a-comment-in-a-vsto-add-in-project"></a>Agregar y eliminar un comentario en un proyecto de complemento de VSTO
 En los ejemplos siguientes, se da por hecho que hay una sola celda <xref:Microsoft.Office.Interop.Excel.Range> denominada `dateComment` en una hoja de cálculo.

### <a name="to-add-a-new-comment-to-an-excel-range"></a>Agregar un nuevo comentario a un intervalo de Excel

1. Llame al método <xref:Microsoft.Office.Interop.Excel.Range.AddComment%2A> de <xref:Microsoft.Office.Interop.Excel.Range> y escriba el texto del comentario.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet20":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet20":::

### <a name="to-delete-a-comment-from-an-excel-range"></a>Eliminar un comentario de un intervalo de Excel

1. Compruebe si en el intervalo hay un comentario y elimínelo.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet19":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet19":::

## <a name="see-also"></a>Consulte también
- [Trabajar con hojas de cálculo](../vsto/working-with-worksheets.md)
- [Cómo: Mostrar comentarios de hojas de cálculo mediante programación](../vsto/how-to-programmatically-display-worksheet-comments.md)
- [Control NamedRange](../vsto/namedrange-control.md)
