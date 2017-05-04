---
title: "Crear p&#225;ginas de aplicaci&#243;n para SharePoint | Microsoft Docs"
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
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "páginas de aplicación [desarrollo de SharePoint en Visual Studio], crear"
  - "páginas de aplicación [desarrollo de SharePoint en Visual Studio], desarrollar"
  - "desarrollo de SharePoint en Visual Studio, páginas de aplicación"
  - "desarrollo de SharePoint en Visual Studio, páginas de contenido"
  - "desarrollo de SharePoint en Visual Studio, páginas web"
ms.assetid: a6e97149-15dd-4bdb-8d75-3b53f886f76c
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 35
---
# Crear p&#225;ginas de aplicaci&#243;n para SharePoint
  Una *página de aplicación* es una página web ASP.NET que está diseñada para el uso en un sitio web de SharePoint.  Las páginas de aplicación son un tipo especializado de página ASP.NET.  La diferencia básica entre una página de aplicación y una página ASP.NET estándar es que una página de aplicación incluye contenido combinado con una página maestra de SharePoint.  Una página maestra permite a las páginas de aplicación compartir el aspecto y comportamiento de otras páginas de un sitio.  
  
 Visual Studio permite diseñar páginas de aplicación con un diseñador.  El diseñador muestra un área de contenido para cada marcador de posición de contenido que se define en una página maestra.  Puede diseñar la página de aplicación arrastrando los controles a estas áreas de contenido.  
  
## Páginas de aplicación  
 Las páginas de aplicación se comparten entre todos los sitios del servidor, mientras que una página de sitio es específica de un sitio.  Para obtener más información, [Tipos de páginas de SharePoint](http://go.microsoft.com/fwlink/?LinkID=211584)vea.  
  
 De forma predeterminada, la mayoría de las páginas que aparecen al crear un sitio de SharePoint son páginas de sitio.  Una página de sitio se puede agregar a una biblioteca de páginas de SharePoint.  Los usuarios pueden personalizar una página de sitio mediante herramientas como SharePoint Designer.  Una página de sitio también puede hospedar características como los elementos web dinámicos y las zonas de elementos web.  
  
 Las páginas de aplicación no pueden hacer estas cosas.  Sin embardo, una página de aplicación es el mejor tipo de página si desea que la página contenga código personalizado.  Aunque puede agregar código personalizado a una página de sitio, el código deja de ejecutarse cuando el usuario personaliza la página con herramientas como SharePoint Designer.  
  
> [!NOTE]  
>  Visual Studio no proporciona plantillas que ayuden a crear páginas de sitio para un sitio de SharePoint.  Para obtener más información, vea [Tipos de páginas de SharePoint](http://go.microsoft.com/fwlink/?LinkID=211584).  
  
## Crear una página de aplicación  
 Para crear una página de aplicación, agregue un elemento **Página de aplicación** a un proyecto de SharePoint.  Al crear una página de aplicación, Visual Studio agrega las siguientes carpetas a su proyecto:  
  
|Carpeta|Descripción|  
|-------------|-----------------|  
|Layouts|Asigna el directorio virtual \_layouts del sistema de archivos de SharePoint.|  
|Subcarpeta Layouts|Contiene los archivos que constituyen la página de aplicación.  De forma predeterminada, esta carpeta tiene el mismo nombre que el proyecto.  Se puede cambiar el nombre de esta carpeta en cualquier momento.  Al ejecutar el proyecto, Visual Studio implementa esta carpeta en el directorio virtual \_layouts del sistema de archivos de SharePoint.|  
  
 Visual Studio agrega los siguientes archivos al proyecto:  
  
|Archivo|Descripción|  
|-------------|-----------------|  
|Archivo de paginación ASP.NET \(.aspx\)|Contiene formato XML que define la página.|  
|Archivo de código de la página de aplicación|Contiene código subyacente de la página de aplicación.  Agregue código a este archivo para controlar los eventos.|  
|Archivo de código del diseñador de páginas de aplicación|Contiene código generado por el diseñador.  No modifique este archivo directamente.|  
  
## Diseñar y depurar una página de aplicación  
 Diseñe el contenido de una página de aplicación utilizando el diseñador de Visual Web Developer en Visual Studio.  Este diseñador aparece al abrir la página de aplicación del proyecto \(haciendo doble clic o abriendo el menú contextual y elige **Abierta**\).  Para obtener más información sobre cómo utilizar este diseñador, vea [Mapa de contenido del entorno de desarrollo web de Visual Studio](http://msdn.microsoft.com/es-es/9c31f93b-c8fb-4599-9b14-6194ec8c7539).  
  
> [!NOTE]  
>  Puede diseñar la página solo en la vista de **Código** el diseñador.  La **Vista de diseño** del diseñador está deshabilitada en las páginas de aplicación.  
  
 Puede depurar una página de aplicación igual que otros elementos de proyecto de SharePoint en Visual Studio.  Al iniciar el depurador de Visual Studio, Visual Studio abre el sitio de SharePoint.  
  
 Para ver la página de aplicación, debe navegar manualmente hasta la ubicación de la página \(por ejemplo: http:\/\/*Server\_Name*\/\_layouts\/*Project\_Name*\/ApplicationPage1.aspx\).  
  
 Para obtener más información sobre la depuración de proyectos de SharePoint, vea [Solucionar problemas de soluciones de SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md).  
  
## Elegir una página maestra  
 De forma predeterminada, un elemento **Página de aplicación** hace referencia a la página maestra del sitio que está utilizando para depurar el proyecto.  Esa página se denomina V4.master y puede encontrarla en la **Galería de páginas maestras** del sitio de SharePoint.  
  
 Puede cambiar explícitamente la página maestra que usa la página de aplicación; para ello, establezca el atributo `MasterPageFile` del elemento `Page` de la aplicación. Por ejemplo: `MasterPageFile="~/_layouts/applicationv4.master"`.  De hecho, debe establecer este atributo si las páginas maestra dinámicas no están habilitadas en el servidor de SharePoint.  Para obtener más información sobre las páginas maestras en SharePoint, vea [Páginas maestras](http://go.microsoft.com/fwlink/?LinkID=169281).  
  
## Vea también  
 [Desarrollo de windows presentation foundation SharePoint detallado](http://go.microsoft.com/fwlink/?LinkID=182103)   
 [Información general sobre ASP.NET Web Pages](http://msdn.microsoft.com/library/52fa0455-41ea-4315-8208-2861d1527da2)   
 [Información general sobre sintaxis de páginas web ASP.NET](http://msdn.microsoft.com/library/09074b20-ece9-46fa-bc8f-ab2595ed2c02)   
 [Programar ASP.NET Web Pages](http://msdn.microsoft.com/es-es/5626c661-8057-4de8-b658-c2e35ed4b4c9)  
  
  