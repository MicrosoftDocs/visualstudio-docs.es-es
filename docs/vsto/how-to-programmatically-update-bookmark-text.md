---
title: "Cómo: actualizar mediante programación el texto de marcador | Documentos de Microsoft"
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
- bookmarks, updating text
- text [Office development in Visual Studio], updating in bookmarks
- Bookmark control, updating contents
ms.assetid: 2324164d-2538-4695-9aaf-7285ce403be3
caps.latest.revision: "46"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ee78ad2aac4ff9cefcb3291d3b1b2010d8a1c26c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-update-bookmark-text"></a>Cómo: Actualizar texto de marcador mediante programación
  Puede insertar texto en un marcador de marcador de posición de un documento de Microsoft Office Word para poder recuperar el texto posteriormente o reemplazar el texto de un marcador. Si está desarrollando una personalización de nivel de documento, también puede actualizar el texto de un control <xref:Microsoft.Office.Tools.Word.Bookmark> que está enlazado a datos. Para obtener más información, consulte [enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 El objeto de marcador puede ser de uno de los dos tipos indicados a continuación:  
  
-   Un control host <xref:Microsoft.Office.Tools.Word.Bookmark>.  
  
     Los controles <xref:Microsoft.Office.Tools.Word.Bookmark> amplían los objetos nativos <xref:Microsoft.Office.Interop.Word.Bookmark> habilitando el enlace de datos y exponiendo los eventos. Para más información sobre los controles host, consulte [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md).  
  
-   Un objeto <xref:Microsoft.Office.Interop.Word.Bookmark> nativo.  
  
     Los objetos <xref:Microsoft.Office.Interop.Word.Bookmark> no tienen funcionalidad de enlace de datos o eventos.  
  
 Cuando se asigna texto a un marcador, el comportamiento de los objetos <xref:Microsoft.Office.Interop.Word.Bookmark> y <xref:Microsoft.Office.Tools.Word.Bookmark> es diferente. Para obtener más información, consulta [Bookmark Control](../vsto/bookmark-control.md).  
  
## <a name="using-host-controls"></a>Usar controles host  
  
#### <a name="to-update-bookmark-contents-using-a-bookmark-control"></a>Para actualizar el contenido del marcador usando un control Bookmark  
  
1.  Cree un procedimiento que tome un argumento `bookmark` para el nombre del marcador y un argumento `newText` para la cadena que se va a asignar a la propiedad <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A>.  
  
    > [!NOTE]  
    >  Asignar texto a la propiedad <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> o <xref:Microsoft.Office.Tools.Word.Bookmark.FormattedText%2A> de un control <xref:Microsoft.Office.Tools.Word.Bookmark> no hace que se elimine el marcador.  
  
     [!code-vb[Trin_VstcoreWordAutomation#63](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#63)]
     [!code-csharp[Trin_VstcoreWordAutomation#63](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#63)]  
  
2.  Asigne el *TextoNuevo* de cadena para el <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> propiedad de la <xref:Microsoft.Office.Tools.Word.Bookmark>.  
  
     [!code-vb[Trin_VstcoreWordAutomation#64](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#64)]
     [!code-csharp[Trin_VstcoreWordAutomation#64](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#64)]  
  
## <a name="using-word-objects"></a>Usar objetos de Word  
  
#### <a name="to-update-bookmark-contents-using-a-word-bookmark-object"></a>Para actualizar el contenido del marcador usando un objeto Bookmark de Word  
  
1.  Cree un procedimiento que tenga un argumento `bookmark` para el nombre del objeto <xref:Microsoft.Office.Interop.Word.Bookmark> y un argumento `newText` para la cadena que se va a asignar a la propiedad <xref:Microsoft.Office.Interop.Word.Range.Text%2A> del marcador.  
  
    > [!NOTE]  
    >  Si se asigna texto a un objeto <xref:Microsoft.Office.Interop.Word.Bookmark> nativo de Word, se elimina el marcador.  
  
     [!code-vb[Trin_VstcoreWordAutomation#65](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#65)]
     [!code-csharp[Trin_VstcoreWordAutomation#65](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#65)]  
  
2.  Asigne el *TextoNuevo* de cadena para el <xref:Microsoft.Office.Interop.Word.Range.Text%2A> propiedad del marcador, lo cual elimina automáticamente el marcador. A continuación, vuelva a agregar el marcador a la colección <xref:Microsoft.Office.Interop.Word.Bookmarks>.  
  
     El siguiente ejemplo de código se puede usar en una personalización de nivel de documento.  
  
     [!code-vb[Trin_VstcoreWordAutomation#66](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#66)]
     [!code-csharp[Trin_VstcoreWordAutomation#66](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#66)]  
  
     El siguiente ejemplo de código se puede usar en un complemento de VSTO. En este ejemplo se usa el documento activo.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#66](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#66)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#66](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#66)]  
  
## <a name="see-also"></a>Vea también  
 [Cómo: insertar texto en documentos de Word mediante programación](../vsto/how-to-programmatically-insert-text-into-word-documents.md)   
 [Información general sobre el modelo de objetos de Word](../vsto/word-object-model-overview.md)   
 [Bookmark (Control)](../vsto/bookmark-control.md)  
  
  