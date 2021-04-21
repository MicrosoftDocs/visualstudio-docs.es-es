---
title: 'Cómo: Cerrar libros mediante programación'
description: Obtenga información sobre cómo puede cerrar el libro activo o puede especificar un libro para cerrarlo mediante programación.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, closing
- Excel [Office development in Visual Studio], closing workbooks
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: d09cbff06b1bb7048316629b7b958ee299029ec8
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825269"
---
# <a name="how-to-programmatically-close-workbooks"></a>Cómo: Cerrar libros mediante programación
  Puede cerrar el libro activo o especificar el libro que se va a cerrar.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="close-the-active-workbook"></a>Cierre del libro activo
 Hay dos procedimientos para cerrar el libro activo: uno para las personalizaciones de nivel de documento y uno para los complementos de VSTO.

### <a name="to-close-the-active-workbook-in-a-document-level-customization"></a>Para cerrar el libro activo en una personalización de nivel de documento

1. Llame al método <xref:Microsoft.Office.Tools.Excel.Workbook.Close%2A> para cerrar el libro asociado a la personalización. Para usar el ejemplo de código siguiente, ejecútelo en la clase `Sheet1` en un proyecto de nivel de documento para Excel.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet3":::

### <a name="to-close-the-active-workbook-in-a-vsto-add-in"></a>Para cerrar el libro activo en un complemento de VSTO

1. Llame al método <xref:Microsoft.Office.Interop.Excel._Workbook.Close%2A> para cerrar el libro activo. Para usar el ejemplo de código siguiente, ejecútelo en la clase `ThisAddIn` en un proyecto de complemento de VSTO para Excel.

:::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet1":::
:::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet1":::

## <a name="close-a-workbook-that-you-specify-by-name"></a>Cierre un libro que especifique por nombre.
 El modo de cerrar un libro que se especifica según el nombre, es el mismo para los complementos VSTO y para las personalizaciones de nivel de documento.

### <a name="to-close-a-workbook-that-you-specify-by-name"></a>Para cerrar un libro que se especifica por el nombre

1. Especifique el nombre del libro como argumento para la colección <xref:Microsoft.Office.Interop.Excel.Workbooks> . En el siguiente ejemplo de código, se supone que un libro denominado **NewWorkbook** está abierto en Excel.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet2":::

## <a name="see-also"></a>Consulte también
- [Trabajar con libros](../vsto/working-with-workbooks.md)
- [Cómo: Guardar libros mediante programación](../vsto/how-to-programmatically-save-workbooks.md)
- [Cómo: Abrir libros mediante programación](../vsto/how-to-programmatically-open-workbooks.md)
- [Limitaciones de programación de los elementos host y los controles host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Parámetros opcionales en soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)
- [Introducción a los elementos host y los controles host](../vsto/host-items-and-host-controls-overview.md)
