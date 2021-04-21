---
title: 'Cómo: Mostrar documentos mediante programación en la vista previa de impresión'
description: Obtenga información sobre cómo puede mostrar documentos mediante programación en vista previa de impresión en un documento de Microsoft Word.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], displaying documents in print preview
- documents [Office development in Visual Studio], displaying in print preview
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 90979fbc7cd0b46329b8d9e9bc142e8cf0066db0
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825893"
---
# <a name="how-to-programmatically-display-documents-in-print-preview"></a>Cómo: Mostrar documentos mediante programación en la vista previa de impresión
  Si una solución genera un informe, tal vez sea conveniente presentarlo al usuario en el modo Vista previa de impresión.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="procedures-for-document-level-customizations"></a>Procedimientos para personalizaciones de nivel de documento

### <a name="to-display-a-document-in-print-preview-by-calling-the-printpreview-method"></a>Para mostrar un documento en vista previa de impresión llamando al método PrintPreview

1. Llame al método <xref:Microsoft.Office.Tools.Word.Document.PrintPreview%2A> de la clase <xref:Microsoft.Office.Tools.Word.Document> . Para usar este ejemplo de código, ejecútelo desde la clase `ThisDocument` del proyecto.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet13":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet13":::

### <a name="to-display-a-document-in-print-preview-by-setting-the-printpreview-property"></a>Para mostrar un documento en vista previa de impresión llamando al método PrintPreview

1. Establezca la propiedad <xref:Microsoft.Office.Interop.Word._Application.PrintPreview%2A> del objeto <xref:Microsoft.Office.Interop.Word.Application> en **true**.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet14":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet14":::

## <a name="procedures-for-vsto-add-ins"></a>Procedimientos para los complementos de VSTO

### <a name="to-display-a-document-in-print-preview-by-calling-the-printpreview-method"></a>Para mostrar un documento en vista previa de impresión llamando al método PrintPreview

1. Llame al método <xref:Microsoft.Office.Interop.Word._Document.PrintPreview%2A> del objeto <xref:Microsoft.Office.Interop.Word.Document> del que quiere obtener una vista previa. Para usar este ejemplo de código, ejecútelo desde la clase `ThisAddIn` del proyecto.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet13":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet13":::

### <a name="to-display-a-document-in-print-preview-by-setting-the-printpreview-property"></a>Para mostrar un documento en vista previa de impresión llamando al método PrintPreview

1. Establezca la propiedad <xref:Microsoft.Office.Interop.Word._Application.PrintPreview%2A> del objeto <xref:Microsoft.Office.Interop.Word.Application> en **true**.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet14":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet14":::

## <a name="see-also"></a>Consulte también
- [Cómo: Imprimir documentos mediante programación](../vsto/how-to-programmatically-print-documents.md)
- [Cómo: Abrir documentos existentes mediante programación](../vsto/how-to-programmatically-open-existing-documents.md)
- [Cómo: Crear nuevos documentos mediante programación](../vsto/how-to-programmatically-create-new-documents.md)
