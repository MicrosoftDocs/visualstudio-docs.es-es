---
title: Procedimiento Cerrar libros mediante programación
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, closing
- Excel [Office development in Visual Studio], closing workbooks
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ea2ec3162ae7ffdee20f65452f67b0ddf4cc2dd1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62575408"
---
# <a name="how-to-programmatically-close-workbooks"></a>Procedimiento Cerrar libros mediante programación
  Puede cerrar el libro activo o especificar el libro que se va a cerrar.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="close-the-active-workbook"></a>Cerrar el libro activo
 Hay dos procedimientos para cerrar el libro activo: uno para las personalizaciones de nivel de documento y uno para los complementos de VSTO.

### <a name="to-close-the-active-workbook-in-a-document-level-customization"></a>Para cerrar el libro activo en una personalización de nivel de documento

1. Llame al método <xref:Microsoft.Office.Tools.Excel.Workbook.Close%2A> para cerrar el libro asociado a la personalización. Para usar el ejemplo de código siguiente, ejecútelo en la clase `Sheet1` en un proyecto de nivel de documento para Excel.

     [!code-csharp[Trin_VstcoreExcelAutomation#3](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#3)]
     [!code-vb[Trin_VstcoreExcelAutomation#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#3)]

### <a name="to-close-the-active-workbook-in-a-vsto-add-in"></a>Para cerrar el libro activo en un complemento de VSTO

1. Llame al método <xref:Microsoft.Office.Interop.Excel._Workbook.Close%2A> para cerrar el libro activo. Para usar el ejemplo de código siguiente, ejecútelo en la clase `ThisAddIn` en un proyecto de complemento de VSTO para Excel.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#1](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#1)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#1](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#1)]

## <a name="close-a-workbook-that-you-specify-by-name"></a>Cerrar un libro que se especifica por nombre
 El modo de cerrar un libro que se especifica según el nombre, es el mismo para los complementos VSTO y para las personalizaciones de nivel de documento.

### <a name="to-close-a-workbook-that-you-specify-by-name"></a>Para cerrar un libro que se especifica por el nombre

1. Especifique el nombre del libro como argumento para la colección <xref:Microsoft.Office.Interop.Excel.Workbooks> . En el siguiente ejemplo de código, se supone que un libro denominado **NewWorkbook** está abierto en Excel.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#2](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#2)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#2](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#2)]

## <a name="see-also"></a>Vea también
- [Trabajar con libros](../vsto/working-with-workbooks.md)
- [Cómo: Guardar libros mediante programación](../vsto/how-to-programmatically-save-workbooks.md)
- [Cómo: Abrir libros mediante programación](../vsto/how-to-programmatically-open-workbooks.md)
- [Limitaciones de programación de elementos host y controles host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)
- [Elementos host y la información general sobre controles de host](../vsto/host-items-and-host-controls-overview.md)
