---
title: Procedimiento Mostrar una cadena en una celda de la hoja de cálculo mediante programación
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- text [Office development in Visual Studio], adding to worksheets
- worksheets, displaying text in cells
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 021fe02e501fc5a8921ec8f2a50329653ca45401
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53849773"
---
# <a name="how-to-programmatically-display-a-string-in-a-worksheet-cell"></a>Procedimiento Mostrar una cadena en una celda de la hoja de cálculo mediante programación
  En este ejemplo se muestra cómo mostrar texto en una celda mediante programación. Para mostrar texto en la celda, use un <xref:Microsoft.Office.Tools.Excel.NamedRange> control o un objeto nativo de rango de Excel.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="use-a-namedrange-control"></a>Usar un control NamedRange  
 Este ejemplo se usa un <xref:Microsoft.Office.Tools.Excel.NamedRange> control denominado `message`. El control debe agregarse a una personalización de nivel de documento en tiempo de diseño. El siguiente código debe colocarse en una clase sheet, no en el `ThisWorkbook` clase.  
  
### <a name="to-display-text-in-a-namedrange-control"></a>Para mostrar texto en un control NamedRange  
  
1.  Establezca el valor de la <xref:Microsoft.Office.Tools.Excel.NamedRange> control **Hello World**.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#68](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#68)]
     [!code-vb[Trin_VstcoreExcelAutomation#68](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#68)]  
  
## <a name="use-a-native-excel-range"></a>Usar un rango de Excel nativo  
 El código siguiente crea un nuevo rango mediante programación y, a continuación, le asigna un valor.  
  
### <a name="to-display-text-in-an-excel-range"></a>Para mostrar texto en un rango de Excel  
  
1.  Recuperar el rango en la celda **A1** en `Sheet1` y establezca el valor en **Hello World**.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#69](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#69)]
     [!code-vb[Trin_VstcoreExcelAutomation#69](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#69)]  
  
## <a name="see-also"></a>Vea también  
 [Tutorial: Recopilación de datos mediante un formulario de Windows](../vsto/walkthrough-collecting-data-using-a-windows-form.md)   
 [Solucionar problemas de soluciones de Office](../vsto/troubleshooting-office-solutions.md)   
 [NamedRange (control)](../vsto/namedrange-control.md)   
 [Acceso global a objetos en los proyectos de Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)  
