---
title: Crear elemento plantillas y plantillas de proyecto para elementos de proyecto de SharePoint | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d181891fb36645e4f246aa0c2238c12ea1dc4903
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2018
ms.locfileid: "51296013"
---
# <a name="create-item-templates-and-project-templates-for-sharepoint-project-items"></a>Crear plantillas de elemento y plantillas de proyecto para los elementos de proyecto de SharePoint
  Al definir un tipo de elemento de proyecto de SharePoint personalizado, puede asociarlo con una plantilla de elemento o una plantilla de proyecto. Esta asociación permite que otros desarrolladores usen el elemento de proyecto en Visual Studio. También puede crear a un Asistente para la plantilla.

 Por ejemplo, Visual Studio no incluye una plantilla de proyecto o elemento para agregar un campo a un sitio de SharePoint. Puede definir un tipo de elemento de proyecto de SharePoint que representa un campo y, a continuación, crear una plantilla de elemento que otros desarrolladores pueden usar para agregar el elemento de campo a un proyecto de SharePoint. O bien, puede crear una plantilla de proyecto para que los desarrolladores pueden crear un nuevo proyecto de SharePoint que tiene el elemento de campo. En ambos casos, también puede proporcionar a un asistente que aparece cuando los desarrolladores usar la plantilla. Este asistente puede recopilar información de los desarrolladores a configurar el nuevo elemento o proyecto.

 Las plantillas de elemento y plantillas de proyecto son *.zip* archivos que contienen archivos que se utilizan por Visual Studio para crear un proyecto o elemento de proyecto. Para obtener más información sobre los fundamentos de las plantillas de elemento y plantillas de proyecto, vea [crear plantillas de proyecto y elemento](../ide/creating-project-and-item-templates.md).

## <a name="create-item-templates"></a>Crear plantillas de elemento
 Cuando se crea una plantilla de elemento para un elemento de proyecto de SharePoint, hay algunos archivos que siempre son necesarios y archivos opcionales que pueden usarse para determinados tipos de elementos de proyecto. Para ver un tutorial que muestra cómo definir un tipo de elemento de proyecto de SharePoint y crear una plantilla de elemento para ella, consulte [Tutorial: crear elemento de proyecto de acción personalizado con una plantilla de elementos, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).

 En la tabla siguiente se enumera los archivos necesarios para crear una plantilla de elemento para un elemento de proyecto de SharePoint.

|Archivo necesario|Descripción|
|-------------------|-----------------|
|Un *.spdata* archivo|Este archivo XML especifica el contenido y el comportamiento predeterminado del elemento de proyecto. Este archivo debe incluirse en la plantilla de elemento. Para obtener más información sobre el contenido de *.spdata* archivos, consulte [referencia de esquemas de elemento de proyecto de SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md).|
|Un *.vstemplate* archivo.|Este archivo proporciona Visual Studio con la información necesaria para mostrar la plantilla en el **Agregar nuevo elemento** cuadro de diálogo y crear un elemento de proyecto de la plantilla. Este archivo debe incluirse en la plantilla de elemento. Para obtener más información, consulte [archivos de metadatos de plantilla de Visual Studio](/previous-versions/visualstudio/visual-studio-2010/xsxc3ete\(v\=vs.100\)).|
|Un ensamblado de extensión de Visual Studio que implementa el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> interfaz.|Este ensamblado define el comportamiento de tiempo de ejecución del elemento de proyecto. Este ensamblado debe incluirse en el paquete VSIX con la plantilla de elemento. Para obtener más información, consulte [definir tipos de elemento de proyecto de SharePoint personalizados](../sharepoint/defining-custom-sharepoint-project-item-types.md) y [implementar extensiones para las herramientas de SharePoint en Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).|

 En la tabla siguiente se enumera algunos de los archivos opcionales más comunes que pueden incluirse en la plantilla de elemento. Algunos tipos de elementos de proyecto podrían requerir otros archivos que no aparece aquí.


| Archivo opcional | Descripción |
|----------------------| - |
| *Elements.Xml* | Un *elemento Feature* archivo. Este archivo define la interfaz de usuario y el comportamiento de la personalización creada por el elemento de proyecto. Cada tipo de personalización como instancias de listas, tipos de contenido o acciones personalizadas, tiene un esquema diferente que define el contenido de este archivo. Para obtener más información, consulte [bloques de creación: características](http://go.microsoft.com/fwlink/?LinkId=169183) y [característica esquemas](http://go.microsoft.com/fwlink/?LinkId=169192). |
| *Schema.Xml* | El archivo de esquema para definiciones de lista. Para obtener más información, consulte [bloques de creación: listas y bibliotecas de documentos](http://go.microsoft.com/fwlink/?LinkId=177792) y [Schema.xml](http://go.microsoft.com/fwlink/?LinkId=177793). |
| *.WebPart* | Un *definición de elemento Web* archivo. Este archivo contiene los valores de propiedad para un elemento Web. Para obtener más información, consulte [bloques de creación: elementos Web](http://go.microsoft.com/fwlink/?LinkId=177791). |
| *.ascx* | Un archivo de control de usuario ASP.NET. Este archivo define la interfaz de usuario de un elemento Web Visual. |
| *.aspx* | Un archivo de página ASP.NET. Este archivo contiene el marcado XML que define una página de aplicación. |
| *.cs* o *.vb* archivos | Estos archivos de código definen el comportamiento de las personalizaciones de SharePoint que tienen un modelo de programación que se puede acceder desde Visual C# o código de Visual Basic, como las páginas de aplicación, elementos Web y flujos de trabajo. |

## <a name="create-project-templates"></a>Crear plantillas de proyecto
 Cuando se crea una plantilla de proyecto de SharePoint, hay algunos archivos que son siempre los archivos obligatorios y opcionales que pueden usarse para determinados tipos de proyectos. Normalmente, los proyectos de SharePoint incluyen al menos un elemento de proyecto de SharePoint. Sin embargo, esto no es necesario. Por ejemplo, podría definir una plantilla de proyecto de SharePoint que está pensada para usarse solo para implementar soluciones de SharePoint que se crearon en otros proyectos.

 Para ver un tutorial que muestra cómo definir un tipo de elemento de proyecto de SharePoint y crear una plantilla de proyecto para él, consulte [Tutorial: crear un elemento de proyecto de la columna de sitio con una plantilla de proyecto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).

 En la tabla siguiente se enumera los archivos que deben incluirse en una plantilla de proyecto de SharePoint.

|Archivo necesario|Descripción|
|-------------------|-----------------|
|Un *.vstemplate* archivo|Este archivo proporciona Visual Studio con la información necesaria para mostrar la plantilla en el **nuevo proyecto** cuadro de diálogo y crear un proyecto de la plantilla. Para obtener más información, consulte [archivos de metadatos de plantilla de Visual Studio](/previous-versions/visualstudio/visual-studio-2010/xsxc3ete\(v\=vs.100\)).|
|Un *.csproj* o *.vbproj* archivo|Este es el archivo de proyecto. Define el contenido y valores de configuración del proyecto.|
|*Package.Package*|Este archivo define el paquete de implementación para el proyecto. Cuando usa el Diseñador de paquetes para personalizar el paquete de solución para el proyecto, Visual Studio almacena datos sobre el paquete de solución de este archivo.<br /><br /> Cuando se crea una plantilla de proyecto de SharePoint personalizada, se recomienda que incluya solo el contenido mínimo necesario en el *Package.package* archivo y que configure el paquete de soluciones mediante las API en el <xref:Microsoft.VisualStudio.SharePoint.Packages> espacio de nombres en una extensión que está asociada con la plantilla de proyecto. Si lo hace, la plantilla de proyecto está protegida de futuros cambios en la estructura de la *Package.package* archivo. Para obtener un ejemplo que muestra cómo crear un *Package.package* contenido del archivo con solo el mínimo requerido, consulte [Tutorial: crear un elemento de proyecto de la columna de sitio con una plantilla de proyecto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).<br /><br /> Si desea modificar el *Package.package* archivo directamente, puede comprobar el contenido mediante el esquema en *% archivos de programa (x86)%\Microsoft Visual Studio 11.0\Xml\Schemas\PackageModelSchema.xsd* .|
|*Package.Template.xml*|Este archivo proporciona la base para el archivo de manifiesto de la solución (*manifest.xml*) para el paquete de solución de SharePoint (*.wsp*) que se genera a partir del proyecto. Puede agregar contenido a este archivo si desea especificar algún comportamiento que no está pensado para los usuarios de su tipo de proyecto pueden cambiar. Para obtener más información, consulte [bloques de creación: soluciones](http://go.microsoft.com/fwlink/?LinkId=169186) y [solución esquema](http://go.microsoft.com/fwlink/?LinkId=177794).<br /><br /> Al compilar un paquete de solución del proyecto, Visual Studio combina el contenido de la *Package.package* y *Package.Template.xml* archivo de manifiesto de archivos en la solución. Para obtener más información sobre la creación de paquetes de soluciones, consulte [Cómo: crear un paquete de solución de SharePoint mediante el uso de las tareas de MSBuild](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md).|

 En la tabla siguiente se enumera los archivos opcionales que pueden incluirse en la plantilla de proyecto.

|Archivo opcional|Descripción|
|-------------------|-----------------|
|elementos de proyecto de SharePoint|Puede incluir uno o varios archivos .spdata que definen los tipos de elemento de proyecto de SharePoint. Cada *.spdata* debe tener su correspondiente archivo <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> implementación en un ensamblado de extensión que se incluye en el paquete VSIX con la plantilla de proyecto. Para obtener más información, consulte [creación de plantillas de elemento](#creatingitemtemplates).<br /><br /> Normalmente, los proyectos de SharePoint incluyen al menos un elemento de proyecto de SharePoint. Sin embargo, esto no es necesario.|
|*\<featureName > .feature*|Este archivo define una característica de SharePoint que se usa para agrupar varios elementos de proyecto para la implementación. Cuando usa el Diseñador de características para personalizar una característica en el proyecto, Visual Studio almacena datos sobre la característica de este archivo. Si desea agrupar los elementos de proyecto en diferentes características, puede incluir varios *.feature* archivos.<br /><br /> Cuando se crea una plantilla de proyecto de SharePoint personalizada, se recomienda que incluya solo el contenido mínimo necesario en cada *.feature* archivos y configuración de características mediante las API en el <xref:Microsoft.VisualStudio.SharePoint.Features> espacio de nombres en un extensión que está asociada con la plantilla de proyecto. Si lo hace, la plantilla de proyecto está protegida de futuros cambios en la estructura de la *.feature* archivo. Para obtener un ejemplo que muestra cómo crear un *.feature* contenido del archivo con solo el mínimo requerido, consulte [Tutorial: crear un elemento de proyecto de la columna de sitio con una plantilla de proyecto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).<br /><br /> Si desea modificar un *.feature* archivo directamente, puede comprobar el contenido mediante el esquema en *% archivos de programa (x86)%\Microsoft Visual Studio 11.0\Xml\Schemas\FeatureModelSchema.xsd*.|
|*\<featureName >. Template.Xml*|Este archivo proporciona la base para el archivo de manifiesto de característica (*Feature.xml*) para cada característica que se genera a partir del proyecto. Puede agregar contenido a este archivo si desea especificar algún comportamiento que no está pensado para los usuarios de su tipo de proyecto pueden cambiar. Para obtener más información, consulte [bloques de creación: características](http://go.microsoft.com/fwlink/?LinkId=169183) y [Feature.xml](http://go.microsoft.com/fwlink/?LinkId=177795) archivos.<br /><br /> Al compilar un paquete de solución del proyecto, Visual Studio combina el contenido de cada par de  *\<NombreDeCaracterística > .feature* archivo y  *\<NombreDeCaracterística >. Template.XML* archivos en función de un archivo de manifiesto. Para obtener más información sobre la creación de paquetes de soluciones, consulte [Cómo: crear un paquete de solución de SharePoint mediante el uso de las tareas de MSBuild](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md).|

## <a name="create-wizards-for-item-templates-and-project-templates"></a>Crear a asistentes para plantillas de elemento y plantillas de proyecto
 Después de definir un tipo de elemento de proyecto de SharePoint y asociarlo con una plantilla de elemento o un proyecto, también puede crear a un asistente. El asistente muestra cuando un desarrollador usa la plantilla de elemento para agregar el elemento de proyecto de SharePoint a un proyecto, o cuando un desarrollador usa la plantilla de proyecto para crear un nuevo proyecto que contiene el elemento de proyecto de SharePoint. El asistente puede usarse para recopilar información de los desarrolladores e inicializar el nuevo elemento de proyecto de SharePoint.

 Para ver tutoriales que muestran cómo crear asistentes para plantillas de elemento y plantillas de proyecto, vea [Tutorial: crear un elemento de proyecto de acción personalizado con una plantilla de elementos, parte 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md) y [Tutorial: crear un sitio elemento de proyecto de columna con una plantilla de proyecto, parte 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).

## <a name="see-also"></a>Vea también

- [Definir tipos de elemento de proyecto de SharePoint personalizados](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Tutorial: Crear un elemento de proyecto de acción personalizado con una plantilla de elementos, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [Tutorial: Crear un elemento de proyecto de acción personalizado con una plantilla de elementos, parte 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)
- [Tutorial: Crear un elemento de proyecto de la columna de sitio con una plantilla de proyecto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)
- [Tutorial: Crear un elemento de proyecto de la columna de sitio con una plantilla de proyecto, parte 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)
- [Creación de plantillas de proyecto y elemento](../ide/creating-project-and-item-templates.md)
