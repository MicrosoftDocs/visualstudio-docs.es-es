---
title: "How to: Add a Property to a Custom SharePoint Project Item Type"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "SharePoint project items, defining your own types"
  - "project items [SharePoint development in Visual Studio], defining your own types"
  - "SharePoint development in Visual Studio, defining new project item types"
ms.assetid: 47e940f6-1779-4530-aea6-c43a370c544f
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# How to: Add a Property to a Custom SharePoint Project Item Type
  Cuando se define un tipo de elemento de proyecto de SharePoint personalizado, se puede agregar una propiedad al elemento de proyecto.  La propiedad aparece en la ventana **Propiedades** cuando se selecciona el elemento de proyecto en el **Explorador de soluciones**.  
  
 En los siguientes pasos se supone que ha definido un tipo de elemento de proyecto de SharePoint.  Para obtener más información, vea [How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).  
  
### Para agregar una propiedad a una definición de un tipo de elemento de proyecto  
  
1.  Defina una clase con una propiedad pública que represente la propiedad que va a agregar al tipo de elemento de proyecto personalizado.  Si desea agregar varias propiedades a un tipo de elemento de proyecto personalizado, puede definirlas todas en la misma clase o en clases diferentes.  
  
2.  En el método <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> de la implementación <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>, controle el evento <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> del parámetro *projectItemTypeDefinition*.  
  
3.  En el controlador de eventos del evento <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested>, agregue una instancia de la clase de propiedades personalizada a la colección <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemPropertiesRequestedEventArgs.PropertySources%2A> del parámetro de argumentos del evento.  
  
## Ejemplo  
 En el siguiente ejemplo de código se muestra cómo agregar una propiedad denominada **Example Property** a un tipo de elemento de proyecto personalizado.  
  
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#11](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/cs/extension/projectitemtypeproperty.cs#11)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#11](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/vb/extension/projectitemtypeproperty.vb#11)]  
  
### Introducción al código  
 Para garantizar que se usa la misma instancia de la clase `CustomProperties` cada vez que se genera el evento <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested>, el ejemplo de código guarda el objeto de propiedades en la propiedad <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> del elemento de proyecto la primera vez que se genera este evento.  El código recupera este objeto cada vez que el evento se genera.  Para obtener más información sobre el uso de la propiedad <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> para guardar los datos con los elementos de proyecto, vea [Associating Custom Data with SharePoint Tools Extensions](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).  
  
 Para conservar los cambios en el valor de propiedad, el descriptor de acceso **set** de la propiedad `ExampleProperty` guarda el nuevo valor en la propiedad <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> del objeto <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> al que está asociada la propiedad.  Para obtener más información sobre el uso de la propiedad <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> para mantener los datos con los elementos de proyecto, vea [Saving Data in Extensions of the SharePoint Project System](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
### Especificar el comportamiento de las propiedades personalizadas  
 Puede definir el aspecto y comportamiento de una propiedad personalizada en la ventana **Propiedades** aplicando los atributos del espacio de nombres <xref:System.ComponentModel> a la definición de la propiedad.  Los siguientes atributos son útiles en muchos escenarios:  
  
-   <xref:System.ComponentModel.DisplayNameAttribute>: especifica el nombre de la propiedad que aparece en la ventana **Propiedades**.  
  
-   <xref:System.ComponentModel.DescriptionAttribute>: especifica la cadena descriptiva que aparece en la parte inferior de la ventana **Propiedades** cuando la propiedad está seleccionada.  
  
-   <xref:System.ComponentModel.DefaultValueAttribute> especifica el valor predeterminado de la propiedad.  
  
-   <xref:System.ComponentModel.TypeConverterAttribute>: especifica una conversión personalizada entre la cadena que se muestra en la ventana **Propiedades** y un valor de propiedad que no es de cadena.  
  
-   <xref:System.ComponentModel.EditorAttribute>: especifica un editor personalizado para modificar la propiedad.  
  
## Compilar el código  
 En estos ejemplos de código se requiere un proyecto de biblioteca de clases con referencias a los siguientes ensamblados:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## Implementar el elemento de proyecto  
 Para permitir que otros desarrolladores usen el elemento de proyecto, cree una plantilla de proyecto o una plantilla de elemento de proyecto.  Para obtener más información, vea [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
 Para implementar el elemento de proyecto, cree un paquete de extensión \(VSIX\) de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] para el ensamblado, la plantilla y cualquier otro archivo que desee distribuir con el elemento de proyecto.  Para obtener más información, vea [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## Vea también  
 [How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)   
 [How to: Add a Shortcut Menu Item to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)   
 [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md)  
  
  