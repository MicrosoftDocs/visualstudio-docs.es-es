---
title: 'Cómo: agregar una propiedad a proyectos de SharePoint | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: eb72b0546b504e2df1a7e93ea9d4def350143d1d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "86015920"
---
# <a name="how-to-add-a-property-to-sharepoint-projects"></a>Cómo: agregar una propiedad a proyectos de SharePoint
  Puede usar una extensión de proyecto para agregar una propiedad a cualquier proyecto de SharePoint. La propiedad aparece en la ventana **propiedades** cuando se selecciona el proyecto en **Explorador de soluciones**.

 En los pasos siguientes se supone que ya ha creado una extensión de proyecto. Para obtener más información, vea [Cómo: crear una extensión de proyecto de SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).

### <a name="to-add-a-property-to-a-sharepoint-project"></a>Para agregar una propiedad a un proyecto de SharePoint

1. Defina una clase con una propiedad pública que represente la propiedad que va a agregar a los proyectos de SharePoint. Si desea agregar varias propiedades, puede definir todas las propiedades de la misma clase o de clases diferentes.

2. En el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> método de la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> implementación, controle el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> evento del parámetro *projectService* .

3. En el controlador de eventos para el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> evento, agregue una instancia de la clase de propiedades a la <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectPropertiesRequestedEventArgs.PropertySources%2A> colección del parámetro de argumentos de evento.

## <a name="example"></a>Ejemplo
 En el ejemplo de código siguiente se muestra cómo agregar dos propiedades a los proyectos de SharePoint. Una propiedad conserva sus datos en el archivo de opciones de usuario del proyecto (el archivo *. csproj. User* o *. vbproj. User* ). La otra propiedad conserva sus datos en el archivo de proyecto (archivo *. csproj* o *. vbproj* ).

 [!code-vb[SpExt_SPCustomPrjProperty#1](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#1)]
 [!code-csharp[SpExt_SPCustomPrjProperty#1](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#1)]

### <a name="understand-the-code"></a>Comprendiendo el código
 Para asegurarse de que se utiliza la misma instancia de la `CustomProjectProperties` clase cada vez que <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> se produce el evento, el ejemplo de código agrega el objeto de propiedades a la <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> propiedad del proyecto la primera vez que se produce este evento. El código recupera este objeto cada vez que se produce de nuevo este evento. Para obtener más información sobre el uso de la <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> propiedad para asociar datos a proyectos, vea [asociar datos personalizados con extensiones de herramientas de SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).

 Para conservar los cambios en los valores de propiedad, los descriptores de acceso del **conjunto** de las propiedades usan las siguientes API:

- `CustomUserFileProperty` utiliza la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A> propiedad para guardar su valor en el archivo de opciones de usuario del proyecto.

- `CustomProjectFileProperty` utiliza el <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> método para guardar su valor en el archivo de proyecto.

  Para obtener más información sobre cómo conservar los datos en estos archivos, vea [guardar datos en extensiones del sistema de proyectos de SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).

### <a name="specify-the-behavior-of-custom-properties"></a>Especificar el comportamiento de las propiedades personalizadas
 Puede definir el modo en que una propiedad personalizada aparece y se comporta en la ventana **propiedades** aplicando atributos del <xref:System.ComponentModel> espacio de nombres a la definición de la propiedad. Los atributos siguientes son útiles en muchos escenarios:

- <xref:System.ComponentModel.DisplayNameAttribute>: Especifica el nombre de la propiedad que aparece en la ventana **propiedades** .

- <xref:System.ComponentModel.DescriptionAttribute>: Especifica la cadena de descripción que aparece en la parte inferior de la ventana **propiedades** cuando se selecciona la propiedad.

- <xref:System.ComponentModel.DefaultValueAttribute>: Especifica el valor predeterminado de la propiedad.

- <xref:System.ComponentModel.TypeConverterAttribute>: Especifica una conversión personalizada entre la cadena que se muestra en la ventana **propiedades** y un valor de propiedad que no es de cadena.

- <xref:System.ComponentModel.EditorAttribute>: Especifica un editor personalizado que se va a utilizar para modificar la propiedad.

## <a name="compile-the-code"></a>Compilar el código
 Este ejemplo requiere referencias a los ensamblados siguientes:

- Microsoft.VisualStudio.SharePoint

- Microsoft. VisualStudio. Shell

- Microsoft. VisualStudio. Shell. Interop

- Microsoft. VisualStudio. Shell. Interop. 8.0

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Implementar la extensión
 Para implementar la extensión, cree un [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] paquete de extensión (VSIX) para el ensamblado y cualquier otro archivo que desee distribuir con la extensión. Para obtener más información, vea [deploy Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Consulte también
- [Extender proyectos de SharePoint](../sharepoint/extending-sharepoint-projects.md)
- [Cómo: crear una extensión de proyecto de SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)
- [Cómo: agregar un elemento de menú contextual a los proyectos de SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)
- [Extender el sistema de proyectos de SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)
