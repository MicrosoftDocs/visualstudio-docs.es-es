---
title: Definir tipos de elemento de proyecto personalizado de SharePoint | Documentos de Microsoft
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
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
ms.assetid: be300c24-fd1b-4fc7-a4e9-a5df1d81d3fc
caps.latest.revision: "22"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: e627d78e5c040614c29e7503cd7efab728b02bfa
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="defining-custom-sharepoint-project-item-types"></a>Definir tipos de elementos de proyecto personalizados de SharePoint
  Definir un nuevo tipo de elemento de proyecto de SharePoint al que desea crear un nuevo tipo de elemento de proyecto de SharePoint. Por ejemplo, Visual Studio no incluye elementos de proyecto de SharePoint para agregar campos o acciones personalizadas para un sitio de SharePoint. Puede definir sus propios tipos de elementos de proyecto de SharePoint para crear campos, acciones personalizadas u otros tipos de componentes de SharePoint.  
  
## <a name="tasks-for-defining-sharepoint-project-item-types"></a>Tareas para definir los tipos de elemento de proyecto de SharePoint  
 Para definir un tipo de elemento de proyecto personalizado, generar un ensamblado de extensión de Visual Studio que implementa el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> interfaz. Para obtener más información, consulte [Cómo: definir un tipo de elemento de proyecto de SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).  
  
 Cuando se define un tipo de elemento de proyecto personalizado, también puede agregar la siguiente funcionalidad para el elemento de proyecto:  
  
-   Agregar un elemento de menú contextual para el elemento de proyecto. El elemento de menú aparece al abrir el menú contextual para el elemento de proyecto en **el Explorador de soluciones** haciendo clic en el elemento de proyecto o seleccionándola y, a continuación, elija la tecla MAYÚS + F10 claves. Para obtener más información, consulte [Cómo: agregar un elemento de menú contextual a un tipo de elemento de proyecto de SharePoint personalizado](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md).  
  
-   Agregar una propiedad personalizada para el elemento de proyecto. La propiedad aparece en la **propiedades** ventana cuando se elige el elemento de proyecto en **el Explorador de soluciones**. Para obtener más información, consulte [Cómo: agregar una propiedad a un tipo de elemento de proyecto de SharePoint personalizado](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md).  
  
 Para permitir que otros desarrolladores usen el elemento de proyecto en Visual Studio, cree un archivo .spdata y crear una plantilla de elemento o una plantilla de proyecto que está asociado con el elemento de proyecto. Para obtener más información, consulte [crear plantillas de elementos y las plantillas de proyecto para los elementos de proyecto de SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
## <a name="understanding-the-relationship-between-project-item-types-and-project-item-instances"></a>Descripción de la relación entre los tipos de elemento de proyecto y las instancias de elemento de proyecto  
 Cuando se define un tipo de elemento de proyecto de SharePoint, Visual Studio carga su extensión cuando se agrega un elemento de proyecto del tipo asociado a un proyecto de SharePoint. Por ejemplo, si define un nuevo **la acción personalizada** tipo de elemento de proyecto, Visual Studio carga su extensión cuando un usuario agrega un **la acción personalizada** elemento de proyecto para un proyecto. Visual Studio usa la misma instancia de la extensión para todas las instancias del tipo de elemento de proyecto asociado. En el ejemplo anterior, si el usuario agrega un segundo **la acción personalizada** elementos de proyecto al proyecto, la misma instancia de la extensión se usa para personalizar el segundo elemento de proyecto.  
  
 Para obtener acceso a una instancia específica de su tipo de elemento de proyecto, controle uno de los <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> eventos de la *projectItemTypeDefinition* parámetro en la implementación de la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> método. Por ejemplo, para determinar cuándo se agrega un elemento de proyecto de su tipo personalizado a un proyecto, controle el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> eventos. Para obtener más información, consulte [Cómo: definir un tipo de elemento de proyecto de SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).  
  
## <a name="see-also"></a>Vea también  
 [Cómo: definir un tipo de elemento de proyecto de SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)   
 [Cómo: agregar una propiedad a un tipo de elemento de proyecto personalizado de SharePoint](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)   
 [Cómo: agregar un elemento de menú contextual a un tipo de elemento de proyecto personalizado de SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)   
 [Crear plantillas de proyecto y plantillas de elementos para los elementos de proyecto de SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Tutorial: Crear un elemento de proyecto de acción personalizado con una plantilla de elementos, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [Tutorial: Crear un elemento de proyecto de la columna de sitio con una plantilla de proyecto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)   
 [Tutorial: Crear un elemento de proyecto de acción personalizado con una plantilla de elementos, parte 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)   
 [Tutorial: Crear un elemento de proyecto de la columna de sitio con una plantilla de proyecto, parte 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)   
 [Implementación de extensiones para las herramientas de SharePoint en Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
  