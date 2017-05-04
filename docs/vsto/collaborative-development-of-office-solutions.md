---
title: "Desarrollo en colaboraci&#243;n de las soluciones de Office | Microsoft Docs"
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
  - "desarrollo en colaboración [desarrollo de Office en Visual Studio]"
  - "aplicaciones de Office [desarrollo de Office en Visual Studio], desarrollo en colaboración"
  - "desarrollo de Office en Visual Studio, colaboración"
  - "control de código fuente [desarrollo de Office en Visual Studio]"
ms.assetid: c493354b-17d3-4e50-85f0-968b104bc978
caps.latest.revision: 29
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 28
---
# Desarrollo en colaboraci&#243;n de las soluciones de Office
  En un proyecto de Office pueden trabajar varios desarrolladores del mismo modo que colaboran en otros proyectos de Visual Studio.  Visual Studio localiza correctamente la instalación de Microsoft Office en cada uno de los equipos, incluso en caso de que Office esté instalado en distintas ubicaciones.  Sin embargo, hay algunas consideraciones importantes que deben tenerse en cuenta.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## Las propiedades de depuración no se comparten  
 Las propiedades de depuración no se comparten entre los distintos usuarios mediante el control de código fuente.  Los proyectos de Visual Basic y Visual C\# almacenan las propiedades de depuración en un archivo específico para cada usuario \(*nombreDeProyecto*.vbproj.user o *nombreDeProyecto*.csproj.user\) y este archivo no está sometido al control de código fuente.  Si hay varias personas depurando, cada una de ellas debe introducir las propiedades de depuración manualmente.  
  
 Si el proyecto está alojado en un recurso compartido de red en lugar de estarlo en el sistema de control de código fuente, deben realizarse algunos pasos adicionales para permitir que los desarrolladores que trabajan en equipo puedan abrir la solución y probar el ensamblado.  
  
## Los controles de código fuente requieren la desprotección de todos los archivos  
 Si utiliza un control de código fuente para los proyectos, deberá desproteger todos los archivos bajo un archivo de código en el **Explorador de soluciones** \(como los archivos ThisDocument, ThisWorkbook o ThisAddIn\) cada vez que cambie el archivo de código, incluso los archivos que están ocultos de manera predeterminada.  Si desprotege sólo el archivo de código de nivel superior, pueden que se pierdan los cambios.  
  
 Después de realizar los cambios, proteja de nuevo todos los archivos.  Para obtener más información sobre los archivos de código ocultos en los proyectos, vea [Proyectos de Office en el entorno de Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
## Seguridad para la colaboración informal en una red  
 En todas las soluciones de nivel de documento incluidas en una ubicación de red \(como \\\\*nombreDeServidor*\\*nombreDeRecursoCompartido*\), se debe agregar la ubicación completa a la lista de carpetas de confianza en la aplicación de Microsoft Office con la que está trabajando.  Seleccione la opción para incluir los subdirectorios bajo la carpeta principal o bien agregue específicamente las carpetas de depuración y compilación a la lista de carpetas de confianza.  Para obtener más información sobre cómo hacerlo, vea [Otorgar confianza a los documentos](../vsto/granting-trust-to-documents.md).  
  
 Las contraseñas no protegen los certificados temporales que se generan automáticamente en tiempo de compilación.  Los certificados contienen el nombre de inicio de sesión del programador y otros datos personales.  Si implementa personalizaciones firmadas por certificados temporales, otros podrían poder tener acceso a esta información.  
  
## Vea también  
 [Asegurar las soluciones de Office](../vsto/securing-office-solutions.md)   
 [Diseñar y crear soluciones de Office](../vsto/designing-and-creating-office-solutions.md)   
 [Compilar soluciones de Office](../vsto/building-office-solutions.md)  
  
  