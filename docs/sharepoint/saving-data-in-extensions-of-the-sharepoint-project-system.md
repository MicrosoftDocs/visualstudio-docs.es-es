---
title: Guardar datos en las extensiones del sistema del proyecto de SharePoint | Documentos de Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
helpviewer_keywords:
- SharePoint project items, saving string data
- project items [SharePoint development in Visual Studio], saving string data
- projects [SharePoint development in Visual Studio], saving string data
- SharePoint projects, saving string data
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5efc6a11852c0f843415623f4a5ac94f9d3e392b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="saving-data-in-extensions-of-the-sharepoint-project-system"></a>Guardar datos asociados en extensiones del sistema de proyectos de SharePoint
  Cuando se amplía el sistema de proyectos de SharePoint, puede guardar los datos de cadena que se conserva después de cerrar un proyecto de SharePoint. Los datos se suelen estar asociados con un elemento de proyecto concreto o con el propio proyecto.  
  
 Si tiene datos que no necesita conservar, puede agregar los datos a cualquier objeto en el modelo de objetos de herramientas de SharePoint que implementa el <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject> interfaz. Para obtener más información, consulte [asociar datos personalizados con extensiones de herramientas de SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).  
  
## <a name="saving-data-that-is-associated-with-a-project-item"></a>Guardar los datos que está asociado a un elemento de proyecto  
 Si tiene datos que está asociados a un determinado elemento de proyecto de SharePoint, como el valor de una propiedad que se agrega a un elemento de proyecto, puede guardar los datos en el archivo .spdata del elemento de proyecto. Para ello, use la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> propiedad de un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> objeto. Datos que se agregan a esta propiedad se guardan en el **ExtensionData** elemento en el archivo .spdata del elemento de proyecto. Para obtener más información, consulte [ExtensionData (elemento)](../sharepoint/extensiondata-element.md).  
  
 En el ejemplo de código siguiente se muestra cómo utilizar el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> propiedad que se va a guardar el valor de una propiedad de cadena que se define en un tipo de elemento de proyecto de SharePoint personalizado. Para ver este ejemplo en el contexto de un ejemplo más extenso, vea [Cómo: agregar una propiedad a un tipo de elemento de proyecto de SharePoint personalizado](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md).  
  
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#14](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb#14)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#14](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs#14)]  
  
## <a name="saving-data-that-is-associated-with-a-project"></a>Guardar los datos que está asociado a un proyecto  
 Si tiene datos de nivel de proyecto, como el valor de una propiedad que se agrega a los proyectos de SharePoint, puede guardar los datos en el archivo de proyecto (el archivo .csproj o .vbproj archivo) o el archivo de opción de usuario de proyecto (el. archivo csproj.user o. vbproj.user archivo). El archivo que elija para guardar los datos depende de cómo desea que los datos que se usará:  
  
-   Si desea que los datos estén disponibles para los desarrolladores que abra el proyecto de SharePoint, guardar los datos en el archivo de proyecto. Este archivo siempre se comprueba bases de datos de control de código fuente, por lo que los datos de este archivo están disponibles para otros desarrolladores que desproteja el proyecto.  
  
-   Si desea que los datos que estén disponibles sólo para el desarrollador actual que tiene el proyecto de SharePoint abierto en Visual Studio, guardar los datos en el archivo de opción de usuario de proyecto. Este archivo no normalmente se comprueba bases de datos de control de código fuente, por lo que los datos de este archivo no están disponibles para otros desarrolladores que desproteja el proyecto.  
  
### <a name="saving-data-to-the-project-file"></a>Guardar los datos en el archivo de proyecto  
 Para guardar datos en el archivo de proyecto, convertir un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> el objeto a una <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> objeto y, a continuación, utilice el <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> método. En el ejemplo de código siguiente se muestra cómo utilizar este método para guardar el valor de una propiedad del proyecto en el archivo de proyecto. Para ver este ejemplo en el contexto de un ejemplo más extenso, vea [Cómo: agregar una propiedad a los proyectos de SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).  
  
 [!code-vb[SpExt_SPCustomPrjProperty#3](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#3)]
 [!code-csharp[SpExt_SPCustomPrjProperty#3](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#3)]  
  
 Para obtener más información sobre cómo convertir <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> objetos a otros tipos en el modelo de objetos de automatización de Visual Studio o el modelo de objetos de integración, vea [convertir entre SharePoint Project System Types and Other Visual Studio Project Types ](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).  
  
### <a name="saving-data-to-the-project-user-option-file"></a>Guardar los datos en el archivo de opción de usuario de proyecto  
 Para guardar datos en el archivo de opción de usuario de proyecto, use la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A> propiedad de un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> objeto. En el ejemplo de código siguiente se muestra cómo utilizar esta propiedad para guardar el valor de una propiedad del proyecto en el archivo de opción de usuario de proyecto. Para ver este ejemplo en el contexto de un ejemplo más extenso, vea [Cómo: agregar una propiedad a los proyectos de SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).  
  
 [!code-vb[SpExt_SPCustomPrjProperty#2](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#2)]
 [!code-csharp[SpExt_SPCustomPrjProperty#2](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#2)]  
  
## <a name="see-also"></a>Vea también  
 [Extender el sistema de proyectos de SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)   
 [Asociar datos personalizados con extensiones de herramientas de SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)   
 [Conversión de los tipos de sistema de proyectos de SharePoint en otros tipos de proyecto de Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)  
  
  