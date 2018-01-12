---
title: "Cómo: mostrar una cadena en una celda de la hoja de cálculo mediante programación | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- text [Office development in Visual Studio], adding to worksheets
- worksheets, displaying text in cells
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 4a76d2588ec07c461794381a2edd502d367be274
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-display-a-string-in-a-worksheet-cell"></a>Cómo: Mostrar una cadena en la celda de una hoja de cálculo mediante programación
  Este ejemplo muestra cómo mostrar texto en una celda mediante programación. Para mostrar texto en la celda, use un <xref:Microsoft.Office.Tools.Excel.NamedRange> control o un objeto de rango de Excel nativo.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="using-a-namedrange-control"></a>Uso de un Control NamedRange  
 Este ejemplo se utiliza un <xref:Microsoft.Office.Tools.Excel.NamedRange> control denominado `message`. El control debe agregarse a una personalización de nivel de documento en tiempo de diseño. El siguiente código se debe colocar en una clase sheet, no en la `ThisWorkbook` clase.  
  
#### <a name="to-display-text-in-a-namedrange-control"></a>Para mostrar texto en un control NamedRange  
  
1.  Establezca el valor de la <xref:Microsoft.Office.Tools.Excel.NamedRange> el control a **Hello World**.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#68](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#68)]
     [!code-vb[Trin_VstcoreExcelAutomation#68](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#68)]  
  
## <a name="using-a-native-excel-range"></a>Uso de un rango de Excel nativo  
 El código siguiente crea un nuevo rango mediante programación y, a continuación, asigna un valor a él.  
  
#### <a name="to-display-text-in-an-excel-range"></a>Para mostrar texto en un rango de Excel  
  
1.  Recuperar el rango en la celda **A1** en `Sheet1` y establezca el valor en **Hello World**.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#69](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#69)]
     [!code-vb[Trin_VstcoreExcelAutomation#69](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#69)]  
  
## <a name="see-also"></a>Vea también  
 [Tutorial: Recopilar datos con un formulario Windows Forms](../vsto/walkthrough-collecting-data-using-a-windows-form.md)   
 [Solucionar problemas de soluciones de Office](../vsto/troubleshooting-office-solutions.md)   
 [NamedRange (Control)](../vsto/namedrange-control.md)   
 [Acceso global a objetos en los proyectos de Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  