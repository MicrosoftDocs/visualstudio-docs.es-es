---
title: Procedimiento Eliminar hojas de cálculo de libros mediante programación
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 7a70e6b7c8126b2e9d2fc3274d5ecf905dce960d
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56644515"
---
# <a name="how-to-programmatically-delete-worksheets-from-workbooks"></a>Filtrar Eliminar hojas de cálculo de libros mediante programación
  Puede eliminar cualquier hoja de cálculo de un libro. Para eliminar una hoja de cálculo, use el elemento host worksheet o acceda a la hoja de cálculo mediante la colección Sheets del libro.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-the-worksheet-host-item"></a>Utilice el elemento host worksheet
 Si la hoja de cálculo se agregó en tiempo de diseño en una personalización de nivel de documento, use el método <xref:Microsoft.Office.Tools.Excel.Worksheet.Delete%2A> para eliminar una hoja de cálculo especificada. El siguiente código elimina una hoja de cálculo de un libro haciendo referencia directamente al elemento host worksheet.

> [!IMPORTANT]
>  Este código solo se ejecuta en proyectos creados mediante cualquiera de las siguientes plantillas de proyecto:
>
> - Libro de Excel 2013
> - Plantilla de Excel 2013
> - Libro de Excel 2010
> - Plantilla de Excel 2010
>
>   Si desea realizar esta tarea en cualquier otro tipo de proyecto, debe agregar una referencia a la **Microsoft.Office.Interop.Excel** ensamblado y, a continuación, debe usar clases de dicho ensamblado para abrir un libro y eliminar una hoja de cálculo. Para obtener más información, vea [Cómo: Apuntar a las aplicaciones de Office a través de los ensamblados de interoperabilidad primarios](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md) y [referencia de ensamblado de interoperabilidad primario de Excel 2010](http://go.microsoft.com/fwlink/?LinkId=189585).

### <a name="to-delete-a-worksheet-by-using-a-worksheet-host-item"></a>Para eliminar una hoja de cálculo mediante un elemento host worksheet

1.  Llame al método <xref:Microsoft.Office.Tools.Excel.Worksheet.Delete%2A> de `Sheet1`.

     [!code-csharp[Trin_VstcoreExcelAutomation#17](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#17)]
     [!code-vb[Trin_VstcoreExcelAutomation#17](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#17)]

## <a name="use-the-sheets-collection-of-the-excel-workbook"></a>Usar la colección Sheets del libro de Excel
 Acceda a las hojas de cálculo a través de la colección <xref:Microsoft.Office.Interop.Excel.Sheets> de Microsoft Office Excel en los siguientes casos:

- Desea eliminar una hoja de cálculo de un complemento de VSTO.

- La hoja de cálculo que desea eliminar se creó en tiempo de ejecución en una personalización de nivel de documento.

  El código siguiente elimina una hoja de cálculo de un libro haciendo referencia al número de índice de la hoja de la **hojas** colección. Este código supone que se ha creado una nueva hoja de cálculo mediante programación.

> [!IMPORTANT]
>  Si desea realizar esta tarea en cualquier otro tipo de proyecto, debe agregar una referencia a la **Microsoft.Office.Interop.Excel** ensamblado y, a continuación, debe usar clases de dicho ensamblado para abrir un libro y eliminar una hoja de cálculo. Para obtener más información, vea [Cómo: Apuntar a las aplicaciones de Office a través de los ensamblados de interoperabilidad primarios](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md) y [referencia de ensamblado de interoperabilidad primario de Excel 2010](http://go.microsoft.com/fwlink/?LinkId=189585).

### <a name="to-delete-a-worksheet-by-using-the-sheets-collection-of-the-excel-workbook"></a>Para eliminar una hoja de cálculo mediante la colección Sheets del libro de Excel

1.  Llame al método <xref:Microsoft.Office.Interop.Excel._Worksheet.Delete%2A> de la colección <xref:Microsoft.Office.Interop.Excel.Sheets>.

     [!code-csharp[Trin_VstcoreExcelAutomation#18](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#18)]
     [!code-vb[Trin_VstcoreExcelAutomation#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#18)]

## <a name="see-also"></a>Vea también
- [Trabajar con hojas de cálculo](../vsto/working-with-worksheets.md)
- [Cómo: Ocultar mediante programación las hojas de cálculo](../vsto/how-to-programmatically-hide-worksheets.md)
- [Cómo: Mover hojas de cálculo dentro de los libros de programación](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)
- [Cómo: Seleccionar mediante programación las hojas de cálculo](../vsto/how-to-programmatically-select-worksheets.md)
- [Cómo: Agregar nuevas hojas de cálculo a libros mediante programación](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)
- [Elemento host Worksheet](../vsto/worksheet-host-item.md)
- [Acceso global a objetos en los proyectos de Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Limitaciones de programación de elementos host y controles host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
