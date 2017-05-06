---
title: "C&#243;mo: Buscar texto en rangos de hojas de c&#225;lculo mediante programaci&#243;n"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "texto [desarrollo de Office en Visual Studio], buscar en hojas de cálculo"
  - "búsquedas de texto, hojas de cálculo"
  - "hojas de cálculo, buscar"
ms.assetid: a6902711-fefb-450a-a76b-b1446d11c423
caps.latest.revision: 48
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 47
---
# C&#243;mo: Buscar texto en rangos de hojas de c&#225;lculo mediante programaci&#243;n
  El método <xref:Microsoft.Office.Interop.Excel.Range.Find%2A> del objeto <xref:Microsoft.Office.Interop.Excel.Range> le permite buscar texto dentro del rango.  Este texto también puede ser cualquiera de las cadenas de error que aparecen en una celda, por ejemplo `#NULL!` o `#VALUE!`.  Para obtener más información sobre cadenas de error, vea [Valores de error en celdas](HV10038459).  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 En el siguiente ejemplo se busca un rango denominado `Fruits` y se modifica la fuente de las celdas que contienen la palabra "apples".  Este procedimiento también utiliza el método <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A>, que usa los valores de la búsqueda establecidos previamente para repetirla.  Especifique la celda a partir de la que se va a realizar la búsqueda y el método <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> se ocupará del resto.  
  
> [!NOTE]  
>  La búsqueda del método <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> vuelve al principio del rango de búsqueda una vez que ha llegado al final del rango.  El código debe garantizar que la búsqueda no entre en un bucle infinito.  El procedimiento del ejemplo muestra una forma de tratar este caso usando la propiedad <xref:Microsoft.Office.Interop.Excel.Range.Address%2A>.  
  
 ![vínculo a vídeo](../vsto/media/playvideo.png "vínculo a vídeo") Dispone de una demostración en vídeo relacionada en [How Do I: Use the Find Method in an Excel Add\-in?](http://go.microsoft.com/fwlink/?LinkID=130294).  
  
### Para buscar texto en un rango de hoja de cálculo  
  
1.  Declare las variables para realizar un seguimiento en todo el rango, el primer rango encontrado y el rango encontrado actual.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#58](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#58)]
     [!code-vb[Trin_VstcoreExcelAutomation#58](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#58)]  
  
2.  Busque la primera coincidencia, especificando todos los parámetros menos la celda a partir de la cual se realiza la búsqueda.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#59](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#59)]
     [!code-vb[Trin_VstcoreExcelAutomation#59](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#59)]  
  
3.  Prosiga con la búsqueda mientras haya coincidencias.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#60](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#60)]
     [!code-vb[Trin_VstcoreExcelAutomation#60](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#60)]  
  
4.  Compare el primer rango encontrado \(`firstFind`\) con **Nothing**.  Si `firstFind` no contiene ningún valor, el código almacena aparte el rango encontrado \(`currentFind`\).  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#61](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#61)]
     [!code-vb[Trin_VstcoreExcelAutomation#61](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#61)]  
  
5.  Sale del bucle si la dirección del rango encontrado coincide con la dirección del primer rango encontrado.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#62](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#62)]
     [!code-vb[Trin_VstcoreExcelAutomation#62](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#62)]  
  
6.  Establezca el aspecto del rango encontrado.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#63](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#63)]
     [!code-vb[Trin_VstcoreExcelAutomation#63](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#63)]  
  
7.  Realice otra búsqueda.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#64](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#64)]
     [!code-vb[Trin_VstcoreExcelAutomation#64](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#64)]  
  
 En el siguiente ejemplo se muestra el método completo.  
  
## Ejemplo  
 [!code-csharp[Trin_VstcoreExcelAutomation#57](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#57)]
 [!code-vb[Trin_VstcoreExcelAutomation#57](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#57)]  
  
## Vea también  
 [Trabajar con rangos](../vsto/working-with-ranges.md)   
 [Cómo: Aplicar estilos a rangos de libros mediante programación](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [Cómo: Hacer referencia a rangos de hojas de cálculo en el código mediante programación](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  