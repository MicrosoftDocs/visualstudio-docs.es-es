---
title: Extender elementos de proyecto de SharePoint | Documentos de Microsoft
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
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
ms.assetid: f09f6664-196d-46d6-819f-3c6500f23536
caps.latest.revision: "22"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8f17e43e2fe98e36939c91b37e72b185cb14d09e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="extending-sharepoint-project-items"></a>Extender elementos de proyecto de SharePoint
  Crear una extensión de elemento de proyecto cuando desee agregar funcionalidad a un tipo de elemento de proyecto de SharePoint que ya está instalado en Visual Studio. Por ejemplo, puede crear una extensión para integrado **receptor de eventos** o **definición de lista** elementos de proyecto de Visual Studio, o puede crear una extensión para un tipo de elemento de proyecto personalizado. También puede crear una extensión para todos los tipos de elementos de proyecto de SharePoint.  
  
## <a name="tasks-for-extending-sharepoint-project-items"></a>Tareas para extender elementos de proyecto de SharePoint  
 Para extender un elemento de proyecto, generar un ensamblado de extensión de Visual Studio que implementa el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> interfaz. Para obtener más información, consulte [Cómo: crear una extensión de elemento de proyecto de SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).  
  
 Cuando se amplía un elemento de proyecto, también puede agregar la siguiente funcionalidad para el elemento de proyecto:  
  
-   Agregar un elemento de menú contextual para el elemento de proyecto. El elemento de menú aparece al abrir el menú contextual para el elemento de proyecto en **el Explorador de soluciones**. Abra el menú contextual haciendo clic en el elemento de proyecto o seleccionándola y, a continuación, elija la tecla MAYÚS + F10 claves. Para obtener más información, consulte [Cómo: agregar un elemento de menú contextual a una extensión de elemento de proyecto de SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md).  
  
-   Agregar una propiedad personalizada para el elemento de proyecto. La propiedad aparece en la **propiedades** ventana cuando se elige el elemento de proyecto en **el Explorador de soluciones**. Para obtener más información, consulte [Cómo: agregar una propiedad a una extensión de elemento de proyecto de SharePoint](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md).  
  
 Para ver un tutorial que muestra cómo crear, implementar y probar una extensión de elemento de proyecto, vea [Tutorial: Extender un tipo de elemento de proyecto de SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md).  
  
## <a name="understanding-the-relationship-between-project-item-extensions-and-project-item-instances"></a>Descripción de la relación entre las extensiones de elemento de proyecto y las instancias de elemento de proyecto  
 Cuando se crea una extensión de elemento de proyecto, Visual Studio carga su extensión cuando se agrega un elemento de proyecto del tipo asociado a un proyecto de SharePoint. Por ejemplo, si crea una extensión para **receptor de eventos** elementos de proyecto, Visual Studio carga su extensión cuando un usuario agrega un **receptor de eventos** elemento de proyecto para un proyecto. Visual Studio usa la misma instancia de la extensión para todas las instancias del tipo de elemento de proyecto asociado. En el ejemplo anterior, si el usuario agrega un segundo **receptor de eventos** elementos de proyecto al proyecto, la misma instancia de la extensión se usa para personalizar el segundo elemento de proyecto.  
  
 Para obtener acceso a una instancia concreta del tipo de elemento de proyecto está ampliando, controle uno de los <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> eventos de la *projectItemType* parámetro en la implementación de la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> método. Por ejemplo, para determinar cuando se agrega un elemento de proyecto del tipo está ampliando a un proyecto, controle el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> eventos. Para obtener más información, consulte [Cómo: crear una extensión de elemento de proyecto de SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).  
  
## <a name="identifiers-for-sharepoint-project-items"></a>Identificadores de elementos de proyecto de SharePoint  
 Cada elemento de proyecto de SharePoint tiene un identificador de cadena correspondiente. Debe conocer el identificador de un elemento de proyecto si desea realizar las siguientes tareas:  
  
-   Crear una extensión del elemento de proyecto. En este caso, debe pasar el identificador del elemento de proyecto que desea extender al constructor de la <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. Para crear una extensión para todos los elementos de proyecto tipos, pasar la  **\***  valor de cadena.  
  
-   Agregar el elemento de proyecto a un proyecto mediante programación. En este caso, debe pasar el identificador del elemento de proyecto para el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemCollection.Add%2A> método.  
  
 En la tabla siguiente enumera los identificadores de los elementos de proyecto de SharePoint que se incluyen con Visual Studio.  
  
|Nombre del elemento de proyecto|Identificador de cadena|  
|-----------------------|-----------------------|  
|Modelo de catálogo de datos profesionales|Microsoft.VisualStudio.SharePoint.BusinessDataConnectivity|  
|Tipo de contenido|Microsoft.VisualStudio.SharePoint.ContentType|  
|Receptor de eventos|Microsoft.VisualStudio.SharePoint.EventHandler|  
|Elemento vacío|Microsoft.VisualStudio.SharePoint.GenericElement|  
|Definición de lista<br /><br /> Definición de lista de tipo de contenido|Microsoft.VisualStudio.SharePoint.ListDefinition|  
|Instancia de lista|Microsoft.VisualStudio.SharePoint.ListInstance|  
|Módulo|Microsoft.VisualStudio.SharePoint.Module|  
|Flujo de trabajo secuencial<br /><br /> Flujo de trabajo de equipo de estado|Microsoft.VisualStudio.SharePoint.Workflow|  
|Definición de sitio|Microsoft.VisualStudio.SharePoint.SiteDefinition|  
|Elemento web visual|Microsoft.VisualStudio.SharePoint.VisualWebPart|  
|Elemento web|Microsoft.VisualStudio.SharePoint.WebPart|  
|Formulario de asociación de flujo de trabajo|Microsoft.VisualStudio.SharePoint.WorkflowAssociation|  
  
## <a name="see-also"></a>Vea también  
 [Cómo: crear una extensión de elemento de proyecto de SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)   
 [Cómo: agregar un elemento de menú contextual a una extensión de elemento de proyecto de SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)   
 [Cómo: agregar una propiedad a una extensión de elemento de proyecto de SharePoint](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md)   
 [Tutorial: Extender un tipo de elemento de proyecto de SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)   
 [Extender el sistema de proyectos de SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)  
  