---
title: 'Cómo: Copiar hojas de cálculo mediante programación'
description: Obtenga información sobre cómo crear una copia de una hoja de cálculo e insertarla antes o después de una hoja de cálculo existente en el libro.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, copying
- Excel [Office development in Visual Studio], copying worksheets
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 2a5b24d7896ec1f81c7e8d5d4c41a5e6af807b13
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828584"
---
# <a name="how-to-programmatically-copy-worksheets"></a>Cómo: Copiar hojas de cálculo mediante programación
  Puede crear una copia de una hoja de cálculo e insertarla antes o después de otra hoja existente en el libro. Si no especifica dónde insertarla, Excel crea un nuevo libro para la nueva hoja de cálculo.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

> [!NOTE]
> Tanto si copia la hoja de cálculo mediante programación como si el usuario final copia la hoja de cálculo manualmente, no hay ningún código detrás de la nueva hoja de cálculo y los controles de la nueva hoja de cálculo no funcionan. Esto se debe a que la hoja de cálculo recién copiada es un objeto <xref:Microsoft.Office.Interop.Excel.Worksheet> y no un elemento host <xref:Microsoft.Office.Tools.Excel.Worksheet>. Los controles de Windows Forms y los controles host solo pueden agregarse a elementos host. Para obtener más información, vea [Limitaciones de programación de elementos host y controles host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).

## <a name="to-add-a-copied-worksheet-to-a-workbook-in-a-document-level-customization"></a>Para agregar una hoja de cálculo copiada a un libro en una personalización de nivel de documento

1. Use el método <xref:Microsoft.Office.Interop.Excel.Worksheets.Copy%2A> para copiar la primera hoja de cálculo en el libro actual y colocarla tras la tercera hoja.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet16":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet16":::

## <a name="to-add-a-copied-worksheet-to-a-workbook-in-a-vsto-add-in"></a>Para agregar una hoja de cálculo copiada a un libro en un complemento de VSTO

1. Use el método <xref:Microsoft.Office.Interop.Excel.Worksheets.Copy%2A> para copiar la primera hoja de cálculo en el libro actual y colocarla tras la tercera hoja.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet12":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet12":::

## <a name="see-also"></a>Consulte también
- [Trabajar con hojas de cálculo](../vsto/working-with-worksheets.md)
- [Introducción a los elementos host y los controles host](../vsto/host-items-and-host-controls-overview.md)
- [Cómo: Agregar nuevas hojas de cálculo a libros mediante programación](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)
- [Cómo: Eliminar hojas de cálculo de libros mediante programación](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)
- [Cómo: Seleccionar hojas de cálculo mediante programación](../vsto/how-to-programmatically-select-worksheets.md)
- [Automatización de Excel mediante objetos extendidos](../vsto/automating-excel-by-using-extended-objects.md)
- [Acceso global a objetos en proyectos de Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Limitaciones de programación de los elementos host y los controles host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Parámetros opcionales en soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)
