---
title: Extender elementos de proyecto de SharePoint | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b83d5f92a54d58aae2d4c7860e6648920615d63f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49823637"
---
# <a name="extend-sharepoint-project-items"></a>Extender elementos de proyecto de SharePoint
  Crear una extensión de elemento de proyecto cuando desea agregar funcionalidad a un tipo de elemento de proyecto de SharePoint que ya está instalada en Visual Studio. Por ejemplo, puede crear una extensión para integrado **receptor de eventos** o **definición de lista** los elementos de proyecto de Visual Studio, o puede crear una extensión para un tipo de elemento de proyecto personalizado. También puede crear una extensión para todos los tipos de elementos de proyecto de SharePoint.  
  
## <a name="tasks-for-extending-sharepoint-project-items"></a>Tareas para extender elementos de proyecto de SharePoint
 Para extender un elemento de proyecto, compilar un ensamblado de extensión de Visual Studio que implementa el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> interfaz. Para obtener más información, consulte [Cómo: crear una extensión de elemento de proyecto de SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).  
  
 Cuando se amplía un elemento de proyecto, también puede agregar la siguiente funcionalidad para el elemento de proyecto:  
  
- Agregue un elemento de menú contextual para el elemento de proyecto. El elemento de menú aparece al abrir el menú contextual para el elemento de proyecto en **el Explorador de soluciones**. Abra el menú contextual haciendo clic con el elemento de proyecto o seleccionarlo y, a continuación, eligiendo el **MAYÚS**+**F10** claves. Para obtener más información, consulte [Cómo: agregar un elemento de menú contextual para una extensión de elemento de proyecto de SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md).  
  
- Agregar una propiedad personalizada para el elemento de proyecto. La propiedad aparece en la **propiedades** ventana cuando se elige el elemento de proyecto en **el Explorador de soluciones**. Para obtener más información, consulte [Cómo: agregar una propiedad a una extensión de elemento de proyecto de SharePoint](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md).  
  
  Para ver un tutorial que muestra cómo crear, implementar y probar una extensión de elemento de proyecto, vea [Tutorial: Extender un tipo de elemento de proyecto de SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md).  
  
## <a name="understand-the-relationship-between-project-item-extensions-and-project-item-instances"></a>Comprender la relación entre las extensiones de elemento de proyecto y las instancias de elemento de proyecto
 Cuando se crea una extensión de elemento de proyecto, Visual Studio carga su extensión cuando se agrega un elemento de proyecto del tipo asociado a un proyecto de SharePoint. Por ejemplo, si crea una extensión para **receptor de eventos** elementos de proyecto, Visual Studio carga su extensión cuando un usuario agrega un **receptor de eventos** elemento de proyecto a un proyecto. Visual Studio usa la misma instancia de la extensión para todas las instancias del tipo de elemento de proyecto asociado. En el ejemplo anterior, si el usuario agrega un segundo **receptor de eventos** elemento de proyecto al proyecto, la misma instancia de la extensión se usa para personalizar el segundo elemento de proyecto.  
  
 Para obtener acceso a una instancia específica del tipo de elemento de proyecto que está extendiendo, controle uno de los <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> eventos de la *projectItemType* parámetro en la implementación de la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> método. Por ejemplo, para determinar cuando se agrega un elemento de proyecto del tipo está ampliando a un proyecto, controle el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> eventos. Para obtener más información, consulte [Cómo: crear una extensión de elemento de proyecto de SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).  
  
## <a name="identifiers-for-sharepoint-project-items"></a>Identificadores para los elementos de proyecto de SharePoint
 Cada elemento de proyecto de SharePoint tiene un identificador de cadena correspondiente. Debe conocer el identificador para un elemento de proyecto si desea realizar las siguientes tareas:  
  
- Crear una extensión para el elemento de proyecto. En este caso, debe pasar el identificador del elemento de proyecto que desee extender al constructor de la <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. Para crear una extensión para todos los tipos de proyecto elemento, pase el **\\*** valor de cadena.  
  
- Agregar el elemento de proyecto a un proyecto mediante programación. En este caso, debe pasar el identificador del elemento de proyecto para el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemCollection.Add%2A> método.  
  
  En la tabla siguiente se enumera los identificadores de los elementos de proyecto de SharePoint que se incluyen con Visual Studio.  
  
|Nombre del elemento de proyecto|Identificador de cadena|  
|-----------------------|-----------------------|  
|Modelo del catálogo de datos profesionales|Microsoft.VisualStudio.SharePoint.BusinessDataConnectivity|  
|Tipo de contenido|Microsoft.VisualStudio.SharePoint.ContentType|  
|Receptor de eventos|Microsoft.VisualStudio.SharePoint.EventHandler|  
|Elemento vacío|Microsoft.VisualStudio.SharePoint.GenericElement|  
|Definición de lista<br /><br /> Definición de lista del tipo de contenido|Microsoft.VisualStudio.SharePoint.ListDefinition|  
|Instancia de lista|Microsoft.VisualStudio.SharePoint.ListInstance|  
|Module|Microsoft.VisualStudio.SharePoint.Module|  
|Flujo de trabajo secuencial<br /><br /> Flujo de trabajo de equipo de estado|Microsoft.VisualStudio.SharePoint.Workflow|  
|Definición de sitio|Microsoft.VisualStudio.SharePoint.SiteDefinition|  
|Elemento web visual|Microsoft.VisualStudio.SharePoint.VisualWebPart|  
|Elemento web|Microsoft.VisualStudio.SharePoint.WebPart|  
|Formulario de asociación de flujo de trabajo|Microsoft.VisualStudio.SharePoint.WorkflowAssociation|  
  
## <a name="see-also"></a>Vea también
 [Cómo: crear una extensión de elemento de proyecto de SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)   
 [Cómo: agregar un elemento de menú contextual para una extensión de elemento de proyecto de SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)   
 [Cómo: agregar una propiedad a una extensión de elemento de proyecto de SharePoint](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md)   
 [Tutorial: Extender un tipo de elemento de proyecto de SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)   
 [Extender el sistema de proyecto de SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)  
  
