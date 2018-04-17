---
title: Utilizar formularios Windows Forms controles en hojas de cálculo de Excel | Documentos de Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Windows Forms controls [Office development in Visual Studio], Excel
- Excel [Office development in Visual Studio], Windows Forms controls
- controls [Office development in Visual Studio], Window Forms controls
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d4c754c0fff7f7a0f5c3bf31293696e3ec57961f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="using-windows-forms-controls-on-excel-worksheets"></a>Usar controles de formularios Windows Forms en hojas de cálculo de Excel
  Puede agregar controles de formularios Windows Forms a los libros de Microsoft Office Excel de la misma manera que se agregan controles a formularios Windows Forms. Para obtener información general sobre cómo trabajar con controles en documentos, consulte [controles de Windows Forms en documentos de Office Overview](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="control-considerations-for-excel"></a>Consideraciones sobre controles para Excel  
 Hay algunas consideraciones que son específicas de Excel.  
  
### <a name="matching-control-size-to-cell-size"></a>Tamaño del Control correspondiente al tamaño de la celda  
 Puede establecer el control para cambiar de tamaño automáticamente cuando se cambia el tamaño de la celda principal. Para obtener más información, consulte [Cómo: cambiar el tamaño de controles en celdas de hoja de cálculo](../vsto/how-to-resize-controls-within-worksheet-cells.md).  
  
### <a name="adding-components-that-are-shared-by-all-worksheets"></a>Agregar componentes compartidos por todas las hojas de cálculo  
 Puede agregar componentes que desee compartir entre todas las hojas de cálculo, como un <xref:System.Data.DataSet>, al diseñador del libro en lugar de a las hojas de cálculo. El componente aparecerá en la bandeja de componentes.  
  
### <a name="formula-for-embedding-controls"></a>Fórmula para incrustar controles  
 Cuando seleccione un control en Excel, verá **=EMBED("WinForms.Control.Host","")** en la **Barra de fórmulas**. Este texto es necesario y no se debe eliminar.  
  
## <a name="see-also"></a>Vea también  
 [Cómo: cambiar el tamaño de controles dentro de las celdas de la hoja de cálculo](../vsto/how-to-resize-controls-within-worksheet-cells.md)   
 [Cómo: ocultar controles en hojas de cálculo al imprimir](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)   
 [Tutorial: Cambiar el formato de hoja de cálculo utilizando controles CheckBox](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)   
 [Tutorial: Mostrar texto en un cuadro de texto en una hoja de cálculo utilizando un botón](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)   
 [Tutorial: Actualización de un gráfico en una hoja de cálculo mediante botones de radio](../vsto/walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons.md)  
  
  