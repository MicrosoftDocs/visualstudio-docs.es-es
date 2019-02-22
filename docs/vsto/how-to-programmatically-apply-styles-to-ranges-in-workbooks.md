---
title: Filtrar Aplicar estilos a rangos de libros mediante programación
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, styles
- styles, workbook ranges
- workbooks, styles
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 178d5c22c74386cb70ced170b8643baeedfab55e
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56607972"
---
# <a name="how-to-programmatically-apply-styles-to-ranges-in-workbooks"></a>Filtrar Aplicar estilos a rangos de libros mediante programación
  Puede aplicar estilos con nombre a distintas áreas de los libros. Excel proporciona una serie de estilos predefinidos.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 El cuadro de diálogo **Formato de celdas** muestra todas las opciones que puede usar para dar formato a las celdas; estas opciones también están disponibles en el código. Para mostrar este cuadro de diálogo en Excel, haga clic en **Celdas** en el menú **Formato** .

## <a name="to-apply-a-style-to-a-named-range-in-a-document-level-customization"></a>Para aplicar un estilo a un rango con nombre en una personalización de nivel de documento

1.  Cree un estilo nuevo y establezca sus atributos.

     [!code-csharp[Trin_VstcoreExcelAutomation#53](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#53)]
     [!code-vb[Trin_VstcoreExcelAutomation#53](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#53)]

2.  Cree un control <xref:Microsoft.Office.Tools.Excel.NamedRange>, asígnele texto y aplique el nuevo estilo. Este código se debe colocar en una clase Sheet, no en la clase `ThisWorkbook` .

     [!code-csharp[Trin_VstcoreExcelAutomation#54](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#54)]
     [!code-vb[Trin_VstcoreExcelAutomation#54](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#54)]

## <a name="to-clear-a-style-from-a-named-range-in-a-document-level-customization"></a>Para borrar un estilo de un rango con nombre en una personalización de nivel de documento

1.  Aplique el estilo Normal al rango. Este código se debe colocar en una clase Sheet, no en la clase `ThisWorkbook` .

     [!code-csharp[Trin_VstcoreExcelAutomation#55](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#55)]
     [!code-vb[Trin_VstcoreExcelAutomation#55](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#55)]

## <a name="to-apply-a-style-to-a-named-range-in-a-vsto-add-in"></a>Para aplicar un estilo a un rango con nombre en un complemento de VSTO

1.  Cree un estilo nuevo y establezca sus atributos.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#28](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#28)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#28](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#28)]

2.  Cree un <xref:Microsoft.Office.Interop.Excel.Range>, asígnele texto y aplique el nuevo estilo.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#29](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#29)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#29](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#29)]

## <a name="to-clear-a-style-from-a-named-range-in-a-vsto-add-in"></a>Para borrar un estilo de un rango con nombre en un complemento de VSTO

1.  Aplique el estilo Normal al rango.

     [!code-csharp[Trin_VstcoreExcelAutomation#56](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#56)]
     [!code-vb[Trin_VstcoreExcelAutomation#56](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#56)]

## <a name="see-also"></a>Vea también
- [Trabajar con rangos](../vsto/working-with-ranges.md)
- [NamedRange (control)](../vsto/namedrange-control.md)
- [Acceso global a objetos en los proyectos de Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)
