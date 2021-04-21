---
title: 'Cómo: Cambiar el tamaño de los controles NamedRange'
description: Obtenga información sobre cómo puede usar Visual Studio cambiar el tamaño de los controles NamedRange en un libro de Microsoft Excel mediante programación.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], resizing
- NamedRange control, resizing
- ranges, resizing in Excel
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 3b70b34de222c35903a4f08b95d9efe8d8f896d9
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826465"
---
# <a name="how-to-resize-namedrange-controls"></a>Cómo: Cambiar el tamaño de los controles NamedRange
  Aunque se puede establecer el tamaño de un control <xref:Microsoft.Office.Tools.Excel.NamedRange> al agregarlo a un documento de Microsoft Office Excel, podrían ser necesarios cambios posteriores.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 En proyectos de nivel de documento, el tamaño de un rango con nombre se puede cambiar en tiempo de diseño o en tiempo de ejecución También se puede cambiar su tamaño en tiempo de ejecución en los complementos de VSTO de nivel de aplicación.

 En este tema se describen las tareas siguientes:

- [Cambiar el tamaño de los controles NamedRange en tiempo de diseño](#designtime)

- [Cambiar el tamaño de los controles NamedRange en tiempo de ejecución en un proyecto de nivel de documento](#runtimedoclevel)

- [Cambiar el tamaño de los controles NamedRange en tiempo de ejecución en un proyecto de complemento de VSTO](#runtimeaddin)

## <a name="resize-namedrange-controls-at-design-time"></a><a name="designtime"></a> Cambiar el tamaño de los controles NamedRange en tiempo de diseño
 Para cambiar el tamaño de un rango con nombre, es necesario volver a definir el tamaño en el cuadro de diálogo **Definir nombre** .

### <a name="to-resize-a-named-range-by-using-the-define-name-dialog-box"></a>Para cambiar el tamaño de un rango con nombre mediante el cuadro de diálogo Definir nombre

1. Haga clic en un control <xref:Microsoft.Office.Tools.Excel.NamedRange> .

2. Haga clic en **Administrar rangos con nombre** en el menú contextual.

     Se mostrará el cuadro de diálogo **Definir nombre** .

3. Seleccione el rango con nombre cuyo tamaño quiere cambiar.

4. Desactive el cuadro **Se refiere a** .

5. Seleccione las celdas que quiere usar para definir el tamaño del rango con nombre.

6. Haga clic en **OK**.

## <a name="resize-namedrange-controls-at-run-time-in-a-document-level-project"></a><a name="runtimedoclevel"></a> Cambiar el tamaño de los controles NamedRange en tiempo de ejecución en un proyecto de nivel de documento
 Este tamaño se puede cambiar mediante programación, con la propiedad <xref:Microsoft.Office.Tools.Excel.NamedRange.RefersTo%2A> .

> [!NOTE]
> En la ventana **Propiedades** , la propiedad <xref:Microsoft.Office.Tools.Excel.NamedRange.RefersTo%2A> se marca como de solo lectura.

### <a name="to-resize-a-named-range-programmatically"></a>Para cambiar el tamaño de un rango con nombre mediante programación

1. Cree un control <xref:Microsoft.Office.Tools.Excel.NamedRange> en la celda **A1** de `Sheet1`.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet4":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb" id="Snippet4":::

2. Cambie el tamaño del rango con nombre para incluir la celda **B1**.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet5":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb" id="Snippet5":::

## <a name="resize-namedrange-controls-at-run-time-in-a-vsto-add-in-project"></a><a name="runtimeaddin"></a> Cambiar el tamaño de los controles NamedRange en tiempo de ejecución en un proyecto de complemento de VSTO
 Se puede cambiar el tamaño de un control <xref:Microsoft.Office.Tools.Excel.NamedRange> en tiempo de ejecución en cualquier hoja de cálculo abierta. Para obtener más información sobre cómo agregar un control a una hoja de cálculo mediante un complemento de VSTO, vea Cómo: Agregar controles <xref:Microsoft.Office.Tools.Excel.NamedRange> NamedRange a [hojas de cálculo.](../vsto/how-to-add-namedrange-controls-to-worksheets.md)

### <a name="to-resize-a-named-range-programmatically"></a>Para cambiar el tamaño de un rango con nombre mediante programación

1. Cree un control <xref:Microsoft.Office.Tools.Excel.NamedRange> en la celda **A1** de `Sheet1`.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs" id="Snippet10":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb" id="Snippet10":::

2. Cambie el tamaño del rango con nombre para incluir la celda **B1**.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs" id="Snippet11":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb" id="Snippet11":::

## <a name="see-also"></a>Consulte también
- [Extensión de documentos de Word y libros de Excel en complementos VSTO en tiempo de ejecución](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Controles en documentos de Office](../vsto/controls-on-office-documents.md)
- [Introducción a los elementos host y los controles host](../vsto/host-items-and-host-controls-overview.md)
- [Automatización de Excel mediante objetos extendidos](../vsto/automating-excel-by-using-extended-objects.md)
- [Control NamedRange](../vsto/namedrange-control.md)
- [Cómo: Agregar controles NamedRange a hojas de cálculo](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Cómo: Cambiar el tamaño de los controles Bookmark](../vsto/how-to-resize-bookmark-controls.md)
- [Cómo: Cambiar el tamaño de los controles ListObject](../vsto/how-to-resize-listobject-controls.md)
