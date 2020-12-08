---
title: 'Cómo: agregar controles Chart a hojas de cálculo'
description: Obtenga información sobre cómo puede Agregar controles Chart a un Microsoft Office hoja de cálculo de Excel en tiempo de diseño y en tiempo de ejecución en personalizaciones de nivel de documento.
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7e48b8cfbcf4ee1c7340aef4cd59e09698f89412
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/08/2020
ms.locfileid: "96845471"
---
# <a name="how-to-add-chart-controls-to-worksheets"></a>Cómo: agregar controles Chart a hojas de cálculo
  Puede agregar <xref:Microsoft.Office.Tools.Excel.Chart> controles a una hoja de cálculo de Excel Microsoft Office en tiempo de diseño y en tiempo de ejecución en personalizaciones de nivel de documento. También puede agregar <xref:Microsoft.Office.Tools.Excel.Chart> controles en tiempo de ejecución en complementos de VSTO.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 En este tema se describen las tareas siguientes:

- [Agregar controles Chart en tiempo de diseño](#designtime)

- [Agregar controles Chart en tiempo de ejecución en un proyecto de nivel de documento](#runtimedoclevel)

- [Agregar controles Chart en tiempo de ejecución en un proyecto de complemento de VSTO](#runtimeaddin)

  Para obtener más información sobre <xref:Microsoft.Office.Tools.Excel.Chart> los controles, vea [Chart control](../vsto/chart-control.md).

## <a name="add-chart-controls-at-design-time"></a><a name="designtime"></a> Agregar controles Chart en tiempo de diseño
 Puede agregar el control <xref:Microsoft.Office.Tools.Excel.Chart> a la hoja de cálculo de la misma manera que agregaría un gráfico desde la aplicación.

> [!NOTE]
> El <xref:Microsoft.Office.Tools.Excel.Chart> control no está disponible en el **cuadro de herramientas** o en la ventana **orígenes de datos** .

### <a name="to-add-a-chart-host-control-to-a-worksheet-in-excel"></a>Para agregar un control host Chart a una hoja de cálculo de Excel

1. En la pestaña **Insertar** , en el grupo **gráficos** , haga clic en **columna**, haga clic en una categoría de gráficos y, a continuación, haga clic en el tipo de gráfico que desee.

2. En el cuadro de diálogo **Insertar gráfico** , haga clic en **Aceptar**.

3. En la pestaña **diseño** , en el grupo **datos** , haga clic en **seleccionar datos**.

4. En el cuadro de diálogo **Seleccionar origen de datos** , haga clic en el cuadro **rango de datos** del **gráfico** y borre cualquier selección predeterminada.

5. En la hoja **datos de del gráfico** , seleccione el rango de celdas que contiene los datos del gráfico (celdas **a5** a **D8**).

6. En el cuadro de diálogo **Seleccionar origen de datos** , haga clic en **Aceptar**.

## <a name="add-chart-controls-at-run-time-in-a-document-level-project"></a><a name="runtimedoclevel"></a> Agregar controles Chart en tiempo de ejecución en un proyecto de nivel de documento
 Puede agregar el control <xref:Microsoft.Office.Tools.Excel.Chart> dinámicamente en tiempo de ejecución. Los gráficos creados dinámicamente no se conservan en el documento como controles host cuando se cierra. Para obtener más información, vea [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md).

#### <a name="to-add-a-chart-control-to-a-worksheet-programmatically"></a>Para agregar un control Chart a una hoja de cálculo mediante programación

1. En el controlador de eventos <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> de `Sheet1`, inserte el siguiente código para agregar el control <xref:Microsoft.Office.Tools.Excel.Chart>.

     [!code-csharp[Trin_VstcoreHostControlsExcel#1](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#1)]
     [!code-vb[Trin_VstcoreHostControlsExcel#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#1)]

## <a name="add-chart-controls-at-run-time-in-a-vsto-add-in-project"></a><a name="runtimeaddin"></a> Agregar controles Chart en tiempo de ejecución en un proyecto de complemento de VSTO
 Puede agregar un control <xref:Microsoft.Office.Tools.Excel.Chart> mediante programación a cualquier hoja de cálculo abierta de un proyecto de complemento de VSTO. Para obtener más información, vea [ampliar documentos de Word y libros de Excel en complementos de VSTO en tiempo de ejecución](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

 Los controles Chart creados de forma dinámica no se conservan en la hoja de cálculo como controles host cuando se cierra la hoja de cálculo. Para obtener más información, vea [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md).

#### <a name="to-add-a-chart-control-to-a-worksheet-programmatically"></a>Para agregar un control Chart a una hoja de cálculo mediante programación

1. El siguiente código genera un elemento host de hoja de cálculo que se basa en la hoja de cálculo abierta; luego, agrega un control <xref:Microsoft.Office.Tools.Excel.Chart>.

     [!code-csharp[Trin_Excel_Dynamic_Controls#9](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#9)]
     [!code-vb[Trin_Excel_Dynamic_Controls#9](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#9)]

## <a name="compile-the-code"></a>Compilar el código
 Este ejemplo tiene los siguientes requisitos:

- Datos que se deben representar gráficamente, almacenados en el rango de celdas A5 a D8 en la hoja de cálculo.

## <a name="see-also"></a>Vea también
- [Ampliar documentos de Word y libros de Excel en complementos de VSTO en tiempo de ejecución](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Controles en documentos de Office](../vsto/controls-on-office-documents.md)
- [Chart (control)](../vsto/chart-control.md)
- [Automatizar Excel usando objetos extendidos](../vsto/automating-excel-by-using-extended-objects.md)
- [Información general sobre elementos y controles host](../vsto/host-items-and-host-controls-overview.md)
- [Enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Limitaciones de programación de elementos y controles host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
