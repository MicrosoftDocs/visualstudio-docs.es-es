---
title: 'Cómo: Eliminar hojas de cálculo de libros mediante programación'
description: Obtenga información sobre cómo puede eliminar mediante programación cualquier hoja de cálculo de un libro de Microsoft Excel mediante el elemento host de la hoja de cálculo, por ejemplo.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, deleting worksheets
- worksheets, deleting
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: f3413eaf82b323bc23164687dc3ae3ac0b9d3c48
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825945"
---
# <a name="how-to-programmatically-delete-worksheets-from-workbooks"></a>Cómo: Eliminar hojas de cálculo de libros mediante programación
  Puede eliminar cualquier hoja de cálculo de un libro. Para eliminar una hoja de cálculo, use el elemento host worksheet o acceda a la hoja de cálculo mediante la colección Sheets del libro.

 [!INCLUDE[appliesto_xlalldocapp](includes/appliesto-xlalldocapp-md.md)]

## <a name="use-the-worksheet-host-item"></a>Usar el elemento host de la hoja de cálculo
 Si la hoja de cálculo se agregó en tiempo de diseño en una personalización de nivel de documento, use el método <xref:Microsoft.Office.Tools.Excel.Worksheet.Delete%2A> para eliminar una hoja de cálculo especificada. El siguiente código elimina una hoja de cálculo de un libro haciendo referencia directamente al elemento host worksheet.

> [!IMPORTANT]
> Este código solo se ejecuta en proyectos creados mediante cualquiera de las siguientes plantillas de proyecto:
>
> - Libro de Excel 2013
> - Plantilla de Excel 2013
> - Libro de Excel 2010
> - Plantilla de Excel 2010
>
>   Si desea realizar esta tarea en cualquier otro tipo de proyecto, debe agregar una referencia al ensamblado **Microsoft.Office.Interop.Excel** y, a continuación, debe usar clases de ese ensamblado para abrir un libro y eliminar una hoja de cálculo. Para obtener más información, vea [Cómo:](how-to-target-office-applications-through-primary-interop-assemblies.md) Aplicaciones de Office de destino a través de ensamblados de interoperabilidad primarios y Referencia de ensamblados de [interoperabilidad primarios de Excel 2010](office-primary-interop-assemblies.md).

### <a name="to-delete-a-worksheet-by-using-a-worksheet-host-item"></a>Para eliminar una hoja de cálculo mediante un elemento host worksheet

1. Llame al método <xref:Microsoft.Office.Tools.Excel.Worksheet.Delete%2A> de `Sheet1`.

     :::code language="csharp" source="codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet17":::
     :::code language="vb" source="codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet17":::

## <a name="use-the-sheets-collection-of-the-excel-workbook"></a>Usar la colección Sheets del libro de Excel
 Acceda a las hojas de cálculo a través de la colección <xref:Microsoft.Office.Interop.Excel.Sheets> de Microsoft Office Excel en los siguientes casos:

- Desea eliminar una hoja de cálculo de un complemento de VSTO.

- La hoja de cálculo que desea eliminar se creó en tiempo de ejecución en una personalización de nivel de documento.

  El código siguiente elimina una hoja de cálculo de un libro haciendo referencia a la hoja a través del número de índice de la **colección Sheets.** Este código supone que se ha creado una nueva hoja de cálculo mediante programación.

> [!IMPORTANT]
> Si desea realizar esta tarea en cualquier otro tipo de proyecto, debe agregar una referencia al ensamblado **Microsoft.Office.Interop.Excel** y, a continuación, debe usar clases de ese ensamblado para abrir un libro y eliminar una hoja de cálculo. Para obtener más información, vea [Cómo:](how-to-target-office-applications-through-primary-interop-assemblies.md) Aplicaciones de Office de destino a través de ensamblados de interoperabilidad primarios y Referencia de ensamblados de [interoperabilidad primarios de Excel 2010](office-primary-interop-assemblies.md).

### <a name="to-delete-a-worksheet-by-using-the-sheets-collection-of-the-excel-workbook"></a>Para eliminar una hoja de cálculo mediante la colección Sheets del libro de Excel

1. Llame al método <xref:Microsoft.Office.Interop.Excel._Worksheet.Delete%2A> de la colección <xref:Microsoft.Office.Interop.Excel.Sheets>.

     :::code language="csharp" source="codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet18":::
     :::code language="vb" source="codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet18":::

## <a name="see-also"></a>Consulte también
- [Trabajar con hojas de cálculo](working-with-worksheets.md)
- [Cómo: Ocultar hojas de cálculo mediante programación](how-to-programmatically-hide-worksheets.md)
- [Cómo: Mover hojas de cálculo mediante programación dentro de libros](how-to-programmatically-move-worksheets-within-workbooks.md)
- [Cómo: Seleccionar hojas de cálculo mediante programación](how-to-programmatically-select-worksheets.md)
- [Cómo: Agregar nuevas hojas de cálculo a libros mediante programación](how-to-programmatically-add-new-worksheets-to-workbooks.md)
- [Elemento host de hoja de cálculo](worksheet-host-item.md)
- [Acceso global a objetos en proyectos de Office](global-access-to-objects-in-office-projects.md)
- [Limitaciones de programación de los elementos host y los controles host](programmatic-limitations-of-host-items-and-host-controls.md)
