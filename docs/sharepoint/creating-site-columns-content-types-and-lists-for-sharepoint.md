---
title: Crear listas, tipos de contenido y columnas de sitio para SharePoint | Documentos de Microsoft
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
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
ms.assetid: 9ceed263-3aec-41dc-8708-63cb37a08fa8
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a5f111efa5c2276adcc76fdf13cdf5a805929c63
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="creating-site-columns-content-types-and-lists-for-sharepoint"></a>Crear listas, tipos de contenido y columnas de sitio para SharePoint
  Visual Studio proporciona plantillas de elemento de proyecto para muchos elementos diferentes, fundamentales SharePoint, incluidos *enumera* y *tipos de contenido*, ambos de los cuales pueden incorporar columnas de sitio (o  *campos*). Los nuevos diseñadores para listas y tipos de contenido que la creación de estos elementos más fácil que nunca.  
  
## <a name="site-columns"></a>Columnas de sitio  
 Columnas de sitio son uno de los elementos más básicos que puede agregar a un proyecto de SharePoint. Una columna de sitio representa un tipo de datos, como un número de teléfono, un comentario o el nombre de la ciudad de un contacto en una lista de contactos.  
  
 La nueva plantilla de elemento de proyecto de columna de sitio facilita la creación de columnas de sitio que en la versión anterior de Visual Studio. Después de crear una nueva columna de sitio, puede modificar el XML en el archivo Elements.xml de la columna de sitio para incluir la información que desee, como su nombre para mostrar, su tipo de datos y el grupo en el que desea que aparezca en SharePoint, la columna de sitio. Para obtener más información acerca de las columnas de sitio, consulte [Introducción a las columnas](http://go.microsoft.com/fwlink/?LinkId=224996).  
  
## <a name="content-types-and-lists"></a>Listas y tipos de contenido  
 Listas y tipos de contenido se encuentran entre con más frecuencia los elementos utilizados en SharePoint.  
  
 Un tipo de contenido define los metadatos, el flujo de trabajo y el comportamiento de una categoría de elementos en una biblioteca de documentos o lista de SharePoint. Por ejemplo, puede crear un tipo de contenido para obtener información en una lista de contactos o una lista de tareas. Un tipo de contenido contacto puede incluir columnas como nombre, correo electrónico, número de teléfono y dirección. Un tipo de contenido que define en el nivel de sitio es independiente de cualquier lista o biblioteca de documentos en el sitio. Puede usar el mismo tipo de contenido con diferentes listas o bibliotecas de documentos en el sitio de SharePoint. También puede usar varios tipos de contenido en la misma lista o biblioteca de documentos.  
  
 Una lista es una colección de información de SharePoint que se puede compartir con otros usuarios. Las listas constan de filas de las columnas que contienen datos. Algunos ejemplos de las listas son: una lista de tareas, una lista de contactos y una lista de anuncios.  
  
 Los diseñadores de tipo de contenido y lista de nuevo en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Asegúrese de crear listas y tipos de contenido de sitio de mucho más sencilla e intuitiva que en la versión anterior de Visual Studio. La interfaz de usuario permite construir visualmente listas y tipos de contenido de una manera conocida y le permite ordenar y agrupar los datos de listas o usar encabezados de grupo. Para obtener más información acerca de los tipos de contenido, consulte [tipos de contenido de](http://go.microsoft.com/fwlink/?LinkId=224997). Para obtener más información acerca de las listas, vea [formularios de lista](http://go.microsoft.com/fwlink/?LinkId=224998) y [vistas de lista](http://go.microsoft.com/fwlink/?LinkId=224999).  
  
## <a name="related-topics"></a>Temas relacionados  
  
|Título|Descripción|  
|-----------|-----------------|  
|[Tutorial: Crear una lista, tipo de contenido y columna de sitio para SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)|Muestra cómo crear columnas de sitio que se usan en un tipo de contenido personalizado. El tipo de contenido, a continuación, se utiliza en una lista personalizada.|  
  
## <a name="see-also"></a>Vea también  
 [Introducción al desarrollo de SharePoint 2010](http://go.microsoft.com/fwlink/?LinkId=225000)  
  
  