---
title: 'Cómo: ordenar los datos en hojas de cálculo mediante programación | Documentos de Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data sorting, worksheets
- data [Office development in Visual Studio], sorting in worksheets
- worksheets, sorting data
- sorting data, in worksheets
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4d53baac81bc3a2e583743a61635560b1486a76e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-sort-data-in-worksheets"></a>Cómo: Ordenar datos en hojas de cálculo mediante programación
  Puede ordenar los datos contenidos en rangos de hojas de cálculo y listas en tiempo de ejecución. El siguiente código ordena un rango con varias columnas denominado `Fruits` en función de los datos de la primera columna y, a continuación, en función de los datos de la segunda columna.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="sorting-data-in-a-document-level-customization"></a>Ordenar datos en una personalización de nivel de documento  
  
#### <a name="to-sort-data-in-a-namedrange-control"></a>Para ordenar datos en un control NamedRange  
  
1.  Llame al método <xref:Microsoft.Office.Tools.Excel.NamedRange.Sort%2A> del control <xref:Microsoft.Office.Tools.Excel.NamedRange>. El siguiente ejemplo requiere un control <xref:Microsoft.Office.Tools.Excel.NamedRange> denominado `Fruits` en una hoja de cálculo. Este código se debe colocar en una clase Sheet, no en la clase `ThisWorkbook` .  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#78](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#78)]
     [!code-vb[Trin_VstcoreExcelAutomation#78](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#78)]  
  
 Coloque el siguiente código en Sheet1.vb o Sheet1.cs para ordenar los datos de un control <xref:Microsoft.Office.Tools.Excel.ListObject>. El código supone que tiene un control <xref:Microsoft.Office.Tools.Excel.ListObject> denominado `fruitList` en una hoja de cálculo denominada `Sheet1`.  
  
#### <a name="to-sort-data-in-a-listobject-control"></a>Para ordenar los datos de un control ListObject  
  
1.  Llame al método <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> de la propiedad <xref:Microsoft.Office.Tools.Excel.ListObject.Range%2A> de del control host <xref:Microsoft.Office.Tools.Excel.ListObject>.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#79](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#79)]
     [!code-vb[Trin_VstcoreExcelAutomation#79](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#79)]  
  
## <a name="sorting-data-in-a-vsto-add-in"></a>Ordenar los datos de un complemento de VSTO  
  
#### <a name="to-sort-data-in-a-native-range"></a>Para ordenar los datos en un rango nativo  
  
1.  Llame al método <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> del control <xref:Microsoft.Office.Interop.Excel.Range> nativo de Excel. El siguiente ejemplo requiere un control nativo de Excel denominado `Fruits` en una hoja de cálculo.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#23](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#23)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#23](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#23)]  
  
#### <a name="to-sort-data-in-a-listobject-control"></a>Para ordenar los datos de un control ListObject  
  
1.  Llame al método <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> de la propiedad <xref:Microsoft.Office.Tools.Excel.ListObject.Range%2A> del control <xref:Microsoft.Office.Interop.Excel.ListObject> nativo de Excel. El siguiente ejemplo supone que tiene un control <xref:Microsoft.Office.Interop.Excel.ListObject> nativo de Excel denominado `fruitList` en la hoja de cálculo activa.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#24](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#24)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#24](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#24)]  
  
## <a name="see-also"></a>Vea también  
 [Trabajar con hojas de cálculo](../vsto/working-with-worksheets.md)   
 [Cómo: rellenar rangos automáticamente mediante programación con cambian los datos de forma incremental](../vsto/how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data.md)   
 [Cómo: hacer referencia mediante programación a los rangos de hoja de cálculo en el código](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [Cómo: aplicar estilos a rangos de libros mediante programación](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [NamedRange (Control)](../vsto/namedrange-control.md)   
 [ListObject (Control)](../vsto/listobject-control.md)   
 [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  