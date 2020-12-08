---
title: Automatizar Word con objetos extendidos
description: Obtenga información sobre cómo puede usar elementos host y controles host en sus soluciones al desarrollar soluciones de Word en Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 39ac9d50d0f75f595568c66b02bda1c5ed46a3d6
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/08/2020
ms.locfileid: "96844457"
---
# <a name="automate-word-by-using-extended-objects"></a>Automatizar Word con objetos extendidos
  Cuando desarrolla soluciones de Word en Visual Studio, puede usar la opción *elementos host* y *controles host* en sus soluciones. Se trata de objetos que extienden algunos objetos de uso común en el modelo de objetos de Word (es decir, el modelo de objetos expuesto por el ensamblado de interoperabilidad primario de Word), como los objetos <xref:Microsoft.Office.Interop.Word.Document> y <xref:Microsoft.Office.Interop.Word.ContentControl> . Los objetos extendidos se comportan como los objetos de Word en los que se basan, pero agregan eventos adicionales y capacidades de enlace de datos a los objetos.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Los elementos y controles host están disponibles tanto en los complementos VSTO como en las personalizaciones de nivel de documento, aunque el contexto en el que se pueden usar es diferente para cada tipo de solución. Para obtener más información, vea [información general sobre elementos y controles host](../vsto/host-items-and-host-controls-overview.md).

## <a name="document-host-item"></a>Elemento host de documento
 Los proyectos de Word le proporcionan acceso a varios elementos host <xref:Microsoft.Office.Tools.Word.Document> : El elemento host <xref:Microsoft.Office.Tools.Word.Document> también actúa como contenedor de otros controles, incluyendo los controles host y los controles de Windows Forms; asimismo, mantiene información acerca de los controles en su superficie. Igualmente, el elemento host <xref:Microsoft.Office.Tools.Word.Document> también proporciona casi los mismos miembros que la clase <xref:Microsoft.Office.Interop.Word.Document> , que es la clase correspondiente al modelo de objetos de Word.

 Para obtener más información, vea [elemento host del documento](../vsto/document-host-item.md).

## <a name="word-host-controls"></a>controles host de Word
 Existen varios controles host de Word que le ayudarán a crear, organizar y automatizar documentos. La mayor parte de su funcionalidad implica importar, presentar y proteger los datos. Estos controles host proporcionan eventos y capacidades de enlace de datos que no tienen sus homólogos en el modelo de objetos nativo de Word.

 En proyectos de nivel de documento, puede agregar cualquier control host al documento en tiempo de diseño, o agregar controles de contenido y de marcador en tiempo de ejecución. En los proyectos de complementos VSTO, puede agregar controles de contenido y de marcador a cualquier documento abierto en tiempo de ejecución.

 Para obtener más información acerca de los controles host que puede usar en proyectos de Word, consulte los siguientes temas:

- [Controles de contenido](../vsto/content-controls.md)

- [Bookmark (control)](../vsto/bookmark-control.md)

- [XMLNode (control)](../vsto/xmlnode-control.md)

- [XMLNodes (control)](../vsto/xmlnodes-control.md)

## <a name="see-also"></a>Vea también
- [Cómo: agregar controles de contenido a documentos de Word](../vsto/how-to-add-content-controls-to-word-documents.md)
- [Cómo: agregar controles Bookmark a documentos de Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)
- [Cómo: agregar controles XMLNode a documentos de Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)
- [Cómo: agregar controles XMLNodes a documentos de Word](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)
- [Cómo: cambiar el tamaño de los controles Bookmark](../vsto/how-to-resize-bookmark-controls.md)
- [Tutorial: crear una plantilla mediante controles de contenido](../vsto/walkthrough-creating-a-template-by-using-content-controls.md)
- [Tutorial: enlazar controles de contenido a elementos XML personalizados](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md)
- [Tutorial: crear menús contextuales para marcadores](../vsto/walkthrough-creating-shortcut-menus-for-bookmarks.md)
- [Soluciones de Word](../vsto/word-solutions.md)
- [Información general sobre elementos y controles host](../vsto/host-items-and-host-controls-overview.md)
- [Limitaciones de programación de elementos y controles host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Ampliar documentos de Word y libros de Excel en complementos de VSTO en tiempo de ejecución](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
