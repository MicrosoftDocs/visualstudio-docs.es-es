---
title: 'Cómo: Cambiar el tamaño de los controles ListObject'
description: Obtenga información sobre cómo puede usar Visual Studio cambiar el tamaño de los controles ListObject en un libro de Microsoft Excel mediante programación.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], resizing
- ListObject control, resizing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a2fd0b8ce46ba15066ab4cf070807e2457c21e70
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828961"
---
# <a name="how-to-resize-listobject-controls"></a>Cómo: Cambiar el tamaño de los controles ListObject
  Aunque se puede establecer el tamaño de un control <xref:Microsoft.Office.Tools.Excel.ListObject> al agregarlo a un libro de Microsoft Office Excel, podrían ser necesarios cambios posteriores. Por ejemplo, conviene cambiar una lista de columnas de dos a tres columnas.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 En proyectos de nivel de documento, el tamaño de los controles <xref:Microsoft.Office.Tools.Excel.ListObject> se puede cambiar en tiempo de diseño o en tiempo de ejecución. Puede cambiar el tamaño <xref:Microsoft.Office.Tools.Excel.ListObject> de los controles en tiempo de ejecución en un proyecto de complemento de VSTO.

 En este tema se describen las tareas siguientes:

- [Cambiar el tamaño de los controles ListObject en tiempo de diseño](#designtime)

- [Cambiar el tamaño de los controles ListObject en tiempo de ejecución en un proyecto de nivel de documento](#runtimedoclevel)

- [Cambiar el tamaño de los controles ListObject en tiempo de ejecución en un proyecto de complemento de VSTO](#runtimeaddin)

  Para obtener más información sobre <xref:Microsoft.Office.Tools.Excel.ListObject> los controles, vea [Control ListObject](../vsto/listobject-control.md).

## <a name="resize-a-listobject-control-at-design-time"></a><a name="designtime"></a> Cambio de tamaño de un control ListObject en tiempo de diseño
 Para cambiar el tamaño de una lista, puede hacer clic y arrastrar uno de los controladores de tamaño, o puede volver a definir su tamaño en el cuadro de diálogo **Cambiar el tamaño de la lista** .

### <a name="to-resize-a-list-by-using-the-resize-list-dialog-box"></a>Para cambiar el tamaño de una lista mediante el cuadro de diálogo Cambiar el tamaño de la lista

1. Haga clic en cualquier parte de la  <xref:Microsoft.Office.Tools.Excel.ListObject> tabla. Aparece **la pestaña Diseño** de  >  **herramientas** de tabla en la cinta de opciones.

2. En la sección Propiedades, haga clic en **Cambiar el tamaño de la tabla**.

    ![VSTO_ResizeTable](../vsto/media/vsto-resizetable.png)

3. Seleccione el nuevo intervalo de datos de la tabla.

4. Haga clic en **OK**.

## <a name="resize-a-listobject-control-at-run-time-in-a-document-level-project"></a><a name="runtimedoclevel"></a> Cambio de tamaño de un control ListObject en tiempo de ejecución en un proyecto de nivel de documento
 Puede cambiar el tamaño de un control <xref:Microsoft.Office.Tools.Excel.ListObject> en tiempo de ejecución usando el método <xref:Microsoft.Office.Tools.Excel.ListObject.Resize%2A> . No puede usar este método para mover el control <xref:Microsoft.Office.Tools.Excel.ListObject> a una nueva ubicación en la hoja de cálculo. Los encabezados deben permanecer en la misma fila y el cambio de tamaño del control <xref:Microsoft.Office.Tools.Excel.ListObject> debe superponerse sobre el objeto de lista original. El control <xref:Microsoft.Office.Tools.Excel.ListObject> con el tamaño cambiado debe contener una fila de encabezado y al menos una fila de datos.

### <a name="to-resize-a-list-object-programmatically"></a>Para cambiar el tamaño de un objeto de lista mediante programación

1. Cree un control <xref:Microsoft.Office.Tools.Excel.ListObject> que abarque de la celda **A1** a la **B3** en `Sheet1`.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet6":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb" id="Snippet6":::

2. Cambie el tamaño de la lista para incluir las celdas de la **A1** a la **C5**.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet7":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb" id="Snippet7":::

## <a name="resize-a-listobject-at-run-time-in-a-vsto-add-in-project"></a><a name="runtimeaddin"></a> Cambiar el tamaño de un elemento ListObject en tiempo de ejecución en un proyecto de complemento de VSTO
 Se puede cambiar el tamaño de un control <xref:Microsoft.Office.Tools.Excel.ListObject> en tiempo de ejecución en cualquier hoja de cálculo abierta. Para obtener más información sobre cómo agregar un control a una hoja de cálculo mediante un complemento de VSTO, vea Cómo: Agregar controles <xref:Microsoft.Office.Tools.Excel.ListObject> ListObject a [hojas de cálculo.](../vsto/how-to-add-listobject-controls-to-worksheets.md)

### <a name="to-resize-a-list-object-programmatically"></a>Para cambiar el tamaño de un objeto de lista mediante programación

1. Cree un control <xref:Microsoft.Office.Tools.Excel.ListObject> que abarque de la celda **A1** a la **B3** en `Sheet1`.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs" id="Snippet12":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb" id="Snippet12":::

2. Cambie el tamaño de la lista para incluir las celdas de la **A1** a la **C5**.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs" id="Snippet13":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb" id="Snippet13":::

## <a name="see-also"></a>Consulte también
- [Extensión de documentos de Word y libros de Excel en complementos VSTO en tiempo de ejecución](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Controles en documentos de Office](../vsto/controls-on-office-documents.md)
- [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Introducción a los elementos host y los controles host](../vsto/host-items-and-host-controls-overview.md)
- [Automatización de Excel mediante objetos extendidos](../vsto/automating-excel-by-using-extended-objects.md)
- [Control ListObject](../vsto/listobject-control.md)
- [Cómo: Agregar controles ListObject a hojas de cálculo](../vsto/how-to-add-listobject-controls-to-worksheets.md)
- [Cómo: Cambiar el tamaño de los controles Bookmark](../vsto/how-to-resize-bookmark-controls.md)
- [Cómo: Cambiar el tamaño de los controles NamedRange](../vsto/how-to-resize-namedrange-controls.md)
