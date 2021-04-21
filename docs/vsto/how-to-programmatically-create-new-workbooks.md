---
title: 'Cómo: Crear nuevos libros mediante programación'
description: Obtenga información sobre cómo puede crear mediante programación un nuevo libro de Microsoft Excel mediante Visual Studio.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 8a0a6e0b7b81c472ce03b1255c2c6899df0389da
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825984"
---
# <a name="how-to-programmatically-create-new-workbooks"></a>Cómo: Crear nuevos libros mediante programación
  Al crear mediante programación un libro, es un objeto <xref:Microsoft.Office.Interop.Excel.Workbook> nativo, no un elemento host <xref:Microsoft.Office.Tools.Excel.Workbook>.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Puede generar un elemento host <xref:Microsoft.Office.Tools.Excel.Workbook> para un objeto <xref:Microsoft.Office.Interop.Excel.Workbook> en un proyecto de complemento de VSTO. Para obtener más información, vea Extender documentos de Word y libros de Excel en [complementos de VSTO en tiempo de ejecución.](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)

## <a name="to-create-a-new-workbook"></a>Para crear un libro nuevo

1. Use el método <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A> de la colección <xref:Microsoft.Office.Interop.Excel.Workbooks> .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet1":::

    > [!NOTE]
    > Puede crear un libro basado en una plantilla distinta de la plantilla predeterminada: pase la plantilla que desea usar como un parámetro al método <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A>.

## <a name="see-also"></a>Consulte también
- [Extensión de documentos de Word y libros de Excel en complementos de VSTO en tiempo de ejecución](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Trabajar con libros](../vsto/working-with-workbooks.md)
- [Cómo: Abrir libros mediante programación](../vsto/how-to-programmatically-open-workbooks.md)
- [Cómo: Guardar libros mediante programación](../vsto/how-to-programmatically-save-workbooks.md)
- [Cómo: Cerrar libros mediante programación](../vsto/how-to-programmatically-close-workbooks.md)
- [Limitaciones mediante programación de elementos host y controles host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Parámetros opcionales en soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)
- [Introducción a los elementos host y los controles host](../vsto/host-items-and-host-controls-overview.md)
