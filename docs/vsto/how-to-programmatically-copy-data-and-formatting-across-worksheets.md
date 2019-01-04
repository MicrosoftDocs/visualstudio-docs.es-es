---
title: Procedimiento Copiar datos y formato entre hojas de cálculo mediante programación
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, copying data
- formatting [Office development in Visual Studio]
- data [Office development in Visual Studio], copying across worksheets
- copying data, Office development in Visual Studio
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9995b347fdfcb60acf72c79b0e1bddc20bab717b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53924870"
---
# <a name="how-to-programmatically-copy-data-and-formatting-across-worksheets"></a>Procedimiento Copiar datos y formato entre hojas de cálculo mediante programación
  Puede copiar datos desde un rango de una hoja a todas las hojas en un libro mediante el <xref:Microsoft.Office.Interop.Excel.Worksheets.FillAcrossSheets%2A> método. Especificar un intervalo, y si desea copiar los datos, formato o ambos.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="example"></a>Ejemplo  
 [!code-csharp[Trin_VstcoreExcelAutomation#44](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#44)]
 [!code-vb[Trin_VstcoreExcelAutomation#44](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#44)]  
  
## <a name="compile-the-code"></a>Compilar el código  
 En este ejemplo requiere un rango denominado `rangeData` en una hoja de cálculo.  
  
## <a name="see-also"></a>Vea también  
 [Trabajar con hojas de cálculo](../vsto/working-with-worksheets.md)   
 [Cómo: Agregar nuevas hojas de cálculo a libros mediante programación](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)   
 [Cómo: Cambiar el formato en filas de la hoja de cálculo que contienen celdas seleccionadas mediante programación](../vsto/how-to-programmatically-change-formatting-in-worksheet-rows-containing-selected-cells.md)   
 [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)  
