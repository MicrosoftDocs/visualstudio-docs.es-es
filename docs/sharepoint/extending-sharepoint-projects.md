---
title: Extender proyectos de SharePoint | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 56e714f910a2421a909cba6714e65d21b66991ce
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49835844"
---
# <a name="extend-sharepoint-projects"></a>Extender los proyectos de SharePoint
  Crear una extensión de proyecto cuando desea personalizar las características de nivel de proyecto de proyectos de SharePoint. Por ejemplo, puede agregar propiedades de proyecto personalizadas o responder a eventos de nivel de proyecto que se generan cuando el usuario desarrolla una solución de SharePoint en Visual Studio.  
  
## <a name="create-project-extensions"></a>Crear extensiones de proyecto
 Para extender un elemento de proyecto, compilar un ensamblado de extensión de Visual Studio que implementa el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> interfaz. Para obtener más información, consulte [Cómo: crear una extensión de proyecto de SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
 Cuando se crea una extensión de proyecto, también puede agregar la siguiente funcionalidad a los proyectos de SharePoint:  
  
- Agregue un elemento de menú contextual. El elemento de menú aparece al abrir el menú contextual de un nodo de proyecto de SharePoint en **el Explorador de soluciones** haciendo clic en el nodo o seleccionarlo y, a continuación, elegir el **MAYÚS** +  **F10** claves. Para obtener más información, consulte [Cómo: agregar un elemento de menú contextual a los proyectos de SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md).  
  
- Agregar una propiedad personalizada. La propiedad aparece en la **propiedades** ventana cuando se elige un proyecto de SharePoint en **el Explorador de soluciones**. Para obtener más información, consulte [Cómo: agregar una propiedad a proyectos de SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).  
  
  Para ver un tutorial que muestra cómo crear, implementar y probar una extensión de proyecto, vea [Tutorial: crear una extensión de proyecto de SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md).  
  
## <a name="understand-the-relationship-between-project-extensions-and-project-instances"></a>Comprender la relación entre las extensiones de proyecto y las instancias de proyecto
 Cuando se crea una extensión de proyecto, la extensión de carga cuando se abre cualquier tipo de proyecto de SharePoint en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] incluye varias plantillas de proyecto de SharePoint, como las definiciones de listas, tipos de contenido y los receptores de eventos. Sin embargo, hay solo un tipo de proyecto de SharePoint. Los tipos de proyectos que aparecen en la **nuevo proyecto** cuadro de diálogo solo son plantillas que agrupación uno o varios elementos de proyecto de SharePoint. Dado que hay solo un tipo de proyecto de SharePoint, las extensiones creadas para un proyecto se aplican a todos los proyectos de SharePoint. Por ejemplo, no es posible, cree una extensión que solo se aplica a un **tipo de contenido** proyecto.  
  
 Para tener acceso a una instancia específica del proyecto, controle uno de los <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents> eventos de la *projectService* parámetro en la implementación de la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> método. Por ejemplo, para determinar cuándo se agrega un proyecto de SharePoint a una solución, controle el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectAdded> eventos. Para obtener más información, consulte [Cómo: crear una extensión de proyecto de SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
## <a name="see-also"></a>Vea también
 [Cómo: crear una extensión de proyecto de SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)   
 [Cómo: agregar un elemento de menú contextual a los proyectos de SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)   
 [Cómo: agregar una propiedad a proyectos de SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [Tutorial: Crear una extensión de proyecto de SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)   
 [Definir tipos de elemento de proyecto de SharePoint personalizados](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Extender elementos de proyecto de SharePoint](../sharepoint/extending-sharepoint-project-items.md)   
 [Ampliar la implementación y empaquetado de SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Extender el sistema de proyecto de SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)  
  
  
