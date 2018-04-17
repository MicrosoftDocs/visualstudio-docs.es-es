---
title: 'Cómo: insertar texto en documentos de Word mediante programación | Documentos de Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, inserting text in documents
- text [Office development in Visual Studio], inserting in documents
- ranges, replacing text in documents
- documents [Office development in Visual Studio], inserting text
- text [Office development in Visual Studio], replacing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: bbbcc0543ce6017ac83ed2d1fcc09fed201e466f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-insert-text-into-word-documents"></a>Cómo: Insertar texto en documentos de Word mediante programación
  Existen tres maneras principales de insertar texto en documentos de Microsoft Office Word:  
  
-   Insertar texto en un intervalo.  
  
-   Reemplazar texto en un intervalo con texto nuevo.  
  
-   Usar el método <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> de un objeto <xref:Microsoft.Office.Interop.Word.Selection> para insertar texto en el cursor o la selección.  
  
> [!NOTE]  
>  También puede insertar texto en controles de contenido y marcadores. Para obtener más información, consulte [controles de contenido](../vsto/content-controls.md) y [Bookmark (Control)](../vsto/bookmark-control.md).  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="inserting-text-in-a-range"></a>Insertar texto en un intervalo  
 Use la propiedad <xref:Microsoft.Office.Interop.Word.Range.Text%2A> de un objeto <xref:Microsoft.Office.Interop.Word.Range> para insertar texto en un documento.  
  
#### <a name="to-insert-text-in-a-range"></a>Para insertar texto en un intervalo  
  
1.  Especifique un intervalo al principio de un documento e inserte el texto **New Text**.  
  
     El siguiente ejemplo de código se puede usar en una personalización de nivel de documento.  
  
     [!code-vb[Trin_VstcoreWordAutomation#51](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#51)]
     [!code-csharp[Trin_VstcoreWordAutomation#51](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#51)]  
  
     El siguiente ejemplo de código se puede usar en un complemento de VSTO. Este código usa el documento activo.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#51](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#51)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#51](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#51)]  
  
2.  Seleccione el objeto <xref:Microsoft.Office.Interop.Word.Range> , que se ha ampliado de un carácter a la longitud del texto insertado.  
  
     [!code-vb[Trin_VstcoreWordAutomation#52](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#52)]
     [!code-csharp[Trin_VstcoreWordAutomation#52](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#52)]  
  
## <a name="replacing-text-in-a-range"></a>Reemplazar texto en un intervalo  
 Si el intervalo especificado contiene texto, se reemplaza todo el texto en el intervalo por el texto insertado.  
  
#### <a name="to-replace-text-in-a-range"></a>Para reemplazar texto en un intervalo  
  
1.  Cree un objeto <xref:Microsoft.Office.Interop.Word.Range> que consista de los 12 primeros caracteres del documento.  
  
     El siguiente ejemplo de código se puede usar en una personalización de nivel de documento.  
  
     [!code-vb[Trin_VstcoreWordAutomation#53](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#53)]
     [!code-csharp[Trin_VstcoreWordAutomation#53](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#53)]  
  
     El siguiente ejemplo de código se puede usar en un complemento de VSTO. Este código usa el documento activo.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#53](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#53)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#53](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#53)]  
  
2.  Reemplace esos caracteres por la cadena **New Text**.  
  
     [!code-vb[Trin_VstcoreWordAutomation#54](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#54)]
     [!code-csharp[Trin_VstcoreWordAutomation#54](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#54)]  
  
3.  Seleccione el intervalo.  
  
     [!code-vb[Trin_VstcoreWordAutomation#55](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#55)]
     [!code-csharp[Trin_VstcoreWordAutomation#55](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#55)]  
  
## <a name="inserting-text-using-typetext"></a>Insertar texto usando TypeText  
 El método <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> inserta texto en la selección. <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> se comporta de forma distinta según las opciones establecidas en el equipo del usuario. El código en el siguiente procedimiento declara una variable de objeto <xref:Microsoft.Office.Interop.Word.Selection> y desactiva la opción **Overtype** si está activada. Si la opción **Overtype** está activada, se sobrescribe cualquier texto situado junto al cursor.  
  
#### <a name="to-insert-text-using-the-typetext-method"></a>Para insertar texto mediante el método TypeText  
  
1.  Declare una variable de objeto <xref:Microsoft.Office.Interop.Word.Selection> .  
  
     [!code-vb[Trin_VstcoreWordAutomation#57](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#57)]
     [!code-csharp[Trin_VstcoreWordAutomation#57](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#57)]  
  
2.  Desactive la opción **Overtype** si está activada.  
  
     [!code-vb[Trin_VstcoreWordAutomation#58](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#58)]
     [!code-csharp[Trin_VstcoreWordAutomation#58](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#58)]  
  
3.  Compruebe si la selección actual es un punto de inserción.  
  
     Si lo es, el código inserta una frase usando <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A>y, a continuación, una marca de párrafo usando el método <xref:Microsoft.Office.Interop.Word.Selection.TypeParagraph%2A> .  
  
     [!code-vb[Trin_VstcoreWordAutomation#59](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#59)]
     [!code-csharp[Trin_VstcoreWordAutomation#59](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#59)]  
  
4.  El código del bloque **ElseIf** comprueba si la selección es una selección normal. Si lo es, otro bloque **If** comprueba si la opción **ReplaceSelection** está activada. Si es así, el código usa el método <xref:Microsoft.Office.Interop.Word.Selection.Collapse%2A> de la selección para contraer la selección hasta un punto de inserción al principio del bloque de texto seleccionado. Inserte el texto y una marca de párrafo.  
  
     [!code-vb[Trin_VstcoreWordAutomation#60](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#60)]
     [!code-csharp[Trin_VstcoreWordAutomation#60](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#60)]  
  
5.  Si la selección no es un punto de inserción o un bloque de texto seleccionado, el código del bloque **Else** no hace nada.  
  
     [!code-vb[Trin_VstcoreWordAutomation#61](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#61)]
     [!code-csharp[Trin_VstcoreWordAutomation#61](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#61)]  
  
 También puede usar el método <xref:Microsoft.Office.Interop.Word.Selection.TypeBackspace%2A> del objeto <xref:Microsoft.Office.Interop.Word.Selection> , que imita la funcionalidad de la tecla Retroceso del teclado. Sin embargo, cuando se trata de insertar y manipular texto, el objeto <xref:Microsoft.Office.Interop.Word.Range> ofrece un mayor control.  
  
 El ejemplo siguiente muestra el código completo: Para usar este ejemplo, ejecute el código desde la clase `ThisDocument` o `ThisAddIn` del proyecto.  
  
 [!code-vb[Trin_VstcoreWordAutomation#56](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#56)]
 [!code-csharp[Trin_VstcoreWordAutomation#56](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#56)]  
  
## <a name="see-also"></a>Vea también  
 [Cómo: dar formato a texto en documentos mediante programación](../vsto/how-to-programmatically-format-text-in-documents.md)   
 [Cómo: definir mediante programación y seleccionar rangos en documentos](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Cómo: Ampliar intervalos en documentos mediante programación](../vsto/how-to-programmatically-extend-ranges-in-documents.md)  
  
  