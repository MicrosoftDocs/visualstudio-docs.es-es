---
title: 'Cómo: actualizar texto de marcador mediante programación'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- bookmarks, updating text
- text [Office development in Visual Studio], updating in bookmarks
- Bookmark control, updating contents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: efa56c94e211a40e314025ae06d263164de1afd7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49833023"
---
# <a name="how-to-programmatically-update-bookmark-text"></a>Cómo: actualizar texto de marcador mediante programación
  Puede insertar texto en un marcador de marcador de posición de un documento de Microsoft Office Word para poder recuperar el texto posteriormente o reemplazar el texto de un marcador. Si está desarrollando una personalización de nivel de documento, también puede actualizar el texto de un control <xref:Microsoft.Office.Tools.Word.Bookmark> que está enlazado a datos. Para obtener más información, consulte [enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 El objeto de marcador puede ser de uno de los dos tipos indicados a continuación:  
  
- Un control host <xref:Microsoft.Office.Tools.Word.Bookmark>.  
  
   Los controles <xref:Microsoft.Office.Tools.Word.Bookmark> amplían los objetos nativos <xref:Microsoft.Office.Interop.Word.Bookmark> habilitando el enlace de datos y exponiendo los eventos. Para obtener más información acerca de los controles host, consulte [elementos Host y hospedar información general sobre controles](../vsto/host-items-and-host-controls-overview.md).  
  
- Un objeto <xref:Microsoft.Office.Interop.Word.Bookmark> nativo.  
  
   Los objetos <xref:Microsoft.Office.Interop.Word.Bookmark> no tienen funcionalidad de enlace de datos o eventos.  
  
  Cuando se asigna texto a un marcador, el comportamiento de los objetos <xref:Microsoft.Office.Interop.Word.Bookmark> y <xref:Microsoft.Office.Tools.Word.Bookmark> es diferente. Para obtener más información, consulte [Bookmark (control)](../vsto/bookmark-control.md).  
  
## <a name="use-host-controls"></a>Usar controles de host  
  
### <a name="to-update-bookmark-contents-using-a-bookmark-control"></a>Para actualizar el contenido del marcador usando un control Bookmark  
  
1.  Cree un procedimiento que tome un argumento `bookmark` para el nombre del marcador y un argumento `newText` para la cadena que se va a asignar a la propiedad <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A>.  
  
    > [!NOTE]  
    >  Asignar texto a la propiedad <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> o <xref:Microsoft.Office.Tools.Word.Bookmark.FormattedText%2A> de un control <xref:Microsoft.Office.Tools.Word.Bookmark> no hace que se elimine el marcador.  
  
     [!code-vb[Trin_VstcoreWordAutomation#63](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#63)]
     [!code-csharp[Trin_VstcoreWordAutomation#63](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#63)]  
  
2.  Asignar el *newText* de string a la <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> propiedad de la <xref:Microsoft.Office.Tools.Word.Bookmark>.  
  
     [!code-vb[Trin_VstcoreWordAutomation#64](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#64)]
     [!code-csharp[Trin_VstcoreWordAutomation#64](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#64)]  
  
## <a name="use-word-objects"></a>Usar objetos de Word  
  
### <a name="to-update-bookmark-contents-using-a-word-bookmark-object"></a>Para actualizar el contenido del marcador usando un objeto Bookmark de Word  
  
1.  Cree un procedimiento que tenga un argumento `bookmark` para el nombre del objeto <xref:Microsoft.Office.Interop.Word.Bookmark> y un argumento `newText` para la cadena que se va a asignar a la propiedad <xref:Microsoft.Office.Interop.Word.Range.Text%2A> del marcador.  
  
    > [!NOTE]  
    >  Si se asigna texto a un objeto <xref:Microsoft.Office.Interop.Word.Bookmark> nativo de Word, se elimina el marcador.  
  
     [!code-vb[Trin_VstcoreWordAutomation#65](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#65)]
     [!code-csharp[Trin_VstcoreWordAutomation#65](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#65)]  
  
2.  Asignar el *newText* de string a la <xref:Microsoft.Office.Interop.Word.Range.Text%2A> propiedades del marcador, lo cual elimina automáticamente el marcador. A continuación, vuelva a agregar el marcador a la colección <xref:Microsoft.Office.Interop.Word.Bookmarks>.  
  
     El siguiente ejemplo de código se puede usar en una personalización de nivel de documento.  
  
     [!code-vb[Trin_VstcoreWordAutomation#66](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#66)]
     [!code-csharp[Trin_VstcoreWordAutomation#66](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#66)]  
  
     El siguiente ejemplo de código se puede usar en un complemento de VSTO. En este ejemplo se usa el documento activo.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#66](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#66)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#66](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#66)]  
  
## <a name="see-also"></a>Vea también  
 [Cómo: insertar texto en documentos de Word mediante programación](../vsto/how-to-programmatically-insert-text-into-word-documents.md)   
 [Información general sobre el modelo de objetos de Word](../vsto/word-object-model-overview.md)   
 [Bookmark (control)](../vsto/bookmark-control.md)  
  
  