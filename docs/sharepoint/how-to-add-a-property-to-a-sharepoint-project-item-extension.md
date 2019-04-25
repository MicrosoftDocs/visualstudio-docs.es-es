---
title: Procedimiento Agregar una propiedad a una extensión de elemento de proyecto de SharePoint | Documentos de Microsoft
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 20a7abaa8c132b3cd1679ab95ed8154b8ca86502
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60068566"
---
# <a name="how-to-add-a-property-to-a-sharepoint-project-item-extension"></a>Procedimiento Agregar una propiedad a una extensión de elemento de proyecto de SharePoint
  Puede usar una extensión de elemento de proyecto para agregar una propiedad a cualquier elemento de proyecto de SharePoint que ya está instalado en Visual Studio. La propiedad aparece en la **propiedades** ventana cuando se selecciona el elemento de proyecto en **el Explorador de soluciones**.

 Los pasos siguientes se supone que ya ha creado una extensión de elemento de proyecto. Para obtener más información, vea [Cómo: Crear una extensión de elemento de proyecto de SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).

### <a name="to-add-a-property-to-a-project-item-extension"></a>Para agregar una propiedad a una extensión de elemento de proyecto

1. Defina una clase con una propiedad pública que representa la propiedad que se va a agregar a un tipo de elemento de proyecto. Si desea agregar varias propiedades a un tipo de elemento de proyecto, puede definir todas las propiedades de la misma clase o en clases diferentes.

2. En el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> método de su <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> implementación, el identificador de la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> eventos de la *projectItemType* parámetro.

3. En el controlador de eventos para el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> evento, agregue una instancia de la clase de propiedades para el <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemPropertiesRequestedEventArgs.PropertySources%2A> colección del parámetro de argumentos del evento.

## <a name="example"></a>Ejemplo
 En el ejemplo de código siguiente se muestra cómo agregar una propiedad denominada **ejemplo de propiedad** al elemento de proyecto de receptor de eventos.

 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#8](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemextensionproperty.cs#8)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#8](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemextensionproperty.vb#8)]

### <a name="understand-the-code"></a>Entender el código
 Para asegurarse de que la misma instancia de la `CustomProperties` clase se usa cada vez que el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> se produce el evento, el ejemplo de código agrega el objeto de propiedades para el <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> propiedad del tiempo del primer elemento de proyecto, este evento se produce. El código recupera un objeto cada vez que este evento se produce de nuevo. Para obtener más información sobre el uso de la <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> propiedad para asociar los datos con elementos de proyecto, vea [asociar datos personalizados con SharePoint de extensiones de herramientas](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).

 Para conservar los cambios realizados en el valor de propiedad, el **establecer** descriptor de acceso para `ExampleProperty` guarda el nuevo valor para el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> propiedad de la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> objeto que está asociada la propiedad. Para obtener más información sobre el uso de la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> propiedad para conservar los datos con elementos de proyecto, vea [guardar datos en las extensiones del sistema del proyecto de SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).

### <a name="specify-the-behavior-of-custom-properties"></a>Especificar el comportamiento de las propiedades personalizadas
 Puede definir cómo una propiedad personalizada aparece y se comporta en la **propiedades** ventana aplicando los atributos de la <xref:System.ComponentModel> espacio de nombres para la definición de propiedad. Los atributos siguientes son útiles en muchos escenarios:

- <xref:System.ComponentModel.DisplayNameAttribute>: Especifica el nombre de la propiedad que aparece en el **propiedades** ventana.

- <xref:System.ComponentModel.DescriptionAttribute>: Especifica la cadena de descripción que aparece en la parte inferior de la **propiedades** ventana cuando se selecciona la propiedad.

- <xref:System.ComponentModel.DefaultValueAttribute>: Especifica el valor predeterminado de la propiedad.

- <xref:System.ComponentModel.TypeConverterAttribute>: Especifica una conversión personalizada entre la cadena que se muestra en el **propiedades** ventana y un valor de propiedad que no son de cadena.

- <xref:System.ComponentModel.EditorAttribute>: Especifica un editor personalizado para usar para modificar la propiedad.

## <a name="compile-the-code"></a>Compilar el código
 Estos ejemplos requieren un proyecto de biblioteca de clases con referencias a los ensamblados siguientes:

- Microsoft.VisualStudio.SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Implementar la extensión
 Para implementar la extensión, cree un [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] paquete de extensión (VSIX) para el ensamblado y otros archivos que desea distribuir con la extensión. Para obtener más información, consulte [implementar extensiones para las herramientas de SharePoint en Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Vea también
- [Cómo: Crear una extensión de elemento de proyecto de SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)
- [Cómo: Agregar un elemento de menú contextual para una extensión de elemento de proyecto de SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)
- [Extender elementos de proyecto de SharePoint](../sharepoint/extending-sharepoint-project-items.md)
- [Tutorial: Extender un tipo de elemento de proyecto de SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)
