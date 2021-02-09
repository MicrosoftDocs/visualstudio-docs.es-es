---
title: 'Cómo: asignar columnas ListObject a datos'
description: Obtenga información sobre cómo puede asignar las columnas que desea que aparezcan en ListObject cuando se llama al método SetDataBinding.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], mapping to ListObject column
- ListObject control, mapping data
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: ec82809a694e735fed553a1c79ba36687de0fbb1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99900906"
---
# <a name="how-to-map-listobject-columns-to-data"></a>Cómo: asignar columnas ListObject a datos
  Al enlazar un control <xref:Microsoft.Office.Tools.Excel.ListObject> a un <xref:System.Data.DataTable>, puede que no desee mostrar todas las columnas de una lista o puede que tenga algunas columnas que no están enlazadas a datos. Puede asignar las columnas que desea que aparezca en <xref:Microsoft.Office.Tools.Excel.ListObject> al llamar al método <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> .

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="map-columns"></a>Asignar columnas

### <a name="to-map-a-data-table-to-columns-in-a-list"></a>Para asignar una tabla de datos a columnas en una lista

1. Cree la <xref:System.Data.DataTable> en el nivel de clase.

     [!code-csharp[Trin_VstcoreHostControlsExcel#16](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs#16)]
     [!code-vb[Trin_VstcoreHostControlsExcel#16](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb#16)]

2. Agregue columnas de ejemplo y datos en el `Startup` controlador de eventos de la `Sheet1` clase (en un proyecto de nivel de documento) o `ThisAddIn` una clase (en un proyecto de complemento de VSTO).

     [!code-csharp[Trin_VstcoreHostControlsExcel#17](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs#17)]
     [!code-vb[Trin_VstcoreHostControlsExcel#17](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb#17)]

3. Llame al método <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> y pase los nombres de columna en el orden en que deben aparecer. El objeto de lista se enlazará al recién creado <xref:System.Data.DataTable> , pero el orden de las columnas en el objeto de lista será diferente del orden en que aparecen en <xref:System.Data.DataTable> .

     [!code-csharp[Trin_VstcoreHostControlsExcel#18](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs#18)]
     [!code-vb[Trin_VstcoreHostControlsExcel#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb#18)]

## <a name="specify-unmapped-columns"></a>Especificar columnas no asignadas
 Al asignar columnas a un <xref:System.Data.DataTable>, también puede especificar que algunas columnas no se enlacen a datos pasando una cadena vacía. A continuación, se agrega al control <xref:Microsoft.Office.Tools.Excel.ListObject> una nueva columna que no esté enlazada a datos.

### <a name="to-specify-an-unmapped-column-when-mapping-listobject-columns"></a>Para especificar una columna no asignada al asignar columnas ListObject

1. Llame al método <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> y pase los nombres de columna en el orden en que deben aparecer. Use una cadena vacía para indicar dónde se agrega una columna no asignada; en este caso, entre la columna de título y la última columna de nombre.

     [!code-csharp[Trin_VstcoreHostControlsExcel#19](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs#19)]
     [!code-vb[Trin_VstcoreHostControlsExcel#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb#19)]

## <a name="compile-the-code"></a>Compilar el código
 En este ejemplo de código se supone que dispone de un elemento <xref:Microsoft.Office.Tools.Excel.ListObject> existente denominado `list1` en la hoja de cálculo en la que aparece este código.

## <a name="see-also"></a>Vea también
- [Ampliar documentos de Word y libros de Excel en complementos de VSTO en tiempo de ejecución](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Controles en documentos de Office](../vsto/controls-on-office-documents.md)
- [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Cómo: rellenar los controles ListObject con datos](../vsto/how-to-fill-listobject-controls-with-data.md)
- [Automatizar Excel usando objetos extendidos](../vsto/automating-excel-by-using-extended-objects.md)
- [ListObject (control)](../vsto/listobject-control.md)
