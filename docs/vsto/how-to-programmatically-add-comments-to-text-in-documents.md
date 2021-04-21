---
title: 'Cómo: Agregar comentarios a texto en documentos mediante programación'
description: Agregue comentarios a texto en documentos mediante programación. La propiedad Comments de la clase Document agrega un comentario a un intervalo de texto en un documento de Microsoft Word.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- comments, adding to documents
- documents [Office development in Visual Studio], adding comments
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 4e03f189f2236131308b8f9ea5d90c52ffa3147d
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825828"
---
# <a name="how-to-programmatically-add-comments-to-text-in-documents"></a>Cómo: Agregar comentarios a texto en documentos mediante programación
  La propiedad Comments de la clase Document agrega un comentario a un intervalo de texto en un Microsoft Office Word.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 En el siguiente ejemplo se agrega un comentario al primer párrafo del documento.

## <a name="to-add-a-new-comment-to-text-in-a-document-level-customization"></a>Agregar un nuevo comentario al texto en una personalización de nivel de documento

1. Llame al método <xref:Microsoft.Office.Interop.Word.Comments.Add%2A> de la propiedad <xref:Microsoft.Office.Tools.Word.Document.Comments%2A> y proporcione un intervalo y el texto del comentario. Para usar el siguiente ejemplo de código, ejecútelo desde la clase `ThisDocument` del proyecto.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet118":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet118":::

## <a name="to-add-a-new-comment-to-text-in-a-vsto-add-in"></a>Para agregar un nuevo comentario al texto en un complemento de VSTO

1. Llame al método <xref:Microsoft.Office.Interop.Word.Comments.Add%2A> de la propiedad <xref:Microsoft.Office.Interop.Word._Document.Comments%2A> y proporcione un intervalo y el texto del comentario.

     En el ejemplo de código siguiente se agrega un comentario al documento activo. Para usar este ejemplo, ejecútelo desde la clase `ThisAddIn` del proyecto.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet118":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet118":::

## <a name="robust-programming"></a>Programación sólida
 Para cambiar las iniciales del usuario que Word agrega a los comentarios, use la propiedad <xref:Microsoft.Office.Interop.Word._Application.UserInitials%2A> .

## <a name="see-also"></a>Consulte también
- [Cómo: Quitar todos los comentarios de documentos mediante programación](../vsto/how-to-programmatically-remove-all-comments-from-documents.md)
- [Elemento host de documento](../vsto/document-host-item.md)
