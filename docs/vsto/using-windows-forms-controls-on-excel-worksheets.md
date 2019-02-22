---
title: Utilizar controles de Windows Forms en hojas de cálculo de Excel
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
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56599511"
---
# <a name="use-windows-forms-controls-on-excel-worksheets"></a>Utilizar controles de Windows Forms en hojas de cálculo de Excel
  Puede agregar controles de formularios Windows Forms a los libros de Microsoft Office Excel en la misma manera que se agregan controles a Windows Forms. Para obtener información general sobre cómo trabajar con controles en documentos, consulte [Windows Forms a los controles de información general sobre documentos de Office](../vsto/windows-forms-controls-on-office-documents-overview.md).

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="control-considerations-for-excel"></a>Consideraciones sobre controles para Excel
 Hay algunas consideraciones que son específicas de Excel.

### <a name="match-control-size-to-cell-size"></a>Ajustar el tamaño del control al tamaño de celda
 Puede establecer el control para cambiar de tamaño automáticamente cuando se cambia el tamaño de la celda principal. Para obtener más información, vea [Cómo: Cambiar el tamaño de los controles dentro de las celdas de la hoja de cálculo](../vsto/how-to-resize-controls-within-worksheet-cells.md).

### <a name="add-components-that-are-shared-by-all-worksheets"></a>Agregar componentes compartidos por todas las hojas de cálculo
 Puede agregar componentes que desee compartir entre todas las hojas de cálculo, como un <xref:System.Data.DataSet>, al diseñador del libro en lugar de a las hojas de cálculo. El componente aparecerá en la bandeja de componentes.

### <a name="formula-for-embedding-controls"></a>Fórmula para incrustar controles
 Cuando seleccione un control en Excel, verá **=EMBED("WinForms.Control.Host","")** en la **Barra de fórmulas**. Este texto es necesario y no se debe eliminar.

## <a name="see-also"></a>Vea también
- [Cómo: Cambiar el tamaño de los controles dentro de las celdas de la hoja de cálculo](../vsto/how-to-resize-controls-within-worksheet-cells.md)
- [Cómo: Ocultar controles en hojas de cálculo al imprimir](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)
- [Tutorial: Cambiar el formato de hoja de cálculo utilizando controles CheckBox](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)
- [Tutorial: Mostrar texto en un cuadro de texto en una hoja de cálculo utilizando un botón](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)
- [Tutorial: Actualizar un gráfico en una hoja de cálculo utilizando botones de radio](../vsto/walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons.md)
