---
title: Procedimiento Cambiar el tamaño de los controles Bookmark
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], resizing
- Bookmark control, resizing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f23094aae38cb1b0dc89a2b30ab7a812d7a9cb66
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2019
ms.locfileid: "54869806"
---
# <a name="how-to-resize-bookmark-controls"></a>Procedimiento Cambiar el tamaño de los controles Bookmark
  El tamaño de un control <xref:Microsoft.Office.Tools.Word.Bookmark> se establece cuando lo agrega a un documento de Microsoft Office Word. También puede cambiar su tamaño más adelante.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Hay tres maneras de cambiar el tamaño de un marcador:  
  
- Agregue o quite el texto del control <xref:Microsoft.Office.Tools.Word.Bookmark> .  
  
   Siempre que agregue texto a un marcador, el tamaño del marcador aumentará automáticamente para adaptarse al nuevo texto. Cuando elimine texto, el tamaño del marcador se reducirá automáticamente.  
  
- Cambie las propiedades <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> y <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> del control <xref:Microsoft.Office.Tools.Word.Bookmark> .  
  
   Esto resulta de utilidad si va a cambiar el tamaño en unos cuantos caracteres.  
  
- Vuelva a crear el control <xref:Microsoft.Office.Tools.Word.Bookmark> .  
  
   Esto resulta de utilidad si hay un cambio significativo en el tamaño o la ubicación de un marcador.  
  
  En proyectos de nivel de documento, puede agregar controles <xref:Microsoft.Office.Tools.Word.Bookmark> al documento en el proyecto en tiempo de diseño o en tiempo de ejecución. En proyectos de complemento VSTO, puede agregar <xref:Microsoft.Office.Tools.Word.Bookmark> controles a cualquier documento abierto en tiempo de ejecución. Para obtener más información, vea [Cómo: Agregar controles Bookmark a documentos de Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md).  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="change-the-start-and-end-properties"></a>Cambiar las propiedades de inicio y finalización  
  
### <a name="to-resize-a-bookmark-in-a-document-level-project-at-design-time"></a>Cambiar el tamaño del marcador de un proyecto de nivel de documento en tiempo de diseño  
  
1.  En la ventana **Propiedades** , seleccione el marcador.  
  
2.  Aumente o disminuya el valor de la propiedad <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> .  
  
3.  Aumente o disminuya el valor de la propiedad <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> .  
  
### <a name="to-resize-a-bookmark-in-a-document-level-project-at-runtime"></a>Para cambiar el tamaño de un marcador en un proyecto de nivel de documento en tiempo de ejecución  
  
1.  Modificar el <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> y <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> las propiedades de un <xref:Microsoft.Office.Tools.Word.Bookmark> que creó en tiempo de ejecución o en tiempo de diseño.  
  
     En el ejemplo de código siguiente se agregan cinco caracteres al inicio de un marcador denominado `SampleBookmark`. De esta manera, el código supone que hay al menos cinco caracteres de texto antes del marcador.  
  
     [!code-csharp[Trin_VstcoreHostControlsWord#2](../vsto/codesnippet/CSharp/trin_vstcorehostcontrolsword/ThisDocument.cs#2)]
     [!code-vb[Trin_VstcoreHostControlsWord#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsWordVB/ThisDocument.vb#2)]  
  
     En el ejemplo de código siguiente se agregan cinco caracteres al final del mismo marcador. Así, el código asume que hay al menos cinco caracteres de texto después del marcador.  
  
     [!code-csharp[Trin_VstcoreHostControlsWord#3](../vsto/codesnippet/CSharp/trin_vstcorehostcontrolsword/ThisDocument.cs#3)]
     [!code-vb[Trin_VstcoreHostControlsWord#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsWordVB/ThisDocument.vb#3)]  
  
### <a name="to-resize-a-bookmark-in-a-vsto-add-in-project-at-runtime"></a>Para cambiar el tamaño de un marcador en un proyecto de complemento VSTO en tiempo de ejecución  
  
1.  Modificar el <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> y <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> las propiedades de un <xref:Microsoft.Office.Tools.Word.Bookmark> que creó en tiempo de ejecución.  
  
     En el siguiente ejemplo de código se crea un <xref:Microsoft.Office.Tools.Word.Bookmark> que contiene el texto del primer párrafo del documento activo y, a continuación, se quitan cinco caracteres del inicio y del final del <xref:Microsoft.Office.Tools.Word.Bookmark>.  
  
     [!code-vb[Trin_WordAddInDynamicControls#16](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#16)]
     [!code-csharp[Trin_WordAddInDynamicControls#16](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#16)]  
  
## <a name="recreate-the-bookmark"></a>Volver a crear el marcador  
 Puede cambiar el tamaño de un marcador en un proyecto de nivel de documento agregando un nuevo marcador con el mismo nombre que el marcador existente, pero con un tamaño diferente.  
  
### <a name="to-recreate-a-bookmark-in-a-document-level-project-at-design-time"></a>Volver a crear un marcador de un proyecto de nivel de documento en tiempo de diseño  
  
1.  Seleccione el texto que se incluirá en el nuevo control <xref:Microsoft.Office.Tools.Word.Bookmark> .  
  
2.  En el menú **Insertar** , haga clic en **Marcador**.  
  
3.  En el cuadro de diálogo **Marcador** , seleccione el nombre del marcador cuyo tamaño desea cambiar y haga clic en **Agregar**.  
  
## <a name="see-also"></a>Vea también  
 [Cómo: Agregar controles Bookmark a documentos de Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)   
 [Automatizar Word usando objetos extendidos](../vsto/automating-word-by-using-extended-objects.md)   
 [Elementos host y la información general sobre controles de host](../vsto/host-items-and-host-controls-overview.md)   
 [Cómo: Cambiar el tamaño de los controles NamedRange](../vsto/how-to-resize-namedrange-controls.md)   
 [Cómo: Cambiar el tamaño de los controles ListObject](../vsto/how-to-resize-listobject-controls.md)   
 [Limitaciones de programación de elementos host y controles host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
