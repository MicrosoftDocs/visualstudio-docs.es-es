---
title: "Cómo: cambiar el tamaño de los controles Bookmark | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], resizing
- Bookmark control, resizing
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: fc546ed1b840cc072510a49a16696a1bfc91cee7
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-resize-bookmark-controls"></a>Cómo: Cambiar el tamaño de los controles Bookmark
  El tamaño de un control <xref:Microsoft.Office.Tools.Word.Bookmark> se establece cuando lo agrega a un documento de Microsoft Office Word. También puede cambiar su tamaño más adelante.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Hay tres maneras de cambiar el tamaño de un marcador:  
  
-   Agregue o quite el texto del control <xref:Microsoft.Office.Tools.Word.Bookmark> .  
  
     Siempre que agregue texto a un marcador, el tamaño del marcador aumentará automáticamente para adaptarse al nuevo texto. Cuando elimine texto, el tamaño del marcador se reducirá automáticamente.  
  
-   Cambie las propiedades <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> y <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> del control <xref:Microsoft.Office.Tools.Word.Bookmark> .  
  
     Esto resulta de utilidad si va a cambiar el tamaño en unos cuantos caracteres.  
  
-   Vuelva a crear el control <xref:Microsoft.Office.Tools.Word.Bookmark> .  
  
     Esto resulta de utilidad si hay un cambio significativo en el tamaño o la ubicación de un marcador.  
  
 En proyectos de nivel de documento, puede agregar controles <xref:Microsoft.Office.Tools.Word.Bookmark> al documento en el proyecto en tiempo de diseño o en tiempo de ejecución. En proyectos de complemento de VSTO, puede agregar controles <xref:Microsoft.Office.Tools.Word.Bookmark> a cualquier documento abierto en tiempo de ejecución. Para obtener más información, consulte [Cómo: Agregar controles Bookmark a documentos de Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="changing-the-start-and-end-properties"></a>Cambiar las propiedades Start y End  
  
#### <a name="to-resize-a-bookmark-in-a-document-level-project-at-design-time"></a>Cambiar el tamaño del marcador de un proyecto de nivel de documento en tiempo de diseño  
  
1.  En la ventana **Propiedades** , seleccione el marcador.  
  
2.  Aumente o disminuya el valor de la propiedad <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> .  
  
3.  Aumente o disminuya el valor de la propiedad <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> .  
  
#### <a name="to-resize-a-bookmark-in-a-document-level-project-at-run-time"></a>Cambiar el tamaño de un marcador de un proyecto de nivel de documento en tiempo de ejecución  
  
1.  Modifique las propiedades <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> y <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> del <xref:Microsoft.Office.Tools.Word.Bookmark> que creó en tiempo de ejecución o en tiempo de diseño.  
  
     En el ejemplo de código siguiente se agregan cinco caracteres al inicio de un marcador denominado `SampleBookmark`. De esta manera, el código supone que hay al menos cinco caracteres de texto antes del marcador.  
  
     [!code-csharp[Trin_VstcoreHostControlsWord#2](../vsto/codesnippet/CSharp/trin_vstcorehostcontrolsword/ThisDocument.cs#2)]
     [!code-vb[Trin_VstcoreHostControlsWord#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsWordVB/ThisDocument.vb#2)]  
  
     En el ejemplo de código siguiente se agregan cinco caracteres al final del mismo marcador. Así, el código asume que hay al menos cinco caracteres de texto después del marcador.  
  
     [!code-csharp[Trin_VstcoreHostControlsWord#3](../vsto/codesnippet/CSharp/trin_vstcorehostcontrolsword/ThisDocument.cs#3)]
     [!code-vb[Trin_VstcoreHostControlsWord#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsWordVB/ThisDocument.vb#3)]  
  
#### <a name="to-resize-a-bookmark-in-an-vsto-add-in-project-at-run-time"></a>Cambiar el tamaño de un marcador en un proyecto de complemento VSTO en tiempo de ejecución  
  
1.  Modifique las propiedades <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> y <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> del <xref:Microsoft.Office.Tools.Word.Bookmark> que creó en tiempo de ejecución.  
  
     En el siguiente ejemplo de código se crea un <xref:Microsoft.Office.Tools.Word.Bookmark> que contiene el texto del primer párrafo del documento activo y, a continuación, se quitan cinco caracteres del inicio y del final del <xref:Microsoft.Office.Tools.Word.Bookmark>.  
  
     [!code-vb[Trin_WordAddInDynamicControls#16](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#16)]
     [!code-csharp[Trin_WordAddInDynamicControls#16](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#16)]  
  
## <a name="recreating-the-bookmark"></a>Volver a crear el marcador  
 Puede cambiar el tamaño de un marcador en un proyecto de nivel de documento agregando un nuevo marcador con el mismo nombre que el marcador existente, pero con un tamaño diferente.  
  
#### <a name="to-recreate-a-bookmark-in-a-document-level-project-at-design-time"></a>Volver a crear un marcador de un proyecto de nivel de documento en tiempo de diseño  
  
1.  Seleccione el texto que se incluirá en el nuevo control <xref:Microsoft.Office.Tools.Word.Bookmark> .  
  
2.  En el menú **Insertar** , haga clic en **Marcador**.  
  
3.  En el cuadro de diálogo **Marcador** , seleccione el nombre del marcador cuyo tamaño desea cambiar y haga clic en **Agregar**.  
  
## <a name="see-also"></a>Vea también  
 [Cómo: Agregar controles Bookmark a documentos de Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)   
 [Automatizar Word con objetos extendidos](../vsto/automating-word-by-using-extended-objects.md)   
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Cómo: cambiar el tamaño de los controles NamedRange](../vsto/how-to-resize-namedrange-controls.md)   
 [Cómo: cambiar el tamaño de los controles ListObject](../vsto/how-to-resize-listobject-controls.md)   
 [Limitaciones de programación de elementos y controles Host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  