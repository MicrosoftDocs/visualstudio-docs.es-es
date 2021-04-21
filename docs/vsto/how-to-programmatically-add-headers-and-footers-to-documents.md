---
title: 'Cómo: Agregar encabezados y pies de página a documentos mediante programación'
description: Obtenga información sobre cómo puede agregar texto a los encabezados y pies de página del documento mediante la propiedad Headers y la propiedad Footers de la sección .
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- headers, adding to Office documents
- documents [Office development in Visual Studio], adding headers
- documents [Office development in Visual Studio], adding footers
- footers, adding to documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 73844d19ef6bb85c623706ab0d359836e42a3b14
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828753"
---
# <a name="how-to-programmatically-add-headers-and-footers-to-documents"></a>Cómo: Agregar encabezados y pies de página a documentos mediante programación
  Puede agregar texto a los encabezados y pies de página del documento mediante las propiedades <xref:Microsoft.Office.Interop.Word.Section.Headers%2A> y <xref:Microsoft.Office.Interop.Word.Section.Footers%2A> de la <xref:Microsoft.Office.Interop.Word.Section>. Cada sección de un documento contiene tres encabezados y pies de página:

- <xref:Microsoft.Office.Interop.Word.WdHeaderFooterIndex.wdHeaderFooterPrimary>

- <xref:Microsoft.Office.Interop.Word.WdHeaderFooterIndex.wdHeaderFooterEvenPages>

- <xref:Microsoft.Office.Interop.Word.WdHeaderFooterIndex.wdHeaderFooterFirstPage>

  Los procedimientos son diferentes para las personalizaciones de nivel de documento y los complementos de VSTO.

  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="document-level-customizations"></a>Personalizaciones de nivel de documento
 Para usar los siguientes ejemplos de código, ejecútelos desde la clase `ThisDocument` del proyecto.

### <a name="to-add-text-to-footers-in-the-document"></a>Para agregar texto a los pies de página en el documento

1. En el siguiente ejemplo de código se establece la fuente del texto que se va a insertar en el pie de página principal de cada sección del documento y, después, se inserta un texto en el pie de página.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet114":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet114":::

### <a name="to-add-text-to-headers-in-the-document"></a>Para agregar texto a los encabezados del documento

1. En el siguiente ejemplo de código se agrega un campo para mostrar el número de página en cada encabezado del documento y, después, se establece la alineación del párrafo para que el texto se alinee a la derecha del encabezado.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet116":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet116":::

## <a name="vsto-add-ins"></a>Complementos de VSTO
 Para usar los siguientes ejemplos de código, ejecútelos desde la clase `ThisAddIn` del proyecto.

### <a name="to-add-text-to-footers-in-a-document"></a>Para agregar texto a los pies de página de un documento

1. En el siguiente ejemplo de código se establece la fuente del texto que se va a insertar en el pie de página principal de cada sección del documento y, después, se inserta un texto en el pie de página. Este ejemplo de código usa el documento activo.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet114":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet114":::

### <a name="to-add-text-to-headers-in-the-document"></a>Para agregar texto a los encabezados del documento

1. En el siguiente ejemplo de código se agrega un campo para mostrar el número de página en cada encabezado del documento y, después, se establece la alineación del párrafo para que el texto se alinee a la derecha del encabezado. Este ejemplo de código usa el documento activo.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet116":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet116":::

## <a name="see-also"></a>Consulte también
- [Cómo: Crear nuevos documentos mediante programación](../vsto/how-to-programmatically-create-new-documents.md)
- [Cómo: Ampliar rangos en documentos mediante programación](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [Cómo: Recorrer en bucle los elementos encontrados en documentos mediante programación](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)
