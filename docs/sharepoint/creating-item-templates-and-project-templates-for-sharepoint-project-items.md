---
title: Plantillas de elementos/plantillas de proyecto para los elementos de proyecto de SharePoint
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, creating custom templates
- .spdata files
- projects [SharePoint development in Visual Studio], creating custom templates
- SharePoint projects, creating custom templates
- SharePoint development in Visual Studio, creating custom project and item templates
- project items [SharePoint development in Visual Studio], creating custom templates
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 65bbd58bf9b3e0b399603a083615daccc382a98f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72981173"
---
# <a name="create-item-templates-and-project-templates-for-sharepoint-project-items"></a>Crear plantillas de elemento y plantillas de proyecto para los elementos de proyecto de SharePoint

Al definir un tipo de elemento de proyecto de SharePoint personalizado, puede asociarlo a una plantilla de elemento o a una plantilla de proyecto. Esta asociación permite a otros desarrolladores usar el elemento de proyecto en Visual Studio. También puede crear un asistente para la plantilla.

Por ejemplo, Visual Studio no incluye una plantilla de proyecto o una plantilla de elemento para agregar un campo a un sitio de SharePoint. Puede definir un tipo de elemento de proyecto de SharePoint que represente un campo y, a continuación, construir una plantilla de elemento que otros desarrolladores puedan usar para agregar el elemento de campo a un proyecto de SharePoint. O bien, puede crear una plantilla de proyecto para que los desarrolladores puedan crear un nuevo proyecto de SharePoint que tenga el elemento de campo. En ambos casos, también puede proporcionar un asistente que aparece cuando los desarrolladores usan la plantilla. Este asistente puede recopilar información de los desarrolladores para configurar el nuevo elemento o proyecto.

Las plantillas de elementos y las plantillas de proyecto son archivos *zip* que contienen archivos que Visual Studio usa para crear un proyecto o elemento de proyecto. Para obtener más información sobre los aspectos básicos de las plantillas de elemento y plantillas de proyecto, vea [crear plantillas de proyecto y de elemento](../ide/creating-project-and-item-templates.md).

## <a name="create-item-templates"></a>Crear plantillas de elemento
 Cuando se crea una plantilla de elemento para un elemento de proyecto de SharePoint, hay algunos archivos que siempre son necesarios y archivos opcionales que pueden usar determinados tipos de elementos de proyecto. Para ver un tutorial que muestra cómo definir un tipo de elemento de proyecto de SharePoint y crear una plantilla de elemento para él, vea [Tutorial: crear un elemento de proyecto de acción personalizado con una plantilla de elemento, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).

 En la tabla siguiente se enumeran los archivos necesarios para crear una plantilla de elemento para un elemento de proyecto de SharePoint.

|Archivo necesario|Descripción|
|-------------------|-----------------|
|Un archivo *. spdata*|Este archivo XML especifica el contenido y el comportamiento predeterminado del elemento de proyecto. Este archivo debe estar incluido en la plantilla de elementos. Para obtener más información sobre el contenido de los archivos *. spdata* , vea [referencia de esquema de elementos de proyecto de SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md).|
|Un archivo *. vstemplate* .|Este archivo proporciona a Visual Studio la información necesaria para mostrar la plantilla en el cuadro de diálogo **Agregar nuevo elemento** y crear un elemento de proyecto a partir de la plantilla. Este archivo debe estar incluido en la plantilla de elementos. Para obtener más información, vea [archivos de metadatos de plantilla de Visual Studio](/previous-versions/visualstudio/visual-studio-2010/xsxc3ete\(v\=vs.100\)).|
|Un ensamblado de extensión de Visual Studio que implementa la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> interfaz.|Este ensamblado define el comportamiento del tiempo de ejecución del elemento de proyecto. Este ensamblado debe estar incluido en el paquete VSIX con la plantilla de elemento. Para obtener más información, vea [definir tipos de elementos de proyecto personalizados de SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md) e [implementar extensiones para las herramientas de SharePoint en Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).|

 En la tabla siguiente se enumeran algunos de los archivos opcionales más comunes que se pueden incluir en la plantilla de elemento. Algunos tipos de elementos de proyecto podrían requerir otros archivos que no se enumeran aquí.

| Archivo opcional | Descripción |
|----------------------| - |
| *Elements.xml* | Un archivo de *elemento de característica* . Este archivo define la interfaz de usuario y el comportamiento de la personalización creada por el elemento de proyecto. Cada tipo de personalización, como las instancias de lista, los tipos de contenido o las acciones personalizadas, tiene un esquema diferente que define el contenido de este archivo. Para obtener más información, vea [bloque de creación: características](/previous-versions/office/developer/sharepoint-2010/ee537350(v=office.14)) y [esquemas de características](/previous-versions/office/developer/sharepoint-2010/ms414322(v=office.14)). |
| *Schema.xml* | El archivo de esquema para definiciones de lista. Para obtener más información, vea [bloque de creación: listas y bibliotecas de documentos](/previous-versions/office/developer/sharepoint-2010/ee534985(v=office.14)) y [Schema.xml](/previous-versions/office/developer/sharepoint-2010/ms459356(v=office.14)). |
| *. WebPart* | Un archivo de *definición de elemento Web* . Este archivo contiene la configuración de propiedades de un elemento Web. Para obtener más información, vea [bloque de creación: elementos Web](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14)). |
| *.ascx* | Un archivo UserControl de ASP.NET. Este archivo define la interfaz de usuario de un elemento Web visual. |
| *.aspx* | Un archivo de paginación de ASP.NET. Este archivo contiene marcado XML que define una página de aplicación. |
| archivos *. CS* o *. VB* | Estos archivos de código definen el comportamiento de las personalizaciones de SharePoint que tienen un modelo de programación al que se puede tener acceso desde Visual C# o código Visual Basic, como páginas de aplicación, elementos Web y flujos de trabajo. |

## <a name="create-project-templates"></a>Crear plantillas de proyecto
 Al crear una plantilla de proyecto de SharePoint, hay algunos archivos que siempre son necesarios y archivos opcionales que pueden usar determinados tipos de proyectos. Normalmente, los proyectos de SharePoint incluyen al menos un elemento de proyecto de SharePoint. pero esto no es obligatorio. Por ejemplo, podría definir una plantilla de proyecto de SharePoint diseñada para usarse solo para implementar soluciones de SharePoint creadas en otros proyectos.

 Para ver un tutorial que muestra cómo definir un tipo de elemento de proyecto de SharePoint y crear una plantilla de proyecto para él, vea [Tutorial: crear un elemento de proyecto de columna de sitio con una plantilla de proyecto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).

 En la tabla siguiente se enumeran los archivos que deben incluirse en una plantilla de proyecto de SharePoint.

|Archivo necesario|Descripción|
|-------------------|-----------------|
|Un archivo *. vstemplate*|Este archivo proporciona a Visual Studio la información necesaria para mostrar la plantilla en el cuadro de diálogo **nuevo proyecto** y para crear un proyecto a partir de la plantilla. Para obtener más información, vea [archivos de metadatos de plantilla de Visual Studio](/previous-versions/visualstudio/visual-studio-2010/xsxc3ete\(v\=vs.100\)).|
|Un archivo *. csproj* o *. vbproj*|Este es el archivo de proyecto. Define el contenido y los valores de configuración del proyecto.|
|*Package.package*|Este archivo define el paquete de implementación para el proyecto. Cuando se usa el diseñador de paquetes para personalizar el paquete de la solución para el proyecto, Visual Studio almacena los datos sobre el paquete de la solución en este archivo.<br /><br /> Al crear una plantilla de proyecto de SharePoint personalizada, se recomienda incluir solo el contenido mínimo necesario en el archivo *Package. Package* y configurar el paquete de la solución mediante el uso de las API en el <xref:Microsoft.VisualStudio.SharePoint.Packages> espacio de nombres de una extensión que esté asociada a la plantilla de proyecto. Si lo hace, la plantilla de proyecto está protegida frente a cambios futuros en la estructura del archivo *Package. Package* . Para obtener un ejemplo en el que se muestra cómo crear un archivo *Package. Package* con solo el contenido mínimo necesario, vea [Tutorial: crear un elemento de proyecto de columna de sitio con una plantilla de proyecto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).<br /><br /> Si desea modificar el archivo *Package. Package* directamente, puede comprobar el contenido con el esquema en *% archivos de programa (x86)% \ Microsoft Visual Studio 11.0 \ Xml\Schemas\PackageModelSchema.xsd*.|
|*Package.Template.xml*|Este archivo proporciona la base del archivo de manifiesto de la solución (*manifest.xml*) para el paquete de solución de SharePoint (*. wsp*) que se genera a partir del proyecto. Puede agregar contenido a este archivo si desea especificar algún comportamiento que no pretende ser modificado por los usuarios del tipo de proyecto. Para obtener más información, vea [bloque de creación: soluciones](/previous-versions/office/developer/sharepoint-2010/ee537008(v=office.14)) y esquema de la [solución](/sharepoint/dev/schema/solution-schema).<br /><br /> Al compilar un paquete de solución desde el proyecto, Visual Studio combina el contenido del *paquete. Package* y los archivos *Package.Template.xml* en el archivo de manifiesto de la solución. Para obtener más información sobre cómo compilar paquetes de soluciones, vea [Cómo: crear un paquete de solución de SharePoint mediante tareas de MSBuild](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md).|

 En la tabla siguiente se enumeran los archivos opcionales que se pueden incluir en la plantilla de proyecto.

|Archivo opcional|Descripción|
|-------------------|-----------------|
|elementos de proyecto de SharePoint|Puede incluir uno o varios archivos. spdata que definen los tipos de elemento de proyecto de SharePoint. Cada archivo *. spdata* debe tener una <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> implementación correspondiente en un ensamblado de extensión incluido en el paquete VSIX con la plantilla de proyecto. Para obtener más información, vea [crear plantillas de elementos](#create-item-templates).<br /><br /> Normalmente, los proyectos de SharePoint incluyen al menos un elemento de proyecto de SharePoint. pero esto no es obligatorio.|
|*\<featureName>. característica*|Este archivo define una característica de SharePoint que se utiliza para agrupar varios elementos de proyecto para la implementación. Cuando se usa el diseñador de características para personalizar una característica del proyecto, Visual Studio almacena los datos sobre la característica en este archivo. Si desea agrupar los elementos de proyecto en características diferentes, puede incluir varios archivos *. Feature* .<br /><br /> Al crear una plantilla de proyecto de SharePoint personalizada, se recomienda incluir solo el contenido mínimo necesario en cada archivo *. Feature* y configurar características mediante las API del <xref:Microsoft.VisualStudio.SharePoint.Features> espacio de nombres de una extensión que esté asociada a la plantilla de proyecto. Si lo hace, la plantilla de proyecto está protegida frente a cambios futuros en la estructura del archivo *. Feature* . Para obtener un ejemplo en el que se muestra cómo crear un archivo *. Feature* con solo el contenido mínimo necesario, vea [Tutorial: crear un elemento de proyecto de columna de sitio con una plantilla de proyecto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).<br /><br /> Si desea modificar un archivo *. Feature* directamente, puede comprobar el contenido mediante el esquema en *% archivos de programa (x86)% \ Microsoft Visual Studio 11.0 \ Xml\Schemas\FeatureModelSchema.xsd*.|
|*\<featureName>.Template.xml*|Este archivo proporciona la base del archivo de manifiesto de características (*Feature.xml*) para cada característica que se genera a partir del proyecto. Puede agregar contenido a este archivo si desea especificar algún comportamiento que no pretende ser modificado por los usuarios del tipo de proyecto. Para obtener más información, vea [bloque de creación: características](/previous-versions/office/developer/sharepoint-2010/ee537350(v=office.14)) y archivos [Feature.xml](/sharepoint/dev/schema/feature-xml-files) .<br /><br /> Al compilar un paquete de la solución desde el proyecto, Visual Studio combina el contenido de cada par de archivos * \<featureName> . feature* y * \<featureName>.Template.xml* en un archivo de manifiesto de la característica. Para obtener más información sobre cómo compilar paquetes de soluciones, vea [Cómo: crear un paquete de solución de SharePoint mediante tareas de MSBuild](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md).|

## <a name="create-wizards-for-item-templates-and-project-templates"></a>Crear asistentes para plantillas de elementos y plantillas de proyecto
 Después de definir un tipo de elemento de proyecto de SharePoint y asociarlo a un elemento o una plantilla de proyecto, también puede crear un asistente. El asistente muestra Cuándo un desarrollador utiliza la plantilla de elemento para agregar el elemento de proyecto de SharePoint a un proyecto o Cuándo utiliza la plantilla de proyecto para crear un nuevo proyecto que contiene el elemento de proyecto de SharePoint. El asistente se puede usar para recopilar información de los desarrolladores y para inicializar el nuevo elemento de proyecto de SharePoint.

 Para ver tutoriales que muestran cómo crear asistentes para plantillas de elementos y plantillas de proyecto, vea [Tutorial: crear un elemento de proyecto de acción personalizado con una plantilla de elemento, parte 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md) y [Tutorial: crear un elemento de proyecto de columna de sitio con una plantilla de proyecto, parte 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).

## <a name="see-also"></a>Consulte también

- [Definir tipos de elementos de proyecto personalizados de SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Tutorial: crear un elemento de proyecto de acción personalizado con una plantilla de elemento, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [Tutorial: crear un elemento de proyecto de acción personalizado con una plantilla de elemento, parte 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)
- [Tutorial: crear un elemento de proyecto de columna de sitio con una plantilla de proyecto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)
- [Tutorial: crear un elemento de proyecto de columna de sitio con una plantilla de proyecto, parte 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)
- [Creación de plantillas de proyecto y elemento](../ide/creating-project-and-item-templates.md)
