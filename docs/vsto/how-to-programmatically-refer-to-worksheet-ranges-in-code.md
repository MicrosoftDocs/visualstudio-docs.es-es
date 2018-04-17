---
title: 'Cómo: hacer referencia mediante programación a los rangos de hoja de cálculo en el código | Documentos de Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, referring to
- worksheets, referring to ranges
- referring to worksheet ranges
- Excel [Office development in Visual Studio], referring to worksheet ranges
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 68845904a349a94df6ee09c05ca262434b847bbc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-refer-to-worksheet-ranges-in-code"></a>Cómo: Hacer referencia a rangos de hojas de cálculo en el código mediante programación
  Utilizar un proceso similar para hacer referencia al contenido de un <xref:Microsoft.Office.Tools.Excel.NamedRange> control o un objeto de rango de Excel nativo.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="using-a-namedrange-control"></a>Uso de un Control NamedRange  
 En el ejemplo siguiente se agrega un <xref:Microsoft.Office.Tools.Excel.NamedRange> a una hoja de cálculo y, a continuación, se agrega texto a la celda en el intervalo.  
  
#### <a name="to-refer-to-a-namedrange-control"></a>Para hacer referencia a un control NamedRange  
  
1.  Asigna una cadena a la <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> propiedad de la <xref:Microsoft.Office.Tools.Excel.NamedRange> control. Este código se debe colocar en una clase Sheet, no en la clase `ThisWorkbook` .  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#46](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#46)]
     [!code-vb[Trin_VstcoreExcelAutomation#46](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#46)]  
  
## <a name="using-native-excel-ranges"></a>Uso de rangos de Excel nativo  
 En el ejemplo siguiente se agrega un rango de Excel nativo a una hoja de cálculo y, a continuación, agrega texto a la celda en el intervalo.  
  
#### <a name="to-refer-to-a-native-range-object"></a>Para hacer referencia a un objeto de rango nativo  
  
1.  Asigna una cadena a la <xref:Microsoft.Office.Interop.Excel.Range.Value2%2A> propiedad del intervalo.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#47](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#47)]
     [!code-vb[Trin_VstcoreExcelAutomation#47](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#47)]  
  
## <a name="see-also"></a>Vea también  
 [Trabajar con rangos](../vsto/working-with-ranges.md)   
 [Cómo: revisar la ortografía en hojas de cálculo mediante programación](../vsto/how-to-programmatically-check-spelling-in-worksheets.md)   
 [Cómo: aplicar estilos a rangos de libros mediante programación](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [Cómo: rellenar rangos automáticamente mediante programación con cambian los datos de forma incremental](../vsto/how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data.md)   
 [Cómo: buscar texto en rangos de hoja de cálculo mediante programación](../vsto/how-to-programmatically-search-for-text-in-worksheet-ranges.md)   
 [NamedRange (Control)](../vsto/namedrange-control.md)   
 [Información general sobre elementos y controles Host](../vsto/host-items-and-host-controls-overview.md)   
 [Limitaciones de programación de elementos y controles Host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  