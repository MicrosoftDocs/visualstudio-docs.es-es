---
title: Bookmark (Control) | Documentos de Microsoft
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VST.Toolbox.Bookmark
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- bookmarks, controlling
- Bookmark control, data binding
- Bookmark control, events
- Bookmark control
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 38e3286d24f0591ca4ced3339118b6d0d4bfe1d7
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="bookmark-control"></a>Bookmark (control)
  El control <xref:Microsoft.Office.Tools.Word.Bookmark> es un marcador que tiene un nombre único, expone eventos y se puede enlazar a datos. El marcador se puede usar como marcador de posición para marcar un elemento o una ubicación en un documento de Microsoft Office Word. El control <xref:Microsoft.Office.Tools.Word.Bookmark> s una combinación de un objeto <xref:Microsoft.Office.Interop.Word.Bookmark> y un objeto <xref:Microsoft.Office.Interop.Word.Range> .  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 En proyectos de nivel de documento, puede agregar controles <xref:Microsoft.Office.Tools.Word.Bookmark> al documento en tiempo de diseño o en tiempo de ejecución. En proyectos de complemento de VSTO, puede agregar controles <xref:Microsoft.Office.Tools.Word.Bookmark> a cualquier documento abierto en tiempo de ejecución. Para obtener más información, consulte [How to: Add Bookmark Controls to Word Documents](../vsto/how-to-add-bookmark-controls-to-word-documents.md).  
  
## <a name="binding-data-to-the-control"></a>Enlazar datos al control  
 Un control <xref:Microsoft.Office.Tools.Word.Bookmark> admite el enlace de datos simple. El marcador se debe enlazar a un origen de datos mediante la propiedad <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> . La propiedad de enlace de datos predeterminada del marcador es la propiedad <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> .  
  
 Si los datos del conjunto de datos enlazado se actualizan, el control <xref:Microsoft.Office.Tools.Word.Bookmark> reflejará los cambios.  
  
 En los proyectos de nivel de documento, puede enlazar datos a marcadores mediante la ventana **Orígenes de datos** . Para obtener más información, consulta [How to: Populate Documents with Data from Objects](../vsto/how-to-populate-documents-with-data-from-objects.md).  
  
## <a name="formatting"></a>Formato  
 El formato que puede aplicarse a un control <xref:Microsoft.Office.Interop.Word.Bookmark> también puede aplicarse a un control <xref:Microsoft.Office.Tools.Word.Bookmark> . Esto incluye fuentes, sangría, espaciado, numeración y estilos.  
  
## <a name="assigning-text-to-the-bookmark"></a>Asignar texto al marcador  
 Una diferencia adicional entre un objeto <xref:Microsoft.Office.Interop.Word.Bookmark> y un control <xref:Microsoft.Office.Tools.Word.Bookmark> es cómo se comporta cuando se asigna texto al marcador. Si se asigna texto a un <xref:Microsoft.Office.Interop.Word.Bookmark>de longitud cero, el texto se anexa a la derecha del marcador y el marcador conserva la longitud cero. Sin embargo, si se asigna texto a un <xref:Microsoft.Office.Tools.Word.Bookmark>de longitud cero, el texto se inserta en el marcador y la longitud del marcador se expande hasta el número total de caracteres insertados.  
  
 El control <xref:Microsoft.Office.Tools.Word.Bookmark> también tiene la propiedad <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> . Difiere de la propiedad <xref:Microsoft.Office.Interop.Word.Range.Text%2A> que está disponible en la propiedad <xref:Microsoft.Office.Tools.Word.Bookmark.Range%2A> de un control <xref:Microsoft.Office.Tools.Word.Bookmark> o en la propiedad <xref:Microsoft.Office.Interop.Word.Bookmark.Range%2A> de un objeto <xref:Microsoft.Office.Interop.Word.Bookmark> .  
  
|Propiedad Text|Descripción|  
|-------------------|-----------------|  
|<xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A>|Use esta propiedad para mostrar el texto del marcador y dejar el marcador en el documento. Al asignar texto al marcador, se expande el intervalo del marcador y no se elimina el marcador.<br /><br /> Por ejemplo, `Bookmark1.Text = "Hello world"` inserta el texto en el marcador y deja el marcador intacto.|  
|<xref:Microsoft.Office.Interop.Word.Range.Text%2A>|Use esta propiedad para mostrar texto en la ubicación del marcador y eliminar automáticamente el marcador. Por ejemplo, `Bookmark1.Range.Text = "Hello world"` inserta el texto en el marcador y elimina el marcador.|  
  
## <a name="renaming-the-control-at-design-time"></a>Cambiar el nombre de un control en tiempo de diseño  
 En los proyectos de nivel de documento, si arrastra un control <xref:Microsoft.Office.Tools.Word.Bookmark> desde el **Cuadro de herramientas** hasta el documento, Visual Studio genera automáticamente un nombre para el control. Puede cambiar el nombre del control en la ventana **Propiedades** .  
  
## <a name="overlapping-controls"></a>Controles superpuestos  
 Los controles Bookmark pueden superponerse entre sí; es decir, más de un marcador puede compartir el mismo texto. Al asignar nuevo texto a uno de los marcadores superpuestos, este solo contendrá el nuevo texto y los marcadores dejarán de superponerse. El otro marcador solo contendrá el texto que no se comparte entre los marcadores superpuestos originales.  
  
 En la tabla siguiente se muestra cómo dos marcadores superpuestos comparten la frase "This is sample text".  
  
|Marcador|Texto|  
|--------------|----------|  
|Marcadores superpuestos|[this is {sample] text.}|  
|Bookmark1|This is sample|  
|Bookmark2|sample text.|  
  
 Si asigna el nuevo texto "This is replacement." al marcador Bookmark1, los marcadores ya no se superpondrán y Bookmark2 conservará solo el texto que inicialmente no formaba parte del marcador Bookmark1.  
  
|Marcador|Texto|  
|--------------|----------|  
|Dos marcadores independientes|[this is replacement]{ text.}|  
|Bookmark1|This is replacement|  
|Bookmark2|text.|  
  
 Si un marcador está totalmente contenido en otro marcador y se cambia el texto del marcador exterior, el marcador interno no se elimina. Sin embargo, el marcador interno se convierte en un marcador vacío que se desplaza al final del marcador exterior. En la tabla siguiente se muestra cómo un marcador incluido en otro marcador comparte con él la frase "This is sample text.".  
  
|Marcador|Texto|  
|--------------|----------|  
|Marcadores superpuestos|[this is {sample} text.]|  
|Bookmark1|This is sample text.|  
|Bookmark2|sample|  
  
 Si asigna el nuevo texto "This is replacement." al marcador Bookmark1, los marcadores ya no se superpondrán y Bookmark2 se convertirá en un marcador vacío situado al final de Bookmark1.  
  
|Marcador|Texto|  
|--------------|----------|  
|Dos marcadores independientes|[this is replacement.]{}|  
|Bookmark1|This is replacement.|  
|Bookmark2|*\<vacía >*|  
  
## <a name="events"></a>Eventos  
 Los eventos siguientes están disponibles para el control <xref:Microsoft.Office.Tools.Word.Bookmark> :  
  
-   <xref:Microsoft.Office.Tools.Word.Bookmark.BeforeDoubleClick>  
  
-   <xref:Microsoft.Office.Tools.Word.Bookmark.BeforeRightClick>  
  
-   <xref:Microsoft.Office.Tools.Word.Bookmark.BindingContextChanged>  
  
-   <xref:Microsoft.Office.Tools.Word.Bookmark.Deselected>  
  
-   <xref:System.ComponentModel.IComponent.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Word.Bookmark.Selected>  
  
-   <xref:Microsoft.Office.Tools.Word.Bookmark.SelectionChange>  
  
## <a name="see-also"></a>Vea también  
 [Automatizar Word con objetos extendidos](../vsto/automating-word-by-using-extended-objects.md)   
 [How to: Add Bookmark Controls to Word Documents](../vsto/how-to-add-bookmark-controls-to-word-documents.md)   
 [Tutorial: Crear menús contextuales para marcadores](../vsto/walkthrough-creating-shortcut-menus-for-bookmarks.md)   
 [Enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Limitaciones de programación de elementos y controles Host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  