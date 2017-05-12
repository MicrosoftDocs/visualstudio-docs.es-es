---
title: "Crear listas, tipos de contenido y columnas de sitio para SharePoint"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.ListDesigner.ContentTypeSetting"
  - "VS.SharePointTools.ContentTypeDesigner.CommonPropertiesPage"
  - "VS.SharePointTools.ListDesigner.CreatingLists"
  - "VS.SharePointTools.ListDesigner.ListPage"
  - "VS.SharePointTools.ListDesigner.ViewPage"
  - "VS.SharePointTools.ListDesigner.CommonPropertiesPage"
  - "VS.SharePointTools.ContentTypeDesigner.ColumnsPage"
dev_langs: 
  - "VB"
  - "CSharp"
ms.assetid: 9ceed263-3aec-41dc-8708-63cb37a08fa8
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# Crear listas, tipos de contenido y columnas de sitio para SharePoint
  Visual Studio incluye plantillas de elemento de proyecto para diferentes elementos fundamentales de SharePoint, incluidos *listas* y *tipos de contenido*, que pueden especificar columnas de sitio \(o *campos*\).  Los nuevos diseñadores para los tipos de contenido y listas crean creando estos elementos más fácil que nunca.  
  
## Columnas de sitio  
 Las columnas de sitio son uno de los elementos más básicos que puede agregar a un proyecto de SharePoint.  Una columna de sitio representa un tipo de datos, como un número de teléfono, un comentario, o el nombre de la ciudad de un contacto en una lista de contactos.  
  
 La nueva plantilla de elemento de proyecto de columnas de sitio permite la creación de columnas de sitio más fácil que en la versión anterior de Visual Studio.  Después de crear una nueva columna de sitio, puede modificar XML en el archivo Elements.xml de la columna de sitio para incluir la información que desee, como su nombre para mostrar, su tipo de datos, y al grupo en el que desea que la columna de sitio aparezca en SharePoint.  Para obtener más información sobre columnas de sitio, vea [Introducción a las columnas](http://go.microsoft.com/fwlink/?LinkId=224996).  
  
## Tipos de contenido y listas  
 Los tipos de contenido y las listas están entre frecuentemente los elementos utilizados en SharePoint.  
  
 Un tipo de contenido define los metadatos, el flujo de trabajo, y el comportamiento de una categoría de elementos en una lista de SharePoint o una biblioteca de documentos.  Por ejemplo, puede crear un tipo de contenido de la información en una lista de contactos o una lista de tareas.  Un tipo de contenido de contacto podría incluir columnas como nombre, correo electrónico, número de teléfono, y dirección.  Un tipo de contenido que se define en el nivel de sitio es independiente de cualquier lista o biblioteca de documentos en el sitio.  Puede utilizar el mismo tipo de contenido con varias listas o bibliotecas de documentos en el sitio de SharePoint.  También puede utilizar varios tipos de contenido en la misma lista o biblioteca de documentos.  
  
 Una lista es una colección de información en SharePoint que puede compartir con otros.  Las listas se componen de filas de columnas que contienen datos.  Algunos ejemplos de las listas: una lista de tareas, una lista de contactos, y una lista de anuncios.  
  
 El nuevo tipo de contenido y los diseñadores mostrados en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] crean crear tipos de contenido y listas de sitio más fáciles y más intuitivos que en la versión anterior de Visual Studio.  La interfaz de usuario permite crear visualmente los tipos de contenido y listas de una manera familiarizado, y permite ordenar y agrupar datos de listas y utilizar encabezados de grupo.  Para obtener más información sobre los tipos de contenido, vea [Tipos de contenido](http://go.microsoft.com/fwlink/?LinkId=224997).  Para obtener más información sobre las listas, vea [Formularios de lista](http://go.microsoft.com/fwlink/?LinkId=224998) y [Vistas de lista](http://go.microsoft.com/fwlink/?LinkId=224999).  
  
## Temas relacionados  
  
|Título|Descripción|  
|------------|-----------------|  
|[Tutorial: Crear una lista, tipo de contenido y columna de sitio para SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)|Muestra cómo crear las columnas de sitio que se utilizan en un tipo de contenido personalizado.  A continuación se utiliza el tipo de contenido en una lista personalizada.|  
  
## Vea también  
 [Obtenga el convertir iniciado en SharePoint 2010](http://go.microsoft.com/fwlink/?LinkId=225000)  
  
  