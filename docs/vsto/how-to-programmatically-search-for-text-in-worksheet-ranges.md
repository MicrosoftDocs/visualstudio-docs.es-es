---
title: 'Cómo: buscar texto en rangos de hojas de cálculo mediante programación'
description: Obtenga información sobre cómo puede usar Visual Studio para buscar texto en rangos de hojas de cálculo de Microsoft Excel mediante programación.
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
ms.openlocfilehash: 3cf3894a2fb6d34678786686fe3c229d2e16a9a2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877894"
---
# <a name="how-to-programmatically-search-for-text-in-worksheet-ranges"></a>Cómo: buscar texto en rangos de hojas de cálculo mediante programación
  El <xref:Microsoft.Office.Interop.Excel.Range.Find%2A> método del <xref:Microsoft.Office.Interop.Excel.Range> objeto permite buscar texto dentro del intervalo. Este texto también puede ser cualquiera de las cadenas de error que pueden aparecer en una celda de la hoja de cálculo, como `#NULL!` o `#VALUE!` . Para obtener más información acerca de las cadenas de error, consulte [valores de error de celda](/office/vba/excel/Concepts/Cells-and-Ranges/cell-error-values).

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 En el siguiente ejemplo se busca un rango denominado `Fruits` y se modifica la fuente de las celdas que contienen la palabra "manzanas". Este procedimiento también utiliza el <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> método, que usa la configuración de búsqueda establecida previamente para repetir la búsqueda. Especifique la celda después de la que se va a buscar y el <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> método controla el resto.

> [!NOTE]
> La <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> búsqueda del método vuelve al principio del intervalo de búsqueda una vez que se ha alcanzado el final del intervalo. El código debe asegurarse de que la búsqueda no se ajusta en un bucle infinito. En el procedimiento de ejemplo se muestra una manera de controlar esto mediante la <xref:Microsoft.Office.Interop.Excel.Range.Address%2A> propiedad.

## <a name="to-search-for-text-in-a-worksheet-range"></a>Para buscar texto en un intervalo de la hoja de cálculo

1. Declare las variables para realizar el seguimiento de todo el intervalo, el primer intervalo encontrado y el intervalo encontrado actual.

    [!code-csharp[Trin_VstcoreExcelAutomation#58](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#58)]
    [!code-vb[Trin_VstcoreExcelAutomation#58](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#58)]

2. Busque la primera coincidencia, especificando todos los parámetros excepto la celda en la que se va a buscar.

    [!code-csharp[Trin_VstcoreExcelAutomation#59](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#59)]
    [!code-vb[Trin_VstcoreExcelAutomation#59](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#59)]

3. Siga buscando en el tiempo que haya coincidencias.

    [!code-csharp[Trin_VstcoreExcelAutomation#60](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#60)]
    [!code-vb[Trin_VstcoreExcelAutomation#60](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#60)]

4. Compare el primer intervalo encontrado ( `firstFind` ) con **nada**. Si `firstFind` no contiene ningún valor, el código almacena el intervalo encontrado ( `currentFind` ).

    [!code-csharp[Trin_VstcoreExcelAutomation#61](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#61)]
    [!code-vb[Trin_VstcoreExcelAutomation#61](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#61)]

5. Salga del bucle si la dirección del intervalo encontrado coincide con la dirección del primer intervalo encontrado.

    [!code-csharp[Trin_VstcoreExcelAutomation#62](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#62)]
    [!code-vb[Trin_VstcoreExcelAutomation#62](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#62)]

6. Establece la apariencia del intervalo encontrado.

    [!code-csharp[Trin_VstcoreExcelAutomation#63](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#63)]
    [!code-vb[Trin_VstcoreExcelAutomation#63](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#63)]

7. Realice otra búsqueda.

    [!code-csharp[Trin_VstcoreExcelAutomation#64](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#64)]
    [!code-vb[Trin_VstcoreExcelAutomation#64](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#64)]

   En el siguiente ejemplo se muestra el método completo.

## <a name="example"></a>Ejemplo
 [!code-csharp[Trin_VstcoreExcelAutomation#57](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#57)]
 [!code-vb[Trin_VstcoreExcelAutomation#57](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#57)]

## <a name="see-also"></a>Vea también
- [Trabajar con rangos](../vsto/working-with-ranges.md)
- [Cómo: aplicar estilos a rangos de libros mediante programación](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [Cómo: hacer referencia a rangos de hojas de cálculo en el código mediante programación](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)
