---
title: 'Cómo: mostrar una cadena en una celda de una hoja de cálculo mediante programación'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- text [Office development in Visual Studio], adding to worksheets
- worksheets, displaying text in cells
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: eb3dbaec2efd95f63428e8494598720953f791e7
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/30/2020
ms.locfileid: "91585228"
---
# <a name="how-to-programmatically-display-a-string-in-a-worksheet-cell"></a>Cómo: mostrar una cadena en una celda de una hoja de cálculo mediante programación
  En este ejemplo se muestra cómo mostrar texto en una celda mediante programación. Para mostrar texto en la celda, use un <xref:Microsoft.Office.Tools.Excel.NamedRange> control o un objeto de intervalo de Excel nativo.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-a-namedrange-control"></a>Usar un control NamedRange
 En este ejemplo se utiliza un <xref:Microsoft.Office.Tools.Excel.NamedRange> control denominado `message` . El control se debe agregar a una personalización de nivel de documento en tiempo de diseño. El código siguiente se debe colocar en una clase Sheet, no en la `ThisWorkbook` clase.

### <a name="to-display-text-in-a-namedrange-control"></a>Para mostrar texto en un control NamedRange

1. Establezca el valor del <xref:Microsoft.Office.Tools.Excel.NamedRange> control en **Hola mundo**.

     [!code-csharp[Trin_VstcoreExcelAutomation#68](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#68)]
     [!code-vb[Trin_VstcoreExcelAutomation#68](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#68)]

## <a name="use-a-native-excel-range"></a>Usar un intervalo de Excel nativo
 En el código siguiente se crea un nuevo intervalo mediante programación y, a continuación, se le asigna un valor.

### <a name="to-display-text-in-an-excel-range"></a>Para mostrar texto en un intervalo de Excel

1. Recupere el intervalo de la celda **a1** en `Sheet1` y establezca el valor en **Hola mundo**.

     [!code-csharp[Trin_VstcoreExcelAutomation#69](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#69)]
     [!code-vb[Trin_VstcoreExcelAutomation#69](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#69)]

## <a name="see-also"></a>Vea también
- [Tutorial: recopilar datos con Windows Forms](../vsto/walkthrough-collecting-data-using-a-windows-form.md)
- [Solucionar problemas de soluciones de Office](../vsto/troubleshooting-office-solutions.md)
- [NamedRange (control)](../vsto/namedrange-control.md)
- [Acceso global a objetos en proyectos de Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)
