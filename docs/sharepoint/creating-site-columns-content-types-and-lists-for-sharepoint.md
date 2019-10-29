---
title: Crear columnas de sitio, tipos de contenido y listas para SharePoint | Microsoft Docs
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
ms.openlocfilehash: 538d82794fcecb91e4f13ab6d7718d0bf407b86f
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/28/2019
ms.locfileid: "72984516"
---
# <a name="create-site-columns-content-types-and-lists-for-sharepoint"></a>Crear columnas de sitio, tipos de contenido y listas para SharePoint
  Visual Studio proporciona plantillas de elementos de proyecto para muchos elementos fundamentales de SharePoint diferentes, como *listas* y *tipos de contenido*, que pueden incorporar columnas de sitio (o *campos*). Los nuevos diseñadores de tipos de contenido y listas hacen que la creación de estos elementos sea más fácil que nunca.

## <a name="site-columns"></a>Columnas del sitio
 Las columnas de sitio son uno de los elementos más básicos que se pueden agregar a un proyecto de SharePoint. Una columna de sitio representa un tipo de datos, como un número de teléfono, un comentario o el nombre de la ciudad de un contacto en una lista de contactos.

 La nueva plantilla de elemento de proyecto de columna de sitio simplifica la creación de columnas de sitio que en la versión anterior de Visual Studio. Después de crear una nueva columna de sitio, puede modificar el código XML del archivo *Elements. XML* de la columna del sitio para incluir la información que desee, como su nombre para mostrar, su tipo de datos y el grupo en el que desea que aparezca la columna de sitio en SharePoint. Para obtener más información sobre las columnas de sitio, vea [Introducción a las columnas](/previous-versions/office/developer/sharepoint-2010/ms450825(v=office.14)).

## <a name="content-types-and-lists"></a>Tipos de contenido y listas
 Los tipos de contenido y las listas se encuentran entre los elementos que se usan con más frecuencia en SharePoint.

 Un tipo de contenido define los metadatos, el flujo de trabajo y el comportamiento de una categoría de elementos en una lista o biblioteca de documentos de SharePoint. Por ejemplo, puede crear un tipo de contenido para obtener información en una lista de contactos o una lista de tareas. Un tipo de contenido de contacto podría incluir columnas como el nombre, el correo electrónico, el número de teléfono y la dirección. Un tipo de contenido que se define en el nivel de sitio es independiente de cualquier biblioteca de listas o documentos del sitio. Puede usar el mismo tipo de contenido con distintas listas o bibliotecas de documentos en el sitio de SharePoint. También puede usar varios tipos de contenido en la misma lista o biblioteca de documentos.

 Una lista es una colección de información de SharePoint que puede compartir con otros usuarios. Las listas se componen de filas de columnas que contienen datos. Algunos ejemplos de listas son: una lista de tareas, una lista de contactos y una lista de anuncios.

 El nuevo tipo de contenido y los diseñadores de listas de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] hacen que la creación de tipos de contenido de sitio y listas sea mucho más sencilla y más intuitiva que en la versión anterior de Visual Studio. La interfaz de usuario permite crear visualmente listas y tipos de contenido de una manera familiar, y permite ordenar y agrupar los datos de las listas y usar los encabezados de grupo. Para obtener más información sobre los tipos de contenido, vea [tipos de contenido](/previous-versions/office/developer/sharepoint-2010/ms479905(v=office.14)). Para obtener más información acerca de las listas, vea [lista de formularios](/previous-versions/office/developer/sharepoint-2010/aa543232(v=office.14)) y [vistas de lista](/previous-versions/office/developer/sharepoint-2010/ff604021(v=office.14)).

## <a name="related-topics"></a>Temas relacionados

|Title|Descripción|
|-----------|-----------------|
|[Tutorial: crear una columna de sitio, un tipo de contenido y una lista para SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)|Muestra cómo crear columnas de sitio que se usan en un tipo de contenido personalizado. A continuación, se usa el tipo de contenido en una lista personalizada.|

## <a name="see-also"></a>Vea también
- [Introducción al desarrollo en SharePoint 2010](/sharepoint/dev/)
