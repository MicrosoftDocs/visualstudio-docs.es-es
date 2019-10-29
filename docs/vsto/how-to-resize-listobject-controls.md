---
title: 'Cómo: cambiar el tamaño de los controles ListObject'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], resizing
- ListObject control, resizing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: fdebceb7ed6357542877bf13522425f7c013da73
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985752"
---
# <a name="how-to-resize-listobject-controls"></a>Cómo: cambiar el tamaño de los controles ListObject
  Aunque se puede establecer el tamaño de un control <xref:Microsoft.Office.Tools.Excel.ListObject> al agregarlo a un libro de Microsoft Office Excel, podrían ser necesarios cambios posteriores. Por ejemplo, conviene cambiar una lista de columnas de dos a tres columnas.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 En proyectos de nivel de documento, el tamaño de los controles <xref:Microsoft.Office.Tools.Excel.ListObject> se puede cambiar en tiempo de diseño o en tiempo de ejecución. Puede cambiar el tamaño de los controles de <xref:Microsoft.Office.Tools.Excel.ListObject> en tiempo de ejecución en un proyecto de complemento de VSTO.

 En este tema se describen las tareas siguientes:

- [Cambiar el tamaño de controles ListObject en tiempo de diseño](#designtime)

- [Cambiar el tamaño de los controles ListObject en tiempo de ejecución en un proyecto de nivel de documento](#runtimedoclevel)

- [Cambiar el tamaño de los controles ListObject en tiempo de ejecución en un proyecto de complemento de VSTO](#runtimeaddin)

  Para obtener más información sobre los controles de <xref:Microsoft.Office.Tools.Excel.ListObject>, vea [ListObject (control](../vsto/listobject-control.md)).

## <a name="designtime"></a>Cambiar el tamaño de un control ListObject en tiempo de diseño
 Para cambiar el tamaño de una lista, puede hacer clic y arrastrar uno de los controladores de tamaño, o puede volver a definir su tamaño en el cuadro de diálogo **Cambiar el tamaño de la lista** .

### <a name="to-resize-a-list-by-using-the-resize-list-dialog-box"></a>Para cambiar el tamaño de una lista mediante el cuadro de diálogo Cambiar el tamaño de la lista

1. Haga clic en cualquier lugar de la tabla <xref:Microsoft.Office.Tools.Excel.ListObject>. Aparece la pestaña **herramientas de tabla** > **diseño** en la cinta de opciones.

2. En la sección Propiedades, haga clic en **cambiar el tamaño**de la tabla.

    ![VSTO_ResizeTable](../vsto/media/vsto-resizetable.png)

3. Seleccione el nuevo rango de datos de la tabla.

4. Haga clic en **Aceptar**.

## <a name="runtimedoclevel"></a>Cambiar el tamaño de un control ListObject en tiempo de ejecución en un proyecto de nivel de documento
 Puede cambiar el tamaño de un control <xref:Microsoft.Office.Tools.Excel.ListObject> en tiempo de ejecución usando el método <xref:Microsoft.Office.Tools.Excel.ListObject.Resize%2A> . No puede usar este método para mover el control <xref:Microsoft.Office.Tools.Excel.ListObject> a una nueva ubicación en la hoja de cálculo. Los encabezados deben permanecer en la misma fila y el cambio de tamaño del control <xref:Microsoft.Office.Tools.Excel.ListObject> debe superponerse sobre el objeto de lista original. El control <xref:Microsoft.Office.Tools.Excel.ListObject> con el tamaño cambiado debe contener una fila de encabezado y al menos una fila de datos.

### <a name="to-resize-a-list-object-programmatically"></a>Para cambiar el tamaño de un objeto de lista mediante programación

1. Cree un control <xref:Microsoft.Office.Tools.Excel.ListObject> que abarque de la celda **A1** a la **B3** en `Sheet1`.

     [!code-csharp[Trin_VstcoreHostControlsExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#6)]
     [!code-vb[Trin_VstcoreHostControlsExcel#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#6)]

2. Cambie el tamaño de la lista para incluir las celdas de la **A1** a la **C5**.

     [!code-csharp[Trin_VstcoreHostControlsExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#7)]
     [!code-vb[Trin_VstcoreHostControlsExcel#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#7)]

## <a name="runtimeaddin"></a>Cambiar el tamaño de un ListObject en tiempo de ejecución en un proyecto de complemento de VSTO
 Se puede cambiar el tamaño de un control <xref:Microsoft.Office.Tools.Excel.ListObject> en tiempo de ejecución en cualquier hoja de cálculo abierta. Para obtener más información sobre cómo agregar un control de <xref:Microsoft.Office.Tools.Excel.ListObject> a una hoja de cálculo mediante un complemento de VSTO, consulte [Cómo: agregar controles ListObject a hojas](../vsto/how-to-add-listobject-controls-to-worksheets.md)de cálculo.

### <a name="to-resize-a-list-object-programmatically"></a>Para cambiar el tamaño de un objeto de lista mediante programación

1. Cree un control <xref:Microsoft.Office.Tools.Excel.ListObject> que abarque de la celda **A1** a la **B3** en `Sheet1`.

     [!code-csharp[Trin_Excel_Dynamic_Controls#12](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#12)]
     [!code-vb[Trin_Excel_Dynamic_Controls#12](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#12)]

2. Cambie el tamaño de la lista para incluir las celdas de la **A1** a la **C5**.

     [!code-csharp[Trin_Excel_Dynamic_Controls#13](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#13)]
     [!code-vb[Trin_Excel_Dynamic_Controls#13](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#13)]

## <a name="see-also"></a>Vea también
- [Ampliar documentos de Word y libros de Excel en complementos de VSTO en tiempo de ejecución](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Controles en documentos de Office](../vsto/controls-on-office-documents.md)
- [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Información general sobre elementos y controles host](../vsto/host-items-and-host-controls-overview.md)
- [Automatizar Excel usando objetos extendidos](../vsto/automating-excel-by-using-extended-objects.md)
- [ListObject (control)](../vsto/listobject-control.md)
- [Cómo: agregar controles ListObject a hojas de cálculo](../vsto/how-to-add-listobject-controls-to-worksheets.md)
- [Cómo: cambiar el tamaño de los controles Bookmark](../vsto/how-to-resize-bookmark-controls.md)
- [Cómo: cambiar el tamaño de los controles NamedRange](../vsto/how-to-resize-namedrange-controls.md)
