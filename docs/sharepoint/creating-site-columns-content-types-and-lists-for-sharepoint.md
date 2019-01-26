---
title: Crear listas, tipos de contenido y columnas de sitio para SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.ListDesigner.ContentTypeSetting
- VS.SharePointTools.ContentTypeDesigner.CommonPropertiesPage
- VS.SharePointTools.ListDesigner.CreatingLists
- VS.SharePointTools.ListDesigner.ListPage
- VS.SharePointTools.ListDesigner.ViewPage
- VS.SharePointTools.ListDesigner.CommonPropertiesPage
- VS.SharePointTools.ContentTypeDesigner.ColumnsPage
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8ec1bc999025128c0dd68281dfc53e3f6353ae6b
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2019
ms.locfileid: "54875555"
---
# <a name="create-site-columns-content-types-and-lists-for-sharepoint"></a>Crear listas, tipos de contenido y columnas de sitio para SharePoint
  Visual Studio proporciona plantillas de elemento de proyecto para muchos elementos diferentes, fundamentales SharePoint, incluidos *enumera* y *tipos de contenido*, ambos de los cuales pueden incorporar columnas de sitio (o  *campos*). Los nuevos diseñadores para listas y tipos de contenido que sea más fácil que nunca la creación de estos elementos.  
  
## <a name="site-columns"></a>Columnas del sitio
 Columnas de sitio son uno de los elementos más básicos que puede agregar a un proyecto de SharePoint. Una columna de sitio representa un tipo de datos, como un número de teléfono, un comentario o el nombre de la ciudad de un contacto en una lista de contactos.  
  
 La nueva plantilla de elemento de proyecto de columna de sitio facilita la creación de columnas de sitio que en la versión anterior de Visual Studio. Después de crear una nueva columna de sitio, puede modificar el XML en la columna de sitio *Elements.xml* archivo que incluya la información que desee, como su nombre para mostrar, su tipo de datos y el grupo en el que desea que aparezca en la columna de sitio SharePoint. Para obtener más información acerca de las columnas de sitio, consulte [Introducción a las columnas](http://go.microsoft.com/fwlink/?LinkId=224996).  
  
## <a name="content-types-and-lists"></a>Listas y tipos de contenido
 Listas y tipos de contenido son con más frecuencia los elementos usados en SharePoint.  
  
 Un tipo de contenido define metadatos, el flujo de trabajo y el comportamiento de una categoría de elementos en una biblioteca de documentos o lista de SharePoint. Por ejemplo, puede crear un tipo de contenido para obtener información en una lista de contactos o una lista de tareas. Póngase en contacto con un tipo de contenido puede incluir columnas como nombre, correo electrónico, número de teléfono y dirección. Un tipo de contenido que define en el nivel de sitio es independiente de cualquier lista o biblioteca de documentos en el sitio. Puede usar el mismo tipo de contenido con diferentes listas o bibliotecas de documentos en el sitio de SharePoint. También puede usar varios tipos de contenido en la misma lista o biblioteca de documentos.  
  
 Una lista es una colección de información de SharePoint que puede compartir con otros usuarios. Las listas se componen de filas de las columnas que contienen datos. Algunos ejemplos de listas: una lista de tareas, una lista de contactos y una lista de anuncios.  
  
 Los nuevos diseñadores Content Type y lista en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Asegúrese de crear listas y tipos de contenido de sitio de mucho más fácil y más intuitiva que en la versión anterior de Visual Studio. La interfaz de usuario le permite construir visualmente listas y tipos de contenido de una manera familiar y le permite ordenar y agrupar los datos de listas y usar los encabezados de grupo. Para obtener más información acerca de los tipos de contenido, consulte [tipos de contenido](http://go.microsoft.com/fwlink/?LinkId=224997). Para obtener más información acerca de las listas, vea [formularios de lista](http://go.microsoft.com/fwlink/?LinkId=224998) y [vistas de lista](http://go.microsoft.com/fwlink/?LinkId=224999).  
  
## <a name="related-topics"></a>Temas relacionados
  
|Título|Descripción|  
|-----------|-----------------|  
|[Tutorial: Crear una columna de sitio, el tipo de contenido y la lista de SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)|Muestra cómo crear columnas de sitio que se usan en un tipo de contenido personalizado. El tipo de contenido, a continuación, se usa en una lista personalizada.|  
  
## <a name="see-also"></a>Vea también
 [Introducción al desarrollo en SharePoint 2010](http://go.microsoft.com/fwlink/?LinkId=225000)  
