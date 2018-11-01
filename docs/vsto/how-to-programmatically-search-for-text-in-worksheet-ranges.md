---
title: 'Cómo: buscar texto en rangos de hoja de cálculo mediante programación'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, searching
- text [Office development in Visual Studio], searching in worksheets
- text searches, worksheets
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a323336979e16be376cfcd3da44cbc9b12bd73ea
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50671968"
---
# <a name="how-to-programmatically-search-for-text-in-worksheet-ranges"></a>Cómo: buscar texto mediante programación en intervalos de hoja de cálculo
  El <xref:Microsoft.Office.Interop.Excel.Range.Find%2A> método de la <xref:Microsoft.Office.Interop.Excel.Range> objeto le permite buscar texto dentro del intervalo. Este texto puede ser cualquiera de las cadenas de error que pueden aparecer en una celda de la hoja de cálculo como `#NULL!` o `#VALUE!`. Para obtener más información acerca de las cadenas de error, consulte [los valores de error de celda](/office/vba/excel/Concepts/Cells-and-Ranges/cell-error-values).  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 El ejemplo siguiente busca un rango denominado `Fruits` y modifica la fuente de las celdas que contienen la palabra "manzanas". Este procedimiento también utiliza el <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> método, que usa previamente establecido valores para repetir la búsqueda de búsqueda. Especifique la celda después de que se va a buscar y el <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> método encarga del resto.  
  
> [!NOTE]  
>  El <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> búsqueda del método se ajusta al principio del intervalo de búsqueda una vez que ha llegado al final del intervalo. El código debe asegurarse de que la búsqueda no se ajusta alrededor de un bucle infinito. El procedimiento de ejemplo muestra una forma de controlar esto mediante la <xref:Microsoft.Office.Interop.Excel.Range.Address%2A> propiedad.  
  
 ![vínculo a vídeo](../vsto/media/playvideo.gif "vínculo al vídeo") para una demostración en vídeo relacionada, vea [¿cómo lo hago?: Use el método Find en un complemento de Excel?](http://go.microsoft.com/fwlink/?LinkID=130294).  
  
## <a name="to-search-for-text-in-a-worksheet-range"></a>Para buscar texto en un intervalo de hoja de cálculo  
  
1. Declare las variables para el seguimiento de todo el rango, el primer intervalo se encuentra y el intervalo actual se encuentra.  
  
    [!code-csharp[Trin_VstcoreExcelAutomation#58](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#58)]
    [!code-vb[Trin_VstcoreExcelAutomation#58](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#58)]  
  
2. Busque la primera coincidencia, especificando todos los parámetros excepto la celda que se va a buscar después.  
  
    [!code-csharp[Trin_VstcoreExcelAutomation#59](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#59)]
    [!code-vb[Trin_VstcoreExcelAutomation#59](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#59)]  
  
3. Continuar la búsqueda siempre y cuando no hay coincidencia.  
  
    [!code-csharp[Trin_VstcoreExcelAutomation#60](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#60)]
    [!code-vb[Trin_VstcoreExcelAutomation#60](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#60)]  
  
4. Compare el primer rango encontrado (`firstFind`) a **nada**. Si `firstFind` no contiene ningún valor, los almacenes de código fuera del intervalo se encuentra (`currentFind`).  
  
    [!code-csharp[Trin_VstcoreExcelAutomation#61](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#61)]
    [!code-vb[Trin_VstcoreExcelAutomation#61](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#61)]  
  
5. Salir del bucle si la dirección del rango encontrado coincide con la dirección del primer intervalo se encuentra.  
  
    [!code-csharp[Trin_VstcoreExcelAutomation#62](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#62)]
    [!code-vb[Trin_VstcoreExcelAutomation#62](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#62)]  
  
6. Establecer el aspecto del rango encontrado.  
  
    [!code-csharp[Trin_VstcoreExcelAutomation#63](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#63)]
    [!code-vb[Trin_VstcoreExcelAutomation#63](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#63)]  
  
7. Realizar otra búsqueda.  
  
    [!code-csharp[Trin_VstcoreExcelAutomation#64](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#64)]
    [!code-vb[Trin_VstcoreExcelAutomation#64](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#64)]  
  
   En el siguiente ejemplo se muestra el método completo.  
  
## <a name="example"></a>Ejemplo  
 [!code-csharp[Trin_VstcoreExcelAutomation#57](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#57)]
 [!code-vb[Trin_VstcoreExcelAutomation#57](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#57)]  
  
## <a name="see-also"></a>Vea también  
 [Trabajar con rangos](../vsto/working-with-ranges.md)   
 [Cómo: aplicar estilos a rangos de libros mediante programación](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [Cómo: hacer referencia mediante programación a los rangos de hoja de cálculo en el código](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  