---
title: Usar controles de formularios Windows Forms en hojas de cálculo de Excel
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
ms.openlocfilehash: fd367087f48ababb390ddd87e289ec22258b4921
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/05/2018
ms.locfileid: "34767928"
---
# <a name="use-windows-forms-controls-on-excel-worksheets"></a>Usar controles de formularios Windows Forms en hojas de cálculo de Excel
  Puede agregar controles de formularios Windows Forms a los libros de Microsoft Office Excel de la misma manera que se agregan controles a formularios Windows Forms. Para obtener información general sobre cómo trabajar con controles en documentos, consulte [controles de Windows Forms en información general acerca de documentos de Office](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="control-considerations-for-excel"></a>Consideraciones sobre controles para Excel  
 Hay algunas consideraciones que son específicas de Excel.  
  
### <a name="match-control-size-to-cell-size"></a>Ajustar el tamaño del control al tamaño de la celda  
 Puede establecer el control para cambiar de tamaño automáticamente cuando se cambia el tamaño de la celda principal. Para obtener más información, consulte [Cómo: cambiar el tamaño de controles dentro de las celdas de la hoja de cálculo](../vsto/how-to-resize-controls-within-worksheet-cells.md).  
  
### <a name="add-components-that-are-shared-by-all-worksheets"></a>Agregar componentes compartidos por todas las hojas de cálculo  
 Puede agregar componentes que desee compartir entre todas las hojas de cálculo, como un <xref:System.Data.DataSet>, al diseñador del libro en lugar de a las hojas de cálculo. El componente aparecerá en la bandeja de componentes.  
  
### <a name="formula-for-embedding-controls"></a>Fórmula para incrustar controles  
 Cuando seleccione un control en Excel, verá **=EMBED("WinForms.Control.Host","")** en la **Barra de fórmulas**. Este texto es necesario y no se debe eliminar.  
  
## <a name="see-also"></a>Vea también  
 [Cómo: cambiar el tamaño de controles dentro de las celdas de la hoja de cálculo](../vsto/how-to-resize-controls-within-worksheet-cells.md)   
 [Cómo: ocultar controles en hojas de cálculo al imprimir](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)   
 [Tutorial: Cambiar el formato de hoja de cálculo utilizando controles CheckBox](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)   
 [Tutorial: Mostrar texto en un cuadro de texto en una hoja de cálculo utilizando un botón](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)   
 [Tutorial: Actualizar un gráfico en una hoja de cálculo utilizando botones de radio](../vsto/walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons.md)  
  
  