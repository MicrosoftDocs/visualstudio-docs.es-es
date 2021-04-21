---
title: 'Cómo: Aplicar estilos mediante programación a intervalos en libros'
description: Obtenga información sobre cómo puede aplicar estilos con nombre a las regiones de los libros. Excel proporciona una serie de estilos predefinidos.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, styles
- styles, workbook ranges
- workbooks, styles
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b1ce30c9a0e21bd4b8860f7a4d17191c48cd2ad9
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828311"
---
# <a name="how-to-programmatically-apply-styles-to-ranges-in-workbooks"></a>Cómo: Aplicar estilos mediante programación a intervalos en libros
  Puede aplicar estilos con nombre a distintas áreas de los libros. Excel proporciona una serie de estilos predefinidos.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 El cuadro de diálogo **Formato de celdas** muestra todas las opciones que puede usar para dar formato a las celdas; estas opciones también están disponibles en el código. Para mostrar este cuadro de diálogo en Excel, haga clic en **Celdas** en el menú **Formato** .

## <a name="to-apply-a-style-to-a-named-range-in-a-document-level-customization"></a>Para aplicar un estilo a un rango con nombre en una personalización de nivel de documento

1. Cree un estilo nuevo y establezca sus atributos.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet53":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet53":::

2. Cree un control <xref:Microsoft.Office.Tools.Excel.NamedRange>, asígnele texto y aplique el nuevo estilo. Este código se debe colocar en una clase Sheet, no en la clase `ThisWorkbook` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet54":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet54":::

## <a name="to-clear-a-style-from-a-named-range-in-a-document-level-customization"></a>Para borrar un estilo de un rango con nombre en una personalización de nivel de documento

1. Aplique el estilo Normal al rango. Este código se debe colocar en una clase Sheet, no en la clase `ThisWorkbook` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet55":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet55":::

## <a name="to-apply-a-style-to-a-named-range-in-a-vsto-add-in"></a>Para aplicar un estilo a un rango con nombre en un complemento de VSTO

1. Cree un estilo nuevo y establezca sus atributos.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet28":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet28":::

2. Cree un <xref:Microsoft.Office.Interop.Excel.Range>, asígnele texto y aplique el nuevo estilo.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet29":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet29":::

## <a name="to-clear-a-style-from-a-named-range-in-a-vsto-add-in"></a>Para borrar un estilo de un intervalo con nombre en un complemento de VSTO

1. Aplique el estilo Normal al rango.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet56":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet56":::

## <a name="see-also"></a>Consulte también
- [Trabajar con intervalos](../vsto/working-with-ranges.md)
- [Control NamedRange](../vsto/namedrange-control.md)
- [Acceso global a objetos en proyectos de Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Parámetros opcionales en soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)
