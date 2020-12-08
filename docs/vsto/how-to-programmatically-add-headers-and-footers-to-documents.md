---
title: 'Cómo: agregar encabezados y pies de página a documentos mediante programación'
description: Obtenga información sobre cómo puede Agregar texto a los encabezados y pies de página del documento mediante la propiedad headers y Footers de la sección.
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1abf9c0726a6b4afd1764aec095f129a4fcaf510
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/08/2020
ms.locfileid: "96844523"
---
# <a name="how-to-programmatically-add-headers-and-footers-to-documents"></a>Cómo: agregar encabezados y pies de página a documentos mediante programación
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

     [!code-vb[Trin_VstcoreWordAutomation#114](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#114)]
     [!code-csharp[Trin_VstcoreWordAutomation#114](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#114)]

### <a name="to-add-text-to-headers-in-the-document"></a>Para agregar texto a los encabezados del documento

1. En el siguiente ejemplo de código se agrega un campo para mostrar el número de página en cada encabezado del documento y, después, se establece la alineación del párrafo para que el texto se alinee a la derecha del encabezado.

     [!code-vb[Trin_VstcoreWordAutomation#116](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#116)]
     [!code-csharp[Trin_VstcoreWordAutomation#116](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#116)]

## <a name="vsto-add-ins"></a>Complementos de VSTO
 Para usar los siguientes ejemplos de código, ejecútelos desde la clase `ThisAddIn` del proyecto.

### <a name="to-add-text-to-footers-in-a-document"></a>Para agregar texto a los pies de página de un documento

1. En el siguiente ejemplo de código se establece la fuente del texto que se va a insertar en el pie de página principal de cada sección del documento y, después, se inserta un texto en el pie de página. Este ejemplo de código usa el documento activo.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#114](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#114)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#114](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#114)]

### <a name="to-add-text-to-headers-in-the-document"></a>Para agregar texto a los encabezados del documento

1. En el siguiente ejemplo de código se agrega un campo para mostrar el número de página en cada encabezado del documento y, después, se establece la alineación del párrafo para que el texto se alinee a la derecha del encabezado. Este ejemplo de código usa el documento activo.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#116](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#116)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#116](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#116)]

## <a name="see-also"></a>Vea también
- [Cómo: crear nuevos documentos mediante programación](../vsto/how-to-programmatically-create-new-documents.md)
- [Cómo: ampliar intervalos en documentos mediante programación](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [Cómo: recorrer los elementos encontrados en documentos mediante programación](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)
