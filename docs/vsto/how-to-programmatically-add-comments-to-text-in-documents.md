---
title: "Cómo: agregar comentarios al texto en documentos mediante programación | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- comments, adding to documents
- documents [Office development in Visual Studio], adding comments
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 2702d8aed4dce16a2dde1c42b2b1410ebded14e3
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-add-comments-to-text-in-documents"></a>Cómo: Agregar comentarios al texto en documentos mediante programación
  La propiedad de comentarios de la clase de documento, agrega un comentario a un intervalo de texto en un documento de Microsoft Office Word.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 En el siguiente ejemplo se agrega un comentario al primer párrafo del documento.  
  
### <a name="to-add-a-new-comment-to-text-in-a-document-level-customization"></a>Agregar un nuevo comentario al texto en una personalización de nivel de documento  
  
1.  Llame al método <xref:Microsoft.Office.Interop.Word.Comments.Add%2A> de la propiedad <xref:Microsoft.Office.Tools.Word.Document.Comments%2A> y proporcione un intervalo y el texto del comentario. Para usar el siguiente ejemplo de código, ejecútelo desde la clase `ThisDocument` del proyecto.  
  
     [!code-vb[Trin_VstcoreWordAutomation#118](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#118)]
     [!code-csharp[Trin_VstcoreWordAutomation#118](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#118)]  
  
### <a name="to-add-a-new-comment-to-text-in-an-vsto-add-in"></a>Agregar un nuevo comentario al texto en un complemento VSTO  
  
1.  Llame al método <xref:Microsoft.Office.Interop.Word.Comments.Add%2A> de la propiedad <xref:Microsoft.Office.Interop.Word._Document.Comments%2A> y proporcione un intervalo y el texto del comentario.  
  
     En el ejemplo de código siguiente se agrega un comentario al documento activo. Para usar este ejemplo, ejecútelo desde la clase `ThisAddIn` del proyecto.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#118](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#118)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#118](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#118)]  
  
## <a name="robust-programming"></a>Programación sólida  
 Para cambiar las iniciales del usuario que Word agrega a los comentarios, use la propiedad <xref:Microsoft.Office.Interop.Word._Application.UserInitials%2A> .  
  
## <a name="see-also"></a>Vea también  
 [Cómo: quitar todos los comentarios de documentos mediante programación](../vsto/how-to-programmatically-remove-all-comments-from-documents.md)   
 [Elemento host de documento](../vsto/document-host-item.md)  
  
  