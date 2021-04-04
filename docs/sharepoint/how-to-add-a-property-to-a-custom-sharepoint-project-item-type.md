---
title: Agregar propiedad a un tipo de elemento de proyecto personalizado de SharePoint
description: Agregue una propiedad a un tipo de elemento de proyecto personalizado de SharePoint. La propiedad aparece en el ventana Propiedades cuando se selecciona el elemento de proyecto en Explorador de soluciones.
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
ms.openlocfilehash: 17d9ac144b97c090292395dd5ae5e85319dd1308
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2021
ms.locfileid: "106215518"
---
# <a name="how-to-add-a-property-to-a-custom-sharepoint-project-item-type"></a>Cómo: agregar una propiedad a un tipo de elemento de proyecto personalizado de SharePoint
  Al definir un tipo de elemento de proyecto de SharePoint personalizado, puede Agregar una propiedad al elemento de proyecto. La propiedad aparece en la ventana **propiedades** cuando se selecciona el elemento de proyecto en **Explorador de soluciones**.

 En los pasos siguientes se supone que ya ha definido su propio tipo de elemento de proyecto de SharePoint. Para obtener más información, vea [Cómo: definir un tipo de elemento de proyecto de SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).

### <a name="to-add-a-property-to-a-definition-of-a-project-item-type"></a>Para agregar una propiedad a una definición de un tipo de elemento de proyecto

1. Defina una clase con una propiedad pública que represente la propiedad que va a agregar al tipo de elemento de proyecto personalizado. Si desea agregar varias propiedades a un tipo de elemento de proyecto personalizado, puede definir todas las propiedades de la misma clase o de clases diferentes.

2. En el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> método de la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> implementación, controle el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> evento del parámetro *projectItemTypeDefinition* .

3. En el controlador de eventos para el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> evento, agregue una instancia de la clase de propiedades personalizadas a la <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemPropertiesRequestedEventArgs.PropertySources%2A> colección del parámetro de argumentos de evento.

## <a name="example"></a>Ejemplo
 En el ejemplo de código siguiente se muestra cómo agregar una propiedad denominada **propiedad de ejemplo** a un tipo de elemento de proyecto personalizado.

 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb" id="Snippet11":::
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs" id="Snippet11":::

### <a name="understand-the-code"></a>Comprendiendo el código
 Para asegurarse de que se utiliza la misma instancia de la `CustomProperties` clase cada vez que <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> se produce el evento, el ejemplo de código guarda el objeto de propiedades en la <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> propiedad del elemento de proyecto la primera vez que se produce este evento. El código recupera este objeto cada vez que se produce de nuevo este evento. Para obtener más información sobre cómo usar la <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> propiedad para guardar datos con elementos de proyecto, vea [asociar datos personalizados con extensiones de herramientas de SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).

 Para conservar los cambios en el valor de propiedad, el descriptor de acceso **set** para `ExampleProperty` guarda el nuevo valor en la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> propiedad del <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> objeto al que está asociada la propiedad. Para obtener más información sobre el uso de la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> propiedad para conservar los datos con los elementos de proyecto, vea [guardar datos en extensiones del sistema de proyectos de SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).

### <a name="specify-the-behavior-of-custom-properties"></a>Especificar el comportamiento de las propiedades personalizadas
 Puede definir el modo en que una propiedad personalizada aparece y se comporta en la ventana **propiedades** aplicando atributos del <xref:System.ComponentModel> espacio de nombres a la definición de la propiedad. Los atributos siguientes son útiles en muchos escenarios:

- <xref:System.ComponentModel.DisplayNameAttribute>: Especifica el nombre de la propiedad que aparece en la ventana **propiedades** .

- <xref:System.ComponentModel.DescriptionAttribute>: Especifica la cadena de descripción que aparece en la parte inferior de la ventana **propiedades** cuando se selecciona la propiedad.

- <xref:System.ComponentModel.DefaultValueAttribute>: Especifica el valor predeterminado de la propiedad.

- <xref:System.ComponentModel.TypeConverterAttribute>: Especifica una conversión personalizada entre la cadena que se muestra en la ventana **propiedades** y un valor de propiedad que no es de cadena.

- <xref:System.ComponentModel.EditorAttribute>: Especifica un editor personalizado que se va a utilizar para modificar la propiedad.

## <a name="compile-the-code"></a>Compilar el código
 Estos ejemplos de código requieren un proyecto de biblioteca de clases con referencias a los ensamblados siguientes:

- Microsoft.VisualStudio.SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-project-item"></a>Implementar el elemento de proyecto
 Para permitir que otros desarrolladores utilicen el elemento de proyecto, cree una plantilla de proyecto o una plantilla de elemento de proyecto. Para obtener más información, vea [crear plantillas de elemento y plantillas de proyecto para los elementos de proyecto de SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

 Para implementar el elemento de proyecto, cree un [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] paquete de extensión (VSIX) para el ensamblado, la plantilla y cualquier otro archivo que desee distribuir con el elemento de proyecto. Para obtener más información, vea [deploy Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Consulte también
- [Cómo: definir un tipo de elemento de proyecto de SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)
- [Cómo: agregar un elemento de menú contextual a un tipo de elemento de proyecto personalizado de SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)
- [Definir tipos de elementos de proyecto personalizados de SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md)
