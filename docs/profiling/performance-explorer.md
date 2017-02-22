---
title: "Uso de las herramientas de generaci&#243;n de perfiles | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance"
  - "vs.performance.wizard.website"
helpviewer_keywords: 
  - "herramientas de rendimiento [Visual Studio ALM]"
  - "Herramientas de generación de perfiles"
ms.assetid: df52b717-a55d-4b1d-8c2e-d5a6a38042f4
caps.latest.revision: 45
caps.handback.revision: 45
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Uso de las herramientas de generaci&#243;n de perfiles
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Las herramientas de generación de perfiles de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] permiten a los desarrolladores medir, evaluar y detectar los problemas relacionados con el rendimiento del código.  Estas herramientas se integran totalmente en el IDE a fin de proporcionar al usuario una experiencia accesible y sin fisuras.  
  
 La generación de perfiles de una aplicación es bastante sencilla.  Comienza por la creación de una nueva sesión de rendimiento.  En Visual Studio Team System Development Edition, puede usar el Asistente para crear una nueva sesión de rendimiento.  Una vez finalizada la sesión de rendimiento, los datos recopilados durante la generación de perfiles se guardan en un archivo .vsp.  Puede ver el archivo .vsp desde el IDE.  Existen varias vistas de informe que ayudan a ver y detectar los problemas de rendimiento a partir de los datos recopilados.  
  
 Las herramientas de generación de perfiles también puede utilizarse desde la línea de comandos.  Esto ofrece al usuario la flexibilidad de ejecutar estas herramientas desde la línea de comandos o utilizarlas para automatizar tareas que utilizan script.  
  
 Para obtener más información sobre temas actuales y avanzados relacionados con el rendimiento y la generación de perfiles, busque en los temas y blogs de Microsoft en Microsoft Developer Network.  Utilice las palabras clave Enterprise Performance Tools Team.  
  
## Tareas comunes  
  
|Tarea|Contenido relacionado|  
|-----------|---------------------------|  
|**Nuevas técnicas para Windows 8**|[Generar perfiles de aplicaciones de Windows 8 y Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)|  
|**Entender los conceptos de generación de perfiles:** proporciona información sobre los conceptos y los términos que utilizará para recopilar, ver y analizar el rendimiento del código mediante las herramientas de generación de perfiles.|[Temas de introducción](../profiling/overviews-performance-tools.md)|  
|**Comenzar el aprendizaje:** proporciona información sobre los procedimientos básicos que utilizará al recopilar, ver y analizar el rendimiento del código mediante las herramientas de generación de perfiles.  Pruébelo con un tutorial práctico.|[Introducción](../profiling/getting-started-with-performance-tools.md)|  
|**Configurar una sesión de generación de perfiles:** proporciona información sobre cómo especificar los proyectos o binarios de los que se van a generar perfiles, seleccionar un método de generación de perfiles, elegir los datos de rendimiento que se van a recopilar y establecer otras opciones de la sesión de generación de perfiles.|[Configurar sesiones de rendimiento](../profiling/configuring-performance-sessions.md)|  
|**Controlar los datos que recopila el generador de perfiles:** proporciona información sobre cómo utilizar las propiedades de una sesión de rendimiento y los procedimientos interactivos para iniciar y detener la generación de perfiles, además de cómo limitar los datos de rendimiento que va a recopilar a la información estrictamente deseada.|[Controlar la recolección de datos](../profiling/controlling-data-collection.md)|  
|**Buscar problemas de rendimiento:** proporciona información sobre cómo ver y analizar los datos de rendimiento recopilados en la ventana de la vista de informe de las herramientas de generación de perfiles.|[Analizar los datos de las Herramientas de generación de perfiles](../profiling/analyzing-performance-tools-data.md)|  
|**Analizar cambios de rendimiento:** proporciona información sobre cómo comparar dos archivos de datos del generador de perfiles para analizar los cambios de rendimiento.|[Comparar archivos de datos de las herramientas de generación de perfiles](../profiling/comparing-performance-data-files.md)|  
|**Guardar y compartir los resultados:** obtenga información sobre cómo guardar datos de generación de perfiles para archivarlos o compartirlos.|[Guardar y exportar datos de herramientas de rendimiento](../profiling/saving-and-exporting-performance-tools-data.md)|  
|**Generación automática de perfiles:** proporciona información sobre cómo utilizar las herramientas de generación de perfiles desde el símbolo del sistema.|[Generación de perfiles desde la línea de comandos](../profiling/using-the-profiling-tools-from-the-command-line.md)|  
|**Controlar la generación de perfiles mediante programación:** proporciona información sobre cómo utilizar las API administradas y nativas de las herramientas de generación de perfiles para controlar la recolección de datos del código fuente directamente.|[APIs de herramientas de generación de perfiles](../profiling/profiling-tools-apis.md)|  
|**Solucionar problemas de generación de perfiles**|[Solucionar problemas de las herramientas de generación de perfiles](../profiling/troubleshooting-performance-tools-issues.md)|  
  
## Vea también  
 [Herramientas de generación de perfiles](../profiling/profiling-tools.md)