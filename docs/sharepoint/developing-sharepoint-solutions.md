---
title: Desarrollar soluciones de SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.ProjectProperties
- VS.SharePointTools.Project.ProjectItemProperties
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, overview
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: bc45f1420f073347153c6b7b8dd72cae44dd6b0f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53871062"
---
# <a name="develop-sharepoint-solutions"></a>Desarrollar soluciones de SharePoint
  En [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] están disponibles varias plantillas de tipo de proyecto de SharePoint para crear sitios y elementos de sitio de SharePoint. Para obtener una lista de los tipos de proyecto disponibles, consulte [SharePoint plantillas de elemento de proyecto y](../sharepoint/sharepoint-project-and-project-item-templates.md). A continuación se ofrece una descripción de los elementos y las propiedades de un proyecto de SharePoint.  
  
 Para obtener información sobre SharePoint 2013 y los complementos de SharePoint, vea [SharePoint 2013](https://msdn.microsoft.com/library/jj162979.aspx) y [Crear complementos de SharePoint](/sharepoint/dev/sp-add-ins/sharepoint-add-ins).  
  
## <a name="elements-of-a-sharepoint-project"></a>Elementos de un proyecto de SharePoint
 Los nodos de un proyecto SharePoint se conocen como *elementos de SharePoint*. Los elementos de SharePoint pueden contener uno o varios archivos secundarios, a los que se denomina *archivos de elementos de SharePoint*, como los archivos de configuración [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] , los formularios .aspx, etc.  
  
 En lugar de crear los proyectos utilizando plantillas de proyecto que se rellenan con archivos de elementos de proyecto, puede utilizar la plantilla **Proyecto vacío** para crear un proyecto de SharePoint vacío y, a continuación, agregar los elementos de proyecto manualmente. Opcionalmente, los proyectos de SharePoint también pueden contener uno o más archivos de características (para la activación en SharePoint) y un archivo empaquetado en el que distribuir el proyecto.  
  
### <a name="special-nodes"></a>Nodos especiales
 Cada proyecto de SharePoint contiene dos nodos a los que no se pueden cambiar el nombre, eliminar, cortar, copiar ni arrastrar del proyecto. Estos nodos son los siguientes:  
  
- Características    
- Paquete  
  
  Ambos nodos aparecen en todos los proyectos SharePoint aun cuando no se hayan definido característica ni paquetes para el proyecto.  
  
#### <a name="features-node"></a>Nodo características
 El nodo **Características** contiene una o más características de proyecto de SharePoint. Una característica es un contenedor de extensiones para SharePoint. Una vez implementada la característica en el servidor de SharePoint, puede incluirse en las definiciones de sitios o los administradores de SharePoint pueden activarla individualmente en sitios de SharePoint. Para más información, vea [Trabajar con características](http://go.microsoft.com/fwlink/?LinkID=147704).  
  
 Al agregar un elemento, como un tipo de contenido o una instancia de lista, a un proyecto SharePoint, se agrega a una característica del nodo **Características** . El ámbito del elemento determina si se agrega a una característica nueva o existente. Si el nuevo elemento tiene el mismo ámbito que una característica existente, se agrega a esa característica. De lo contrario, se agrega a una nueva característica.  
  
 Para agregar una característica manualmente, ejecute el comando **Agregar característica** del menú contextual del nodo Características. Puede ver o cambiar el contenido de una característica utilizando el Diseñador de características. Para obtener más información, vea [Cómo: Personalizar una característica de SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md).  
  
 Cuando una característica se agrega a un proyecto de SharePoint, aparece en el **Explorador de soluciones** como un nodo con el nombre predeterminado Feature*x*.feature, donde *x* es un número único. Una vez implementada en el servidor de SharePoint, un administrador de SharePoint puede activarla y ponerla a disposición de los usuarios del sitio de SharePoint.  
  
#### <a name="package-node"></a>Nodo paquete
 El nodo **Paquete** contiene un archivo único que actúa como el mecanismo de distribución para el proyecto de SharePoint. Este archivo, conocido como un *paquete de solución*, es. Basado en el archivo CAB con un. Extensión WSP. Un paquete de solución es un archivo implementable y reutilizable que contiene un conjunto de características, definiciones del sitio y ensamblados que se aplican a los sitios de SharePoint y que es posible habilitar o deshabilitar individualmente. El nodo **Paquete** también contiene siempre un archivo que se denomina Package.wspdef, un archivo de definición de [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] para el paquete. Una vez que se implementa un paquete en el servidor que ejecuta SharePoint, el administrador de SharePoint puede instalarlo y activar sus características.  
  
 Puede ver o cambiar el contenido del paquete en el Diseñador de paquetes haciendo doble clic en el nodo del paquete o abra su menú contextual y, a continuación, eligiendo **abierto**. Para obtener más información, consulte [paquetes de solución de SharePoint crear](../sharepoint/creating-sharepoint-solution-packages.md).  
  
## <a name="sharepoint-project-and-project-item-properties"></a>Proyecto de SharePoint y las propiedades del elemento de proyecto
 Los proyectos SharePoint, al igual que otros proyectos de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , muestran las propiedades en la ventana Propiedades y en la página Propiedades. Las propiedades que se muestran dependen del nodo que está seleccionado.  
  
 Cuando un proyecto, un elemento de proyecto o un nodo de archivo de elemento de proyecto de SharePoint se selecciona en el **Explorador de soluciones**, aparecen las siguientes propiedades en la ventana Propiedades o en la página del propiedades:  
  
### <a name="project-properties"></a>Propiedades del proyecto
  
|Nombre de la propiedad|Descripción|  
|-------------------|-----------------|  
|Configuración de implementación activa|Especifica la serie de pasos realizados durante la implementación. Para obtener más información, vea [Cómo: Editar una configuración de implementación de SharePoint](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md).|  
|Destino de implementación del ensamblado|Determina dónde se encuentran los *ensamblados de aplicación de SharePoint* . Los valores de ubicación de ensamblados válidos son *GlobalAssemblyCache* (valor predeterminado) o *WebApplication*.<br /><br /> Si la propiedad *Sandboxed Solution* está establecida en **true**, esta propiedad estará deshabilitada.|  
|Retraer automáticamente después de depurar|Especifica si la solución implementada se retrae automáticamente de SharePoint tras ejecutar la aplicación en modo de depuración en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Cuando está activada, la solución se retracta si el IDE vuelve a la Vista de diseño tras la depuración. Cuando está desactivada, la solución no se retrae. Para más información, vea [Retracción de una solución](http://go.microsoft.com/fwlink/?LinkId=183819).|  
|Editar configuración|Especifica la configuración de implementación que se va a usar en el proyecto. Para obtener más información, vea [Cómo: Editar una configuración de implementación de SharePoint](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md) y [implementar, publicar y actualizar paquetes de solución SharePoint](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md).|  
|Habilitar depuración de Silverlight (en lugar de depuración de script)|Cuando está activada, el depurador de Silverlight se incorpora al proceso de depuración. Cuando está desactivada, el depurador de script se incorpora al proceso de depuración. Para más información, vea la [información general sobre depuración de Silverlight](http://go.microsoft.com/fwlink/?LinkId=179826).|  
|Incluir ensamblado en paquete|Especifica si el ensamblado del proyecto se empaqueta en tiempo de compilación o no.|  
|Línea de comandos posterior a la implementación|Especifica los comandos que se van a ejecutar después de implementar la solución de SharePoint. Esta línea admite los comandos de proceso por lotes así como la resolución de variables de MSBuild. Para obtener más información, vea [Cómo: Establecer comandos de implementación de SharePoint](../sharepoint/how-to-set-sharepoint-deployment-commands.md).|  
|Línea de comandos anterior a la implementación|Especifica los comandos que se van a ejecutar antes de implementar la solución de SharePoint. Esta línea admite los comandos de proceso por lotes así como la resolución de variables de MSBuild. Para obtener más información, vea [Cómo: Establecer comandos de implementación de SharePoint](../sharepoint/how-to-set-sharepoint-deployment-commands.md).|  
|Archivo de proyecto|Nombre del archivo que contiene la información sobre el proyecto, incluyendo el modo de compilación, la configuración y otros datos.|  
|Carpeta de proyecto|Ubicación del archivo de proyecto en el sistema. (Solo lectura).|  
|Sandboxed Solution|Especifica si el proyecto se debería implementar como una *solución en espacio aislado*, también conocida como *solución creada por el usuario*. Las soluciones en espacio aislado no son necesariamente de confianza. Un valor de **true** significa que el proyecto se implementa como una solución en un espacio aislado y un valor de **false** significa que el proyecto se implementa como una solución de granja. Para obtener más información, vea [Sandboxed Solution Considerations](../sharepoint/sandboxed-solution-considerations.md) y [Differences Between Sandboxed and Farm Solutions](../sharepoint/differences-between-sandboxed-and-farm-solutions.md).|  
|URL del sitio|Especifica la dirección [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] del sitio de destino de este proyecto.|  
|Elemento de inicio|Especifica el primer elemento del proyecto que se va a ejecutar.|  
  
 Cuando se elige un archivo de elemento de SharePoint (como un flujo de trabajo o una característica del nodo Características), las propiedades siguientes aparecen en la ventana Propiedades:  
  
### <a name="project-item-properties"></a>Propiedades de elemento de proyecto
  
|Nombre de la propiedad|Descripción|  
|-------------------|-----------------|  
|Resolución de conflictos de implementación|Especifica la acción que se realiza al implementar un elemento de proyecto cuyas propiedades son idénticas a las de un elemento que ya está en el servidor. Para obtener más información, consulta [Troubleshooting SharePoint Packaging and Deployment](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md).|  
|Propiedades de características|Especifica un conjunto de valores (almacenados como pares clave-valor) que se incluye con una característica cuando se implementa en SharePoint. Una vez implementada la característica, se puede obtener acceso a los valores de propiedad en el código. Para obtener más información, consulta [Proporcionar información de empaquetado e implementación en los elementos del proyecto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|  
|Receptor de características|Proporciona código que se ejecuta cuando se producen determinados eventos con una característica de un elemento de proyecto. Para obtener más información, consulta [Proporcionar información de empaquetado e implementación en los elementos del proyecto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|  
|Nombre de carpeta|Nombre de la carpeta de elementos de proyecto de SharePoint.|  
|Referencias de salida del proyecto|Especifica una dependencia, como un ensamblado, que el elemento de proyecto necesita ejecutar. Para obtener más información, consulta [Proporcionar información de empaquetado e implementación en los elementos del proyecto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|  
|Entradas de controles seguros|Especifica controles que están seguros para que los usuarios los editen. Para obtener más información, consulta [Proporcionar información de empaquetado e implementación en los elementos del proyecto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|  
  
### <a name="project-item-file-properties"></a>Propiedades del archivo de elemento de proyecto
  
|Nombre de la propiedad|Descripción|  
|-------------------|-----------------|  
|Acción de compilación|Especifica cómo se relaciona el archivo con los procesos de implementación y compilación. Para más información, vea las [propiedades del archivo](/previous-versions/visualstudio/visual-studio-2010/0c6xyb66\(v\=vs.100\)).|  
|Copiar en el directorio de salida|Especifica si los archivos de origen se copiarán en el directorio de salida. Puede presentar uno de los siguientes valores:<br /><br /> -   *No copiar*<br />-   *Copiar siempre*<br />-   *Copiar si es posterior*<br /><br /> Para más información, vea las [propiedades del archivo](/previous-versions/visualstudio/visual-studio-2010/0c6xyb66\(v\=vs.100\)).|  
|Herramienta personalizada|Especifica el nombre de una herramienta, si existe, que transforma el archivo en tiempo de diseño y coloca la salida de la transformación en otro archivo. Por ejemplo, un archivo del conjunto de datos (.[!INCLUDE[TLA2#tla_xsd](../sharepoint/includes/tla2sharptla-xsd-md.md)]) que tiene una herramienta personalizada predeterminada. Para más información, vea las [propiedades del archivo](/previous-versions/visualstudio/visual-studio-2010/0c6xyb66\(v\=vs.100\)).|  
|Espacio de nombres de la herramienta personalizada|Espacio de nombres en el que se copia la salida de la herramienta personalizada. Para más información, vea las [propiedades del archivo](/previous-versions/visualstudio/visual-studio-2010/0c6xyb66\(v\=vs.100\)).|  
|Ubicación de la implementación|Ruta de acceso completa del archivo en el servidor de SharePoint. Esta ruta de acceso se compone de las subpropiedades Raíz de la implementación y Ruta de acceso de la implementación.|  
|Ruta de acceso de la implementación|La ruta de acceso relativa del archivo en el archivo de SharePoint Server, como Workflow1\\. La ruta de acceso completa del archivo se crea concatenando el valor de *Deployment Path* al final del valor de *Deployment Root* .<br /><br /> Al seleccionar un valor de *RootFile* para el *tipo de implementación* los cambios de propiedad el *Deployment Root* propiedad \<SharePointRoot >\\, lo que da una ruta de acceso completa de \<SharePointRoot > \Workflow1\\. Para obtener más información, consulte [empaquetar e implementar soluciones de SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md).|  
|Deployment Root|Cadena. Carpeta raíz donde se implementa el archivo en el servidor de SharePoint. Por ejemplo, \<SharePointRoot > \Template\Features\\\<NombreDeCaracterística >\\.<br /><br /> El valor de la propiedad *Deployment Root* viene determinado por el valor de *Deployment Type* .|  
|Deployment Type|Tipo de implementación del archivo, que determina su valor *Deployment Root* . Puede presentar uno de los siguientes valores:<br /><br /> NoDeployment:  *\<ningún valor >*<br /><br /> ElementManifest: *\<SharePointRoot > \Template\Features\\\<NombreDeCaracterística >*\\<br /><br /> ElementFile: *\<SharePointRoot > \Template\Features\\\<NombreDeCaracterística >\\*<br /><br /> TemplateFile: *\<SharePointRoot > \Template\\*<br /><br /> RootFile: *\<SharePointRoot >\\*<br /><br /> GlobalResource: *\<SharePointRoot > \Resources\\*<br /><br /> ClassResource: *\<ClassResourcePath >\\*<br /><br /> Para obtener más información, consulta <xref:Microsoft.VisualStudio.SharePoint.DeploymentType>.|  
|Nombre de archivo|Nombre del archivo o carpeta para el archivo de elementos.|  
|Ruta de acceso completa|Ubicación del archivo del elemento. (Solo lectura).|  
  
## <a name="related-topics"></a>Temas relacionados
  
|Título|Descripción|  
|-----------|-----------------|  
|[Plantillas de proyecto y de elementos de proyecto de SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md)|Describe el proyecto de SharePoint y las plantillas de elementos de proyecto disponibles en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].|  
|[Cómo: Agregar elementos a un proyecto de SharePoint](../sharepoint/how-to-add-items-to-a-sharepoint-project.md)|Describe cómo agregar elementos nuevos o existentes a un proyecto de SharePoint en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .|  
|[Tutorial: Crear una columna de sitio, el tipo de contenido y la lista de SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)|Ofrece instrucciones paso a paso para crear un campo de clientes, un tipo de contenido, una definición de lista y una instancia de lista.|  
|[Cómo: Crear un receptor de eventos](../sharepoint/how-to-create-an-event-receiver.md)|Describe cómo agregar un receptor de eventos para el proyecto creado en [Tutorial: Crear una columna de sitio, el tipo de contenido y la lista de SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md).|  
|[Crear soluciones de flujo de trabajo de SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md)|Describe cómo crear proyectos de flujo de trabajo que incluye formularios de asociación y formularios de iniciación de flujos de trabajo.|  
|[Crear páginas para SharePoint](../sharepoint/creating-pages-for-sharepoint.md)|Describe cómo se pueden crear páginas para SharePoint como páginas de aplicación, páginas de sitio, páginas maestras y diseños de página.|  
|[Crear elementos web para SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)|Describe cómo se agregan controles que permiten a los usuarios modificar directamente el contenido, el aspecto y el comportamiento de las páginas del sitio de SharePoint a través de un explorador.|  
|[Crear controles reutilizables para elementos web o páginas de aplicación](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)|Describe cómo se crean los controles de usuario que pueden usar las páginas de la aplicación y los elementos web que se ejecutan en SharePoint.|  
|[Integrar datos profesionales en SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)|Describe cómo integrar los datos de los servicios Web y las aplicaciones de servidor back-end en una aplicación de SharePoint.|  
|[Crear definiciones de sitios para SharePoint](../sharepoint/creating-site-definitions-for-sharepoint.md)|Describe cómo crear las definiciones del sitio: plantillas que se utilizan para crear sitios de SharePoint.|  
|[Importar elementos de un sitio de SharePoint existente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)|Describe cómo importar elementos, como tipos de contenido y módulos, de un sitio de SharePoint existente en un proyecto SharePoint de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .|  
|[Usar módulos para incluir archivos en la solución](../sharepoint/using-modules-to-include-files-in-the-solution.md)|Describe cómo utilizar los módulos para implementar los archivos del proyecto de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] en el sitio de SharePoint.|  
|[Examinar las conexiones de SharePoint mediante el Explorador de servidores](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)|Describe cómo examinar los sitios locales de SharePoint mediante el Explorador de servidores.|  
|[Proporcionar información de empaquetado e implementación de elementos de proyecto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)|Describe cómo utilizar las propiedades de los elementos de proyecto para proporcionar información de empaquetado y distribución de los proyectos, como entradas de controles seguros, referencias de salida del proyecto y propiedades de las características.|  
|[Cómo: Agregar y quitar carpetas asignadas](../sharepoint/how-to-add-and-remove-mapped-folders.md)|Describe cómo se pueden agregar las carpetas asignadas a un proyecto para facilitar el acceso a los recursos de SharePoint.|  
|[Consideraciones sobre la solución en espacio aislado](../sharepoint/sandboxed-solution-considerations.md)|Describe los problemas asociados a las soluciones en recintos de seguridad.|  
|[Seguridad para las soluciones de SharePoint](../sharepoint/security-for-sharepoint-solutions.md)|Describe cuestiones de seguridad relacionadas con el desarrollo de soluciones de SharePoint en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].|  
|[Cuadro de diálogo Selector de URL &#40;desarrollo de SharePoint en Visual Studio&#41;](../sharepoint/url-picker-dialog-box-sharepoint-development-in-visual-studio.md)|Describe un cuadro de diálogo que se puede usar para agregar las referencias de la ruta de acceso a los recursos en el proyecto o en el servidor de SharePoint local.|  
  
## <a name="see-also"></a>Vea también
 [Introducción a &#40;desarrollo de SharePoint en Visual Studio&#41;](../sharepoint/getting-started-sharepoint-development-in-visual-studio.md)   
 [Examinar las conexiones de SharePoint mediante el Explorador de servidores](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)   
 [Compilar y depurar soluciones de SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)   
 [Empaquetar e implementar soluciones de SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
