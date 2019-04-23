---
title: Procedimiento Definir un tipo de elemento de proyecto de SharePoint | Documentos de Microsoft
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
ms.openlocfilehash: 0e0483f535dfd7a483d2b83728f78fa9c7167bcb
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60061442"
---
# <a name="how-to-define-a-sharepoint-project-item-type"></a>Procedimiento Definir un tipo de elemento de proyecto de SharePoint
  Definir un tipo de elemento de proyecto cuando desee crear un elemento de proyecto de SharePoint personalizado. Para obtener más información, consulte [definir tipos de elemento de proyecto de SharePoint personalizados](../sharepoint/defining-custom-sharepoint-project-item-types.md).

### <a name="to-define-a-project-item-type"></a>Para definir un tipo de elemento de proyecto

1. Cree un proyecto de biblioteca de clases.

2. Agregue referencias a los siguientes ensamblados:

    - Microsoft.VisualStudio.SharePoint

    - System.ComponentModel.Composition

3. Cree una clase que implemente la interfaz <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>.

4. Agregue los siguientes atributos a la clase:

    - <xref:System.ComponentModel.Composition.ExportAttribute>. Este atributo permite que Visual Studio detecte y cargue su <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> implementación. Pase el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> tipo al constructor del atributo.

    - <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. En una definición de tipo de elemento de proyecto, este atributo especifica el identificador de cadena para el nuevo elemento de proyecto. Le recomendamos que use el formato *nombre de la compañía*. *nombre de la característica* para ayudar a asegurarse de que todos los elementos del proyecto tienen un nombre único.

    - <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemIconAttribute>. Este atributo especifica el icono para mostrar para este elemento de proyecto en **el Explorador de soluciones**. Este atributo es opcional; Si no se aplican a la clase, Visual Studio muestra un icono predeterminado para el elemento de proyecto. Si establece este atributo, pase el nombre completo de un icono o mapa de bits que se incrusta en el ensamblado.

5. En la implementación de la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> método, los miembros del uso de la *projectItemTypeDefinition* parámetro para definir el comportamiento del tipo de elemento de proyecto. Este parámetro es un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> objeto que proporciona acceso a los eventos definidos en el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> y <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFileEvents> interfaces. Para obtener acceso a una instancia específica del tipo de elemento de proyecto, controlar <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> eventos, como <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> y <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemInitialized>.

## <a name="example"></a>Ejemplo
 El ejemplo de código siguiente muestra cómo definir un tipo de elemento de proyecto simple. Este tipo de elemento de proyecto escribe un mensaje en el **salida** ventana y **lista de errores** ventana cuando un usuario agrega un elemento de proyecto de este tipo a un proyecto.

 [!code-vb[SPExtensibility.ProjectSystemExtension.General#2](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/projectitemtype.vb#2)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#2](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/projectitemtype.cs#2)]

 En este ejemplo usa el servicio de proyecto de SharePoint para escribir el mensaje a la **salida** ventana y **lista de errores** ventana. Para obtener más información, consulte [usar el servicio de proyecto de SharePoint](../sharepoint/using-the-sharepoint-project-service.md).

## <a name="compile-the-code"></a>Compilar el código
 Este ejemplo requiere referencias a los ensamblados siguientes:

- Microsoft.VisualStudio.SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-project-item"></a>Implementar el elemento de proyecto
 Para permitir que otros desarrolladores usen el elemento de proyecto, cree una plantilla de proyecto o una plantilla de elemento de proyecto. Para obtener más información, consulte [crear elementos de plantillas y plantillas de proyecto para los elementos de proyecto de SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

 Para implementar el elemento de proyecto, cree un [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] paquete de extensión (VSIX) para el ensamblado, la plantilla y cualquier otro archivo que desea distribuir con el elemento de proyecto. Para obtener más información, consulte [herramientas de implementación de extensiones de SharePoint en Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Vea también
- [Definir tipos de elemento de proyecto de SharePoint personalizados](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Crear plantillas de elemento y plantillas de proyecto para los elementos de proyecto de SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [Tutorial: Creación de un elemento de proyecto de acción personalizado con una plantilla de elementos, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [Tutorial: Creación de un elemento de proyecto de la columna de sitio con una plantilla de proyecto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)
- [Cómo: Agregar una propiedad a un tipo de elemento de proyecto personalizado de SharePoint](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)
- [Cómo: Agregar un elemento de menú contextual a un tipo de elemento de proyecto personalizado de SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)
