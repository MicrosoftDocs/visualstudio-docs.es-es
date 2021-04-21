---
title: 'Cómo: Insertar texto mediante programación en documentos de Word'
description: Obtenga información sobre cómo insertar texto mediante programación en un documento de Microsoft Word mediante Visual Studio.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 08/14/2019
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, inserting text in documents
- text [Office development in Visual Studio], inserting in documents
- ranges, replacing text in documents
- documents [Office development in Visual Studio], inserting text
- text [Office development in Visual Studio], replacing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: f17828b4617f84cb104761918787b4bbb79f7afc
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827362"
---
# <a name="how-to-programmatically-insert-text-into-word-documents"></a>Cómo: Insertar texto mediante programación en documentos de Word
  Existen tres maneras principales de insertar texto en documentos de Microsoft Office Word:

- Insertar texto en un intervalo.

- Reemplazar texto en un intervalo con texto nuevo.

- Usar el método <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> de un objeto <xref:Microsoft.Office.Interop.Word.Selection> para insertar texto en el cursor o la selección.

> [!NOTE]
> También puede insertar texto en controles de contenido y marcadores. Para obtener más información, vea [Controles de contenido y](../vsto/content-controls.md) Control [Marcador](../vsto/bookmark-control.md).

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="insert-text-in-a-range"></a>Insertar texto en un intervalo
 Use la propiedad <xref:Microsoft.Office.Interop.Word.Range.Text%2A> de un objeto <xref:Microsoft.Office.Interop.Word.Range> para insertar texto en un documento.

### <a name="to-insert-text-in-a-range"></a>Para insertar texto en un intervalo

1. Especifique un intervalo al principio de un documento e inserte el texto **New Text**.

     El siguiente ejemplo de código se puede usar en una personalización de nivel de documento.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet51":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet51":::

     El siguiente ejemplo de código se puede usar en un complemento de VSTO. Este código usa el documento activo.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet51":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet51":::

2. Seleccione el objeto <xref:Microsoft.Office.Interop.Word.Range> , que se ha ampliado de un carácter a la longitud del texto insertado.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet52":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet52":::

## <a name="replace-text-in-a-range"></a>Reemplazo de texto en un intervalo
 Si el intervalo especificado contiene texto, se reemplaza todo el texto en el intervalo por el texto insertado.

### <a name="to-replace-text-in-a-range"></a>Para reemplazar texto en un intervalo

1. Cree un objeto <xref:Microsoft.Office.Interop.Word.Range> que consista de los 12 primeros caracteres del documento.

     El siguiente ejemplo de código se puede usar en una personalización de nivel de documento.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet53":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet53":::

     El siguiente ejemplo de código se puede usar en un complemento de VSTO. Este código usa el documento activo.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet53":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet53":::

2. Reemplace esos caracteres por la cadena **New Text**.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet54":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet54":::

3. Seleccione el intervalo.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet55":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet55":::

## <a name="insert-text-using-typetext"></a>Inserción de texto mediante TypeText
 El método <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> inserta texto en la selección. <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> se comporta de forma distinta según las opciones establecidas en el equipo del usuario. El código en el siguiente procedimiento declara una variable de objeto <xref:Microsoft.Office.Interop.Word.Selection> y desactiva la opción **Overtype** si está activada. Si la opción **Overtype** está activada, se sobrescribe cualquier texto situado junto al cursor.

### <a name="to-insert-text-using-the-typetext-method"></a>Para insertar texto mediante el método TypeText

1. Declare una variable de objeto <xref:Microsoft.Office.Interop.Word.Selection>.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet57":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet57":::

2. Desactive la opción **Overtype** si está activada.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet58":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet58":::

3. Compruebe si la selección actual es un punto de inserción.

    Si lo es, el código inserta una frase usando <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A>y, a continuación, una marca de párrafo usando el método <xref:Microsoft.Office.Interop.Word.Selection.TypeParagraph%2A> .

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet59":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet59":::

4. El código del bloque **ElseIf** comprueba si la selección es una selección normal. Si lo es, otro bloque **If** comprueba si la opción **ReplaceSelection** está activada. Si es así, el código usa el método <xref:Microsoft.Office.Interop.Word.Selection.Collapse%2A> de la selección para contraer la selección hasta un punto de inserción al principio del bloque de texto seleccionado. Inserte el texto y una marca de párrafo.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet60":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet60":::

5. Si la selección no es un punto de inserción o un bloque de texto seleccionado, el código del bloque **Else** no hace nada.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet61":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet61":::

   También puede usar el método del objeto , que imita la funcionalidad de <xref:Microsoft.Office.Interop.Word.Selection.TypeBackspace%2A> <xref:Microsoft.Office.Interop.Word.Selection> la tecla **Retroceso** en el teclado. Sin embargo, cuando se trata de insertar y manipular texto, el objeto <xref:Microsoft.Office.Interop.Word.Range> ofrece un mayor control.

   El ejemplo siguiente muestra el código completo: Para usar este ejemplo, ejecute el código desde la clase `ThisDocument` o `ThisAddIn` del proyecto.

   :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet56":::
   :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet56":::

## <a name="see-also"></a>Consulte también
- [Cómo: Dar formato al texto en documentos mediante programación](../vsto/how-to-programmatically-format-text-in-documents.md)
- [Cómo: Definir y seleccionar rangos en documentos mediante programación](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Cómo: Ampliar rangos en documentos mediante programación](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
