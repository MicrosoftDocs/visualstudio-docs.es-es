---
title: "How to: Add a Property to SharePoint Projects"
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
  - "projects [SharePoint development in Visual Studio], extending"
  - "SharePoint development in Visual Studio, extending projects"
  - "SharePoint projects, extending"
ms.assetid: c5eb4900-c35f-490a-b856-bf167da2d293
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# How to: Add a Property to SharePoint Projects
  Puede usar una extensión de proyecto para agregar una propiedad a cualquier proyecto de SharePoint.  La propiedad aparece en la ventana **Propiedades** cuando se selecciona el proyecto en el **Explorador de soluciones**.  
  
 En los siguientes pasos se presupone que ya ha creado una extensión de proyecto.  Para obtener más información, vea [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
### Para agregar una propiedad a un proyecto de SharePoint  
  
1.  Defina una clase con una propiedad pública que represente la propiedad que va a agregar a los proyectos de SharePoint.  Si desea agregar varias propiedades, puede definirlas todas en la misma clase o en clases diferentes.  
  
2.  En el método <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> de la implementación <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>, controle el evento <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> del parámetro *projectService*.  
  
3.  En el controlador de eventos del evento <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested>, agregue una instancia de la clase de propiedades a la colección <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectPropertiesRequestedEventArgs.PropertySources%2A> del parámetro de argumentos del evento.  
  
## Ejemplo  
 En el ejemplo de código siguiente se muestra cómo agregar dos propiedades a los proyectos de SharePoint.  Una propiedad conserva los datos en el archivo de opciones de usuario del proyecto \(el archivo .csproj.user o .vbproj.user\).  La otra propiedad conserva los datos en el archivo de proyecto \(archivo .csproj o .vbproj\).  
  
 [!code-csharp[SpExt_SPCustomPrjProperty#1](../snippets/csharp/VS_Snippets_OfficeSP/spext_spcustomprjproperty/cs/customspproperty/customproperty.cs#1)]
 [!code-vb[SpExt_SPCustomPrjProperty#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spext_spcustomprjproperty/vb/customspproperty/customproperty.vb#1)]  
  
### Introducción al código  
 Para garantizar que se usa la misma instancia de la clase `CustomProjectProperties` cada vez que se genera el evento <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested>, el ejemplo de código agrega el objeto de propiedades a la propiedad <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> del proyecto la primera vez que se genera este evento.  El código recupera este objeto cada vez que el evento se genera.  Para obtener más información sobre el uso de la propiedad <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> para asociar los datos con los proyectos, vea [Associating Custom Data with SharePoint Tools Extensions](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).  
  
 Para conservar los cambios a los valores de propiedad, los descriptores de acceso **set** de las propiedades usan las API siguientes:  
  
-   `CustomUserFileProperty` usa la propiedad <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A> para guardar su valor en el archivo de opciones de usuario del proyecto.  
  
-   `CustomProjectFileProperty` usa el método <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> para guardar su valor en el archivo de proyecto.  
  
 Para obtener más información sobre la persistencia de datos en estos archivos, vea [Saving Data in Extensions of the SharePoint Project System](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
### Especificar el comportamiento de las propiedades personalizadas  
 Puede definir el aspecto y comportamiento de una propiedad personalizada en la ventana **Propiedades** aplicando los atributos del espacio de nombres <xref:System.ComponentModel> a la definición de la propiedad.  Los siguientes atributos son útiles en muchos escenarios:  
  
-   <xref:System.ComponentModel.DisplayNameAttribute>: especifica el nombre de la propiedad que aparece en la ventana **Propiedades**.  
  
-   <xref:System.ComponentModel.DescriptionAttribute>: especifica la cadena descriptiva que aparece en la parte inferior de la ventana **Propiedades** cuando la propiedad está seleccionada.  
  
-   <xref:System.ComponentModel.DefaultValueAttribute> especifica el valor predeterminado de la propiedad.  
  
-   <xref:System.ComponentModel.TypeConverterAttribute>: especifica una conversión personalizada entre la cadena que se muestra en la ventana **Propiedades** y un valor de propiedad que no es de cadena.  
  
-   <xref:System.ComponentModel.EditorAttribute>: especifica un editor personalizado para modificar la propiedad.  
  
## Compilar el código  
 Para este ejemplo se requieren referencias a los siguientes ensamblados:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   Microsoft.VisualStudio.Shell  
  
-   Microsoft.VisualStudio.Shell.Interop  
  
-   Microsoft.VisualStudio.Shell.Interop.8.0  
  
-   System.ComponentModel.Composition  
  
## Implementar la extensión  
 Para implementar la extensión, cree un paquete de extensión \(VSIX\) de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] para el ensamblado y el resto de archivos que desee distribuir con la extensión.  Para obtener más información, vea [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## Vea también  
 [Extending SharePoint Projects](../sharepoint/extending-sharepoint-projects.md)   
 [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md)   
 [How to: Add a Shortcut Menu Item to SharePoint Projects](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)   
 [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)  
  
  