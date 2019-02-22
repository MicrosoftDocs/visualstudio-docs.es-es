---
title: Guardar datos en extensiones del sistema del proyecto de SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
helpviewer_keywords:
- SharePoint project items, saving string data
- project items [SharePoint development in Visual Studio], saving string data
- projects [SharePoint development in Visual Studio], saving string data
- SharePoint projects, saving string data
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: eba3f66e55c06efad2a540b1be7d3ad66ddfa3d0
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56599680"
---
# <a name="save-data-in-extensions-of-the-sharepoint-project-system"></a>Guardar datos en las extensiones del sistema del proyecto de SharePoint
  Al extender el sistema de proyectos de SharePoint, puede guardar los datos de cadena que se conserva después de cerrar un proyecto de SharePoint. Los datos se suele asociados con un elemento de proyecto en particular o con el propio proyecto.

 Si tiene datos que no necesita conservar, puede agregar los datos a cualquier objeto en el modelo de objetos de herramientas de SharePoint que implementa el <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject> interfaz. Para obtener más información, consulte [asociar datos personalizados con SharePoint de extensiones de herramientas](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).

## <a name="save-data-that-is-associated-with-a-project-item"></a>Guardar los datos que está asociados a un elemento de proyecto
 Si tiene datos que está asociados con un elemento de proyecto de SharePoint determinado, como el valor de una propiedad que se agrega a un elemento de proyecto, puede guardar los datos en el *.spdata* archivo para el elemento de proyecto. Para ello, use el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> propiedad de un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> objeto. Datos que se agregan a esta propiedad se guardan en el **ExtensionData** elemento en el *.spdata* archivo para el elemento de proyecto. Para obtener más información, consulte [ExtensionData (elemento)](../sharepoint/extensiondata-element.md).

 En el ejemplo de código siguiente se muestra cómo usar el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> propiedad para guardar el valor de propiedad de cadena que se define en un tipo de elemento de proyecto de SharePoint personalizado. Para ver este ejemplo en el contexto de un ejemplo más extenso, vea [Cómo: Agregar una propiedad a un tipo de elemento de proyecto de SharePoint personalizado](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md).

 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#14](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb#14)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#14](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs#14)]

## <a name="save-data-that-is-associated-with-a-project"></a>Guardar los datos que está asociados a un proyecto
 Si tiene datos de nivel de proyecto, como el valor de una propiedad que se agrega a los proyectos de SharePoint, puede guardar los datos en el archivo de proyecto (el *.csproj* archivo o *.vbproj* archivo) o la opción de usuario de project archivo (el *. csproj.user* archivo o *. vbproj.user* archivo). El archivo que elija para guardar los datos de depende de cómo desea que los datos que se usará:

-   Si desea que los datos estén disponibles para todos los desarrolladores que abra el proyecto de SharePoint, guardar los datos en el archivo de proyecto. Este archivo se comprueba siempre bases de datos de control de código fuente, por lo que los datos de este archivo están disponibles para otros desarrolladores que desproteja el proyecto.

-   Si desea que los datos estén disponibles sólo para el programador actual que ha abierto en Visual Studio el proyecto de SharePoint, guardar los datos en el archivo de opciones de usuario de proyecto. Este archivo no es suele estar activado bases de datos de control de origen, por lo que los datos de este archivo no están disponibles para otros desarrolladores que desproteja el proyecto.

### <a name="save-data-to-the-project-file"></a>Guardar datos en el archivo de proyecto
 Para guardar datos en el archivo de proyecto, convertir un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> objeto a un <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> objeto y, a continuación, utilice el <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> método. El ejemplo de código siguiente muestra cómo usar este método para guardar el valor de una propiedad de proyecto en el archivo de proyecto. Para ver este ejemplo en el contexto de un ejemplo más extenso, vea [Cómo: Agregar una propiedad a proyectos de SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).

 [!code-vb[SpExt_SPCustomPrjProperty#3](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#3)]
 [!code-csharp[SpExt_SPCustomPrjProperty#3](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#3)]

 Para obtener más información sobre cómo convertir <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> objetos a otros tipos en el modelo de objetos de automatización de Visual Studio o el modelo de objetos de integración, vea [convertir entre tipos de sistema de proyectos de SharePoint y otros tipos de proyecto de Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).

### <a name="save-data-to-the-project-user-option-file"></a>Guardar datos en el archivo de opciones de usuario de proyecto
 Para guardar datos en el archivo de opciones de usuario de proyecto, use el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A> propiedad de un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> objeto. El ejemplo de código siguiente muestra cómo utilizar esta propiedad para guardar el valor de una propiedad de proyecto en el archivo de opciones de usuario de proyecto. Para ver este ejemplo en el contexto de un ejemplo más extenso, vea [Cómo: Agregar una propiedad a proyectos de SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).

 [!code-vb[SpExt_SPCustomPrjProperty#2](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#2)]
 [!code-csharp[SpExt_SPCustomPrjProperty#2](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#2)]

## <a name="see-also"></a>Vea también
- [Extender el sistema de proyecto de SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)
- [Asociar datos personalizados con extensiones de herramientas de SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)
- [Convertir entre tipos de sistema de proyectos de SharePoint y otros tipos de proyecto de Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)
