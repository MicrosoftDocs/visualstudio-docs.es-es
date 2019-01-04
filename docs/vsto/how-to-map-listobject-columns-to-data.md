---
title: Procedimiento Asignar columnas ListObject a datos
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], mapping to ListObject column
- ListObject control, mapping data
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 508a0fa8df58e70eb216f722ee96395c7a9c21ad
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53899988"
---
# <a name="how-to-map-listobject-columns-to-data"></a>Procedimiento Asignar columnas ListObject a datos
  Al enlazar un control <xref:Microsoft.Office.Tools.Excel.ListObject> a un <xref:System.Data.DataTable>, puede que no desee mostrar todas las columnas de una lista o puede que tenga algunas columnas que no están enlazadas a datos. Puede asignar las columnas que desea que aparezca en <xref:Microsoft.Office.Tools.Excel.ListObject> al llamar al método <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> .  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 ![vínculo a vídeo](../vsto/media/playvideo.gif "vínculo al vídeo") para una demostración en vídeo relacionada, vea [¿cómo lo hago?: ¿Crear una lista de Excel que está conectado a una lista de SharePoint? ](http://go.microsoft.com/fwlink/?LinkID=130263).  
  
## <a name="map-columns"></a>Asignar columnas  
  
### <a name="to-map-a-data-table-to-columns-in-a-list"></a>Para asignar una tabla de datos a columnas en una lista  
  
1.  Cree la <xref:System.Data.DataTable> en el nivel de clase.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#16](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs#16)]
     [!code-vb[Trin_VstcoreHostControlsExcel#16](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb#16)]  
  
2.  Agregue columnas de ejemplo y datos en el `Startup` controlador de eventos de la `Sheet1` clase (en un proyecto de nivel de documento) o `ThisAddIn` clase (en un proyecto de complemento de VSTO).  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#17](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs#17)]
     [!code-vb[Trin_VstcoreHostControlsExcel#17](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb#17)]  
  
3.  Llame al método <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> y pase los nombres de columna en el orden en que deben aparecer. El objeto de lista se enlazará a recién creado <xref:System.Data.DataTable>, pero el orden de las columnas del objeto de lista diferirá en el orden en que aparecen en la <xref:System.Data.DataTable>.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#18](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs#18)]
     [!code-vb[Trin_VstcoreHostControlsExcel#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb#18)]  
  
## <a name="specify-unmapped-columns"></a>Especificar columnas no asignadas  
 Al asignar columnas a un <xref:System.Data.DataTable>, también puede especificar que algunas columnas no se enlacen a datos pasando una cadena vacía. A continuación, se agrega al control <xref:Microsoft.Office.Tools.Excel.ListObject> una nueva columna que no esté enlazada a datos.  
  
### <a name="to-specify-an-unmapped-column-when-mapping-listobject-columns"></a>Para especificar una columna no asignada al asignar columnas ListObject  
  
1.  Llame al método <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> y pase los nombres de columna en el orden en que deben aparecer. Use una cadena vacía para indicar dónde se agrega una columna no asignada; en este caso, entre la columna de título y la última columna de nombre.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#19](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs#19)]
     [!code-vb[Trin_VstcoreHostControlsExcel#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb#19)]  
  
## <a name="compile-the-code"></a>Compilar el código  
 En este ejemplo de código se supone que dispone de un elemento <xref:Microsoft.Office.Tools.Excel.ListObject> existente denominado `list1` en la hoja de cálculo en la que aparece este código.  
  
## <a name="see-also"></a>Vea también  
 [Extender documentos de Word y libros de Excel en complementos VSTO en tiempo de ejecución](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Controles en documentos de Office](../vsto/controls-on-office-documents.md)   
 [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Cómo: Rellenar los controles ListObject con datos](../vsto/how-to-fill-listobject-controls-with-data.md)   
 [Automatizar Excel usando objetos extendidos](../vsto/automating-excel-by-using-extended-objects.md)   
 [ListObject (control)](../vsto/listobject-control.md)  
