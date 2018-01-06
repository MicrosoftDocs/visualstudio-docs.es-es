---
title: "Cómo: excluir marcas de párrafo al crear intervalos mediante programación | Documentos de Microsoft"
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
- documents [Office development in Visual Studio], excluding paragraphs
- ranges, excluding paragraph marks in Word
- documents [Office development in Visual Studio], paragraph marks
- paragraphs, controlling structure
ms.assetid: 6d563834-34bd-4462-a556-4339d9277eee
caps.latest.revision: "50"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 5f726a30a7ae50e35726b67336ec41f50be60b24
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-exclude-paragraph-marks-when-creating-ranges"></a>Cómo: Excluir marcas de párrafo al crear intervalos mediante programación
  Siempre que se crea un objeto <xref:Microsoft.Office.Interop.Word.Range> basado en un párrafo, todos los caracteres no imprimibles (como las marcas de párrafo), se incluirán en el intervalo. Es posible que desee insertar el texto de un párrafo de origen en un párrafo de destino. Si no desea dividir el párrafo de destino en párrafos independientes, en primer lugar, tendrá que quitar la marca de párrafo del párrafo de origen. Además, dado que la información de formato de párrafo se almacena en la marca de párrafo, es posible que no desee incluirla cuando inserte el intervalo en un párrafo existente.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 El siguiente procedimiento de ejemplo declara dos variables de cadena, recupera el contenido del primer y del segundo párrafo del documento activo y, a continuación, intercambia su contenido. A continuación, el ejemplo muestra cómo se elimina la marca de párrafo del intervalo mediante el método <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> , y cómo se inserta el texto dentro del párrafo.  
  
### <a name="to-control-paragraph-structure-when-inserting-text"></a>Controlar la estructura de un párrafo cuando se inserta texto  
  
1.  Cree dos variables de intervalo para los párrafos primero y segundo y recupere su contenido mediante la propiedad <xref:Microsoft.Office.Interop.Word.Range.Text%2A> .  
  
     El siguiente ejemplo de código se puede usar en una personalización de nivel de documento.  
  
     [!code-vb[Trin_VstcoreWordAutomation#27](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#27)]
     [!code-csharp[Trin_VstcoreWordAutomation#27](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#27)]  
  
     El siguiente ejemplo de código se puede usar en un complemento VSTO de nivel de aplicación. Este código usa el documento activo.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#27](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#27)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#27](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#27)]  
  
2.  Asigne la propiedad <xref:Microsoft.Office.Interop.Word.Range.Text%2A> , intercambiando el texto entre los dos párrafos.  
  
     [!code-vb[Trin_VstcoreWordAutomation#28](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#28)]
     [!code-csharp[Trin_VstcoreWordAutomation#28](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#28)]  
  
3.  Seleccione los intervalos por turnos y haga una pausa para mostrar los resultados en un cuadro de mensaje.  
  
     [!code-vb[Trin_VstcoreWordAutomation#29](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#29)]
     [!code-csharp[Trin_VstcoreWordAutomation#29](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#29)]  
  
4.  Ajuste `firstRange` con el método <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> , de forma que la marca de párrafo deje de formar parte del elemento `firstRange`.  
  
     [!code-vb[Trin_VstcoreWordAutomation#30](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#30)]
     [!code-csharp[Trin_VstcoreWordAutomation#30](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#30)]  
  
5.  Sustituya el resto del texto del primer párrafo, asignando una cadena nueva a la propiedad <xref:Microsoft.Office.Interop.Word.Range.Text%2A> del intervalo.  
  
     [!code-vb[Trin_VstcoreWordAutomation#31](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#31)]
     [!code-csharp[Trin_VstcoreWordAutomation#31](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#31)]  
  
6.  Sustituya el texto en `secondRange`, incluyendo la marca de párrafo.  
  
     [!code-vb[Trin_VstcoreWordAutomation#32](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#32)]
     [!code-csharp[Trin_VstcoreWordAutomation#32](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#32)]  
  
7.  Seleccione `firstRange` y haga una pausa para mostrar los resultados en un cuadro de mensaje. A continuación, proceda de igual forma con `secondRange`.  
  
     Dado que `firstRange` se ha redefinido para excluir la marca de párrafo, el formato original del párrafo se conserva. Sin embargo, se insertó una frase sobre la marca de párrafo en `secondRange`, lo cual elimina el párrafo independiente.  
  
     [!code-vb[Trin_VstcoreWordAutomation#33](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#33)]
     [!code-csharp[Trin_VstcoreWordAutomation#33](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#33)]  
  
     El contenido original de los dos intervalos se guardó como cadenas, lo que permite restaurar el estado original del documento.  
  
8.  Vuelva a ajustar `firstRange` para que incluya la marca de párrafo mediante el método <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> y así indicar la posición de un carácter.  
  
     [!code-vb[Trin_VstcoreWordAutomation#34](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#34)]
     [!code-csharp[Trin_VstcoreWordAutomation#34](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#34)]  
  
9. Elimine `secondRange`. De esta forma se restablece la posición original del tercer párrafo.  
  
     [!code-vb[Trin_VstcoreWordAutomation#35](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#35)]
     [!code-csharp[Trin_VstcoreWordAutomation#35](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#35)]  
  
10. Restaure el texto del párrafo original en `firstRange`.  
  
     [!code-vb[Trin_VstcoreWordAutomation#36](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#36)]
     [!code-csharp[Trin_VstcoreWordAutomation#36](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#36)]  
  
11. Use el método <xref:Microsoft.Office.Interop.Word.Range.InsertAfter%2A> del objeto <xref:Microsoft.Office.Interop.Word.Range> para insertar el contenido del segundo párrafo original después de `firstRange`y, a continuación, seleccione `firstRange`.  
  
     [!code-vb[Trin_VstcoreWordAutomation#37](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#37)]
     [!code-csharp[Trin_VstcoreWordAutomation#37](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#37)]  
  
## <a name="document-level-customization-example"></a>Ejemplo de personalización de nivel de documento  
  
#### <a name="to-control-paragraph-structure-when-inserting-text-in-document-level-customizations"></a>Controlar la estructura de un párrafo cuando se inserta texto en las personalizaciones de nivel de documento  
  
1.  En el siguiente ejemplo se muestra el método completo de una personalización de nivel de documento. Para usar este código, ejecútelo desde la clase `ThisDocument` del proyecto.  
  
     [!code-vb[Trin_VstcoreWordAutomation#26](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#26)]
     [!code-csharp[Trin_VstcoreWordAutomation#26](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#26)]  
  
## <a name="vsto-add-in-example"></a>Ejemplo de complemento de VSTO  
  
#### <a name="to-control-paragraph-structure-when-inserting-text-in-an-vsto-add-in"></a>Controlar la estructura de un párrafo cuando se inserta texto en un complemento VSTO  
  
1.  En el siguiente ejemplo se muestra el método completo de un complemento VSTO. Para usar este código, ejecútelo desde la clase `ThisAddIn` del proyecto.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#26](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#26)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#26](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#26)]  
  
## <a name="see-also"></a>Vea también  
 [Cómo: ampliar intervalos en documentos de mediante programación](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [Cómo: contraer intervalos o mediante programación las selecciones en documentos](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)   
 [Cómo: insertar texto en documentos de Word mediante programación](../vsto/how-to-programmatically-insert-text-into-word-documents.md)   
 [Cómo: restablecer intervalos en Word documentos mediante programación](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [Cómo: definir mediante programación y seleccionar rangos en documentos](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  