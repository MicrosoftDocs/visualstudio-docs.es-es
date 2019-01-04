---
title: Procedimiento Mostrar documentos en vista previa de impresión mediante programación
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], displaying documents in print preview
- documents [Office development in Visual Studio], displaying in print preview
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 66a21f2def806dc7800caa01d26a989f9a4cf8e8
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53891950"
---
# <a name="how-to-programmatically-display-documents-in-print-preview"></a>Procedimiento Mostrar documentos en vista previa de impresión mediante programación
  Si una solución genera un informe, tal vez sea conveniente presentarlo al usuario en el modo Vista previa de impresión.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="procedures-for-document-level-customizations"></a>Procedimientos para las personalizaciones de nivel de documento  
  
### <a name="to-display-a-document-in-print-preview-by-calling-the-printpreview-method"></a>Para mostrar un documento en vista previa de impresión llamando al método PrintPreview  
  
1.  Llame al método <xref:Microsoft.Office.Tools.Word.Document.PrintPreview%2A> de la clase <xref:Microsoft.Office.Tools.Word.Document> . Para usar este ejemplo de código, ejecútelo desde la clase `ThisDocument` del proyecto.  
  
     [!code-vb[Trin_VstcoreWordAutomation#13](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#13)]
     [!code-csharp[Trin_VstcoreWordAutomation#13](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#13)]  
  
### <a name="to-display-a-document-in-print-preview-by-setting-the-printpreview-property"></a>Para mostrar un documento en vista previa de impresión llamando al método PrintPreview  
  
1.  Establezca la propiedad <xref:Microsoft.Office.Interop.Word._Application.PrintPreview%2A> del objeto <xref:Microsoft.Office.Interop.Word.Application> en **true**.  
  
     [!code-vb[Trin_VstcoreWordAutomation#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#14)]
     [!code-csharp[Trin_VstcoreWordAutomation#14](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#14)]  
  
## <a name="procedures-for-vsto-add-ins"></a>Procedimientos para los complementos de VSTO  
  
### <a name="to-display-a-document-in-print-preview-by-calling-the-printpreview-method"></a>Para mostrar un documento en vista previa de impresión llamando al método PrintPreview  
  
1.  Llame al método <xref:Microsoft.Office.Interop.Word._Document.PrintPreview%2A> del objeto <xref:Microsoft.Office.Interop.Word.Document> del que quiere obtener una vista previa. Para usar este ejemplo de código, ejecútelo desde la clase `ThisAddIn` del proyecto.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#13](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#13)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#13](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#13)]  
  
### <a name="to-display-a-document-in-print-preview-by-setting-the-printpreview-property"></a>Para mostrar un documento en vista previa de impresión llamando al método PrintPreview  
  
1.  Establezca la propiedad <xref:Microsoft.Office.Interop.Word._Application.PrintPreview%2A> del objeto <xref:Microsoft.Office.Interop.Word.Application> en **true**.  
  
     [!code-vb[Trin_VstcoreWordAutomation#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#14)]
     [!code-csharp[Trin_VstcoreWordAutomation#14](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#14)]  
  
## <a name="see-also"></a>Vea también  
 [Cómo: Imprimir documentos mediante programación](../vsto/how-to-programmatically-print-documents.md)   
 [Cómo: Abrir documentos existentes mediante programación](../vsto/how-to-programmatically-open-existing-documents.md)   
 [Cómo: Crear nuevos documentos mediante programación](../vsto/how-to-programmatically-create-new-documents.md)  
