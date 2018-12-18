---
title: 'Cómo: proteger elementos de documentos mediante controles de contenido'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: beee4dd4a67b03f278a296d4b5f129100212fd25
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49850365"
---
# <a name="how-to-protect-parts-of-documents-by-using-content-controls"></a>Cómo: proteger elementos de documentos mediante controles de contenido
  Al proteger un elemento de un documento, se impide que los usuarios cambien o eliminen el contenido de ese elemento. Existen varios modos de proteger los elementos de un documento de Microsoft Office Word mediante los controles de contenido:  
  
- Puede proteger un control de contenido.  
  
- Puede proteger un elemento de un documento que no está en un control de contenido.  
  
  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
##  <a name="EditDeleteControl"></a> Proteger un control de contenido  
 Puede impedir que los usuarios editen o eliminen un control de contenido estableciendo las propiedades del control en un proyecto de nivel de documento en tiempo de diseño o en tiempo de ejecución.  
  
 También puede proteger los controles de contenido que agregue a un documento en tiempo de ejecución mediante un proyecto de complemento de VSTO. Para obtener más información, consulte [Cómo: agregar controles de contenido a documentos de Word](../vsto/how-to-add-content-controls-to-word-documents.md).  
  
### <a name="to-protect-a-content-control-at-design-time"></a>Para proteger un control de contenido en tiempo de diseño  
  
1.  En el documento que se hospeda en el diseñador de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], seleccione el control de contenido que desea proteger.  
  
2.  En el **propiedades** ventana, establezca una o ambas de las siguientes propiedades:  
  
    -   Para evitar que los usuarios editen el control, establezca **LockContents** a **True**.  
  
    -   Para evitar que los usuarios eliminen el control, establezca **LockContentControl** a **True**.  
  
3.  Haga clic en **Aceptar**.  
  
### <a name="to-protect-a-content-control-at-runtime"></a>Para proteger un control de contenido en tiempo de ejecución  
  
1.  Establecer el `LockContents` propiedad del control de contenido a **true** para evitar que los usuarios editen el control y establecer el `LockContentControl` propiedad **true** para impedir que los usuarios eliminen el control.  
  
     En el siguiente ejemplo de código se muestra cómo usar las propiedades <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContents%2A> y <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContentControl%2A> de dos objetos <xref:Microsoft.Office.Tools.Word.RichTextContentControl> diferentes en un proyecto de nivel de documento. Para ejecutar este código, agregue el código a la clase `ThisDocument` del proyecto y llame al método `AddProtectedContentControls` desde el controlador de eventos `ThisDocument_Startup` .  
  
     [!code-csharp[Trin_ContentControlHowToProtect#2](../vsto/codesnippet/CSharp/Trin_ContentControlHowToProtect/ThisDocument.cs#2)]
     [!code-vb[Trin_ContentControlHowToProtect#2](../vsto/codesnippet/VisualBasic/Trin_ContentControlHowToProtect/ThisDocument.vb#2)]  
  
     En el siguiente ejemplo de código se muestra cómo usar las propiedades <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContents%2A> y <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContentControl%2A> de dos objetos <xref:Microsoft.Office.Tools.Word.RichTextContentControl> diferentes en un proyecto de complemento de VSTO. Para ejecutar este código, agregue el código a la clase `ThisAddIn` del proyecto y llame al método `AddProtectedContentControls` desde el controlador de eventos `ThisAddIn_Startup` .  
  
     [!code-vb[Trin_WordAddInDynamicControls#14](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#14)]
     [!code-csharp[Trin_WordAddInDynamicControls#14](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#14)]  
  
## <a name="protect-a-part-of-a-document-that-is-not-in-a-content-control"></a>Proteger un elemento de un documento que no está en un control de contenido  
 Puede impedir que los usuarios cambien un área de un documento colocándola en un <xref:Microsoft.Office.Tools.Word.GroupContentControl>. Esto es útil en los siguientes escenarios:  
  
-   Desea proteger un área que no contiene controles de contenido.  
  
-   Desea proteger un área que ya contiene controles de contenido, pero el texto u otros elementos que desea proteger no se encuentran en los controles de contenido.  
  
> [!NOTE]  
>  Si crea un <xref:Microsoft.Office.Tools.Word.GroupContentControl> que contiene controles de contenido insertados, estos controles no se protegerán automáticamente. Para evitar que los usuarios editen un control de contenido incrustado, utilice la **LockContents** propiedad del control.  
  
### <a name="to-protect-an-area-of-a-document-at-design-time"></a>Para proteger un área de un documento en tiempo de diseño  
  
1.  En el documento que se hospeda en el diseñador de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], seleccione el área que desea proteger.  
  
2.  En la cinta de opciones, haga clic en la pestaña **Desarrollador** .  
  
    > [!NOTE]  
    >  Si la pestaña **Desarrollador** no está visible, primero debe mostrarla. Para obtener más información, consulte [Cómo: mostrar la pestaña Programador en la cinta de opciones](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
3.  En el **controles** grupo, haga clic en el **grupo** botón desplegable y, a continuación, haga clic en **grupo**.  
  
     Se genera automáticamente un <xref:Microsoft.Office.Tools.Word.GroupContentControl> que contiene la región protegida en la clase `ThisDocument` de su proyecto. Un borde que representa el control de grupo está visible en tiempo de diseño, pero no hay ningún borde visible en tiempo de ejecución.  
  
### <a name="to-protect-an-area-of-a-document-at-runtime"></a>Para proteger un área de un documento en tiempo de ejecución  
  
1.  Seleccione el área que desea proteger mediante programación y, a continuación, llame al método <xref:Microsoft.Office.Tools.Word.ControlCollection.AddGroupContentControl%2A> para crear un <xref:Microsoft.Office.Tools.Word.GroupContentControl>.  
  
     El siguiente ejemplo de código para un proyecto de nivel de documento agrega texto al primer párrafo del documento, selecciona el primer párrafo y, a continuación, crea una instancia de un <xref:Microsoft.Office.Tools.Word.GroupContentControl>. Para ejecutar este código, agregue el código a la clase `ThisDocument` del proyecto y llame al método `ProtectFirstParagraph` desde el controlador de eventos `ThisDocument_Startup` .  
  
     [!code-csharp[Trin_ContentControlHowToProtect#1](../vsto/codesnippet/CSharp/Trin_ContentControlHowToProtect/ThisDocument.cs#1)]
     [!code-vb[Trin_ContentControlHowToProtect#1](../vsto/codesnippet/VisualBasic/Trin_ContentControlHowToProtect/ThisDocument.vb#1)]  
  
     El siguiente ejemplo de código para un proyecto de complemento de VSTO agrega texto al primer párrafo del documento activo, selecciona el primer párrafo y, a continuación, crea una instancia de un <xref:Microsoft.Office.Tools.Word.GroupContentControl>. Para ejecutar este código, agregue el código a la clase `ThisAddIn` del proyecto y llame al método `ProtectFirstParagraph` desde el controlador de eventos `ThisAddIn_Startup` .  
  
     [!code-vb[Trin_WordAddInDynamicControls#15](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#15)]
     [!code-csharp[Trin_WordAddInDynamicControls#15](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#15)]  
  
## <a name="see-also"></a>Vea también  
 [Automatizar Word usando objetos extendidos](../vsto/automating-word-by-using-extended-objects.md)   
 [Controles de contenido](../vsto/content-controls.md)   
 [Cómo: agregar controles de contenido a documentos de Word](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [Elementos host y la información general sobre controles de host](../vsto/host-items-and-host-controls-overview.md)   
 [Limitaciones de programación de elementos host y controles host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md)  
   