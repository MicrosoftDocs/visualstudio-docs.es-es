---
title: 'Cómo: crear nuevos libros mediante programación'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel [Office development in Visual Studio], creating workbooks
- workbooks, creating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6a23f4b089d580d482193d278f22e4990d343097
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545982"
---
# <a name="how-to-programmatically-create-new-workbooks"></a>Cómo: crear nuevos libros mediante programación
  Al crear mediante programación un libro, es un objeto <xref:Microsoft.Office.Interop.Excel.Workbook> nativo, no un elemento host <xref:Microsoft.Office.Tools.Excel.Workbook>.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Puede generar un elemento host <xref:Microsoft.Office.Tools.Excel.Workbook> para un objeto <xref:Microsoft.Office.Interop.Excel.Workbook> en un proyecto de complemento de VSTO. Para obtener más información, vea [ampliar documentos de Word y libros de Excel en complementos de VSTO en tiempo de ejecución](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="to-create-a-new-workbook"></a>Para crear un libro nuevo

1. Use el método <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A> de la colección <xref:Microsoft.Office.Interop.Excel.Workbooks> .

     [!code-csharp[Trin_VstcoreExcelAutomation#1](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#1)]
     [!code-vb[Trin_VstcoreExcelAutomation#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#1)]

    > [!NOTE]
    > Puede crear un libro basado en una plantilla distinta de la plantilla predeterminada: pase la plantilla que desea usar como un parámetro al método <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A>.

## <a name="see-also"></a>Consulte también
- [Ampliar documentos de Word y libros de Excel en complementos de VSTO en tiempo de ejecución](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Trabajar con libros](../vsto/working-with-workbooks.md)
- [Cómo: abrir libros mediante programación](../vsto/how-to-programmatically-open-workbooks.md)
- [Cómo: guardar libros mediante programación](../vsto/how-to-programmatically-save-workbooks.md)
- [Cómo: cerrar libros mediante programación](../vsto/how-to-programmatically-close-workbooks.md)
- [Limitaciones de programación de elementos y controles host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)
- [Información general sobre elementos y controles host](../vsto/host-items-and-host-controls-overview.md)
