---
title: "Recopilar datos de simultaneidad de subprocesos y procesos | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "método de generación de perfiles de simultaneidad"
  - "Herramientas de generación de perfiles, método de simultaneidad"
ms.assetid: fa03d381-a9ee-408c-876d-05111e29225b
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Recopilar datos de simultaneidad de subprocesos y procesos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El método de generación de perfiles de simultaneidad de las Herramientas de generación de perfiles de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] permite recopilar datos de contención de recursos que incluyen información sobre cada evento de sincronización que hace que una función de la aplicación de la que se genera el perfil espere para obtener acceso a un recurso.  
  
 **Requisitos**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
 Puede especificar el método de generación de perfiles de simultaneidad utilizando uno de los procedimientos siguientes:  
  
-   En la primera página del Asistente para generación de perfiles, haga clic en **Simultaneidad**.  
  
-   En la página **General** del cuadro de diálogo de propiedades de la sesión de rendimiento, haga clic en **Simultaneidad**.  
  
-   En la barra de herramientas **Explorador de rendimiento**, en la lista **Método**, haga clic en **Simultaneidad**.  
  
## Tareas comunes  
 Puede especificar opciones adicionales en el cuadro de diálogo de *Performance Session***Páginas de propiedades** de la sesión de rendimiento.  Para abrir este cuadro de diálogo:  
  
-   En el **Explorador de rendimiento**, haga clic con el botón secundario en el nombre de la sesión de rendimiento y, a continuación, haga clic en **Propiedades**.  
  
 Las tareas de la tabla siguiente describen opciones que puede especificar en el cuadro de diálogo de *Performance Session***Páginas de propiedades** cuando genere perfiles utilizando el método de simultaneidad.  
  
|Tarea|Contenido relacionado|  
|-----------|---------------------------|  
|En la página **General**, especifique los detalles de nomenclatura del archivo de datos de generación de perfiles \(.vsp\) que se crea.|-   [Cómo: Establecer opciones de nombre de archivo de datos de generación de perfiles](../profiling/how-to-set-performance-data-file-name-options.md)|  
|En la página **Iniciar**, especifique la aplicación que se debe iniciar si existen varios proyectos .exe en la solución de código.|-   [Cómo: Especificar el binario de inicio](../profiling/how-to-specify-the-binary-to-start.md)|  
|En la página **Interacciones de capas**, agregue los datos de llamada de ADO.NET a la ejecución de generación de perfiles.|-   [Recopilar datos de interacción de capas](../profiling/collecting-tier-interaction-data.md)|  
|En la página **Contadores de Windows**, especifique uno o más contadores de rendimiento del sistema operativo que se deben agregar como marcas a los datos de generación de perfiles.|-   [Cómo: Recopilar datos de contadores de Windows](../profiling/how-to-collect-windows-counter-data.md)|  
|En la página **Avanzadas**, especifique la versión del runtime de .NET Framework que se usará en la generación de perfiles si los módulos de aplicación usan varias versiones.  De forma predeterminada, se generan los perfiles de la primera versión cargada.|-   [Cómo: Especificar el runtime de .NET Framework para la generación de perfiles en escenarios en paralelo](../Topic/How%20to:%20Specify%20the%20.NET%20Framework%20Runtime.md)|