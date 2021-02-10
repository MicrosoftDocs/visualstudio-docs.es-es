---
title: Ampliar proyectos de SharePoint | Microsoft Docs
description: Obtenga información sobre cómo crear una extensión de proyecto cuando desee personalizar características de nivel de proyecto de proyectos de SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 8efeb704bb247e653af0ee062efcc71ad390c5ea
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948666"
---
# <a name="extend-sharepoint-projects"></a>Extender proyectos de SharePoint
  Cree una extensión de proyecto si desea personalizar las características de nivel de proyecto de los proyectos de SharePoint. Por ejemplo, puede Agregar propiedades personalizadas del proyecto o responder a eventos de nivel de proyecto que se producen cuando el usuario desarrolla una solución de SharePoint en Visual Studio.

## <a name="create-project-extensions"></a>Crear extensiones de proyecto
 Para extender un elemento de proyecto, cree un ensamblado de extensión de Visual Studio que implemente la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> interfaz. Para obtener más información, vea [Cómo: crear una extensión de proyecto de SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).

 Al crear una extensión de proyecto, también puede Agregar la siguiente funcionalidad a los proyectos de SharePoint:

- Agregue un elemento de menú contextual. El elemento de menú aparece al abrir el menú contextual de un nodo de proyecto de SharePoint en **Explorador de soluciones** al hacer clic con el botón secundario en el nodo o seleccionarlo y, a continuación, elegir las teclas **MAYÚS** + **F10** . Para obtener más información, vea [Cómo: agregar un elemento de menú contextual a los proyectos de SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md).

- Agregue una propiedad personalizada. La propiedad aparece en la ventana **propiedades** al elegir un proyecto de SharePoint en **Explorador de soluciones**. Para obtener más información, vea [Cómo: agregar una propiedad a proyectos de SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).

  Para ver un tutorial que muestra cómo crear, implementar y probar una extensión de proyecto, vea [Tutorial: crear una extensión de proyecto de SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md).

## <a name="understand-the-relationship-between-project-extensions-and-project-instances"></a>Descripción de la relación entre las extensiones de proyecto y las instancias de proyecto
 Cuando se crea una extensión de proyecto, la extensión se carga cuando se abre cualquier tipo de proyecto de SharePoint en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] incluye varias plantillas de proyecto de SharePoint, como definiciones de lista, tipos de contenido y receptores de eventos. Sin embargo, solo hay un tipo de proyecto de SharePoint. Los tipos de proyecto que aparecen en el cuadro de diálogo **nuevo proyecto** son solo plantillas que agrupan uno o más elementos de proyecto de SharePoint. Dado que solo hay un tipo de proyecto de SharePoint, las extensiones creadas para un proyecto se aplican a todos los proyectos de SharePoint. Por ejemplo, no puede crear una extensión que se aplique solo a un proyecto de **tipo de contenido** .

 Para tener acceso a una instancia de proyecto específica, controle uno de los <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents> eventos del parámetro *projectService* en su implementación del <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> método. Por ejemplo, para determinar cuándo se agrega un proyecto de SharePoint a una solución, controle el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectAdded> evento. Para obtener más información, vea [Cómo: crear una extensión de proyecto de SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).

## <a name="see-also"></a>Vea también
- [Cómo: crear una extensión de proyecto de SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)
- [Cómo: agregar un elemento de menú contextual a los proyectos de SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)
- [Cómo: agregar una propiedad a proyectos de SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)
- [Tutorial: crear una extensión de proyecto de SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)
- [Definir tipos de elementos de proyecto personalizados de SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Extender elementos de proyecto de SharePoint](../sharepoint/extending-sharepoint-project-items.md)
- [Extender el empaquetado e implementación de SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [Extensión del sistema de proyectos de SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)
