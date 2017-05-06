---
title: "Creating Item Templates and Project Templates for SharePoint Project Items"
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
  - "SharePoint project items, creating custom templates"
  - ".spdata files"
  - "projects [SharePoint development in Visual Studio], creating custom templates"
  - "SharePoint projects, creating custom templates"
  - "SharePoint development in Visual Studio, creating custom project and item templates"
  - "project items [SharePoint development in Visual Studio], creating custom templates"
ms.assetid: c95b5e35-76c4-4f0a-b645-0467ae683659
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# Creating Item Templates and Project Templates for SharePoint Project Items
  Cuando define un tipo de elemento de proyecto de SharePoint personalizado, puede asociarlo con una plantilla de elemento o una plantilla de proyecto para que otros desarrolladores puedan usarlo en Visual Studio.  También puede crear un asistente para la plantilla.  
  
 Por ejemplo, Visual Studio no incluye una plantilla de proyecto o una plantilla de elemento para agregar un campo a un sitio de SharePoint.  Puede definir un tipo de elemento de proyecto de SharePoint que represente un campo y, a continuación, crear una plantilla de elemento que otros desarrolladores puedan usar para agregar el elemento de campo a un proyecto de SharePoint.  O bien, puede crear una plantilla de proyecto para que los programadores puedan crear un nuevo proyecto de SharePoint que contenga el elemento de campo. En ambos casos, también puede proporcionar un asistente que aparece cuando los desarrolladores usan la plantilla.  Este asistente puede recopilar información de los desarrolladores para configurar el nuevo elemento o proyecto.  
  
 Las plantillas de elemento y plantillas de proyecto son archivos .zip que contienen los archivos que usa Visual Studio para crear un elemento de proyecto o un proyecto.  Para obtener más información sobre los fundamentos de plantillas de elemento y las plantillas de proyecto, vea [Crear plantillas para proyectos y elementos en Visual Studio](../ide/creating-project-and-item-templates.md).  
  
##  <a name="creatingitemtemplates"></a> Crear plantillas de elementos  
 Cuando se crea una plantilla de elemento para un elemento de proyecto de SharePoint, hay algunos archivos que siempre son necesarios y otros opcionales que podrían usar ciertos tipos de elementos de proyecto.  Para consultar un tutorial en el que se muestra cómo se define un tipo de elemento de proyecto de SharePoint y se crea una plantilla de elemento para él, vea [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).  
  
 En la tabla siguiente se enumeran los archivos necesarios para crear una plantilla para un elemento de proyecto de SharePoint.  
  
|Archivo obligatorio|Descripción|  
|-------------------------|-----------------|  
|Un archivo .spdata|Se trata de un archivo XML que especifica el contenido y el comportamiento predeterminado del elemento de proyecto.  Este archivo se debe incluir en la plantilla de elemento.  Para obtener más información sobre el contenido de los archivos .spdata, vea [SharePoint Project Item Schema Reference](../sharepoint/sharepoint-project-item-schema-reference.md).|  
|Un archivo .vstemplate.|Este archivo proporciona a Visual Studio la información necesaria para mostrar la plantilla en el cuadro de diálogo **Agregar nuevo elemento** y crear un elemento de proyecto a partir de la plantilla.  Este archivo se debe incluir en la plantilla de elemento.  Para obtener más información, vea [NIB: Visual Studio Template Metadata Files](http://msdn.microsoft.com/es-es/129d59b5-7f9c-4daf-9832-eaedb3c4c961).|  
|Un ensamblado de extensión de Visual Studio que implemente la interfaz <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>.|Este ensamblado define el comportamiento en tiempo de ejecución del elemento de proyecto.  Este ensamblado se debe incluir en el paquete VSIX con la plantilla de elemento.  Para obtener más información, vea [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md) y [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).|  
  
 En la tabla siguiente se hace una lista de los archivos opcionales más comunes que se pueden incluir en la plantilla de elemento.  Algunos tipos de elementos de proyecto pueden requerir otros archivos no enumerados aquí.  
  
|Archivo opcional|Descripción|  
|----------------------|-----------------|  
|Elements.xml|Un archivo de *elemento de característica*.  Este archivo define la interfaz de usuario y el comportamiento de la personalización creada por el elemento de proyecto.  Cada tipo de personalización, como las instancias de lista, los tipos de contenido o las acciones personalizadas, tiene un esquema diferente que define el contenido de este archivo.  Para obtener más información, vea [Bloques de creación: características](http://go.microsoft.com/fwlink/?LinkId=169183) y [Esquemas de características](http://go.microsoft.com/fwlink/?LinkId=169192).|  
|Schema.xml|El archivo de esquema de las definiciones de lista.  Para obtener más información, vea [Bloque de creación: bibliotecas de listas y documentos](http://go.microsoft.com/fwlink/?LinkId=177792) y [Schema.xml](http://go.microsoft.com/fwlink/?LinkId=177793).|  
|.webpart|Un archivo de *definición de elementos web*.  Este archivo contiene los valores de las propiedades de un elemento web.  Para obtener más información, vea [Bloque de creación: elementos web](http://go.microsoft.com/fwlink/?LinkId=177791).|  
|.ascx|Un archivo ASP.NET UserControl.  Este archivo define la interfaz de usuario de un elemento web visual.|  
|.aspx|Un archivo de paginación ASP.NET.  Este archivo contiene marcado XML que define una página de aplicación.|  
|Archivos .cs o .vb|Estos archivos de código definen el comportamiento de las personalizaciones de SharePoint que tienen un modelo de programación al que se puede tener acceso desde el código de Visual C\# o Visual Basic, como las páginas de aplicación, los elementos web y los flujos de trabajo.|  
  
## Crear plantillas de proyectos  
 Cuando se crea una plantilla de proyecto de SharePoint, hay algunos archivos que siempre son necesarios y otros opcionales que podrían usar ciertos tipos de proyectos.  Normalmente, los proyectos de SharePoint incluyen al menos un elemento de proyecto de SharePoint.  Sin embargo, esto no es necesario.  Por ejemplo, se puede definir una plantilla de proyecto de SharePoint destinada a usarse exclusivamente para implementar soluciones de SharePoint creadas en otros proyectos.  
  
 Para consultar un tutorial en el que se muestra cómo se define un tipo de elemento de proyecto de SharePoint y se crea una plantilla de proyecto para él, vea [Tutorial: Crear un elemento de proyecto de columna de sitio con una plantilla de proyecto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).  
  
 En la tabla siguiente se hace una lista de los archivos que deben incluirse en una plantilla de proyecto de SharePoint.  
  
|Archivo obligatorio|Descripción|  
|-------------------------|-----------------|  
|Un archivo .vstemplate|Este archivo proporciona a Visual Studio la información necesaria para mostrar la plantilla en el cuadro de diálogo **Nuevo proyecto** y crear un proyecto a partir de la plantilla.  Para obtener más información, vea [NIB: Visual Studio Template Metadata Files](http://msdn.microsoft.com/es-es/129d59b5-7f9c-4daf-9832-eaedb3c4c961).|  
|Un archivo .csproj o .vbproj|Este es el archivo de proyecto.  Define el contenido y la configuración del proyecto.|  
|Package.package|Este archivo define el paquete de implementación del proyecto.  Cuando usa el Diseñador de paquetes para personalizar el paquete de solución del proyecto, Visual Studio almacena los datos sobre el paquete de solución en este archivo.<br /><br /> Cuando cree una plantilla de proyecto de SharePoint personalizada, le recomendamos que incluya en el archivo Package.package exclusivamente el contenido mínimo necesario y que configure el paquete de solución usando las API del espacio de nombres <xref:Microsoft.VisualStudio.SharePoint.Packages> en una extensión asociada a la plantilla de proyecto.  De este modo, la plantilla de proyecto estará protegida frente a los cambios que se realicen posteriormente en la estructura del archivo Package.package.  Para obtener un ejemplo en el que se muestra cómo se crea un archivo Package.package únicamente con el contenido mínimo necesario, vea [Tutorial: Crear un elemento de proyecto de columna de sitio con una plantilla de proyecto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).<br /><br /> Si desea modificar directamente el archivo Package.package, puede comprobar el contenido usando el esquema situado en %Program Files \(x86\)%\\Microsoft Visual Studio 11.0\\Xml\\Schemas\\PackageModelSchema.xsd.|  
|Package.Template.xml|Este archivo proporciona la base del archivo de manifiesto de la solución \(manifest.xml\) del paquete de solución de SharePoint \(.wsp\) que se genera a partir del proyecto.  Puede agregar contenido a este archivo si desea especificar algún comportamiento que no es previsible que modifiquen los usuarios del tipo de proyecto.  Para obtener más información, vea [Bloque de creación: Soluciones](http://go.microsoft.com/fwlink/?LinkId=169186) y [Solution Schema](http://go.microsoft.com/fwlink/?LinkId=177794).<br /><br /> Cuando compila un paquete de solución a partir del proyecto, Visual Studio combina el contenido de los archivos Package.package y Package.Template.xml en el archivo de manifiesto de la solución.  Para obtener más información sobre la compilación de paquetes de soluciones, vea [How to: Create a SharePoint Solution Package \(wsp\)](http://msdn.microsoft.com/es-es/b24be45c-e91d-49bb-afb0-7b265404214b).|  
  
 En la tabla siguiente se hace una lista de los archivos opcionales que se pueden incluir en la plantilla de proyecto.  
  
|Archivo opcional|Descripción|  
|----------------------|-----------------|  
|Elementos de proyecto de SharePoint|Puede incluir uno o más archivos .spdata que definen los tipos de elemento de proyecto de SharePoint.  Cada archivo .spdata debe tener una implementación coincidente de <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> en un ensamblado de extensión que se incluye en el paquete VSIX con la plantilla de proyecto.  Para obtener más información, vea [Crear plantillas de elementos](#creatingitemtemplates).<br /><br /> Normalmente, los proyectos de SharePoint incluyen al menos un elemento de proyecto de SharePoint.  Sin embargo, esto no es necesario.|  
|*NombreDeCaracterística*.feature|Este archivo define una característica de SharePoint que se usa para agrupar varios elementos de proyecto para su implementación.  Cuando usa el Diseñador de características para personalizar una característica del proyecto, Visual Studio almacena los datos sobre la característica en este archivo.  Si desea agrupar los elementos de proyecto en características diferentes, puede incluir varios archivos .feature.<br /><br /> Cuando cree una plantilla de proyecto de SharePoint personalizada, le recomendamos que incluya exclusivamente el contenido mínimo necesario en cada archivo .feature y que configure las características usando las API del espacio de nombres <xref:Microsoft.VisualStudio.SharePoint.Features> en una extensión asociada a la plantilla de proyecto.  De este modo, la plantilla de proyecto estará protegida frente a los cambios que se realicen posteriormente en la estructura del archivo .feature.  Para obtener un ejemplo en el que se muestra cómo se crea un archivo .feature únicamente con el contenido mínimo necesario, vea [Tutorial: Crear un elemento de proyecto de columna de sitio con una plantilla de proyecto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).<br /><br /> Si desea modificar directamente el archivo .feature, puede comprobar el contenido usando el esquema situado en %Program Files \(x86\)%\\Microsoft Visual Studio 11.0\\Xml\\Schemas\\FeatureModelSchema.xsd.|  
|*NombreDeCaracterística*.Template.xml|Este archivo proporciona la base del archivo de manifiesto de cada característica \(Feature.xml\) que se genera a partir del proyecto.  Puede agregar contenido a este archivo si desea especificar algún comportamiento que no es previsible que modifiquen los usuarios del tipo de proyecto.  Para obtener más información, vea [Bloque de creación: Características](http://go.microsoft.com/fwlink/?LinkId=169183) y los archivos [Feature.xml](http://go.microsoft.com/fwlink/?LinkId=177795).<br /><br /> Al compilar un paquete de solución del proyecto, Visual Studio combina el contenido de cada par de archivos *NombreDeCaracterística*.feature y *NombreDeCaracterística*.Template.xml en un archivo de manifiesto de característica.  Para obtener más información sobre la compilación de paquetes de soluciones, vea [How to: Create a SharePoint Solution Package \(wsp\)](http://msdn.microsoft.com/es-es/b24be45c-e91d-49bb-afb0-7b265404214b).|  
  
## Crear asistentes para plantillas de elemento y las plantillas de proyecto  
 Después de definir un tipo de elemento de proyecto de SharePoint y asociarlo con una plantilla de elemento o de proyecto, también puede crear un asistente.  El asistente muestra cuándo un desarrollador usa la plantilla de elemento para agregar el elemento de proyecto de SharePoint a un proyecto, o cuándo un desarrollador usa la plantilla de proyecto para crear un nuevo proyecto que contenga el elemento de proyecto de SharePoint.  El asistente se puede usar para recopilar información de los desarrolladores e inicializar el nuevo elemento de proyecto de SharePoint.  
  
 Para consultar los tutoriales que muestran cómo crear asistentes para las plantillas de elemento y plantillas de proyecto, vea [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md) y [Tutorial: crear un elemento de proyecto de columna de sitio con una plantilla de proyecto, parte 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).  
  
## Vea también  
 [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)   
 [Tutorial: Crear un elemento de proyecto de columna de sitio con una plantilla de proyecto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)   
 [Tutorial: crear un elemento de proyecto de columna de sitio con una plantilla de proyecto, parte 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)   
 [Crear plantillas para proyectos y elementos en Visual Studio](../ide/creating-project-and-item-templates.md)  
  
  