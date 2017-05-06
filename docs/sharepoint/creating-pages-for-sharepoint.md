---
title: "Crear p&#225;ginas para SharePoint"
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
  - "páginas de contenido [desarrollo de SharePoint en Visual Studio], diseñar"
  - "páginas maestras [desarrollo de SharePoint en Visual Studio], diseñar"
  - "diseños de página [desarrollo de SharePoint en Visual Studio], diseñar"
  - "desarrollo de SharePoint en Visual Studio, páginas de contenido"
  - "desarrollo de SharePoint en Visual Studio, páginas maestras"
  - "desarrollo de SharePoint en Visual Studio, diseños de página"
ms.assetid: 57678ed1-841f-45de-a1d3-5f9e233bf3ce
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# Crear p&#225;ginas para SharePoint
  Puede crear páginas de aplicación, páginas de sitio, páginas maestras y diseños de página para un sitio de SharePoint.  
  
 Puede crear las páginas de la aplicación mediante una plantilla en Visual Studio.  Cree páginas de sitio, páginas maestras y diseños de página mediante SharePoint Designer.  A continuación, puede importar estas páginas a Visual Studio para usarlas en un proyecto de SharePoint.  
  
 También puede modificar el aspecto y comportamiento de las páginas con las hojas de estilos en cascada, ECMAScript y temas.  
  
## Tipos de páginas de SharePoint  
 En la tabla siguiente se describen los cuatro tipos principales de páginas que contiene un sitio de SharePoint.  
  
|Tipo de página|Descripción|  
|--------------------|-----------------|  
|Páginas de aplicación|Cree una página de aplicación si desea que la página contenga código personalizado o desea que varios sitios la compartan.  De lo contrario, la mejor opción podría ser una página de sitio.|  
|Páginas de sitio|Cree una página de sitio si desea realizar cualquiera de las siguientes tareas:<br /><br /> -   Agregar la página a la biblioteca de SharePoint.<br />-   Habilitar la página para que hospede características como elementos web dinámicos y zonas de elementos web.<br />-   Permitir que los usuarios personalicen la página mediante SharePoint Designer.<br /><br /> No cree una página de sitio si desea que la página contenga código personalizado.  Aunque puede agregar código personalizado a una página de sitio, el código deja de ejecutarse cuando el usuario personaliza la página a través de SharePoint Designer.|  
|Páginas maestras|Cree una página maestra si desea definir una estructura común para las páginas de sitio y las páginas de aplicación.|  
|Diseños de página|Los diseños de página son específicos de [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] y permiten definir con más detalle una estructura común para las páginas de sitio y las páginas de aplicación.|  
  
 Para obtener información general sobre cada tipo de página, vea, [Bloque de creación: Páginas y la interfaz de usuario](http://go.microsoft.com/fwlink/?LinkID=182095)y [Diseños de página y las páginas maestras](http://go.microsoft.com/fwlink/?LinkID=182096).  
  
## Crear páginas de aplicación  
 Para crear páginas de aplicación en Visual Studio, puede agregar un elemento **Página de aplicación** a un proyecto de SharePoint.  Puede agregar los controles a la página y, a continuación, administrar los eventos de control agregando el código.  
  
 Puede establecer puntos de interrupción en el archivo de código de la página, iniciar el depurador y probar la página en un sitio de SharePoint local sin realizar ningún paso de configuración adicional.  Para obtener más información, vea [Crear páginas de aplicación para SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).  
  
## Crear páginas de sitio, páginas maestras y diseños de página  
 Puede crear páginas de sitio, páginas maestras y diseños de página mediante SharePoint Designer.  A continuación, puede importar estas páginas en Visual Studio.  Importe las páginas si desea aprovechar las características de implementación o control de código fuente que están disponibles en Visual Studio.  Para obtener más información, vea [Importar elementos de un sitio de SharePoint existente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).  
  
 Dado que después de importar estas páginas, resulta complicado modificarlas, debe diseñarlas antes de importarlas.  
  
## Crear hojas de estilos en cascada, ECMAScript y temas  
 Visual Studio no proporciona plantillas para desarrollar hojas de estilos en cascada \(CSS\), ECMAScript \(JavaScript, JScript\) ni archivos de temas para los sitios de SharePoint.  Puede crear estos archivos utilizando las orientaciones disponibles en el SDK de SharePoint o utilizando herramientas como SharePoint Designer.  
  
 Puede agregar estos archivos a su solución directamente o puede importarlos.  En cualquier caso, debe crear las carpetas asignadas adecuadas para cada uno de los elementos que agregue.  Para obtener más información acerca de cómo se crea una carpeta asignada, vea [Cómo: Agregar y quitar carpetas asignadas](../sharepoint/how-to-add-and-remove-mapped-folders.md).  
  
 Para obtener más información sobre cómo crear hojas de estilos en cascada, vea [Clase Uso de hojas de estilos en cascada en la base de SharePoint](http://go.microsoft.com/fwlink/?LinkID=182098).  Para obtener más información sobre cómo crear archivos JavaScript y JScript para una solución de SharePoint, vea [Configurar una página básica ASPX para ECMAScript](http://go.microsoft.com/fwlink/?LinkID=182099).  Para obtener más información sobre los temas, [Bloque de creación: Páginas y la interfaz de usuario](http://go.microsoft.com/fwlink/?LinkID=182095)vea.  
  
## Temas relacionados  
  
|Título|Descripción|  
|------------|-----------------|  
|[Crear páginas de aplicación para SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)|Describe cómo agregar páginas de aplicaciones: contenido de .aspx que está combinado con una página maestra de SharePoint.|  
|[Cómo: Crear una página de aplicación](../sharepoint/how-to-create-an-application-page.md)|Muestra cómo se crean páginas ASP.NET que se ejecutan en un sitio de SharePoint.|  
|[Tutorial: Crear una página de una aplicación de SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)|Muestra cómo diseñar y depurar una página web ASP.NET para un sitio de SharePoint.|  
|[Trabajar con Visual Web Developer](http://msdn.microsoft.com/es-es/9c31f93b-c8fb-4599-9b14-6194ec8c7539)|Describe cómo utilizar el diseñador que aparece al abrir una página web en el proyecto.|  
  
  