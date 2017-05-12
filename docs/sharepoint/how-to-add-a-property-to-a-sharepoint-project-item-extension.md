---
title: "How to: Add a Property to a SharePoint Project Item Extension"
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
  - "project items [SharePoint development in Visual Studio], extending"
  - "SharePoint project items, extending"
  - "SharePoint development in Visual Studio, extending project items"
ms.assetid: 4fd97ef2-86e7-4d92-8e34-5b0ec3cc43a0
caps.latest.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# How to: Add a Property to a SharePoint Project Item Extension
  Puede usar una extensión de elemento de proyecto para agregar una propiedad a cualquier elemento de proyecto de SharePoint que ya se encuentre instalado en Visual Studio.  La propiedad aparece en la ventana **Propiedades** cuando se selecciona el elemento de proyecto en el **Explorador de soluciones**.  
  
 En los siguientes pasos se da por supuesto que ha creado una extensión de elemento de proyecto.  Para obtener más información, vea [How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).  
  
### Para agregar una propiedad a una extensión de elemento de proyecto  
  
1.  Defina una clase con una propiedad pública que represente la propiedad que va a agregar a un tipo de elemento de proyecto.  Si desea agregar varias propiedades a un tipo de elemento de proyecto, puede definirlas todas en la misma clase o en clases diferentes.  
  
2.  En el método <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> de la implementación <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>, controle el evento <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> del parámetro *projectItemType*.  
  
3.  En el controlador de eventos del evento <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested>, agregue una instancia de la clase de propiedades a la colección <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemPropertiesRequestedEventArgs.PropertySources%2A> del parámetro de argumentos del evento.  
  
## Ejemplo  
 En el siguiente ejemplo de código se muestra cómo agregar una propiedad denominada **Example Property** al elemento de proyecto de receptor de eventos.  
  
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#8](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/cs/extension/projectitemextensionproperty.cs#8)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#8](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/vb/extension/projectitemextensionproperty.vb#8)]  
  
### Introducción al código  
 Para garantizar que se usa la misma instancia de la clase `CustomProperties` cada vez que se genera el evento <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested>, en el ejemplo de código se agrega el objeto de propiedades a la propiedad <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> del elemento de proyecto la primera vez que se genera este evento.  El código recupera este objeto cada vez que el evento se genera.  Para obtener más información sobre el uso de la propiedad <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> para asociar los datos con los elementos de proyecto, vea [Associating Custom Data with SharePoint Tools Extensions](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).  
  
 Para conservar los cambios en el valor de propiedad, el descriptor de acceso **set** de la propiedad `ExampleProperty` guarda el nuevo valor en la propiedad <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> del objeto <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> al que está asociada la propiedad.  Para obtener más información sobre el uso de la propiedad <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> para mantener los datos con los elementos de proyecto, vea [Saving Data in Extensions of the SharePoint Project System](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
### Especificar el comportamiento de las propiedades personalizadas  
 Puede definir el aspecto y comportamiento de una propiedad personalizada en la ventana **Propiedades** aplicando los atributos del espacio de nombres <xref:System.ComponentModel> a la definición de la propiedad.  Los siguientes atributos son útiles en muchos escenarios:  
  
-   <xref:System.ComponentModel.DisplayNameAttribute>: especifica el nombre de la propiedad que aparece en la ventana **Propiedades**.  
  
-   <xref:System.ComponentModel.DescriptionAttribute>: especifica la cadena descriptiva que aparece en la parte inferior de la ventana **Propiedades** cuando la propiedad está seleccionada.  
  
-   <xref:System.ComponentModel.DefaultValueAttribute> especifica el valor predeterminado de la propiedad.  
  
-   <xref:System.ComponentModel.TypeConverterAttribute>: especifica una conversión personalizada entre la cadena que se muestra en la ventana **Propiedades** y un valor de propiedad que no es de cadena.  
  
-   <xref:System.ComponentModel.EditorAttribute>: especifica un editor personalizado para modificar la propiedad.  
  
## Compilar el código  
 En estos ejemplos se requiere un proyecto de biblioteca de clases con referencias a los siguientes ensamblados:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## Implementar la extensión  
 Para implementar la extensión, cree un paquete de extensión \(VSIX\) de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] para el ensamblado y el resto de archivos que desee distribuir con la extensión.  Para obtener más información, vea [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## Vea también  
 [How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)   
 [How to: Add a Shortcut Menu Item to a SharePoint Project Item Extension](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)   
 [Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md)   
 [Walkthrough: Extending a SharePoint Project Item Type](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)  
  
  