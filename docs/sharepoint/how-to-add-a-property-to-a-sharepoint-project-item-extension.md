---
title: 'Cómo: agregar una propiedad a una extensión de elemento de proyecto de SharePoint | Microsoft Docs'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 752a782bb4aafd977ff10a0b57dd971f7ad6bed4
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584261"
---
# <a name="how-to-add-a-property-to-a-sharepoint-project-item-extension"></a>Cómo: agregar una propiedad a una extensión de elemento de proyecto de SharePoint
  Puede usar una extensión de elemento de proyecto para agregar una propiedad a cualquier elemento de proyecto de SharePoint que ya esté instalado en Visual Studio. La propiedad aparece en la ventana **propiedades** cuando se selecciona el elemento de proyecto en **Explorador de soluciones**.

 En los pasos siguientes se supone que ya ha creado una extensión de elemento de proyecto. Para obtener más información, vea [Cómo: crear una extensión de elemento de proyecto de SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).

### <a name="to-add-a-property-to-a-project-item-extension"></a>Para agregar una propiedad a una extensión de elemento de proyecto

1. Defina una clase con una propiedad pública que represente la propiedad que va a agregar a un tipo de elemento de proyecto. Si desea agregar varias propiedades a un tipo de elemento de proyecto, puede definir todas las propiedades de la misma clase o de clases diferentes.

2. En el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> método de la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> implementación, controle el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> evento del parámetro *projectItemType* .

3. En el controlador de eventos para el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> evento, agregue una instancia de la clase de propiedades a la <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemPropertiesRequestedEventArgs.PropertySources%2A> colección del parámetro de argumentos de evento.

## <a name="example"></a>Ejemplo
 En el ejemplo de código siguiente se muestra cómo agregar una propiedad denominada **ejemplo de propiedad** al elemento de proyecto del receptor de eventos.

 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#8](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemextensionproperty.cs#8)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#8](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemextensionproperty.vb#8)]

### <a name="understand-the-code"></a>Comprendiendo el código
 Para asegurarse de que se utiliza la misma instancia de la `CustomProperties` clase cada vez que <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> se produce el evento, el ejemplo de código agrega el objeto de propiedades a la <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> propiedad del elemento de proyecto la primera vez que se produce este evento. El código recupera este objeto cada vez que se produce de nuevo este evento. Para obtener más información sobre el uso de la <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> propiedad para asociar datos a elementos de proyecto, vea [asociar datos personalizados con extensiones de herramientas de SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).

 Para conservar los cambios en el valor de propiedad, el descriptor de acceso **set** para `ExampleProperty` guarda el nuevo valor en la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> propiedad del <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> objeto al que está asociada la propiedad. Para obtener más información sobre el uso de la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> propiedad para conservar los datos con los elementos de proyecto, vea [guardar datos en extensiones del sistema de proyectos de SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).

### <a name="specify-the-behavior-of-custom-properties"></a>Especificar el comportamiento de las propiedades personalizadas
 Puede definir el modo en que una propiedad personalizada aparece y se comporta en la ventana **propiedades** aplicando atributos del <xref:System.ComponentModel> espacio de nombres a la definición de la propiedad. Los atributos siguientes son útiles en muchos escenarios:

- <xref:System.ComponentModel.DisplayNameAttribute>: Especifica el nombre de la propiedad que aparece en la ventana **propiedades** .

- <xref:System.ComponentModel.DescriptionAttribute>: Especifica la cadena de descripción que aparece en la parte inferior de la ventana **propiedades** cuando se selecciona la propiedad.

- <xref:System.ComponentModel.DefaultValueAttribute>: Especifica el valor predeterminado de la propiedad.

- <xref:System.ComponentModel.TypeConverterAttribute>: Especifica una conversión personalizada entre la cadena que se muestra en la ventana **propiedades** y un valor de propiedad que no es de cadena.

- <xref:System.ComponentModel.EditorAttribute>: Especifica un editor personalizado que se va a utilizar para modificar la propiedad.

## <a name="compile-the-code"></a>Compilar el código
 En estos ejemplos se requiere un proyecto de biblioteca de clases con referencias a los ensamblados siguientes:

- Microsoft.VisualStudio.SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Implementar la extensión
 Para implementar la extensión, cree un [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] paquete de extensión (VSIX) para el ensamblado y cualquier otro archivo que desee distribuir con la extensión. Para obtener más información, vea [deploy Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Vea también
- [Cómo: crear una extensión de elemento de proyecto de SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)
- [Cómo: agregar un elemento de menú contextual a una extensión de elemento de proyecto de SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)
- [Extender elementos de proyecto de SharePoint](../sharepoint/extending-sharepoint-project-items.md)
- [Tutorial: extender un tipo de elemento de proyecto de SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)
