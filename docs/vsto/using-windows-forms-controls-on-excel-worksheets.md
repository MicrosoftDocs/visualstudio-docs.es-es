---
title: Usar controles de Windows Forms en hojas de cálculo de Excel
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Windows Forms controls [Office development in Visual Studio], Excel
- Excel [Office development in Visual Studio], Windows Forms controls
- controls [Office development in Visual Studio], Window Forms controls
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 032ee551ff04590ccdb8744c1274b137dec0b756
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "62982321"
---
# <a name="use-windows-forms-controls-on-excel-worksheets"></a>Usar controles de Windows Forms en hojas de cálculo de Excel
  Puede Agregar controles Windows Forms a los libros de Microsoft Office Excel de la misma manera que agrega controles a Windows Forms. Para obtener información general sobre cómo trabajar con controles en documentos, vea [información general sobre los controles de Windows Forms en documentos de Office](../vsto/windows-forms-controls-on-office-documents-overview.md).

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="control-considerations-for-excel"></a>Consideraciones sobre el control para Excel
 Hay algunas consideraciones que son específicas de Excel.

### <a name="match-control-size-to-cell-size"></a>Coincidencia del tamaño del control con el tamaño de la celda
 Puede establecer el control para cambiar de tamaño automáticamente cuando se cambia el tamaño de la celda principal. Para obtener más información, vea [Cómo: cambiar el tamaño de los controles dentro de las celdas de la hoja de cálculo](../vsto/how-to-resize-controls-within-worksheet-cells.md).

### <a name="add-components-that-are-shared-by-all-worksheets"></a>Agregar componentes compartidos por todas las hojas de cálculo
 Puede agregar componentes que desee compartir entre todas las hojas de cálculo, como un <xref:System.Data.DataSet>, al diseñador del libro en lugar de a las hojas de cálculo. El componente aparecerá en la bandeja de componentes.

### <a name="formula-for-embedding-controls"></a>Fórmula para incrustar controles
 Cuando seleccione un control en Excel, verá **=EMBED("WinForms.Control.Host","")** en la **Barra de fórmulas**. Este texto es necesario y no se debe eliminar.

## <a name="see-also"></a>Consulte también
- [Cómo: cambiar el tamaño de los controles dentro de las celdas de la hoja de cálculo](../vsto/how-to-resize-controls-within-worksheet-cells.md)
- [Cómo: ocultar controles en hojas de cálculo al imprimir](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)
- [Tutorial: cambiar el formato de una hoja de cálculo mediante controles CheckBox](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)
- [Tutorial: mostrar texto en un cuadro de texto de una hoja de cálculo mediante un botón](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)
- [Tutorial: actualizar un gráfico en una hoja de cálculo mediante botones de radio](../vsto/walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons.md)
