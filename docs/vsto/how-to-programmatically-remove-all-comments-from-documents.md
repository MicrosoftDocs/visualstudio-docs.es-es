---
title: 'Cómo: quitar todos los comentarios de documentos mediante programación'
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
ms.openlocfilehash: 005414fce7b7bc04c22b266f5f5f6d54a399a182
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2018
ms.locfileid: "35674852"
---
# <a name="how-to-programmatically-remove-all-comments-from-documents"></a>Cómo: quitar todos los comentarios de documentos mediante programación
  Use el `DeleteAllComments` método para quitar todos los comentarios de un documento de Microsoft Office Word.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="to-remove-all-comments-from-a-document-that-is-part-of-a-document-level-customization"></a>Para quitar todos los comentarios de un documento que forma parte de una personalización de nivel de documento  
  
1.  Llame al método <xref:Microsoft.Office.Tools.Word.Document.DeleteAllComments%2A> de la clase `ThisDocument` en su proyecto. Para usar este ejemplo de código, ejecútelo desde la clase `ThisDocument` .  
  
     [!code-vb[Trin_VstcoreWordAutomation#119](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#119)]
     [!code-csharp[Trin_VstcoreWordAutomation#119](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#119)]  
  
## <a name="to-remove-all-comments-from-a-document-by-using-a-vsto-add-in"></a>Para quitar todos los comentarios de un documento mediante el uso de un complemento de VSTO  
  
1.  Llame al método <xref:Microsoft.Office.Interop.Word._Document.DeleteAllComments%2A> del <xref:Microsoft.Office.Interop.Word.Document> del que quiere quitar los comentarios.  
  
     El ejemplo de código siguiente quita todos los comentarios del documento activo. Para usar este ejemplo de código, ejecútelo desde la clase `ThisAddIn` del proyecto.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#119](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#119)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#119](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#119)]  
  
## <a name="see-also"></a>Vea también  
 [Cómo: agregar comentarios al texto en documentos mediante programación](../vsto/how-to-programmatically-add-comments-to-text-in-documents.md)   
 [Elemento host Document](../vsto/document-host-item.md)  
  
  