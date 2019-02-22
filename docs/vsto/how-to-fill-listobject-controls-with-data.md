---
title: Procedimiento Rellenar los controles ListObject con datos
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- disconnecting from data sources
- ListObject control, disconnecting from a data source
- ListObject control, filling with data
- data [Office development in Visual Studio], adding to worksheets
- data binding, ListObject controls
- worksheets, populating with data
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: cdc2a15db53c8cddb815342a7b6d291c503cdd7f
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56620348"
---
# <a name="how-to-fill-listobject-controls-with-data"></a>Filtrar Rellenar los controles ListObject con datos
  Puede utilizar el enlace de datos como una manera de agregar datos rápidamente al documento. Después de enlazar datos a un objeto de lista, puede desconectar el objeto de lista para que muestre los datos, pero ya no esté enlazado al origen de datos.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 ![vínculo a vídeo](../vsto/media/playvideo.gif "vínculo al vídeo") para una demostración en vídeo relacionada, vea [¿cómo lo hago?: ¿Crear una lista de Excel que está conectado a una lista de SharePoint? ](http://go.microsoft.com/fwlink/?LinkID=130263).

### <a name="to-bind-data-to-a-listobject-control"></a>Para enlazar datos a un control ListObject

1.  Cree un elemento <xref:System.Data.DataTable> en el nivel de clase.

     [!code-csharp[Trin_VstcoreHostControlsExcel#20](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet4.cs#20)]
     [!code-vb[Trin_VstcoreHostControlsExcel#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet4.vb#20)]

2.  Agregue datos y columnas de ejemplo en el controlador de eventos `Startup` de la clase `Sheet1` (en un proyecto de nivel de documento) o una clase `ThisAddIn` (en un proyecto de nivel de aplicación).

     [!code-csharp[Trin_VstcoreHostControlsExcel#21](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet4.cs#21)]
     [!code-vb[Trin_VstcoreHostControlsExcel#21](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet4.vb#21)]

3.  Llame al método <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> y pase los nombres de columna en el orden en que deben aparecer. El orden de las columnas en el objeto de lista puede diferir del orden en que aparecen en el elemento <xref:System.Data.DataTable>.

     [!code-csharp[Trin_VstcoreHostControlsExcel#22](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet4.cs#22)]
     [!code-vb[Trin_VstcoreHostControlsExcel#22](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet4.vb#22)]

### <a name="to-disconnect-the-listobject-control-from-the-data-source"></a>Para desconectar el control ListObject del origen de datos

1.  Llame al método <xref:Microsoft.Office.Tools.Excel.ListObject.Disconnect%2A> de `List1`.

     [!code-csharp[Trin_VstcoreHostControlsExcel#23](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet4.cs#23)]
     [!code-vb[Trin_VstcoreHostControlsExcel#23](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet4.vb#23)]

## <a name="compile-the-code"></a>Compilar el código
 En este ejemplo de código se supone que dispone de un elemento <xref:Microsoft.Office.Tools.Excel.ListObject> existente denominado `list1` en la hoja de cálculo en la que aparece este código.

## <a name="see-also"></a>Vea también
- [Extender documentos de Word y libros de Excel en complementos VSTO en tiempo de ejecución](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Controles en documentos de Office](../vsto/controls-on-office-documents.md)
- [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Cómo: Asignar columnas ListObject a datos](../vsto/how-to-map-listobject-columns-to-data.md)
- [Automatizar Excel usando objetos extendidos](../vsto/automating-excel-by-using-extended-objects.md)
- [ListObject (control)](../vsto/listobject-control.md)
- [Enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Cómo: Rellenar hojas de cálculo con datos de una base de datos](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)
- [Cómo: Rellenar documentos con datos de servicios](../vsto/how-to-populate-documents-with-data-from-services.md)
