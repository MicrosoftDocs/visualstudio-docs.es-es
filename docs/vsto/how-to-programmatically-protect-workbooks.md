---
title: 'Cómo: Proteger libros mediante programación'
description: Obtenga información sobre cómo proteger un libro de Microsoft Excel para que los usuarios no puedan agregar ni eliminar hojas de cálculo, y también desproteger el libro mediante programación.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, passwords
- documents [Office development in Visual Studio], document protection
- workbooks, unprotecting
- document protection, removing from workbooks
- document protection, adding to workbooks
- workbooks, protecting
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 9f0b479c56be6da7b14f87263c8c01d66910ac20
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827115"
---
# <a name="how-to-programmatically-protect-workbooks"></a>Cómo: Proteger libros mediante programación
  Puede proteger un libro de Excel Microsoft Office para que los usuarios no puedan agregar ni eliminar hojas de cálculo, y también desproteger el libro mediante programación. Opcionalmente, puede especificar una contraseña, indicar si desea proteger la estructura (para que los usuarios no puedan mover hojas) e indicar si desea proteger las ventanas del libro.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 La protección de un libro no impedirá que los usuarios editen celdas. Para proteger los datos, debe proteger las hojas de cálculo. Para obtener más información, vea Cómo: Proteger hojas de cálculo [mediante programación.](../vsto/how-to-programmatically-protect-worksheets.md)

 En los ejemplos de código siguientes se usa una variable para contener una contraseña que se obtiene del usuario.

## <a name="protect-a-workbook-that-is-part-of-a-document-level-customization"></a>Protección de un libro que forma parte de una personalización de nivel de documento

### <a name="to-protect-a-workbook"></a>Para proteger un libro

1. Llame al <xref:Microsoft.Office.Tools.Excel.Workbook.Protect%2A> método del libro e incluya una contraseña. Para usar el ejemplo de código siguiente, ejecute en la `ThisWorkbook` clase , no en una clase de hoja.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs" id="Snippet10":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb" id="Snippet10":::

### <a name="to-unprotect-a-workbook"></a>Para desproteger un libro

1. Llame al <xref:Microsoft.Office.Tools.Excel.Workbook.Unprotect%2A> método y pase una contraseña si es necesario. Para usar el ejemplo de código siguiente, ejecute en la `ThisWorkbook` clase , no en una clase de hoja.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs" id="Snippet11":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb" id="Snippet11":::

## <a name="protect-a-workbook-by-using-an-application-level-add-in"></a>Protección de un libro mediante un complemento de nivel de aplicación

### <a name="to-protect-a-workbook"></a>Para proteger un libro

1. Llame al <xref:Microsoft.Office.Interop.Excel._Workbook.Protect%2A> método del libro e incluya una contraseña. En este ejemplo de código se usa el libro activo. Para usar este ejemplo, ejecute el código desde la clase `ThisAddIn` del proyecto.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet6":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet6":::

### <a name="to-unprotect-a-workbook"></a>Para desproteger un libro

1. Llame al <xref:Microsoft.Office.Interop.Excel._Workbook.Unprotect%2A> método del libro activo y pase una contraseña si es necesario. Para usar este ejemplo, ejecute el código desde la clase `ThisAddIn` del proyecto.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet7":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet7":::

## <a name="see-also"></a>Consulte también
- [Trabajar con libros](../vsto/working-with-workbooks.md)
- [Cómo: Proteger hojas de cálculo mediante programación](../vsto/how-to-programmatically-protect-worksheets.md)
- [Cómo: Ocultar hojas de cálculo mediante programación](../vsto/how-to-programmatically-hide-worksheets.md)
- [Parámetros opcionales en soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)
