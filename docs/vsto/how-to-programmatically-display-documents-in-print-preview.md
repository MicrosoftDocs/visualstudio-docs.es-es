---
title: 'Cómo: mostrar documentos en vista previa de impresión mediante programación'
description: Obtenga información sobre cómo puede mostrar documentos mediante programación en la vista previa de impresión en un documento de Microsoft Word.
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
ms.openlocfilehash: 14005f465fd4394e86450017530de457a97b3d4f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885552"
---
# <a name="how-to-programmatically-display-documents-in-print-preview"></a>Cómo: mostrar documentos en vista previa de impresión mediante programación
  Si una solución genera un informe, tal vez sea conveniente presentarlo al usuario en el modo Vista previa de impresión.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="procedures-for-document-level-customizations"></a>Procedimientos para las personalizaciones de nivel de documento

### <a name="to-display-a-document-in-print-preview-by-calling-the-printpreview-method"></a>Para mostrar un documento en vista previa de impresión llamando al método PrintPreview

1. Llame al método <xref:Microsoft.Office.Tools.Word.Document.PrintPreview%2A> de la clase <xref:Microsoft.Office.Tools.Word.Document> . Para usar este ejemplo de código, ejecútelo desde la clase `ThisDocument` del proyecto.

     [!code-vb[Trin_VstcoreWordAutomation#13](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#13)]
     [!code-csharp[Trin_VstcoreWordAutomation#13](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#13)]

### <a name="to-display-a-document-in-print-preview-by-setting-the-printpreview-property"></a>Para mostrar un documento en vista previa de impresión llamando al método PrintPreview

1. Establezca la propiedad <xref:Microsoft.Office.Interop.Word._Application.PrintPreview%2A> del objeto <xref:Microsoft.Office.Interop.Word.Application> en **true**.

     [!code-vb[Trin_VstcoreWordAutomation#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#14)]
     [!code-csharp[Trin_VstcoreWordAutomation#14](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#14)]

## <a name="procedures-for-vsto-add-ins"></a>Procedimientos para los complementos de VSTO

### <a name="to-display-a-document-in-print-preview-by-calling-the-printpreview-method"></a>Para mostrar un documento en vista previa de impresión llamando al método PrintPreview

1. Llame al método <xref:Microsoft.Office.Interop.Word._Document.PrintPreview%2A> del objeto <xref:Microsoft.Office.Interop.Word.Document> del que quiere obtener una vista previa. Para usar este ejemplo de código, ejecútelo desde la clase `ThisAddIn` del proyecto.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#13](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#13)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#13](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#13)]

### <a name="to-display-a-document-in-print-preview-by-setting-the-printpreview-property"></a>Para mostrar un documento en vista previa de impresión llamando al método PrintPreview

1. Establezca la propiedad <xref:Microsoft.Office.Interop.Word._Application.PrintPreview%2A> del objeto <xref:Microsoft.Office.Interop.Word.Application> en **true**.

     [!code-vb[Trin_VstcoreWordAutomation#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#14)]
     [!code-csharp[Trin_VstcoreWordAutomation#14](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#14)]

## <a name="see-also"></a>Vea también
- [Cómo: imprimir documentos mediante programación](../vsto/how-to-programmatically-print-documents.md)
- [Cómo: abrir documentos existentes mediante programación](../vsto/how-to-programmatically-open-existing-documents.md)
- [Cómo: crear nuevos documentos mediante programación](../vsto/how-to-programmatically-create-new-documents.md)
