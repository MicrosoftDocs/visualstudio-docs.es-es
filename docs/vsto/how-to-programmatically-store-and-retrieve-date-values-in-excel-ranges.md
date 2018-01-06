---
title: "Cómo: almacenar mediante programación y recuperar valores de fecha en rangos de Excel | Documentos de Microsoft"
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
- Excel [Office development in Visual Studio], retrieving date values from ranges
- ranges, retrieving data values
- dates, retrieving from Excel ranges
- Excel [Office development in Visual Studio], storing date values in ranges
- date values, storing in Excel ranges
- dates, storing in Excel ranges
- ranges, storing date values
- date values
ms.assetid: e1cdd262-0356-4499-8bc5-e730f74235a2
caps.latest.revision: "40"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 8783a36ac4b15aead5ddb62badd9b56a3c1fa525
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-store-and-retrieve-date-values-in-excel-ranges"></a>Cómo: Almacenar y recuperar valores de fecha en rangos de Excel mediante programación
  Puede almacenar y recuperar valores en un <xref:Microsoft.Office.Tools.Excel.NamedRange> control o un objeto de rango de Excel nativo.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Si almacena un valor de fecha que se encuentra en o después de 1/1/1900 en un intervalo con herramientas de desarrollo de Office en Visual Studio, se almacena en formato de automatización OLE (OA). Debe utilizar el <xref:System.DateTime.FromOADate%2A> método para recuperar el valor de fechas de automatización OLE (OA). Si la fecha es anterior a 1/1/1900, se almacena como una cadena.  
  
> [!NOTE]  
>  Las fechas de Excel se diferencian de las fechas de automatización OLE para los dos primeros meses de 1900. Hay también diferencias si el **sistema de fechas de 1904** opción está activada. Los ejemplos de código siguientes no tratan estas diferencias.  
  
## <a name="using-a-namedrange-control"></a>Uso de un Control NamedRange  
  
-   En este ejemplo es para las personalizaciones de nivel de documento. El siguiente código se debe colocar en una clase sheet, no en la `ThisWorkbook` clase.  
  
#### <a name="to-store-a-date-value-in-a-named-range"></a>Para almacenar un valor de fecha en un rango con nombre  
  
1.  Crear un <xref:Microsoft.Office.Tools.Excel.NamedRange> control en la celda **A1**.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#50](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#50)]
     [!code-vb[Trin_VstcoreExcelAutomation#50](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#50)]  
  
2.  Establecer la fecha de hoy como el valor de `NamedRange1`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#51](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#51)]
     [!code-vb[Trin_VstcoreExcelAutomation#51](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#51)]  
  
#### <a name="to-retrieve-a-date-value-from-a-named-range"></a>Para recuperar un valor de fecha de un rango con nombre  
  
1.  Recuperar el valor de fecha de `NamedRange1`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#52](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#52)]
     [!code-vb[Trin_VstcoreExcelAutomation#52](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#52)]  
  
## <a name="using-native-excel-ranges"></a>Uso de rangos de Excel nativo  
  
#### <a name="to-store-a-date-value-in-a-native-excel-range-object"></a>Para almacenar un valor de fecha en un objeto de rango de Excel nativo  
  
1.  Crear un <xref:Microsoft.Office.Interop.Excel.Range> que representa la celda **A1**.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#25](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#25)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#25](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#25)]  
  
2.  Establecer la fecha de hoy como el valor de `rng`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#26](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#26)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#26](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#26)]  
  
#### <a name="to-retrieve-a-date-value-from-a-native-excel-range-object"></a>Para recuperar un valor de fecha de un objeto de rango de Excel nativo  
  
1.  Recuperar el valor de fecha de `rng`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#27](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#27)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#27](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#27)]  
  
## <a name="see-also"></a>Vea también  
 [Trabajar con rangos](../vsto/working-with-ranges.md)   
 [Información general sobre el modelo de objetos de Excel](../vsto/excel-object-model-overview.md)   
 [NamedRange (Control)](../vsto/namedrange-control.md)   
 [Cómo: hacer referencia mediante programación a los rangos de hoja de cálculo en el código](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [Cómo: agregar controles NamedRange a hojas de cálculo](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  