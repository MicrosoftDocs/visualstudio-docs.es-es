---
title: "Asistente para publicaci&#243;n (Desarrollo de Office en Visual Studio)"
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
  - "VST.ProjectProperties.PublishWizard"
  - "VST.PublishWizard.Publish.2007System"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "implementación ClickOnce [desarrollo de Office en Visual Studio], Asistente para publicación"
  - "implementar aplicaciones [desarrollo de Office en Visual Studio], Asistente para publicación"
  - "aplicaciones de Office [desarrollo de Office en Visual Studio], Asistente para publicación"
  - "Asistente para publicación, soluciones de Office"
ms.assetid: 793314b6-b6a6-4509-8f1c-dd9466cf5190
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# Asistente para publicaci&#243;n (Desarrollo de Office en Visual Studio)
  Utilice **Asistente para publicación** para copiar los archivos de la solución en una ubicación especificada, cree archivos de manifiesto, y crear un programa de instalación.  
  
 Para obtener acceso a este asistente, en el menú de **Compilación** , elija **Publicar** *SolutionName*.  También puede obtener acceso al **Asistente para publicación** desde el **Explorador de soluciones**.  Abrir el menú contextual para el nodo del proyecto y, a continuación **Publicar**.  
  
 En cada una de las siguientes secciones se describe una página del asistente.  
  
## ¿Dónde desea publicar la aplicación?  
 **Especificar la ubicación para la publicación de esta aplicación**  
 Obligatorio.  La ubicación de la publicación es el directorio donde el **Asistente para publicación** copia los archivos de la solución como los manifiestos, los ensamblados, el certificado temporal y otros archivos de la compilación.  Debe tener acceso de escritura a este directorio.  
  
 Escriba la ubicación como una ruta de acceso del disco, un recurso compartido de archivos, un sitio FTP, o dirección URL del sitio Web, o haga clic en el botón de **Examinar** para buscar la ubicación.  La ruta de acceso puede estar en estos formatos:  
  
-   Una ruta de acceso absoluta o relativa en formato Windows estándar, por ejemplo: C:\\Deploy\\MiAplicación o \\MiAplicación.  
  
-   Una ruta de acceso de la Convención de nomenclatura universal \(UNC\), como \\\\NombreServidor\\MiAplicación \\.  
  
-   Dirección URL de un sitio Web, como http:\/\/www.microsoft.com\/MyApplication.  
  
 De manera predeterminada, la ubicación de publicación es *http:\/\/localhost\/nombreDelProyecto\/* si tiene IIS instalado, o el directorio publish\\ si no tiene IIS instalado.  
  
> [!NOTE]  
>  Existen más consideraciones a tener en cuenta si el equipo de destino ejecuta Windows Vista.  Debe ser un administrador en el equipo de Windows Vista para utilizar la opción de publicación local.  Además, la ubicación predeterminada siempre es el directorio *publish\\*, independientemente de que tenga IIS instalado.  
  
## ¿Cuál es la ruta de instalación predeterminada en los equipos del usuario final?  
 La ruta de instalación es opcional.  Puede establecer la ruta de instalación más adelante si lo prefiere.  Para obtener información detallada, vea [Cómo: Cambiar la ruta de instalación de una solución de Office](http://msdn.microsoft.com/es-es/d0eaa07b-2d72-4902-899f-2f9fb165b8fd).  
  
 La ruta de instalación es el directorio desde el que el usuario final instalará la personalización.  Es también la ruta que utilizará la solución para buscar actualizaciones.  El **Asistente para publicación** no implementa la solución en esta ubicación, a menos que la ruta de acceso sea la misma que la que escribió en el cuadro **Especificar la ubicación para la publicación de esta aplicación** de la página anterior.  
  
 **Desde un sitio Web**  
 Especifica la dirección URL que los usuarios finales seguirán para instalar la solución.  
  
 **Desde una ruta de acceso UNC o un recurso compartido de archivos**  
 Especifica la ruta de acceso UNC que los usuarios finales seguirán para instalar la solución.  
  
 **Desde un CD\-ROM o un DVD\-ROM**  
 Esta opción no requiere una ruta de instalación.  
  
 Visual Studio no graba en CD ni en DVD.  Debe copiar manualmente el resultado en un CD o en un DVD.  
  
## Vea también  
 [Implementar una solución de Office mediante ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)   
 [Publicar &#40;página&#41;, Diseñador de proyectos &#40;Desarrollo de Office en Visual Studio&#41;](../vsto/publish-page-project-designer-office-development-in-visual-studio.md)   
 [Implementar una solución de Office](../vsto/deploying-an-office-solution.md)  
  
  