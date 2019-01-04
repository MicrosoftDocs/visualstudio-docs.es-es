---
title: Procedimiento Agregar una propiedad a un tipo de elemento de proyecto personalizado de SharePoint | Documentos de Microsoft
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 44b791c5855838cc8108902305d016fe7f9900ac
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53950490"
---
# <a name="how-to-add-a-property-to-a-custom-sharepoint-project-item-type"></a>Procedimiento Agregar una propiedad a un tipo de elemento de proyecto personalizado de SharePoint
  Al definir un tipo de elemento de proyecto de SharePoint personalizado, puede agregar una propiedad al elemento de proyecto. La propiedad aparece en la **propiedades** ventana cuando se selecciona el elemento de proyecto en **el Explorador de soluciones**.  
  
 Los pasos siguientes se supone que ya se ha definido su propio tipo de elemento de proyecto de SharePoint. Para obtener más información, vea [Cómo: Definir un tipo de elemento de proyecto de SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).  
  
### <a name="to-add-a-property-to-a-definition-of-a-project-item-type"></a>Para agregar una propiedad a una definición de un tipo de elemento de proyecto  
  
1.  Defina una clase con una propiedad pública que representa la propiedad que se va a agregar al tipo de elemento de proyecto personalizado. Si desea agregar varias propiedades a un tipo de elemento de proyecto personalizado, puede definir todas las propiedades de la misma clase o en clases diferentes.  
  
2.  En el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> método de su <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> implementación, el identificador de la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> eventos de la *projectItemTypeDefinition* parámetro.  
  
3.  En el controlador de eventos para el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> evento, agregue una instancia de la clase de propiedades personalizadas para el <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemPropertiesRequestedEventArgs.PropertySources%2A> colección del parámetro de argumentos del evento.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se muestra cómo agregar una propiedad denominada **ejemplo de propiedad** para personalizada proyecto elementos de tipo.  
  
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#11](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb#11)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#11](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs#11)]  
  
### <a name="understand-the-code"></a>Entender el código  
 Para asegurarse de que la misma instancia de la `CustomProperties` clase se usa cada vez que el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> se produce el evento, el ejemplo de código guarda el objeto de propiedades para el <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> propiedad del tiempo del primer elemento de proyecto, este evento se produce. El código recupera un objeto cada vez que este evento se produce de nuevo. Para obtener más información sobre el uso de la <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> propiedad para guardar los datos con elementos de proyecto, vea [asociar datos personalizados con SharePoint de extensiones de herramientas](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).  
  
 Para conservar los cambios realizados en el valor de propiedad, el **establecer** descriptor de acceso para `ExampleProperty` guarda el nuevo valor para el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> propiedad de la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> objeto que está asociada la propiedad. Para obtener más información sobre el uso de la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> propiedad para conservar los datos con elementos de proyecto, vea [guardar datos en las extensiones del sistema del proyecto de SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
### <a name="specify-the-behavior-of-custom-properties"></a>Especificar el comportamiento de las propiedades personalizadas  
 Puede definir cómo una propiedad personalizada aparece y se comporta en la **propiedades** ventana aplicando los atributos de la <xref:System.ComponentModel> espacio de nombres para la definición de propiedad. Los atributos siguientes son útiles en muchos escenarios:  
  
-   <xref:System.ComponentModel.DisplayNameAttribute>: Especifica el nombre de la propiedad que aparece en el **propiedades** ventana.  
  
-   <xref:System.ComponentModel.DescriptionAttribute>: Especifica la cadena de descripción que aparece en la parte inferior de la **propiedades** ventana cuando se selecciona la propiedad.  
  
-   <xref:System.ComponentModel.DefaultValueAttribute>: Especifica el valor predeterminado de la propiedad.  
  
-   <xref:System.ComponentModel.TypeConverterAttribute>: Especifica una conversión personalizada entre la cadena que se muestra en el **propiedades** ventana y un valor de propiedad que no son de cadena.  
  
-   <xref:System.ComponentModel.EditorAttribute>: Especifica un editor personalizado para usar para modificar la propiedad.  
  
## <a name="compile-the-code"></a>Compilar el código  
 Estos ejemplos de código requieren un proyecto de biblioteca de clases con referencias a los ensamblados siguientes:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploy-the-project-item"></a>Implementar el elemento de proyecto  
 Para permitir que otros desarrolladores usen el elemento de proyecto, cree una plantilla de proyecto o una plantilla de elemento de proyecto. Para obtener más información, consulte [crear elementos de plantillas y plantillas de proyecto para los elementos de proyecto de SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
 Para implementar el elemento de proyecto, cree un [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] paquete de extensión (VSIX) para el ensamblado, la plantilla y cualquier otro archivo que desea distribuir con el elemento de proyecto. Para obtener más información, consulte [implementar extensiones para las herramientas de SharePoint en Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Vea también
 [Cómo: Definir un tipo de elemento de proyecto de SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)   
 [Cómo: Agregar un elemento de menú contextual a un tipo de elemento de proyecto personalizado de SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)   
 [Definir tipos de elemento de proyecto de SharePoint personalizados](../sharepoint/defining-custom-sharepoint-project-item-types.md)  
