---
title: 'Cómo: agregar una propiedad a los proyectos de SharePoint | Documentos de Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 44e82b15ff2d4bdfaac5e8e9eca672ecdc1780a9
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/05/2018
ms.locfileid: "34767626"
---
# <a name="how-to-add-a-property-to-sharepoint-projects"></a>Cómo: agregar una propiedad a los proyectos de SharePoint
  Puede utilizar una extensión de proyecto para agregar una propiedad a un proyecto de SharePoint. La propiedad aparece en la **propiedades** ventana cuando se selecciona el proyecto en **el Explorador de soluciones**.  
  
 Los pasos siguientes se supone que ya ha creado una extensión de proyecto. Para obtener más información, consulte [Cómo: crear una extensión de proyecto de SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
### <a name="to-add-a-property-to-a-sharepoint-project"></a>Para agregar una propiedad a un proyecto de SharePoint  
  
1.  Defina una clase con una propiedad pública que representa la propiedad que se va a agregar a los proyectos de SharePoint. Si desea agregar varias propiedades, puede definir todas las propiedades de la misma clase o en clases diferentes.  
  
2.  En el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> método de su <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> implementación, el identificador de la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> eventos de la *projectService* parámetro.  
  
3.  En el controlador de eventos para el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> eventos, debe agregar una instancia de la clase de propiedades para el <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectPropertiesRequestedEventArgs.PropertySources%2A> colección del parámetro de argumentos del evento.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se muestra cómo agregar dos propiedades a los proyectos de SharePoint. Una propiedad conserva sus datos en el archivo de opción de usuario de proyecto (la *. csproj.user* archivo o *. vbproj.user* archivo). La otra propiedad conserva sus datos en el archivo de proyecto (*.csproj* archivo o *.vbproj* archivo).  
  
 [!code-vb[SpExt_SPCustomPrjProperty#1](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#1)]
 [!code-csharp[SpExt_SPCustomPrjProperty#1](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#1)]  
  
### <a name="understanding-the-code"></a>Descripción del código  
 Para asegurarse de que la misma instancia de la `CustomProjectProperties` clase se utiliza cada vez que la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> se produce el evento, el ejemplo de código agrega el objeto de propiedades a la <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> propiedad del proyecto la primera vez que se produce este evento. El código recupera un objeto cada vez que este evento se produce de nuevo. Para obtener más información sobre el uso de la <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> propiedad que se va a asociar los datos a los proyectos, vea [asociar datos personalizados con extensiones de herramientas de SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).  
  
 Para conservar los cambios en los valores de propiedad, el **establecer** descriptores de acceso para las propiedades utilizan las API siguientes:  
  
-   `CustomUserFileProperty` usa el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A> propiedad que se va a guardar su valor en el archivo de opción de usuario de proyecto.  
  
-   `CustomProjectFileProperty` usa el <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> método para guardar su valor en el archivo de proyecto.  
  
 Para obtener más información sobre cómo guardar datos en estos archivos, consulte [guardar datos en las extensiones del sistema del proyecto de SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
### <a name="specifying-the-behavior-of-custom-properties"></a>Especifica el comportamiento de propiedades personalizadas  
 Puede definir cómo aparece una propiedad personalizada y cómo se comporta en la **propiedades** ventana aplicando los atributos de la <xref:System.ComponentModel> espacio de nombres para la definición de propiedad. Los siguientes atributos son útiles en muchos escenarios:  
  
-   <xref:System.ComponentModel.DisplayNameAttribute>: Especifica el nombre de la propiedad que aparece en el **propiedades** ventana.  
  
-   <xref:System.ComponentModel.DescriptionAttribute>: Especifica la cadena de descripción que aparece en la parte inferior de la **propiedades** ventana cuando se selecciona la propiedad.  
  
-   <xref:System.ComponentModel.DefaultValueAttribute>: Especifica el valor predeterminado de la propiedad.  
  
-   <xref:System.ComponentModel.TypeConverterAttribute>: Especifica una conversión personalizada entre la cadena que se muestra en el **propiedades** ventana y un valor de propiedad no es una cadena.  
  
-   <xref:System.ComponentModel.EditorAttribute>: Especifica un editor personalizado para utilizar para modificar la propiedad.  
  
## <a name="compiling-the-code"></a>Compilación del código  
 Este ejemplo requiere referencias a los siguientes ensamblados:  
  
-   Microsoft.VisualStudio.SharePoint
-    
-   Microsoft.VisualStudio.Shell
-     
-   Microsoft.VisualStudio.Shell.Interop
-     
-   Microsoft.VisualStudio.Shell.Interop.8.0
-     
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-extension"></a>Implementar la extensión  
 Para implementar la extensión, cree un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] paquete de extensión (VSIX) para el ensamblado y cualquier otro archivo que desee distribuir con la extensión. Para obtener más información, consulte [extensiones de implementación para las herramientas de SharePoint en Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Vea también
 [Extender proyectos de SharePoint](../sharepoint/extending-sharepoint-projects.md)   
 [Cómo: crear una extensión de proyecto de SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)   
 [Cómo: agregar un elemento de menú contextual a los proyectos de SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)   
 [Extender el sistema de proyectos de SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)  
  
  
