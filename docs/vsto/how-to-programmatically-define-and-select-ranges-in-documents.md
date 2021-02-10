---
title: 'Cómo: definir y seleccionar intervalos en documentos mediante programación'
description: Obtenga información sobre cómo puede definir y seleccionar intervalos en documentos de Microsoft Word mediante programación usando el objeto de intervalo.
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
ms.openlocfilehash: e9c703f4d4e747934d1bab458b75a9d499f0d439
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99963957"
---
# <a name="how-to-programmatically-define-and-select-ranges-in-documents"></a>Cómo: definir y seleccionar intervalos en documentos mediante programación
  Puede definir un intervalo en un documento de Microsoft Office Word mediante un objeto <xref:Microsoft.Office.Interop.Word.Range>. Puede seleccionar todo el documento de varias maneras, por ejemplo, mediante el <xref:Microsoft.Office.Interop.Word.Range.Select%2A> método del <xref:Microsoft.Office.Interop.Word.Range> objeto o mediante la propiedad de contenido de la <xref:Microsoft.Office.Tools.Word.Document> clase (en una personalización de nivel de documento) o la <xref:Microsoft.Office.Interop.Word.Document> clase (en un complemento de VSTO).

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="define-a-range"></a>Definir un intervalo
 En el siguiente ejemplo se muestra cómo crear un nuevo objeto <xref:Microsoft.Office.Interop.Word.Range> que incluya los siete primeros caracteres del documento activo, incluidos los caracteres no imprimibles. A continuación, selecciona el texto dentro del intervalo.

### <a name="to-define-a-range-in-a-document-level-customization"></a>Para definir un intervalo en una personalización de nivel de documento

1. Agregue el intervalo al documento pasando un carácter inicial y final al método <xref:Microsoft.Office.Tools.Word.Document.Range%2A> de la clase <xref:Microsoft.Office.Tools.Word.Document>. Para usar este ejemplo de código, ejecútelo desde la clase `ThisDocument` del proyecto.

     [!code-vb[Trin_VstcoreWordAutomation#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#18)]
     [!code-csharp[Trin_VstcoreWordAutomation#18](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#18)]

### <a name="to-define-a-range-by-using-a-vsto-add-in"></a>Para definir un intervalo mediante un complemento de VSTO

1. Agregue el intervalo al documento pasando un carácter inicial y final al método <xref:Microsoft.Office.Interop.Word._Document.Range%2A> de la clase <xref:Microsoft.Office.Interop.Word.Document>. En el siguiente ejemplo de código se agrega un intervalo al documento activo. Para usar este ejemplo de código, ejecútelo desde la clase `ThisAddIn` del proyecto.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#18)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#18](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#18)]

## <a name="select-a-range-in-a-document-level-customization"></a>Seleccionar un intervalo en una personalización de nivel de documento
 Los siguientes ejemplos muestran cómo seleccionar todo el documento mediante el método <xref:Microsoft.Office.Interop.Word.Range.Select%2A> de un objeto <xref:Microsoft.Office.Interop.Word.Range> o usando la propiedad <xref:Microsoft.Office.Tools.Word.Document.Content%2A> de la clase <xref:Microsoft.Office.Tools.Word.Document>.

### <a name="to-select-the-entire-document-as-a-range-by-using-the-select-method"></a>Para seleccionar todo el documento como un intervalo mediante el método Select

1. Use el método <xref:Microsoft.Office.Interop.Word.Range.Select%2A> de un <xref:Microsoft.Office.Interop.Word.Range> que contenga todo el documento. Para usar el siguiente ejemplo de código, ejecútelo desde la clase `ThisDocument` del proyecto.

     [!code-vb[Trin_VstcoreWordAutomation#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#19)]
     [!code-csharp[Trin_VstcoreWordAutomation#19](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#19)]

### <a name="to-select-the-entire-document-as-a-range-by-using-the-content-property"></a>Para seleccionar todo el documento como un intervalo mediante la propiedad Content

1. Use la propiedad <xref:Microsoft.Office.Tools.Word.Document.Content%2A> para definir un intervalo que abarque todo el documento.

    [!code-vb[Trin_VstcoreWordAutomation#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#20)]
    [!code-csharp[Trin_VstcoreWordAutomation#20](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#20)]

   También puede usar los métodos y propiedades de otros objetos para definir un intervalo.

### <a name="to-select-a-sentence-in-the-active-document"></a>Para seleccionar una frase en el documento activo

1. Establezca el intervalo usando la colección <xref:Microsoft.Office.Interop.Word.Sentences>. Use el índice de la frase que desea seleccionar.

    [!code-vb[Trin_VstcoreWordAutomation#21](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#21)]
    [!code-csharp[Trin_VstcoreWordAutomation#21](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#21)]

   Otra forma de seleccionar una frase es establecer manualmente los valores inicial y final del intervalo.

### <a name="to-select-a-sentence-by-manually-setting-the-start-and-end-values"></a>Para seleccionar una frase estableciendo manualmente los valores inicial y final

1. Cree una variable de intervalo.

     [!code-vb[Trin_VstcoreWordAutomation#23](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#23)]
     [!code-csharp[Trin_VstcoreWordAutomation#23](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#23)]

2. Compruebe si hay al menos dos oraciones en el documento, establezca los argumentos de *Inicio* y *fin* del intervalo y, a continuación, seleccione el intervalo.

     [!code-vb[Trin_VstcoreWordAutomation#24](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#24)]
     [!code-csharp[Trin_VstcoreWordAutomation#24](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#24)]

## <a name="select-a-range-by-using-a-vsto-add-in"></a>Seleccionar un intervalo mediante un complemento de VSTO
 Los siguientes ejemplos muestran cómo seleccionar todo el documento mediante el método <xref:Microsoft.Office.Interop.Word.Range.Select%2A> de un objeto <xref:Microsoft.Office.Interop.Word.Range> o usando la propiedad <xref:Microsoft.Office.Interop.Word._Document.Content%2A> de la clase <xref:Microsoft.Office.Interop.Word.Document>.

### <a name="to-select-the-entire-document-as-a-range-by-using-the-select-method"></a>Para seleccionar todo el documento como un intervalo mediante el método Select

1. Use el método <xref:Microsoft.Office.Interop.Word.Range.Select%2A> de un <xref:Microsoft.Office.Interop.Word.Range> que contenga todo el documento. En el siguiente ejemplo de código se selecciona el contenido del documento activo. Para usar este ejemplo de código, ejecútelo desde la clase `ThisAddIn` del proyecto.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#19)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#19](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#19)]

### <a name="to-select-the-entire-document-as-a-range-by-using-the-content-property"></a>Para seleccionar todo el documento como un intervalo mediante la propiedad Content

1. Use la propiedad <xref:Microsoft.Office.Interop.Word._Document.Content%2A> para definir un intervalo que abarque todo el documento.

    [!code-vb[Trin_VstcoreWordAutomationAddIn#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#20)]
    [!code-csharp[Trin_VstcoreWordAutomationAddIn#20](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#20)]

   También puede usar los métodos y propiedades de otros objetos para definir un intervalo.

### <a name="to-select-a-sentence-in-the-active-document"></a>Para seleccionar una frase en el documento activo

1. Establezca el intervalo usando la colección <xref:Microsoft.Office.Interop.Word.Sentences>. Use el índice de la frase que desea seleccionar.

    [!code-vb[Trin_VstcoreWordAutomationAddIn#21](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#21)]
    [!code-csharp[Trin_VstcoreWordAutomationAddIn#21](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#21)]

   Otra forma de seleccionar una frase es establecer manualmente los valores inicial y final del intervalo.

### <a name="to-select-a-sentence-by-manually-setting-the-start-and-end-values"></a>Para seleccionar una frase estableciendo manualmente los valores inicial y final

1. Cree una variable de intervalo.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#23](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#23)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#23](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#23)]

2. Compruebe si hay al menos dos oraciones en el documento, establezca los argumentos de *Inicio* y *fin* del intervalo y, a continuación, seleccione el intervalo.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#24](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#24)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#24](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#24)]

## <a name="see-also"></a>Vea también
- [Información general sobre el modelo de objetos de Word](../vsto/word-object-model-overview.md)
- [Cómo: ampliar intervalos en documentos mediante programación](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [Cómo: recuperar los caracteres inicial y final de los intervalos mediante programación](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)
- [Cómo: ampliar intervalos en documentos mediante programación](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [Cómo: restablecer intervalos en documentos de Word mediante programación](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
- [Cómo: contraer intervalos o selecciones en documentos mediante programación](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)
- [Cómo: excluir marcas de párrafo al crear intervalos mediante programación](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)
