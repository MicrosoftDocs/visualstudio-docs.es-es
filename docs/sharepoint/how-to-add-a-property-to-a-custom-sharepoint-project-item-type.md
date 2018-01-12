---
title: "Cómo: agregar una propiedad a un tipo de elemento de proyecto de SharePoint personalizado | Documentos de Microsoft"
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
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: fa11cdfa8b46b6dcba889e00068676af5bdd5450
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-add-a-property-to-a-custom-sharepoint-project-item-type"></a>Cómo: Agregar una propiedad a un tipo de elemento de proyecto personalizado de SharePoint
  Cuando se define un tipo de elemento de proyecto de SharePoint personalizado, puede agregar una propiedad al elemento de proyecto. La propiedad aparece en la **propiedades** ventana cuando se selecciona el elemento de proyecto en **el Explorador de soluciones**.  
  
 Los pasos siguientes se supone que ya se ha definido su propio tipo de elemento de proyecto de SharePoint. Para obtener más información, consulte [Cómo: definir un tipo de elemento de proyecto de SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).  
  
### <a name="to-add-a-property-to-a-definition-of-a-project-item-type"></a>Para agregar una propiedad a una definición de un tipo de elemento de proyecto  
  
1.  Defina una clase con una propiedad pública que representa la propiedad que se va a agregar al tipo de elemento de proyecto personalizado. Si desea agregar varias propiedades a un tipo de elemento de proyecto personalizado, puede definir todas las propiedades de la misma clase o en clases diferentes.  
  
2.  En el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> método de su <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> implementación, el identificador de la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> eventos de la *projectItemTypeDefinition* parámetro.  
  
3.  En el controlador de eventos para el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> eventos, debe agregar una instancia de la clase de propiedades personalizadas para el <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemPropertiesRequestedEventArgs.PropertySources%2A> colección del parámetro de argumentos del evento.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se muestra cómo agregar una propiedad denominada **Example Property** a un personalizado de elementos de proyecto tipo.  
  
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#11](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb#11)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#11](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs#11)]  
  
### <a name="understanding-the-code"></a>Descripción del código  
 Para asegurarse de que la misma instancia de la `CustomProperties` clase se utiliza cada vez que la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> se produce el evento, el ejemplo de código guarda el objeto de propiedades para el <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> propiedad de la hora del primer elemento de proyecto se produce este evento. El código recupera un objeto cada vez que este evento se produce de nuevo. Para obtener más información sobre el uso de la <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> propiedad que se va a guardar los datos con los elementos de proyecto, vea [asociar datos personalizados con extensiones de herramientas de SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).  
  
 Para conservar los cambios en el valor de propiedad, el **establecer** descriptor de acceso para `ExampleProperty` guarda el nuevo valor para el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> propiedad de la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> objeto asociado a la propiedad. Para obtener más información sobre el uso de la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> propiedad para conservar los datos con los elementos de proyecto, vea [guardar datos en las extensiones del sistema del proyecto de SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
### <a name="specifying-the-behavior-of-custom-properties"></a>Especifica el comportamiento de propiedades personalizadas  
 Puede definir cómo aparece una propiedad personalizada y cómo se comporta en la **propiedades** ventana aplicando los atributos de la <xref:System.ComponentModel> espacio de nombres para la definición de propiedad. Los siguientes atributos son útiles en muchos escenarios:  
  
-   <xref:System.ComponentModel.DisplayNameAttribute>: Especifica el nombre de la propiedad que aparece en el **propiedades** ventana.  
  
-   <xref:System.ComponentModel.DescriptionAttribute>: Especifica la cadena de descripción que aparece en la parte inferior de la **propiedades** ventana cuando se selecciona la propiedad.  
  
-   <xref:System.ComponentModel.DefaultValueAttribute>: Especifica el valor predeterminado de la propiedad.  
  
-   <xref:System.ComponentModel.TypeConverterAttribute>: Especifica una conversión personalizada entre la cadena que se muestra en el **propiedades** ventana y un valor de propiedad no es una cadena.  
  
-   <xref:System.ComponentModel.EditorAttribute>: Especifica un editor personalizado para utilizar para modificar la propiedad.  
  
## <a name="compiling-the-code"></a>Compilar el código  
 Estos ejemplos de código necesita un proyecto de biblioteca de clases con referencias a los ensamblados siguientes:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-project-item"></a>Implementar el elemento de proyecto  
 Para permitir que otros desarrolladores usen el elemento de proyecto, cree una plantilla de proyecto o una plantilla de elemento de proyecto. Para obtener más información, consulte [crear plantillas de elementos y las plantillas de proyecto para los elementos de proyecto de SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
 Para implementar el elemento de proyecto, crear un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] paquete de extensión (VSIX) para el ensamblado, la plantilla y cualquier otro archivo que desee distribuir con el elemento de proyecto. Para obtener más información, consulte [extensiones de implementación para las herramientas de SharePoint en Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Vea también  
 [Cómo: definir un tipo de elemento de proyecto de SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)   
 [Cómo: agregar un elemento de menú contextual a un tipo de elemento de proyecto personalizado de SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)   
 [Definición de tipos de elementos de proyecto personalizados de SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md)  
  
  