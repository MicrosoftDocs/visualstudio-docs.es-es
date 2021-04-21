---
title: 'Cómo: Buscar texto en intervalos de hojas de cálculo mediante programación'
description: Obtenga información sobre cómo puede usar Visual Studio para buscar texto en los intervalos de hojas de cálculo de Microsoft Excel mediante programación.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, searching
- text [Office development in Visual Studio], searching in worksheets
- text searches, worksheets
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 762cb3fc35b43bfd3ad15aea669adff2d370b632
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827947"
---
# <a name="how-to-programmatically-search-for-text-in-worksheet-ranges"></a>Cómo: Buscar texto en intervalos de hojas de cálculo mediante programación
  El <xref:Microsoft.Office.Interop.Excel.Range.Find%2A> método del objeto permite buscar texto dentro del <xref:Microsoft.Office.Interop.Excel.Range> intervalo. Este texto también puede ser cualquiera de las cadenas de error que pueden aparecer en una celda de hoja de cálculo, como `#NULL!` o `#VALUE!` . Para obtener más información sobre las cadenas de error, vea [Valores de error de celda.](/office/vba/excel/Concepts/Cells-and-Ranges/cell-error-values)

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 En el ejemplo siguiente se busca un intervalo denominado y se modifica la fuente de las celdas `Fruits` que contienen la palabra "apples". Este procedimiento también usa el método , que usa la configuración de búsqueda establecida anteriormente <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> para repetir la búsqueda. Especifique la celda después de la que se va a buscar y el <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> método controla el resto.

> [!NOTE]
> La búsqueda del método se ajusta al principio del intervalo de búsqueda después de que haya <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> alcanzado el final del intervalo. El código debe asegurarse de que la búsqueda no se ajusta en un bucle infinito. El procedimiento de ejemplo muestra una manera de controlar esto mediante la <xref:Microsoft.Office.Interop.Excel.Range.Address%2A> propiedad .

## <a name="to-search-for-text-in-a-worksheet-range"></a>Para buscar texto en un intervalo de hojas de cálculo

1. Declare variables para realizar el seguimiento de todo el intervalo, el primer intervalo encontrado y el intervalo encontrado actual.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet58":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet58":::

2. Busque la primera coincidencia y especifique todos los parámetros excepto la celda después de la que buscar.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet59":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet59":::

3. Siga buscando siempre que haya coincidencias.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet60":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet60":::

4. Compare el primer intervalo encontrado ( `firstFind` ) con **Nothing**. Si `firstFind` no contiene ningún valor, el código almacena el intervalo encontrado ( `currentFind` ).

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet61":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet61":::

5. Salga del bucle si la dirección del intervalo encontrado coincide con la dirección del primer intervalo encontrado.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet62":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet62":::

6. Establezca la apariencia del intervalo encontrado.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet63":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet63":::

7. Realice otra búsqueda.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet64":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet64":::

   En el siguiente ejemplo se muestra el método completo.

## <a name="example"></a>Ejemplo
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet57":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet57":::

## <a name="see-also"></a>Consulte también
- [Trabajar con intervalos](../vsto/working-with-ranges.md)
- [Cómo: Aplicar estilos mediante programación a intervalos en libros](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [Cómo: Hacer referencia mediante programación a los intervalos de hojas de cálculo en el código](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [Parámetros opcionales en soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)
