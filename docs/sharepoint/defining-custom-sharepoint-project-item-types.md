---
title: Definir tipos de elemento de proyecto personalizado de SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 52d1940b38fbf2cbe24e1e35bc56fb7372f50c89
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2019
ms.locfileid: "54865910"
---
# <a name="define-custom-sharepoint-project-item-types"></a>Definir tipos de elemento de proyecto de SharePoint personalizados
  Definir un nuevo tipo de elemento de proyecto de SharePoint cuando desea crear un nuevo tipo de elemento de proyecto de SharePoint. Por ejemplo, Visual Studio no incluye elementos de proyecto de SharePoint para agregar campos o acciones personalizadas a un sitio de SharePoint. Puede definir sus propios tipos de elementos de proyecto de SharePoint para crear campos, acciones personalizadas u otros tipos de componentes de SharePoint.  
  
## <a name="tasks-for-defining-sharepoint-project-item-types"></a>Tareas para definir tipos de elemento de proyecto de SharePoint
 Para definir un tipo de elemento de proyecto personalizado, cree un ensamblado de extensión de Visual Studio que implementa el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> interfaz. Para obtener más información, vea [Cómo: Definir un tipo de elemento de proyecto de SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).  
  
 Al definir un tipo de elemento de proyecto personalizado, también puede agregar la siguiente funcionalidad para el elemento de proyecto:  
  
- Agregue un elemento de menú contextual para el elemento de proyecto. El elemento de menú aparece al abrir el menú contextual para el elemento de proyecto en **el Explorador de soluciones** haciendo clic con el elemento de proyecto o seleccionarlo y, a continuación, eligiendo el **MAYÚS** +  **F10** claves. Para obtener más información, vea [Cómo: Agregar un elemento de menú contextual a un tipo de elemento de proyecto de SharePoint personalizado](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md).  
  
- Agregar una propiedad personalizada para el elemento de proyecto. La propiedad aparece en la **propiedades** ventana cuando se elige el elemento de proyecto en **el Explorador de soluciones**. Para obtener más información, vea [Cómo: Agregar una propiedad a un tipo de elemento de proyecto de SharePoint personalizado](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md).  
  
  Para permitir que otros desarrolladores usen el elemento de proyecto en Visual Studio, cree un archivo .spdata y cree una plantilla de elemento o una plantilla de proyecto que está asociado con el elemento de proyecto. Para obtener más información, consulte [crear elementos de plantillas y plantillas de proyecto para los elementos de proyecto de SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
## <a name="understand-the-relationship-between-project-item-types-and-project-item-instances"></a>Comprender la relación entre los tipos de elemento de proyecto y las instancias de elemento de proyecto
 Al definir un tipo de elemento de proyecto de SharePoint, Visual Studio carga su extensión cuando se agrega un elemento de proyecto del tipo asociado a un proyecto de SharePoint. Por ejemplo, si define un nuevo **acción personalizada** tipo de elemento de proyecto, Visual Studio carga su extensión cuando un usuario agrega un **acción personalizada** elemento de proyecto a un proyecto. Visual Studio usa la misma instancia de la extensión para todas las instancias del tipo de elemento de proyecto asociado. En el ejemplo anterior, si el usuario agrega un segundo **acción personalizada** elemento de proyecto al proyecto, la misma instancia de la extensión se usa para personalizar el segundo elemento de proyecto.  
  
 Para obtener acceso a una instancia específica del tipo de elemento de proyecto, controle uno de los <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> eventos de la *projectItemTypeDefinition* parámetro en la implementación de la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> método. Por ejemplo, para determinar cuándo se agrega un elemento de proyecto del tipo personalizado a un proyecto, controle el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> eventos. Para obtener más información, vea [Cómo: Definir un tipo de elemento de proyecto de SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).  
  
## <a name="see-also"></a>Vea también
 [Cómo: Definir un tipo de elemento de proyecto de SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)   
 [Cómo: Agregar una propiedad a un tipo de elemento de proyecto personalizado de SharePoint](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)   
 [Cómo: Agregar un elemento de menú contextual a un tipo de elemento de proyecto personalizado de SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)   
 [Crear plantillas de elemento y plantillas de proyecto para los elementos de proyecto de SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Tutorial: Crear elemento de proyecto de acción personalizado con una plantilla de elementos, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [Tutorial: Crear elemento de proyecto de columna de sitio con una plantilla de proyecto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)   
 [Tutorial: Creación de un elemento de proyecto de acción personalizado con una plantilla de elementos, parte 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)   
 [Tutorial: Creación de un elemento de proyecto de la columna de sitio con una plantilla de proyecto, parte 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)   
 [Implementar extensiones para las herramientas de SharePoint en Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
