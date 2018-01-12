---
title: Automatizar Word con objetos extendidos | Documentos de Microsoft
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
- Word [Office development in Visual Studio], automating
- extended objects [Office development in Visual Studio], Word
- automation [Office development in Visual Studio], Word
- host items [Office development in Visual Studio], Word
- automating Word
- controls [Office development in Visual Studio], Word host controls
- host controls, Word
- host controls [Office development in Visual Studio], Word
- Word [Office development in Visual Studio], host controls
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: b3073f5f80e805f4c55e6924ada1be9a2ba139f6
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="automating-word-by-using-extended-objects"></a>Automatizar Word con objetos extendidos
  Cuando desarrolla soluciones de Word en Visual Studio, puede usar la opción *elementos host* y *controles host*en sus soluciones. Se trata de objetos que extienden algunos objetos de uso común en el modelo de objetos de Word (es decir, el modelo de objetos expuesto por el ensamblado de interoperabilidad primario de Word), como los objetos <xref:Microsoft.Office.Interop.Word.Document> y <xref:Microsoft.Office.Interop.Word.ContentControl> . Los objetos extendidos se comportan como los objetos de Word en los que se basan, pero agregan eventos adicionales y capacidades de enlace de datos a los objetos.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Los elementos y controles host están disponibles tanto en los complementos VSTO como en las personalizaciones de nivel de documento, aunque el contexto en el que se pueden usar es diferente para cada tipo de solución. Para obtener más información, consulta [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md).  
  
## <a name="document-host-item"></a>Elemento host Document  
 Los proyectos de Word le proporcionan acceso a varios elementos host <xref:Microsoft.Office.Tools.Word.Document> : El elemento host <xref:Microsoft.Office.Tools.Word.Document> también actúa como contenedor de otros controles, incluyendo los controles host y los controles de Windows Forms; asimismo, mantiene información acerca de los controles en su superficie. Igualmente, el elemento host <xref:Microsoft.Office.Tools.Word.Document> también proporciona casi los mismos miembros que la clase <xref:Microsoft.Office.Interop.Word.Document> , que es la clase correspondiente al modelo de objetos de Word.  
  
 Para obtener más información, consulta [Document Host Item](../vsto/document-host-item.md).  
  
## <a name="word-host-controls"></a>Controles host de Word  
 Existen varios controles host de Word que le ayudarán a crear, organizar y automatizar documentos. La mayor parte de su funcionalidad implica importar, presentar y proteger los datos. Estos controles host proporcionan eventos y capacidades de enlace de datos que no tienen sus homólogos en el modelo de objetos nativo de Word.  
  
 En proyectos de nivel de documento, puede agregar cualquier control host al documento en tiempo de diseño, o agregar controles de contenido y de marcador en tiempo de ejecución. En los proyectos de complementos VSTO, puede agregar controles de contenido y de marcador a cualquier documento abierto en tiempo de ejecución.  
  
 Para obtener más información acerca de los controles host que puede usar en proyectos de Word, consulte los siguientes temas:  
  
-   [Controles de contenido](../vsto/content-controls.md)  
  
-   [Bookmark (Control)](../vsto/bookmark-control.md)  
  
-   [XMLNode (control)](../vsto/xmlnode-control.md)  
  
-   [XMLNodes (control)](../vsto/xmlnodes-control.md)  
  
## <a name="see-also"></a>Vea también  
 [Cómo: agregar controles de contenido a documentos de Word](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [How to: Add Bookmark Controls to Word Documents](../vsto/how-to-add-bookmark-controls-to-word-documents.md)   
 [Cómo: agregar controles XMLNode a documentos de Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)   
 [Cómo: agregar controles XMLNodes a documentos de Word](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)   
 [Cómo: cambiar el tamaño de los controles Bookmark](../vsto/how-to-resize-bookmark-controls.md)   
 [Tutorial: Crear una plantilla mediante controles de contenido](../vsto/walkthrough-creating-a-template-by-using-content-controls.md)   
 [Tutorial: Enlazar controles de contenido a elementos XML personalizados](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md)   
 [Tutorial: Crear menús contextuales para marcadores](../vsto/walkthrough-creating-shortcut-menus-for-bookmarks.md)   
 [Soluciones de Word](../vsto/word-solutions.md)   
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Extender documentos de Word y libros de Excel en complementos VSTO en tiempo de ejecución](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)  
  
  