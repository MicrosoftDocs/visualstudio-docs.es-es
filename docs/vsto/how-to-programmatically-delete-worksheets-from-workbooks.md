---
title: 'Cómo: eliminar hojas de cálculo de libros mediante programación'
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 38aa92ae1c320ae9eb5ad4bdb1e43b761048661f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547139"
---
# <a name="how-to-programmatically-delete-worksheets-from-workbooks"></a>Cómo: eliminar hojas de cálculo de libros mediante programación
  Puede eliminar cualquier hoja de cálculo de un libro. Para eliminar una hoja de cálculo, use el elemento host worksheet o acceda a la hoja de cálculo mediante la colección Sheets del libro.

 [!INCLUDE[appliesto_xlalldocapp](includes/appliesto-xlalldocapp-md.md)]

## <a name="use-the-worksheet-host-item"></a>Usar el elemento host Worksheet
 Si la hoja de cálculo se agregó en tiempo de diseño en una personalización de nivel de documento, use el método <xref:Microsoft.Office.Tools.Excel.Worksheet.Delete%2A> para eliminar una hoja de cálculo especificada. El siguiente código elimina una hoja de cálculo de un libro haciendo referencia directamente al elemento host worksheet.

> [!IMPORTANT]
> Este código solo se ejecuta en proyectos creados mediante cualquiera de las siguientes plantillas de proyecto:
>
> - Libro de Excel 2013
> - Plantilla de Excel 2013
> - Libro de Excel 2010
> - Plantilla de Excel 2010
>
>   Si desea realizar esta tarea en cualquier otro tipo de proyecto, debe agregar una referencia al ensamblado **Microsoft. Office. Interop. Excel** y, a continuación, debe usar las clases de ese ensamblado para abrir un libro y eliminar una hoja de cálculo. Para obtener más información, vea [Cómo: establecer como destino aplicaciones de Office mediante ensamblados de interoperabilidad primarios](how-to-target-office-applications-through-primary-interop-assemblies.md) y [referencia de ensamblado de interoperabilidad primario de Excel 2010](office-primary-interop-assemblies.md).

### <a name="to-delete-a-worksheet-by-using-a-worksheet-host-item"></a>Para eliminar una hoja de cálculo mediante un elemento host worksheet

1. Llame al método <xref:Microsoft.Office.Tools.Excel.Worksheet.Delete%2A> de `Sheet1`.

     [!code-csharp[Trin_VstcoreExcelAutomation#17](codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#17)]
     [!code-vb[Trin_VstcoreExcelAutomation#17](codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#17)]

## <a name="use-the-sheets-collection-of-the-excel-workbook"></a>Usar la colección sheets del libro de Excel
 Acceda a las hojas de cálculo a través de la colección <xref:Microsoft.Office.Interop.Excel.Sheets> de Microsoft Office Excel en los siguientes casos:

- Desea eliminar una hoja de cálculo de un complemento de VSTO.

- La hoja de cálculo que desea eliminar se creó en tiempo de ejecución en una personalización de nivel de documento.

  El siguiente código elimina una hoja de cálculo de un libro haciendo referencia a la hoja mediante el número de índice de la colección de **hojas** . Este código supone que se ha creado una nueva hoja de cálculo mediante programación.

> [!IMPORTANT]
> Si desea realizar esta tarea en cualquier otro tipo de proyecto, debe agregar una referencia al ensamblado **Microsoft. Office. Interop. Excel** y, a continuación, debe usar las clases de ese ensamblado para abrir un libro y eliminar una hoja de cálculo. Para obtener más información, vea [Cómo: establecer como destino aplicaciones de Office mediante ensamblados de interoperabilidad primarios](how-to-target-office-applications-through-primary-interop-assemblies.md) y [referencia de ensamblado de interoperabilidad primario de Excel 2010](office-primary-interop-assemblies.md).

### <a name="to-delete-a-worksheet-by-using-the-sheets-collection-of-the-excel-workbook"></a>Para eliminar una hoja de cálculo mediante la colección Sheets del libro de Excel

1. Llame al método <xref:Microsoft.Office.Interop.Excel._Worksheet.Delete%2A> de la colección <xref:Microsoft.Office.Interop.Excel.Sheets>.

     [!code-csharp[Trin_VstcoreExcelAutomation#18](codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#18)]
     [!code-vb[Trin_VstcoreExcelAutomation#18](codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#18)]

## <a name="see-also"></a>Vea también
- [Trabajar con hojas de cálculo](working-with-worksheets.md)
- [Cómo: ocultar hojas de cálculo mediante programación](how-to-programmatically-hide-worksheets.md)
- [Cómo: trasladar hojas de cálculo dentro de libros mediante programación](how-to-programmatically-move-worksheets-within-workbooks.md)
- [Cómo: seleccionar hojas de cálculo mediante programación](how-to-programmatically-select-worksheets.md)
- [Cómo: agregar nuevas hojas de cálculo a libros mediante programación](how-to-programmatically-add-new-worksheets-to-workbooks.md)
- [Elemento host de hoja de cálculo](worksheet-host-item.md)
- [Acceso global a objetos en proyectos de Office](global-access-to-objects-in-office-projects.md)
- [Limitaciones de programación de elementos y controles host](programmatic-limitations-of-host-items-and-host-controls.md)
