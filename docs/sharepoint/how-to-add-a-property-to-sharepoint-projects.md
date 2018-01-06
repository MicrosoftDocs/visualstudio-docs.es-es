---
title: "Cómo: agregar una propiedad a los proyectos de SharePoint | Documentos de Microsoft"
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
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
ms.assetid: c5eb4900-c35f-490a-b856-bf167da2d293
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 290f5d4b3632d5c3ee40e7171aa4a0ed967004dc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-a-property-to-sharepoint-projects"></a>Cómo: Agregar una propiedad a proyectos de SharePoint
  Puede utilizar una extensión de proyecto para agregar una propiedad a un proyecto de SharePoint. La propiedad aparece en la **propiedades** ventana cuando se selecciona el proyecto en **el Explorador de soluciones**.  
  
 Los pasos siguientes se supone que ya ha creado una extensión de proyecto. Para obtener más información, consulte [Cómo: crear una extensión de proyecto de SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
### <a name="to-add-a-property-to-a-sharepoint-project"></a>Para agregar una propiedad a un proyecto de SharePoint  
  
1.  Defina una clase con una propiedad pública que representa la propiedad que se va a agregar a los proyectos de SharePoint. Si desea agregar varias propiedades, puede definir todas las propiedades de la misma clase o en clases diferentes.  
  
2.  En el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> método de su <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> implementación, el identificador de la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> eventos de la *projectService* parámetro.  
  
3.  En el controlador de eventos para el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> eventos, debe agregar una instancia de la clase de propiedades para el <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectPropertiesRequestedEventArgs.PropertySources%2A> colección del parámetro de argumentos del evento.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se muestra cómo agregar dos propiedades a los proyectos de SharePoint. Una propiedad conserva sus datos en el archivo de opción de usuario de proyecto (el. archivo csproj.user o. vbproj.user archivo). La otra propiedad conserva sus datos en el archivo de proyecto (archivo .csproj o .vbproj).  
  
 [!code-vb[SpExt_SPCustomPrjProperty#1](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#1)]
 [!code-csharp[SpExt_SPCustomPrjProperty#1](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#1)]  
  
### <a name="understanding-the-code"></a>Descripción del código  
 Para asegurarse de que la misma instancia de la `CustomProjectProperties` clase se utiliza cada vez que la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> se produce el evento, el ejemplo de código agrega el objeto de propiedades a la <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> propiedad del proyecto la primera vez que se produce este evento. El código recupera un objeto cada vez que este evento se produce de nuevo. Para obtener más información sobre el uso de la <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> propiedad que se va a asociar los datos a los proyectos, vea [asociar datos personalizados con extensiones de herramientas de SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).  
  
 Para conservar los cambios en los valores de propiedad, el **establecer** descriptores de acceso para las propiedades utilizan las API siguientes:  
  
-   `CustomUserFileProperty`usa el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A> propiedad que se va a guardar su valor en el archivo de opción de usuario de proyecto.  
  
-   `CustomProjectFileProperty`usa el <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> método para guardar su valor en el archivo de proyecto.  
  
 Para obtener más información sobre cómo guardar datos en estos archivos, consulte [guardar datos en las extensiones del sistema del proyecto de SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
### <a name="specifying-the-behavior-of-custom-properties"></a>Especifica el comportamiento de propiedades personalizadas  
 Puede definir cómo aparece una propiedad personalizada y cómo se comporta en la **propiedades** ventana aplicando los atributos de la <xref:System.ComponentModel> espacio de nombres para la definición de propiedad. Los siguientes atributos son útiles en muchos escenarios:  
  
-   <xref:System.ComponentModel.DisplayNameAttribute>: Especifica el nombre de la propiedad que aparece en el **propiedades** ventana.  
  
-   <xref:System.ComponentModel.DescriptionAttribute>: Especifica la cadena de descripción que aparece en la parte inferior de la **propiedades** ventana cuando se selecciona la propiedad.  
  
-   <xref:System.ComponentModel.DefaultValueAttribute>: Especifica el valor predeterminado de la propiedad.  
  
-   <xref:System.ComponentModel.TypeConverterAttribute>: Especifica una conversión personalizada entre la cadena que se muestra en el **propiedades** ventana y un valor de propiedad no es una cadena.  
  
-   <xref:System.ComponentModel.EditorAttribute>: Especifica un editor personalizado para utilizar para modificar la propiedad.  
  
## <a name="compiling-the-code"></a>Compilar el código  
 Este ejemplo requiere referencias a los siguientes ensamblados:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   Microsoft.VisualStudio.Shell  
  
-   Microsoft.VisualStudio.Shell.Interop  
  
-   Microsoft.VisualStudio.Shell.Interop.8.0  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-extension"></a>Implementar la extensión  
 Para implementar la extensión, cree un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] paquete de extensión (VSIX) para el ensamblado y cualquier otro archivo que desee distribuir con la extensión. Para obtener más información, consulte [extensiones de implementación para las herramientas de SharePoint en Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Vea también  
 [Extender proyectos de SharePoint](../sharepoint/extending-sharepoint-projects.md)   
 [Cómo: crear una extensión de proyecto de SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)   
 [Cómo: agregar un elemento de menú contextual a los proyectos de SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)   
 [Extender el sistema de proyectos de SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)  
  
  