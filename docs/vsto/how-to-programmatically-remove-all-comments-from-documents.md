---
title: 'Cómo: quitar todos los comentarios de documentos mediante programación | Documentos de Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], removing comments
- comments, removing from documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 19c713356a8949261524eda9f44fee8fae9f9f21
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-remove-all-comments-from-documents"></a>Cómo: Quitar todos los comentarios de documentos mediante programación
  Utilice el método DeleteAllComments para quitar todos los comentarios de un documento de Microsoft Office Word.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### <a name="to-remove-all-comments-from-a-document-that-is-part-of-a-document-level-customization"></a>Para quitar todos los comentarios de un documento que forma parte de una personalización de nivel de documento  
  
1.  Llame al método <xref:Microsoft.Office.Tools.Word.Document.DeleteAllComments%2A> de la clase `ThisDocument` en su proyecto. Para usar este ejemplo de código, ejecútelo desde la clase `ThisDocument` .  
  
     [!code-vb[Trin_VstcoreWordAutomation#119](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#119)]
     [!code-csharp[Trin_VstcoreWordAutomation#119](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#119)]  
  
### <a name="to-remove-all-comments-from-a-document-by-using-an-vsto-add-in"></a>Para quitar todos los comentarios de un documento mediante un complemento de VSTO  
  
1.  Llame al método <xref:Microsoft.Office.Interop.Word._Document.DeleteAllComments%2A> del <xref:Microsoft.Office.Interop.Word.Document> del que quiere quitar los comentarios.  
  
     El ejemplo de código siguiente quita todos los comentarios del documento activo. Para usar este ejemplo de código, ejecútelo desde la clase `ThisAddIn` del proyecto.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#119](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#119)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#119](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#119)]  
  
## <a name="see-also"></a>Vea también  
 [Cómo: agregar comentarios al texto en documentos mediante programación](../vsto/how-to-programmatically-add-comments-to-text-in-documents.md)   
 [Elemento host de documento](../vsto/document-host-item.md)  
  
  