---
title: 'Cómo: agregar una propiedad a proyectos de SharePoint | Microsoft Docs'
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
ms.openlocfilehash: 015725197c2c269a7b6aed2e20f0159e2a9f2fe6
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2018
ms.locfileid: "36758564"
---
# <a name="how-to-add-a-property-to-sharepoint-projects"></a>Cómo: agregar una propiedad a proyectos de SharePoint
  Puede usar una extensión de proyecto para agregar una propiedad a un proyecto de SharePoint. La propiedad aparece en la **propiedades** ventana cuando se selecciona el proyecto en **el Explorador de soluciones**.  
  
 Los pasos siguientes se supone que ya ha creado una extensión de proyecto. Para obtener más información, consulte [Cómo: crear una extensión de proyecto de SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
### <a name="to-add-a-property-to-a-sharepoint-project"></a>Para agregar una propiedad a un proyecto de SharePoint  
  
1.  Defina una clase con una propiedad pública que representa la propiedad que se va a agregar a proyectos de SharePoint. Si desea agregar varias propiedades, puede definir todas las propiedades de la misma clase o en clases diferentes.  
  
2.  En el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> método de su <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> implementación, el identificador de la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> eventos de la *projectService* parámetro.  
  
3.  En el controlador de eventos para el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> evento, agregue una instancia de la clase de propiedades para el <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectPropertiesRequestedEventArgs.PropertySources%2A> colección del parámetro de argumentos del evento.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo de código siguiente muestra cómo agregar dos propiedades a los proyectos de SharePoint. Una propiedad hace persistir los datos en el archivo de opciones de usuario de proyecto (el *. csproj.user* archivo o *. vbproj.user* archivo). La otra propiedad hace persistir los datos en el archivo de proyecto (*.csproj* archivo o *.vbproj* archivo).  
  
 [!code-vb[SpExt_SPCustomPrjProperty#1](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#1)]
 [!code-csharp[SpExt_SPCustomPrjProperty#1](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#1)]  
  
### <a name="understand-the-code"></a>Entender el código  
 Para asegurarse de que la misma instancia de la `CustomProjectProperties` clase se usa cada vez que el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> se produce el evento, el ejemplo de código agrega el objeto de propiedades para el <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> propiedad del proyecto la primera vez que se produce este evento. El código recupera un objeto cada vez que este evento se produce de nuevo. Para obtener más información sobre el uso de la <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> propiedad para asociar los datos con los proyectos, vea [asociar datos personalizados con SharePoint de extensiones de herramientas](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).  
  
 Para conservar los cambios realizados en los valores de propiedad, el **establecer** descriptores de acceso para las propiedades utilizan las siguientes API:  
  
-   `CustomUserFileProperty` usa el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A> propiedad para guardar su valor en el archivo de opciones de usuario de proyecto.  
  
-   `CustomProjectFileProperty` usa el <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> método para guardar su valor en el archivo de proyecto.  
  
 Para obtener más información sobre cómo guardar datos en estos archivos, consulte [guardar datos en las extensiones del sistema del proyecto de SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
### <a name="specify-the-behavior-of-custom-properties"></a>Especificar el comportamiento de las propiedades personalizadas  
 Puede definir cómo una propiedad personalizada aparece y se comporta en la **propiedades** ventana aplicando los atributos de la <xref:System.ComponentModel> espacio de nombres para la definición de propiedad. Los atributos siguientes son útiles en muchos escenarios:  
  
-   <xref:System.ComponentModel.DisplayNameAttribute>: Especifica el nombre de la propiedad que aparece en el **propiedades** ventana.  
  
-   <xref:System.ComponentModel.DescriptionAttribute>: Especifica la cadena de descripción que aparece en la parte inferior de la **propiedades** ventana cuando se selecciona la propiedad.  
  
-   <xref:System.ComponentModel.DefaultValueAttribute>: Especifica el valor predeterminado de la propiedad.  
  
-   <xref:System.ComponentModel.TypeConverterAttribute>: Especifica una conversión personalizada entre la cadena que se muestra en el **propiedades** ventana y un valor de propiedad que no son de cadena.  
  
-   <xref:System.ComponentModel.EditorAttribute>: Especifica un editor personalizado para usar para modificar la propiedad.  
  
## <a name="compile-the-code"></a>Compile el código  
 Este ejemplo requiere referencias a los ensamblados siguientes:  
  
-   Microsoft.VisualStudio.SharePoint
-    
-   Microsoft.VisualStudio.Shell
-     
-   Microsoft.VisualStudio.Shell.Interop
-     
-   Microsoft.VisualStudio.Shell.Interop.8.0
-     
-   System.ComponentModel.Composition  
  
## <a name="deploy-the-extension"></a>Implementar la extensión  
 Para implementar la extensión, cree un [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] paquete de extensión (VSIX) para el ensamblado y otros archivos que desea distribuir con la extensión. Para obtener más información, consulte [implementar extensiones para las herramientas de SharePoint en Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Vea también
 [Extender los proyectos de SharePoint](../sharepoint/extending-sharepoint-projects.md)   
 [Cómo: crear una extensión de proyecto de SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)   
 [Cómo: agregar un elemento de menú contextual a los proyectos de SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)   
 [Extender el sistema de proyecto de SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)  
  
  
