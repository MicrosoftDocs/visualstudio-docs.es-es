---
title: Definir tipos de elementos de proyecto personalizados de SharePoint | Microsoft Docs
description: Defina un tipo de elemento de proyecto de SharePoint personalizado cuando desee crear un nuevo tipo de elemento de proyecto de SharePoint.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: fc2e3670dd734b368795f270fa6c1d63c8c079e8
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672839"
---
# <a name="define-custom-sharepoint-project-item-types"></a>Definir tipos de elementos de proyecto personalizados de SharePoint
  Defina un nuevo tipo de elemento de proyecto de SharePoint si desea crear un nuevo tipo de elemento de proyecto de SharePoint. Por ejemplo, Visual Studio no incluye elementos de proyecto de SharePoint para agregar campos o acciones personalizadas a un sitio de SharePoint. Puede definir sus propios tipos de elementos de proyecto de SharePoint para crear campos, acciones personalizadas u otros tipos de componentes de SharePoint.

## <a name="tasks-for-defining-sharepoint-project-item-types"></a>Tareas para definir tipos de elementos de proyecto de SharePoint
 Para definir un tipo de elemento de proyecto personalizado, cree un ensamblado de extensión de Visual Studio que implemente la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> interfaz. Para obtener más información, vea [Cómo: definir un tipo de elemento de proyecto de SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).

 Al definir un tipo de elemento de proyecto personalizado, también puede Agregar la siguiente funcionalidad al elemento de proyecto:

- Agregue un elemento de menú contextual al elemento de proyecto. El elemento de menú aparece al abrir el menú contextual del elemento de proyecto en **Explorador de soluciones** al hacer clic con el botón secundario en el elemento de proyecto o al elegirlo y, a continuación, elegir las teclas **MAYÚS** + **F10** . Para obtener más información, vea [Cómo: agregar un elemento de menú contextual a un tipo de elemento de proyecto personalizado de SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md).

- Agregue una propiedad personalizada al elemento de proyecto. La propiedad aparece en la ventana **propiedades** cuando se elige el elemento de proyecto en **Explorador de soluciones**. Para obtener más información, vea [Cómo: agregar una propiedad a un tipo de elemento de proyecto personalizado de SharePoint](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md).

  Para que otros desarrolladores puedan usar el elemento de proyecto en Visual Studio, cree un archivo. spdata y cree una plantilla de elemento o una plantilla de proyecto asociada al elemento de proyecto. Para obtener más información, vea [crear plantillas de elemento y plantillas de proyecto para los elementos de proyecto de SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

## <a name="understand-the-relationship-between-project-item-types-and-project-item-instances"></a>Comprender la relación entre los tipos de elemento de proyecto y las instancias de elemento de proyecto
 Al definir un tipo de elemento de proyecto de SharePoint, Visual Studio carga la extensión cuando un elemento de proyecto del tipo asociado se agrega a un proyecto de SharePoint. Por ejemplo, si define un nuevo tipo de elemento de proyecto **acción personalizada** , Visual Studio carga la extensión cuando un usuario agrega un elemento de proyecto **acción personalizada** a un proyecto. Visual Studio usa la misma instancia de la extensión para todas las instancias del tipo de elemento de proyecto asociado. En el ejemplo anterior, si el usuario agrega un segundo elemento de proyecto de **acción personalizada** al proyecto, se usa la misma instancia de la extensión para personalizar el segundo elemento de proyecto.

 Para tener acceso a una instancia específica del tipo de elemento de proyecto, controle uno de los <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> eventos del parámetro *projectItemTypeDefinition* en la implementación del <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> método. Por ejemplo, para determinar cuándo se agrega un elemento de proyecto del tipo personalizado a un proyecto, controle el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> evento. Para obtener más información, vea [Cómo: definir un tipo de elemento de proyecto de SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).

## <a name="see-also"></a>Consulte también
- [Cómo: definir un tipo de elemento de proyecto de SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)
- [Cómo: agregar una propiedad a un tipo de elemento de proyecto personalizado de SharePoint](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)
- [Cómo: agregar un elemento de menú contextual a un tipo de elemento de proyecto personalizado de SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)
- [Crear plantillas de elemento y plantillas de proyecto para los elementos de proyecto de SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [Tutorial: crear un elemento de proyecto de acción personalizado con una plantilla de elemento, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [Tutorial: crear un elemento de proyecto de columna de sitio con una plantilla de proyecto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)
- [Tutorial: crear un elemento de proyecto de acción personalizado con una plantilla de elemento, parte 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)
- [Tutorial: crear un elemento de proyecto de columna de sitio con una plantilla de proyecto, parte 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)
- [Implementación de extensiones para las herramientas de SharePoint en Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)
