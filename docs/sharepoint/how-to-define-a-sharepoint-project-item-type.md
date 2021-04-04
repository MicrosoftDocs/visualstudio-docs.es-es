---
title: 'Cómo: definir un tipo de elemento de proyecto de SharePoint | Microsoft Docs'
description: Aprenda a definir un tipo de elemento de proyecto cuando desee crear un elemento de proyecto de SharePoint personalizado.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 16e7070769edf3ee65ee425a7f9cb5062da315cd
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216831"
---
# <a name="how-to-define-a-sharepoint-project-item-type"></a>Cómo: definir un tipo de elemento de proyecto de SharePoint
  Defina un tipo de elemento de proyecto cuando desee crear un elemento de proyecto de SharePoint personalizado. Para obtener más información, vea [definir tipos de elementos de proyecto personalizados de SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md).

### <a name="to-define-a-project-item-type"></a>Para definir un tipo de elemento de proyecto

1. Cree un proyecto de biblioteca de clases.

2. Agregue referencias a los siguientes ensamblados:

    - Microsoft.VisualStudio.SharePoint

    - System.ComponentModel.Composition

3. Cree una clase que implemente la interfaz <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>.

4. Agregue los siguientes atributos a la clase:

    - <xref:System.ComponentModel.Composition.ExportAttribute>. Este atributo permite a Visual Studio detectar y cargar la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> implementación. Pase el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> tipo al constructor de atributo.

    - <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. En una definición de tipo de elemento de proyecto, este atributo especifica el identificador de cadena para el nuevo elemento de proyecto. Se recomienda usar el formato nombre de la *compañía*. *nombre* de la característica para asegurarse de que todos los elementos de proyecto tienen un nombre único.

    - <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemIconAttribute>. Este atributo especifica el icono que se va a mostrar para este elemento de proyecto en **Explorador de soluciones**. Este atributo es opcional; Si no lo aplica a la clase, Visual Studio muestra un icono predeterminado para el elemento de proyecto. Si establece este atributo, pase el nombre completo de un icono o mapa de bits incrustado en el ensamblado.

5. En la implementación del <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> método, use los miembros del parámetro *projectItemTypeDefinition* para definir el comportamiento del tipo de elemento de proyecto. Este parámetro es un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> objeto que proporciona acceso a los eventos definidos en las <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFileEvents> interfaces y. Para tener acceso a una instancia específica del tipo de elemento de proyecto, controle <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> eventos como <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> y <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemInitialized> .

## <a name="example"></a>Ejemplo
 En el ejemplo de código siguiente se muestra cómo definir un tipo de elemento de proyecto simple. Este tipo de elemento de proyecto escribe un mensaje en la ventana de **salida** y **lista de errores** ventana cuando un usuario agrega un elemento de proyecto de este tipo a un proyecto.

 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/projectitemtype.vb" id="Snippet2":::
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/projectitemtype.cs" id="Snippet2":::

 En este ejemplo se usa el servicio de proyecto de SharePoint para escribir el mensaje en la ventana de **salida** y **lista de errores** ventana. Para obtener más información, vea [usar el servicio de proyecto de SharePoint](../sharepoint/using-the-sharepoint-project-service.md).

## <a name="compile-the-code"></a>Compilar el código
 Este ejemplo requiere referencias a los ensamblados siguientes:

- Microsoft.VisualStudio.SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-project-item"></a>Implementar el elemento de proyecto
 Para permitir que otros desarrolladores utilicen el elemento de proyecto, cree una plantilla de proyecto o una plantilla de elemento de proyecto. Para obtener más información, vea [crear plantillas de elemento y plantillas de proyecto para los elementos de proyecto de SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

 Para implementar el elemento de proyecto, cree un [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] paquete de extensión (VSIX) para el ensamblado, la plantilla y cualquier otro archivo que desee distribuir con el elemento de proyecto. Para obtener más información, vea [deploy Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Consulte también
- [Definir tipos de elementos de proyecto personalizados de SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Crear plantillas de elemento y plantillas de proyecto para los elementos de proyecto de SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [Tutorial: crear un elemento de proyecto de acción personalizado con una plantilla de elemento, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [Tutorial: crear un elemento de proyecto de columna de sitio con una plantilla de proyecto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)
- [Cómo: agregar una propiedad a un tipo de elemento de proyecto personalizado de SharePoint](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)
- [Cómo: agregar un elemento de menú contextual a un tipo de elemento de proyecto personalizado de SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)
