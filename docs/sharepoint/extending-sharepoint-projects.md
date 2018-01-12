---
title: Extender proyectos de SharePoint | Documentos de Microsoft
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
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 403ff3793dfd5ae4211444868af8c37dbd908672
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="extending-sharepoint-projects"></a>Extender los proyectos de SharePoint
  Crear una extensión de proyecto cuando desee personalizar características de nivel de proyecto de proyectos de SharePoint. Por ejemplo, puede agregar propiedades de proyecto personalizadas o responder a eventos de nivel de proyecto que se producen cuando el usuario desarrolla una solución de SharePoint en Visual Studio.  
  
## <a name="creating-project-extensions"></a>Crear extensiones de proyecto  
 Para extender un elemento de proyecto, generar un ensamblado de extensión de Visual Studio que implementa el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> interfaz. Para obtener más información, consulte [Cómo: crear una extensión de proyecto de SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
 Cuando se crea una extensión de proyecto, puede agregar también la siguiente funcionalidad a los proyectos de SharePoint:  
  
-   Agregar un elemento de menú contextual. El elemento de menú aparece al abrir el menú contextual para un nodo de proyecto de SharePoint en **el Explorador de soluciones** haciendo clic en el nodo o seleccionarlo y, a continuación, elija la tecla MAYÚS + F10 claves. Para obtener más información, consulte [Cómo: agregar un elemento de menú contextual a los proyectos de SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md).  
  
-   Agregar una propiedad personalizada. La propiedad aparece en la **propiedades** ventana cuando se elige un proyecto de SharePoint en **el Explorador de soluciones**. Para obtener más información, consulte [Cómo: agregar una propiedad a los proyectos de SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).  
  
 Para ver un tutorial que muestra cómo crear, implementar y probar una extensión de proyecto, vea [Tutorial: crear una extensión de proyecto de SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md).  
  
## <a name="understanding-the-relationship-between-project-extensions-and-project-instances"></a>Descripción de la relación entre las extensiones de proyecto y las instancias de proyecto  
 Cuando se crea una extensión de proyecto, la extensión de carga cuando se abre cualquier tipo de proyecto de SharePoint en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]incluye varias plantillas de proyecto de SharePoint, como las definiciones de lista y tipos de contenido, receptores de eventos. Sin embargo, hay solo un tipo de proyecto de SharePoint. Los tipos de proyecto que aparecen en la **nuevo proyecto** cuadro de diálogo solo son plantillas que agrupación uno o varios elementos de proyecto de SharePoint. Dado que hay solo un tipo de proyecto de SharePoint, las extensiones creadas para un proyecto se aplican a todos los proyectos de SharePoint. Por ejemplo, no es posible, cree una extensión que sólo se aplica a un **tipo de contenido** proyecto.  
  
 Para obtener acceso a una instancia de proyecto concreta, controle uno de los <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents> eventos de la *projectService* parámetro en la implementación de la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> método. Por ejemplo, para determinar cuándo se agrega un proyecto de SharePoint a una solución, controle el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectAdded> eventos. Para obtener más información, consulte [Cómo: crear una extensión de proyecto de SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
## <a name="see-also"></a>Vea también  
 [Cómo: crear una extensión de proyecto de SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)   
 [Cómo: agregar un elemento de menú contextual a los proyectos de SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)   
 [Cómo: agregar una propiedad a los proyectos de SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [Tutorial: Crear una extensión de proyecto de SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)   
 [Definir tipos de elemento de proyecto personalizado de SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Extender elementos de proyecto de SharePoint](../sharepoint/extending-sharepoint-project-items.md)   
 [Extensión de SharePoint de empaquetado e implementación](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Extender el sistema de proyectos de SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)  
  
  