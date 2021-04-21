---
title: 'Cómo: Definir y seleccionar rangos en documentos mediante programación'
description: Obtenga información sobre cómo puede definir y seleccionar rangos en documentos de Microsoft Word mediante programación mediante el objeto Range.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], selecting sentences
- documents [Office development in Visual Studio], ranges
- sentences, selecting in documents
- ranges, selecting in documents
- ranges, defining in documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 3a5dc0c7fb9f3e9a2b4a15447f81239db973c215
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825958"
---
# <a name="how-to-programmatically-define-and-select-ranges-in-documents"></a>Cómo: Definir y seleccionar rangos en documentos mediante programación
  Puede definir un intervalo en un documento de Microsoft Office Word mediante un objeto <xref:Microsoft.Office.Interop.Word.Range>. Puede seleccionar todo el documento de varias maneras, por ejemplo, mediante el método del objeto o mediante la propiedad Content de la clase (en una personalización de nivel de documento) o la clase (en un complemento <xref:Microsoft.Office.Interop.Word.Range.Select%2A> <xref:Microsoft.Office.Interop.Word.Range> de <xref:Microsoft.Office.Tools.Word.Document> <xref:Microsoft.Office.Interop.Word.Document> VSTO).

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="define-a-range"></a>Definición de un intervalo
 En el siguiente ejemplo se muestra cómo crear un nuevo objeto <xref:Microsoft.Office.Interop.Word.Range> que incluya los siete primeros caracteres del documento activo, incluidos los caracteres no imprimibles. A continuación, selecciona el texto dentro del intervalo.

### <a name="to-define-a-range-in-a-document-level-customization"></a>Para definir un intervalo en una personalización de nivel de documento

1. Agregue el intervalo al documento pasando un carácter inicial y final al método <xref:Microsoft.Office.Tools.Word.Document.Range%2A> de la clase <xref:Microsoft.Office.Tools.Word.Document>. Para usar este ejemplo de código, ejecútelo desde la clase `ThisDocument` del proyecto.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet18":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet18":::

### <a name="to-define-a-range-by-using-a-vsto-add-in"></a>Para definir un intervalo mediante un complemento de VSTO

1. Agregue el intervalo al documento pasando un carácter inicial y final al método <xref:Microsoft.Office.Interop.Word._Document.Range%2A> de la clase <xref:Microsoft.Office.Interop.Word.Document>. En el siguiente ejemplo de código se agrega un intervalo al documento activo. Para usar este ejemplo de código, ejecútelo desde la clase `ThisAddIn` del proyecto.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet18":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet18":::

## <a name="select-a-range-in-a-document-level-customization"></a>Selección de un intervalo en una personalización de nivel de documento
 Los siguientes ejemplos muestran cómo seleccionar todo el documento mediante el método <xref:Microsoft.Office.Interop.Word.Range.Select%2A> de un objeto <xref:Microsoft.Office.Interop.Word.Range> o usando la propiedad <xref:Microsoft.Office.Tools.Word.Document.Content%2A> de la clase <xref:Microsoft.Office.Tools.Word.Document>.

### <a name="to-select-the-entire-document-as-a-range-by-using-the-select-method"></a>Para seleccionar todo el documento como un intervalo mediante el método Select

1. Use el método <xref:Microsoft.Office.Interop.Word.Range.Select%2A> de un <xref:Microsoft.Office.Interop.Word.Range> que contenga todo el documento. Para usar el siguiente ejemplo de código, ejecútelo desde la clase `ThisDocument` del proyecto.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet19":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet19":::

### <a name="to-select-the-entire-document-as-a-range-by-using-the-content-property"></a>Para seleccionar todo el documento como un intervalo mediante la propiedad Content

1. Use la propiedad <xref:Microsoft.Office.Tools.Word.Document.Content%2A> para definir un intervalo que abarque todo el documento.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet20":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet20":::

   También puede usar los métodos y propiedades de otros objetos para definir un intervalo.

### <a name="to-select-a-sentence-in-the-active-document"></a>Para seleccionar una frase en el documento activo

1. Establezca el intervalo usando la colección <xref:Microsoft.Office.Interop.Word.Sentences>. Use el índice de la frase que desea seleccionar.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet21":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet21":::

   Otra forma de seleccionar una frase es establecer manualmente los valores inicial y final del intervalo.

### <a name="to-select-a-sentence-by-manually-setting-the-start-and-end-values"></a>Para seleccionar una frase estableciendo manualmente los valores inicial y final

1. Cree una variable de intervalo.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet23":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet23":::

2. Compruebe si hay al menos dos oraciones en el  documento, establezca los argumentos *Inicio* y Fin del intervalo y, a continuación, seleccione el intervalo.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet24":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet24":::

## <a name="select-a-range-by-using-a-vsto-add-in"></a>Selección de un intervalo mediante un complemento de VSTO
 Los siguientes ejemplos muestran cómo seleccionar todo el documento mediante el método <xref:Microsoft.Office.Interop.Word.Range.Select%2A> de un objeto <xref:Microsoft.Office.Interop.Word.Range> o usando la propiedad <xref:Microsoft.Office.Interop.Word._Document.Content%2A> de la clase <xref:Microsoft.Office.Interop.Word.Document>.

### <a name="to-select-the-entire-document-as-a-range-by-using-the-select-method"></a>Para seleccionar todo el documento como un intervalo mediante el método Select

1. Use el método <xref:Microsoft.Office.Interop.Word.Range.Select%2A> de un <xref:Microsoft.Office.Interop.Word.Range> que contenga todo el documento. En el siguiente ejemplo de código se selecciona el contenido del documento activo. Para usar este ejemplo de código, ejecútelo desde la clase `ThisAddIn` del proyecto.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet19":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet19":::

### <a name="to-select-the-entire-document-as-a-range-by-using-the-content-property"></a>Para seleccionar todo el documento como un intervalo mediante la propiedad Content

1. Use la propiedad <xref:Microsoft.Office.Interop.Word._Document.Content%2A> para definir un intervalo que abarque todo el documento.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet20":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet20":::

   También puede usar los métodos y propiedades de otros objetos para definir un intervalo.

### <a name="to-select-a-sentence-in-the-active-document"></a>Para seleccionar una frase en el documento activo

1. Establezca el intervalo usando la colección <xref:Microsoft.Office.Interop.Word.Sentences>. Use el índice de la frase que desea seleccionar.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet21":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet21":::

   Otra forma de seleccionar una frase es establecer manualmente los valores inicial y final del intervalo.

### <a name="to-select-a-sentence-by-manually-setting-the-start-and-end-values"></a>Para seleccionar una frase estableciendo manualmente los valores inicial y final

1. Cree una variable de intervalo.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet23":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet23":::

2. Compruebe si hay al menos dos oraciones en el  documento, establezca los argumentos *Inicio* y Fin del intervalo y, a continuación, seleccione el intervalo.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet24":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet24":::

## <a name="see-also"></a>Consulte también
- [Introducción al modelo de objetos de Word](../vsto/word-object-model-overview.md)
- [Cómo: Ampliar rangos en documentos mediante programación](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [Cómo: Recuperar mediante programación caracteres iniciales y finales en intervalos](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)
- [Cómo: Ampliar rangos en documentos mediante programación](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [Cómo: Restablecer intervalos en documentos de Word mediante programación](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
- [Cómo: Contraer rangos o selecciones en documentos mediante programación](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)
- [Cómo: Excluir marcas de párrafo mediante programación al crear intervalos](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)
