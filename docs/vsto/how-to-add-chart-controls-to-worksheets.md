---
title: 'Cómo: Agregar controles gráficos a hojas de cálculo'
description: Obtenga información sobre cómo agregar controles Chart a una hoja de Microsoft Office excel en tiempo de diseño y en tiempo de ejecución en personalizaciones de nivel de documento.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Chart control [Office development in Visual Studio], adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 88ebe38a881e148f10149189a2d27ac81bd0ddc2
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827037"
---
# <a name="how-to-add-chart-controls-to-worksheets"></a>Cómo: Agregar controles gráficos a hojas de cálculo
  Puede agregar controles a una hoja de Microsoft Office excel en tiempo de diseño y en tiempo de ejecución en <xref:Microsoft.Office.Tools.Excel.Chart> personalizaciones de nivel de documento. También puede agregar controles <xref:Microsoft.Office.Tools.Excel.Chart> en tiempo de ejecución en complementos de VSTO.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 En este tema se describen las tareas siguientes:

- [Agregar controles gráficos en tiempo de diseño](#designtime)

- [Agregar controles Chart en tiempo de ejecución en un proyecto de nivel de documento](#runtimedoclevel)

- [Agregar controles Chart en tiempo de ejecución en un proyecto de complemento de VSTO](#runtimeaddin)

  Para obtener más información sobre <xref:Microsoft.Office.Tools.Excel.Chart> los controles, vea [Control Gráfico](../vsto/chart-control.md).

## <a name="add-chart-controls-at-design-time"></a><a name="designtime"></a> Agregar controles gráficos en tiempo de diseño
 Puede agregar el control <xref:Microsoft.Office.Tools.Excel.Chart> a la hoja de cálculo de la misma manera que agregaría un gráfico desde la aplicación.

> [!NOTE]
> El <xref:Microsoft.Office.Tools.Excel.Chart> control no está disponible en el cuadro de herramientas **ni** en la ventana **Orígenes de** datos.

### <a name="to-add-a-chart-host-control-to-a-worksheet-in-excel"></a>Para agregar un control host Chart a una hoja de cálculo de Excel

1. En la **pestaña Insertar** , en el grupo **Gráficos** , haga clic en Columna **,** haga clic en una categoría de gráficos y, a continuación, haga clic en el tipo de gráfico que desee.

2. En el cuadro **de diálogo Insertar** gráfico , haga clic en **Aceptar.**

3. En la **pestaña Diseño** , en el grupo **Datos** , haga clic en **Seleccionar datos**.

4. En el cuadro **de diálogo Seleccionar origen** de datos , haga clic en el cuadro **Intervalo** de datos **del** gráfico y desactive cualquier selección predeterminada.

5. En la **hoja Datos del gráfico,** seleccione el intervalo de celdas que contiene los datos del gráfico (celdas **A5** a **D8).**

6. En el cuadro **de diálogo Seleccionar origen** de datos , haga clic en **Aceptar.**

## <a name="add-chart-controls-at-run-time-in-a-document-level-project"></a><a name="runtimedoclevel"></a> Agregar controles de gráfico en tiempo de ejecución en un proyecto de nivel de documento
 Puede agregar el control <xref:Microsoft.Office.Tools.Excel.Chart> dinámicamente en tiempo de ejecución. Los gráficos creados dinámicamente no se conservan en el documento como controles host cuando se cierra. Para obtener más información, vea [Agregar controles a documentos de Office en tiempo de ejecución.](../vsto/adding-controls-to-office-documents-at-run-time.md)

#### <a name="to-add-a-chart-control-to-a-worksheet-programmatically"></a>Para agregar un control Chart a una hoja de cálculo mediante programación

1. En el controlador de eventos <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> de `Sheet1`, inserte el siguiente código para agregar el control <xref:Microsoft.Office.Tools.Excel.Chart>.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb" id="Snippet1":::

## <a name="add-chart-controls-at-run-time-in-a-vsto-add-in-project"></a><a name="runtimeaddin"></a> Agregar controles de gráfico en tiempo de ejecución en un proyecto de complemento de VSTO
 Puede agregar un control <xref:Microsoft.Office.Tools.Excel.Chart> mediante programación a cualquier hoja de cálculo abierta de un proyecto de complemento de VSTO. Para obtener más información, vea Extender documentos de Word y libros de Excel en [complementos de VSTO en tiempo de ejecución.](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)

 Los controles Chart creados de forma dinámica no se conservan en la hoja de cálculo como controles host cuando se cierra la hoja de cálculo. Para obtener más información, [vea Agregar controles a documentos de Office en tiempo de ejecución.](../vsto/adding-controls-to-office-documents-at-run-time.md)

#### <a name="to-add-a-chart-control-to-a-worksheet-programmatically"></a>Para agregar un control Chart a una hoja de cálculo mediante programación

1. El siguiente código genera un elemento host de hoja de cálculo que se basa en la hoja de cálculo abierta; luego, agrega un control <xref:Microsoft.Office.Tools.Excel.Chart>.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs" id="Snippet9":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb" id="Snippet9":::

## <a name="compile-the-code"></a>Compilar el código
 Este ejemplo tiene los siguientes requisitos:

- Datos que se deben representar gráficamente, almacenados en el rango de celdas A5 a D8 en la hoja de cálculo.

## <a name="see-also"></a>Consulte también
- [Extensión de documentos de Word y libros de Excel en complementos de VSTO en tiempo de ejecución](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Controles en documentos de Office](../vsto/controls-on-office-documents.md)
- [Control Gráfico](../vsto/chart-control.md)
- [Automatización de Excel mediante objetos extendidos](../vsto/automating-excel-by-using-extended-objects.md)
- [Introducción a los elementos host y los controles host](../vsto/host-items-and-host-controls-overview.md)
- [Enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Limitaciones mediante programación de elementos host y controles host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
