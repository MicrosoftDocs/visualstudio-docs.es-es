---
title: 'Cómo: proteger elementos de documentos mediante controles de contenido'
description: Obtenga información sobre cómo puede usar Visual Studio para proteger partes de un documento de Microsoft Word mediante controles de contenido.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- restricted permissions [Office development in Visual Studio]
- partial document protection [Office development in Visual Studio]
- content controls [Office development in Visual Studio], protecting documents
- Word [Office development in Visual Studio], partial document protection
- document protection [Office development in Visual Studio]
- Word [Office development in Visual Studio], restricted permissions
- GroupContentControl
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 1dc962e372f4406fffb5cf8a6357f3826f0c8845
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99942261"
---
# <a name="how-to-protect-parts-of-documents-by-using-content-controls"></a>Cómo: proteger elementos de documentos mediante controles de contenido
  Al proteger un elemento de un documento, se impide que los usuarios cambien o eliminen el contenido de ese elemento. Existen varios modos de proteger los elementos de un documento de Microsoft Office Word mediante los controles de contenido:

- Puede proteger un control de contenido.

- Puede proteger un elemento de un documento que no está en un control de contenido.

  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="protect-a-content-control"></a><a name="EditDeleteControl"></a> Proteger un control de contenido
 Puede impedir que los usuarios editen o eliminen un control de contenido estableciendo las propiedades del control en un proyecto de nivel de documento en tiempo de diseño o en tiempo de ejecución.

 También puede proteger los controles de contenido que agregue a un documento en tiempo de ejecución mediante un proyecto de complemento de VSTO. Para obtener más información, vea [Cómo: agregar controles de contenido a documentos de Word](../vsto/how-to-add-content-controls-to-word-documents.md).

### <a name="to-protect-a-content-control-at-design-time"></a>Para proteger un control de contenido en tiempo de diseño

1. En el documento que se hospeda en el diseñador de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], seleccione el control de contenido que desea proteger.

2. En la ventana **propiedades** , establezca una o las dos propiedades siguientes:

    - Para evitar que los usuarios editen el control, establezca **LockContents** en **true**.

    - Para evitar que los usuarios eliminen el control, establezca **LockContentControl** en **true**.

3. Haga clic en **OK**.

### <a name="to-protect-a-content-control-at-run-time"></a>Para proteger un control de contenido en tiempo de ejecución

1. Establezca la `LockContents` propiedad del control de contenido en **true** para evitar que los usuarios editen el control y establezca la `LockContentControl` propiedad en **true** para evitar que los usuarios eliminen el control.

     En el siguiente ejemplo de código se muestra cómo usar las propiedades <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContents%2A> y <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContentControl%2A> de dos objetos <xref:Microsoft.Office.Tools.Word.RichTextContentControl> diferentes en un proyecto de nivel de documento. Para ejecutar este código, agregue el código a la clase `ThisDocument` del proyecto y llame al método `AddProtectedContentControls` desde el controlador de eventos `ThisDocument_Startup` .

     [!code-csharp[Trin_ContentControlHowToProtect#2](../vsto/codesnippet/CSharp/Trin_ContentControlHowToProtect/ThisDocument.cs#2)]
     [!code-vb[Trin_ContentControlHowToProtect#2](../vsto/codesnippet/VisualBasic/Trin_ContentControlHowToProtect/ThisDocument.vb#2)]

     En el siguiente ejemplo de código se muestra cómo usar las propiedades <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContents%2A> y <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContentControl%2A> de dos objetos <xref:Microsoft.Office.Tools.Word.RichTextContentControl> diferentes en un proyecto de complemento de VSTO. Para ejecutar este código, agregue el código a la clase `ThisAddIn` del proyecto y llame al método `AddProtectedContentControls` desde el controlador de eventos `ThisAddIn_Startup` .

     [!code-vb[Trin_WordAddInDynamicControls#14](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#14)]
     [!code-csharp[Trin_WordAddInDynamicControls#14](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#14)]

## <a name="protect-a-part-of-a-document-that-is-not-in-a-content-control"></a>Proteger una parte de un documento que no está en un control de contenido
 Puede impedir que los usuarios cambien un área de un documento colocándola en un <xref:Microsoft.Office.Tools.Word.GroupContentControl>. Esto es útil en los siguientes escenarios:

- Desea proteger un área que no contiene controles de contenido.

- Desea proteger un área que ya contiene controles de contenido, pero el texto u otros elementos que desea proteger no se encuentran en los controles de contenido.

> [!NOTE]
> Si crea un <xref:Microsoft.Office.Tools.Word.GroupContentControl> que contiene controles de contenido insertados, estos controles no se protegerán automáticamente. Para evitar que los usuarios editen un control de contenido incrustado, use la propiedad **LockContents** del control.

### <a name="to-protect-an-area-of-a-document-at-design-time"></a>Para proteger un área de un documento en tiempo de diseño

1. En el documento que se hospeda en el diseñador de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], seleccione el área que desea proteger.

2. En la cinta de opciones, haga clic en la pestaña **Desarrollador** .

    > [!NOTE]
    > Si la pestaña **Desarrollador** no está visible, primero debe mostrarla. Para obtener más información, consulte [Cómo: Mostrar la pestaña programador en la cinta de opciones](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

3. En el grupo **controles** , haga clic en el botón desplegable **Grupo** y, a continuación, haga clic en **Grupo**.

     Se genera automáticamente un <xref:Microsoft.Office.Tools.Word.GroupContentControl> que contiene la región protegida en la clase `ThisDocument` de su proyecto. Un borde que representa el control de grupo está visible en tiempo de diseño, pero no hay ningún borde visible en tiempo de ejecución.

### <a name="to-protect-an-area-of-a-document-at-run-time"></a>Para proteger un área de un documento en tiempo de ejecución

1. Seleccione el área que desea proteger mediante programación y, a continuación, llame al método <xref:Microsoft.Office.Tools.Word.ControlCollection.AddGroupContentControl%2A> para crear un <xref:Microsoft.Office.Tools.Word.GroupContentControl>.

     El siguiente ejemplo de código para un proyecto de nivel de documento agrega texto al primer párrafo del documento, selecciona el primer párrafo y, a continuación, crea una instancia de un <xref:Microsoft.Office.Tools.Word.GroupContentControl>. Para ejecutar este código, agregue el código a la clase `ThisDocument` del proyecto y llame al método `ProtectFirstParagraph` desde el controlador de eventos `ThisDocument_Startup` .

     [!code-csharp[Trin_ContentControlHowToProtect#1](../vsto/codesnippet/CSharp/Trin_ContentControlHowToProtect/ThisDocument.cs#1)]
     [!code-vb[Trin_ContentControlHowToProtect#1](../vsto/codesnippet/VisualBasic/Trin_ContentControlHowToProtect/ThisDocument.vb#1)]

     El siguiente ejemplo de código para un proyecto de complemento de VSTO agrega texto al primer párrafo del documento activo, selecciona el primer párrafo y, a continuación, crea una instancia de un <xref:Microsoft.Office.Tools.Word.GroupContentControl>. Para ejecutar este código, agregue el código a la clase `ThisAddIn` del proyecto y llame al método `ProtectFirstParagraph` desde el controlador de eventos `ThisAddIn_Startup` .

     [!code-vb[Trin_WordAddInDynamicControls#15](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#15)]
     [!code-csharp[Trin_WordAddInDynamicControls#15](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#15)]

## <a name="see-also"></a>Vea también
- [Automatizar Word con objetos extendidos](../vsto/automating-word-by-using-extended-objects.md)
- [Controles de contenido](../vsto/content-controls.md)
- [Cómo: agregar controles de contenido a documentos de Word](../vsto/how-to-add-content-controls-to-word-documents.md)
- [Información general sobre elementos y controles host](../vsto/host-items-and-host-controls-overview.md)
- [Limitaciones de programación de elementos y controles host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md)
