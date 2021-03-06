---
title: 'Cómo: Guardar libros mediante programación'
description: Guarde los libros de Microsoft Excel mediante programación sin cambiar la ruta de acceso y guarde una copia de un libro sin modificar el libro abierto en memoria.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, saving in XML format
- workbooks, saving
- workbooks, saving backup copies
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 4559d098a80a1dfd8f1d3f5c2c21cbebc992fcb7
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828987"
---
# <a name="how-to-programmatically-save-workbooks"></a>Cómo: Guardar libros mediante programación
  Existen varias formas de guardar un libro. Puede guardar un libro sin cambiar la ruta de acceso. Si el libro nunca se guardó, debe guardarlo especificando una ruta de acceso. Sin una ruta de acceso explícita, Microsoft Office Excel guarda el archivo en la carpeta actual con el nombre que se especificó cuando se creó. También puede guardar una copia del libro sin modificar el libro abierto en memoria.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="save-a-workbook-without-changing-the-path"></a>Guardar un libro sin cambiar la ruta de acceso

### <a name="to-save-a-workbook-associated-with-a-document-level-customization"></a>Para guardar un libro asociado a una personalización de nivel de documento

1. Llame al método <xref:Microsoft.Office.Tools.Excel.Workbook.Save%2A> de la clase `ThisWorkbook` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs" id="Snippet4":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb" id="Snippet4":::

### <a name="to-save-the-active-workbook-in-a-vsto-add-in"></a>Para guardar el libro activo en un complemento de VSTO

1. Llame al método <xref:Microsoft.Office.Interop.Excel._Workbook.Save%2A> para guardar el libro activo. Para usar el ejemplo de código siguiente, ejecútelo en la clase `ThisAddIn` en un proyecto de complemento de VSTO para Excel.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet3":::

## <a name="save-a-workbook-with-a-new-path"></a>Guardar un libro con una nueva ruta de acceso
 Puede guardar el libro especificado en una ubicación nueva o con un nombre nuevo, especificando opcionalmente un formato de archivo, una contraseña y un modo de acceso, entre otras cosas.

> [!NOTE]
> Es posible que quiera establecer la propiedad en False antes de guardar el libro con una nueva ruta de acceso porque guardar en <xref:Microsoft.Office.Interop.Excel._Application.DisplayAlerts%2A> algunos formatos requiere interacción.  Si se establece esta propiedad en **False,** Excel usará todos los valores predeterminados.

### <a name="to-save-a-workbook-associated-with-a-document-level-customization"></a>Para guardar un libro asociado a una personalización de nivel de documento

1. Llame al método <xref:Microsoft.Office.Tools.Excel.Workbook.SaveAs%2A> de la clase `ThisWorkbook` . Para usar el siguiente ejemplo de código, ejecútelo en la clase `ThisWorkbook`.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs" id="Snippet5":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb" id="Snippet5":::

### <a name="to-save-the-active-workbook-in-a-vsto-add-in"></a>Para guardar el libro activo en un complemento de VSTO

1. Llame al método <xref:Microsoft.Office.Interop.Excel._Workbook.SaveAs%2A> para guardar el libro activo en una nueva ruta de acceso. Para usar el ejemplo de código siguiente, ejecútelo en la clase `ThisAddIn` en un proyecto de complemento de VSTO para Excel.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet4":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet4":::

## <a name="save-a-copy-of-the-workbook"></a>Guardar una copia del libro
 Puede guardar una copia del libro en un archivo sin modificar el libro abierto en memoria. Esto es útil cuando se desea crear una copia de seguridad sin modificar la ubicación del libro.

### <a name="to-save-a-workbook-associated-with-a-document-level-customization"></a>Para guardar un libro asociado a una personalización de nivel de documento

1. Llame al método <xref:Microsoft.Office.Tools.Excel.Workbook.SaveCopyAs%2A> de la clase `ThisWorkbook` . Para usar el siguiente ejemplo de código, ejecútelo en la clase `ThisWorkbook`.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs" id="Snippet6":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb" id="Snippet6":::

### <a name="to-save-the-active-workbook-in-a-vsto-add-in"></a>Para guardar el libro activo en un complemento de VSTO

1. Llame al método <xref:Microsoft.Office.Interop.Excel._Workbook.SaveCopyAs%2A> para guardar una copia del libro activo. Para usar el ejemplo de código siguiente, ejecútelo en la clase `ThisAddIn` en un proyecto de complemento de VSTO para Excel.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet5":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet5":::

## <a name="robust-programming"></a>Programación sólida
 Si se cancela interactivamente cualquiera de los métodos que guardan o copian el libro se produce un error en tiempo de ejecución en el código. Por ejemplo, si el procedimiento llama al método pero no deshabilita los mensajes de Excel y el usuario hace clic en Cancelar cuando se le solicite, Excel genera un error en tiempo <xref:Microsoft.Office.Tools.Excel.Workbook.SaveAs%2A> de ejecución. 

## <a name="see-also"></a>Consulte también
- [Trabajar con libros](../vsto/working-with-workbooks.md)
- [Elemento host del libro](../vsto/workbook-host-item.md)
- [Cómo: Cerrar libros mediante programación](../vsto/how-to-programmatically-close-workbooks.md)
- [Limitaciones mediante programación de elementos host y controles host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Parámetros opcionales en soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)
- [Introducción a los elementos host y los controles host](../vsto/host-items-and-host-controls-overview.md)
