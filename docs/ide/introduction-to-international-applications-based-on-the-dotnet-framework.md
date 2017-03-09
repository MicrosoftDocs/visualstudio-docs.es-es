---
title: "Introducci&#243;n a aplicaciones internacionales basadas en .NET Framework | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ASP.NET, globalización"
  - "plantilla de archivo de recursos de ensamblado"
  - "referencia cultural, establecer"
  - "recursos de reserva"
  - "globalización [Visual Studio], configuración de la referencia cultural"
  - "globalización [Visual Studio], aplicaciones internacionales"
  - "aplicaciones internacionales [Visual Studio], acerca de las aplicaciones internacionales"
  - "localización [Visual Studio], modelo de adaptación .NET"
  - "localización [Visual Studio], configuración de la referencia cultural"
  - "archivos de recursos, procesos de reserva"
  - "recursos [Visual Studio], sistema de reserva"
  - "recursos [Visual Studio], localización"
  - "cadenas [Visual Studio], adaptar"
  - "interfaz de usuario, configuración de la referencia cultural"
  - "aplicaciones web [.NET Framework], globalización"
  - "Windows Forms, globalización"
ms.assetid: b0788993-e62d-4f68-8235-5f87b1d48525
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Introducci&#243;n a aplicaciones internacionales basadas en .NET Framework
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], la creación de aplicaciones preparadas para su uso mundial tiene dos partes: la globalización, el proceso de diseñar aplicaciones que puedan adaptarse a distintas referencias culturales, y la localización, el proceso de traducir los recursos para una referencia cultural específica.  Para obtener información general sobre el diseño de aplicaciones para usuarios internacionales, vea [Prácticas recomendadas para desarrollar aplicaciones de uso internacional](../Topic/Best%20Practices%20for%20Developing%20World-Ready%20Applications.md).  
  
 El modelo de localización de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] consta de un ensamblado principal, que contiene tanto el código de la aplicación como la reserva de recursos: cadenas, imágenes y otros objetos del lenguaje en que se programó originalmente la aplicación.  Cada aplicación adaptada tendrá ensamblados satélite, que contienen sólo recursos adaptados.  Dado que el ensamblado principal contiene siempre los recursos de reserva, si un recurso no se encuentra en el ensamblado satélite adaptado, <xref:System.Resources.ResourceManager> intentará cargarlo de forma jerárquica y utilizará como último recurso el recurso de reserva del ensamblado principal.  El sistema de reserva de recursos se explica con más detalle en [Organización jerárquica de recursos para la localización](../ide/hierarchical-organization-of-resources-for-localization.md).  
  
 Un recurso de localización que se debería utilizar es el glosario de todos los productos localizados de Microsoft.  Este archivo CSV contiene más de 12.000 términos en inglés y las traducciones de estos términos en 59 idiomas diferentes.  El glosario está disponible para su descarga en la página web [Microsoft Terminology Translations](http://go.microsoft.com/fwlink/?LinkId=128146).  
  
 El sistema de proyectos para aplicaciones de formularios Windows Forms puede generar archivos de recursos, tanto para la referencia cultural de reserva como para cada una de las referencias culturales de las interfaces de usuario adicionales que se desee.  El archivo de recursos de reserva se compila en el ensamblado principal y los de recursos para referencias culturales específicas en ensamblados satélite, uno para cada referencia cultural de la interfaz de usuario.  Cuando se genera un proyecto, los archivos de recursos se compilan del formato XML \(.resc\) de Visual Studio a un formato binario intermedio \(.resources\), que a continuación se incrusta en ensamblados satélite.  
  
 Tanto el sistema de proyectos para Windows Forms como para formularios Web Forms permiten compilar archivos de recursos mediante una plantilla Archivo de recursos de ensamblado, tener acceso a los recursos y compilar el proyecto.  Los ensamblados satélite se crean junto con el ensamblado principal.  
  
 Cuando se ejecuta una aplicación adaptada, su aspecto viene determinado por dos valores de referencia cultural.  \(Una *referencia cultural* es un conjunto de información de prioridades del usuario que tiene que ver con su idioma, entorno y costumbres culturales\). La referencia cultural de la interfaz de usuario determina qué recursos se cargarán.  La referencia cultural de la interfaz de usuario está establecida como `UICulture` en los archivos Web.config y en las directivas de página, y <xref:System.Globalization.CultureInfo.CurrentUICulture%2A> en el código Visual Basic o Visual C\#.  La configuración de referencia cultural determina el formato de los valores como las fechas, los números, la moneda, etc.  La referencia cultural está establecida como `Culture` en los archivos Web.config y en las directivas de página, y <xref:System.Globalization.CultureInfo.CurrentCulture%2A> en el código Visual Basic o Visual C\#.  
  
## Vea también  
 <xref:System.Globalization>   
 <xref:System.Resources>   
 [Globalizar y localizar aplicaciones](../ide/globalizing-and-localizing-applications.md)   
 [Seguridad y ensamblados satélite localizados](../ide/security-and-localized-satellite-assemblies.md)