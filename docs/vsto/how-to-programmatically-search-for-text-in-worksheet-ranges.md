---
title: "Cómo: buscar texto en rangos de hoja de cálculo mediante programación | Documentos de Microsoft"
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
- worksheets, searching
- text [Office development in Visual Studio], searching in worksheets
- text searches, worksheets
ms.assetid: a6902711-fefb-450a-a76b-b1446d11c423
caps.latest.revision: "48"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 031894a3307a40af981ad974898ae819ba68d24a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-search-for-text-in-worksheet-ranges"></a>Cómo: Buscar texto en rangos de hojas de cálculo mediante programación
  El <xref:Microsoft.Office.Interop.Excel.Range.Find%2A> método de la <xref:Microsoft.Office.Interop.Excel.Range> objeto le permite buscar texto dentro del intervalo. Este texto puede ser cualquiera de las cadenas de error que pueden aparecer en una celda de la hoja de cálculo como `#NULL!` o `#VALUE!`. Para obtener más información acerca de las cadenas de error, consulte [valores de Error de celda](http://msdn.microsoft.com/library/office/ff839168.aspx).  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 En el ejemplo siguiente se busca un rango denominado `Fruits` y modifica la fuente de las celdas que contienen la palabra "apples". Este procedimiento también utiliza el <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> método, que usa establecidas previamente valores para repetir la búsqueda de búsqueda. Especifica la celda después de que se va a buscar y el <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> método encarga del resto.  
  
> [!NOTE]  
>  El <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> búsqueda del método ajusta hacia el principio del intervalo de búsqueda después de que se ha alcanzado el final del intervalo. El código debe asegurarse de que la búsqueda no se ajusta alrededor de un bucle infinito. El procedimiento de ejemplo muestra una forma de tratar este caso usando la <xref:Microsoft.Office.Interop.Excel.Range.Address%2A> propiedad.  
  
 ![vínculo a vídeo](../vsto/media/playvideo.gif "vínculo a vídeo") para una demostración en vídeo relacionada, vea [Cómo: usar el método Find en un complemento de Excel?](http://go.microsoft.com/fwlink/?LinkID=130294).  
  
### <a name="to-search-for-text-in-a-worksheet-range"></a>Para buscar texto en un intervalo de hoja de cálculo  
  
1.  Declare las variables para el seguimiento de todo el rango, el primer rango encontrado y el rango encontrado actual.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#58](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#58)]
     [!code-vb[Trin_VstcoreExcelAutomation#58](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#58)]  
  
2.  Busque la primera coincidencia, especificando todos los parámetros excepto la celda para su búsqueda después.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#59](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#59)]
     [!code-vb[Trin_VstcoreExcelAutomation#59](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#59)]  
  
3.  Continuar la búsqueda siempre que hay coincidencia.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#60](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#60)]
     [!code-vb[Trin_VstcoreExcelAutomation#60](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#60)]  
  
4.  Compare el primer rango encontrado (`firstFind`) a **nada**. Si `firstFind` no contiene ningún valor, los almacenes de código fuera del intervalo se encuentra (`currentFind`).  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#61](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#61)]
     [!code-vb[Trin_VstcoreExcelAutomation#61](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#61)]  
  
5.  Salir del bucle si la dirección del rango encontrado coincide con la dirección del primer intervalo se encuentra.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#62](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#62)]
     [!code-vb[Trin_VstcoreExcelAutomation#62](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#62)]  
  
6.  Establecer el aspecto del rango encontrado.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#63](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#63)]
     [!code-vb[Trin_VstcoreExcelAutomation#63](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#63)]  
  
7.  Realizar otra búsqueda.  
  
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
  
  