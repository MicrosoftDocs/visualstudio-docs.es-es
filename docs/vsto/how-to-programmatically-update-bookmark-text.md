---
title: 'Cómo: Actualizar texto de marcador mediante programación'
description: Obtenga información sobre cómo puede usar Visual Studio insertar texto mediante programación en un marcador de posición en un documento de Microsoft Word.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- bookmarks, updating text
- text [Office development in Visual Studio], updating in bookmarks
- Bookmark control, updating contents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: f67dbbe4d1d5c24d617f9cbc49a58ec2d134e90b
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826205"
---
# <a name="how-to-programmatically-update-bookmark-text"></a>Cómo: Actualizar texto de marcador mediante programación
  Puede insertar texto en un marcador de marcador de posición de un documento de Microsoft Office Word para poder recuperar el texto posteriormente o reemplazar el texto de un marcador. Si está desarrollando una personalización de nivel de documento, también puede actualizar el texto de un control <xref:Microsoft.Office.Tools.Word.Bookmark> que está enlazado a datos. Para obtener más información, vea [Enlazar datos a controles en soluciones de Office.](../vsto/binding-data-to-controls-in-office-solutions.md)

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 El objeto de marcador puede ser de uno de los dos tipos indicados a continuación:

- Un control host <xref:Microsoft.Office.Tools.Word.Bookmark>.

   Los controles <xref:Microsoft.Office.Tools.Word.Bookmark> amplían los objetos nativos <xref:Microsoft.Office.Interop.Word.Bookmark> habilitando el enlace de datos y exponiendo los eventos. Para obtener más información sobre los controles host, vea [Host items and host controls overview](../vsto/host-items-and-host-controls-overview.md).

- Un objeto <xref:Microsoft.Office.Interop.Word.Bookmark> nativo.

   Los objetos <xref:Microsoft.Office.Interop.Word.Bookmark> no tienen funcionalidad de enlace de datos o eventos.

  Cuando se asigna texto a un marcador, el comportamiento de los objetos <xref:Microsoft.Office.Interop.Word.Bookmark> y <xref:Microsoft.Office.Tools.Word.Bookmark> es diferente. Para obtener más información, vea [Bookmark control](../vsto/bookmark-control.md).

## <a name="use-host-controls"></a>Uso de controles host

### <a name="to-update-bookmark-contents-using-a-bookmark-control"></a>Para actualizar el contenido del marcador usando un control Bookmark

1. Cree un procedimiento que tome un argumento `bookmark` para el nombre del marcador y un argumento `newText` para la cadena que se va a asignar a la propiedad <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A>.

    > [!NOTE]
    > Asignar texto a la propiedad <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> o <xref:Microsoft.Office.Tools.Word.Bookmark.FormattedText%2A> de un control <xref:Microsoft.Office.Tools.Word.Bookmark> no hace que se elimine el marcador.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet63":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet63":::

2. Asigne la *cadena newText* a la <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> propiedad de <xref:Microsoft.Office.Tools.Word.Bookmark> .

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet64":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet64":::

## <a name="use-word-objects"></a>Uso de objetos de Word

### <a name="to-update-bookmark-contents-using-a-word-bookmark-object"></a>Para actualizar el contenido del marcador usando un objeto Bookmark de Word

1. Cree un procedimiento que tenga un argumento `bookmark` para el nombre del objeto <xref:Microsoft.Office.Interop.Word.Bookmark> y un argumento `newText` para la cadena que se va a asignar a la propiedad <xref:Microsoft.Office.Interop.Word.Range.Text%2A> del marcador.

    > [!NOTE]
    > Si se asigna texto a un objeto <xref:Microsoft.Office.Interop.Word.Bookmark> nativo de Word, se elimina el marcador.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet65":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet65":::

2. Asigne la *cadena newText* a <xref:Microsoft.Office.Interop.Word.Range.Text%2A> la propiedad del marcador, que elimina automáticamente el marcador. A continuación, vuelva a agregar el marcador a la colección <xref:Microsoft.Office.Interop.Word.Bookmarks>.

     El siguiente ejemplo de código se puede usar en una personalización de nivel de documento.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet66":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet66":::

     El siguiente ejemplo de código se puede usar en un complemento de VSTO. En este ejemplo se usa el documento activo.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet66":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet66":::

## <a name="see-also"></a>Consulte también
- [Cómo: Insertar texto mediante programación en documentos de Word](../vsto/how-to-programmatically-insert-text-into-word-documents.md)
- [Introducción al modelo de objetos de Word](../vsto/word-object-model-overview.md)
- [Bookmark (control)](../vsto/bookmark-control.md)
