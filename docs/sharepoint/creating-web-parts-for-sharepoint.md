---
title: "Crear elementos web para SharePoint | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Microsoft.SharePoint.WebControls.DateTimeControl"
  - "Microsoft.SharePoint.WebControls.CssLink"
  - "Microsoft.SharePoint.WebControls.RssLink"
  - "Microsoft.SharePoint.WebControls.Theme"
  - "Microsoft.SharePoint.WebControls.AspMenu"
  - "Microsoft.SharePoint.WebControls.ListProperty"
  - "Microsoft.SharePoint.WebControls.ProjectProperty"
  - "Microsoft.SharePoint.WebControls.FormsDigest"
  - "Microsoft.SharePoint.WebControls.ScriptLink"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "desarrollo de SharePoint en Visual Studio, Elementos web"
  - "elementos web [desarrollo de SharePoint en Visual Studio], diseñar"
ms.assetid: a6349e85-45cf-4766-b856-e25c9f1ffd34
caps.latest.revision: 42
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 41
---
# Crear elementos web para SharePoint
  Usando elementos web, puede modificar el contenido, el aspecto y el comportamiento de las páginas de un sitio de SharePoint a través de un explorador.  Los elementos web son controles de servidor que se ejecutan dentro de una página de elementos web: son los bloques de creación de las páginas que aparecen en un sitio de SharePoint.  Vea [Bloque de creación: elementos web](http://go.microsoft.com/fwlink/?LinkID=182097).  
  
 Puede crear y depurar elementos web en un sitio de SharePoint mediante el uso de plantillas de Visual Studio.  
  
## Crear un elemento web en Visual Studio  
 Cree un elemento web agregando un **elemento web** a un proyecto de SharePoint.  Puede utilizar un elemento **elemento web** en una solución en espacio aislado o en una solución de granja de servidores.  
  
 Si desea diseñar un elemento web utilizando un diseñador, cree un proyecto **Elemento web visual** o agregue el elemento **elemento web visual** a un proyecto de SharePoint.  Solo puede utilizar un elemento **elemento web visual** en una solución de granja de servidores.  
  
### Elemento de elemento web  
 Un **elemento web** proporciona archivos que puede usar para diseñar un elemento web para un sitio de SharePoint.  Al agregar un elemento **elemento web**, Visual Studio crea una carpeta en el proyecto y le agrega varios archivos.  En la tabla siguiente se describe cada archivo.  
  
|Archivo|Descripción|  
|-------------|-----------------|  
|Elements.xml|Contiene información que utiliza el archivo de definición de características en el proyecto para implementar el elemento web.|  
|Archivo .webpart|Proporciona información que SharePoint necesita para mostrar el elemento web en una galería de elementos web.|  
|Archivo de código|Contiene métodos que agregan controles al elemento web y generan el contenido personalizado dentro del elemento web.|  
  
 Para obtener más información, vea [Cómo: Crear un elemento web de SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md).  
  
### Elemento de elemento web visual  
 Un elemento web visual es un elemento web que se crea utilizando el diseñador de Visual Web Developer en Visual Studio.  Vea [Mapa de contenido del entorno de desarrollo web de Visual Studio](http://msdn.microsoft.com/es-es/9c31f93b-c8fb-4599-9b14-6194ec8c7539).  
  
 Un elemento web visual funciona igual que cualquier otro elemento web.  Para agregar controles, como botones y cuadros de texto, a elemento web, agregue código a un archivo XML.  Sin embargo, se agregan controles a un elemento web visual arrastrándolos o copiándolos en el elemento web del **Cuadro de herramientas** de Visual Studio.  El diseñador entonces genera el código necesario en el archivo XML.  Vea [Cómo: Crear un elemento web de SharePoint con un diseñador](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md).  
  
## Controles de SharePoint  
 Visual Studio proporciona algunos controles para crear páginas de SharePoint, como páginas de aplicación.  Estos controles aparecen en el **Cuadro de herramientas** en **Controles de SharePoint**.  La funcionalidad para estos controles se deriva del espacio de nombres [Microsoft.SharePoint.WebControls](http://go.microsoft.com/fwlink/?LinkId=235315), que contiene controles de servidor ASP.NET que se utilizan en el sitio de SharePoint y muestran las páginas.  
  
|Nombre del control|Descripción|  
|------------------------|-----------------|  
|[AspMenu](http://go.microsoft.com/fwlink/?LinkId=235307)|Inserta un menú de ASP.  Para obtener más información, vea [Información general sobre el control Menu](http://go.microsoft.com/fwlink/?LinkId=235316).|  
|[CssLink](http://go.microsoft.com/fwlink/?LinkId=235308)|Inserta un elemento de **LINK** en la página .aspx y aplica una o varias hojas de estilos externas definidas por **CssRegistration**.|  
|[DateTimeControl](http://go.microsoft.com/fwlink/?LinkId=235306)|Inserta un control DateTime en la página .aspx.|  
|[FormDigest](http://go.microsoft.com/fwlink/?LinkId=235309)|Inserta una validación de seguridad en la página .aspx|  
|[ListProperty](http://go.microsoft.com/fwlink/?LinkId=235310)|Devuelve una propiedad de una lista especificada.|  
|[ProjectProperty](http://go.microsoft.com/fwlink/?LinkId=235311)|Devuelve una propiedad global del sitio web actual.|  
|[RssLink](http://go.microsoft.com/fwlink/?LinkId=235312)|Inserta un vínculo a una fuente RSS en la página .aspx.|  
|[ScriptLink](http://go.microsoft.com/fwlink/?LinkId=235313)|Proporciona propiedades y métodos para registrar recursos, como scripts, en una página para que se puedan solicitar cuando se representa la página.|  
|[Theme](http://go.microsoft.com/fwlink/?LinkId=235314)|Aplica un tema a la página .aspx.|  
  
## Depurar un elemento web  
 Puede depurar un proyecto de SharePoint que contiene un elemento web igual que otros proyectos de Visual Studio.  Al iniciar el depurador de Visual Studio, Visual Studio abre el sitio de SharePoint.  
  
 Para iniciar la depuración del código, agregue el elemento web a una página de elementos web de SharePoint.  
  
 Para obtener más información sobre la depuración de proyectos de SharePoint, vea [Solucionar problemas de soluciones de SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md).  
  
## Limitaciones de los elementos web visuales  
 A partir de Visual Studio, puede agregar elementos web visuales a las soluciones en espacio aislado de SharePoint y a las soluciones de granja.  Sin embargo, los elementos web visuales tienen las siguientes limitaciones:  
  
-   Los elementos web visuales no admiten parámetros reemplazables.  Para obtener más información, vea [Parámetros reemplazables](../sharepoint/replaceable-parameters.md).  
  
-   Los controles de usuario o elementos web visuales no se pueden arrastrar y quitar, o copiar sobre elementos web visuales.  Esta acción provocará un error de compilación.  
  
-   Los elementos web visuales no admiten directamente tokens del servidor de SharePoint como $SPUrl.  Para obtener más información, vea "Restricciones de token en elementos web visuales en espacio aislado" en el tema [Solucionar problemas de soluciones de SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md).  
  
-   De vez en cuando, en los elementos web visuales en una solución de espacio aislado aparece el error, "Se rechazó la solicitud de ejecución de código de espacio aislado porque el servicio host de código de espacio aislado estaba demasiado ocupado para atender la solicitud". Para obtener más información sobre este error, vea este artículo en el [blog del equipo de SharePoint Developer](http://go.microsoft.com/fwlink/?LinkId=225932).  
  
-   La depuración de JavaScript de servidor no se admite en Visual Studio, pero se admite la depuración de JavaScript de cliente.  
  
     Aunque se puede agregar JavaScript alineado en un archivo de marcado de servidor, no se admite la depuración en los puntos de interrupción agregados al marcado.  Para depurar JavaScript, haga referencia a un archivo externo de JavaScript en el archivo de marcado y después establezca puntos de interrupción en el archivo JavaScript.  
  
-   La depuración de código [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] alineado debe realizarse en el archivo de código generado en lugar de en el archivo de marcado.  
  
-   Los elementos visuales web no admiten el uso de la directiva `<@ Assembly Src=`.  
  
-   Los controles web de SharePoint y algunos controles de [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] no se admiten en el entorno de SharePoint en espacio aislado.  Si los controles no compatibles se utilizan en un elemento web visual en una solución en espacio aislado, aparece el error "El tipo o nombre del espacio de nombres 'Theme' no existe en el espacio de nombres 'Microsoft.SharePoint.WebControls'".  
  
 Para obtener más información sobre soluciones en espacio aislado, vea [Diferencias entre soluciones en espacio aislado y soluciones de granja](../sharepoint/differences-between-sandboxed-and-farm-solutions.md).  
  
## Crear elementos web basados en el estilo anterior de SharePoint  
 Puede usar las plantillas de Visual Studio para crear elementos web de [!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)] personalizados para SharePoint.  Los elementos web de [!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)] se compilan sobre la infraestructura de los elementos web de [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] y son el tipo recomendado para los nuevos proyectos.  
  
 En muy pocos casos podría tener que crear un elemento web utilizando el elemento web del estilo anterior de SharePoint.  Puede utilizar Visual Studio para crear estos tipos de elementos web, pero Visual Studio no proporciona plantillas diseñadas específicamente para ayudarle a crearlos.  
  
 Para obtener más información sobre cuándo crear un elemento web del estilo anterior de SharePoint, vea [Infraestructura de elementos web en SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=169290).  Para obtener más información sobre cómo crear un elemento web utilizando el elemento web basado en el estilo anterior de SharePoint, vea el [tutorial para crear un elemento web básico de SharePoint](http://go.microsoft.com/fwlink/?LinkId=169288).  
  
## Temas relacionados  
  
|Título|Descripción|  
|------------|-----------------|  
|[Cómo: Crear un elemento web de SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md)|Muestra cómo se crean elementos web para las páginas de SharePoint.|  
|[Cómo: Crear un elemento web de SharePoint con un diseñador](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)|Muestra cómo se crean elementos web de SharePoint utilizando una superficie de diseño visual.|  
|[Cómo: Crear un control de usuario para una página de aplicación o elemento web de SharePoint](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|Muestra cómo se crean controles personalizados y reutilizables que se pueden usar en las páginas de aplicación y los elementos web que se ejecutan en SharePoint.|  
|[Tutorial: Crear un elemento web para SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)|Describe cómo diseñar un elemento web para SharePoint.|  
|[Tutorial: Crear un elemento web para SharePoint mediante un diseñador](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)|Describe cómo se diseña un elemento web de SharePoint arrastrando controles a una superficie de diseño visual.|  
|[Tutorial: Crear un elemento web de Silverlight que muestre OData para SharePoint](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md)|Describe cómo diseñar un elemento web para SharePoint que hospeda una aplicación de Silverlight y muestra datos de listas de SharePoint.|  
|[Trabajar con Visual Web Developer](http://msdn.microsoft.com/es-es/9c31f93b-c8fb-4599-9b14-6194ec8c7539)|Describe cómo utilizar el diseñador que aparece al abrir una página web en el proyecto.|  
  
  