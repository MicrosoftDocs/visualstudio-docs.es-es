---
title: "Generar perfiles y seguridad en Windows Vista | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Herramientas de generación de perfiles, seguridad"
  - "Herramientas de rendimiento, seguridad"
ms.assetid: 842112fc-b886-4801-8cd7-a25b314b0393
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Generar perfiles y seguridad en Windows Vista
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dependiendo de la configuración de los permisos de acceso de usuario para [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)] que haya establecido un administrador de equipo, cada usuario podría tener permisos de seguridad para generar los perfiles de un proceso en dicho equipo.  En los ejemplos siguientes se muestran las posibles diferencias entre los usuarios:  
  
-   Algunos usuarios pueden tener acceso a las características avanzadas de generación de perfiles cuando el administrador ha configurado el controlador y el servicio que deben iniciarse.  
  
-   Los usuarios del dominio pueden tener acceso sólo a la generación de perfiles de muestreo.  
  
-   Algunos usuarios pueden denegar a todos los demás usuarios el acceso a la generación de perfiles.  
  
 Para obtener más información, vea las opciones de ADMIN en [VSPerfCmd](../profiling/vsperfcmd.md).  
  
## Generación de perfiles entre sesiones  
 La *generación de perfiles entre sesiones* es la capacidad de generar perfiles de un proceso que se ejecuta en otra sesión de inicio.  Por ejemplo, la mayoría de los servicios se ejecutan en la sesión 0 y los usuarios no pueden ejecutar directamente en la sesión 0.  Mediante el botón **Asociar al proceso** de la barra de herramientas del Explorador de rendimiento, o con la opción \/attach de la herramienta de la línea de comandos VSPerfCmd, puede generar perfiles de la mayoría de los procesos en otras sesiones de inicio.  
  
 Para ver una lista de los procesos disponibles, establezca las opciones de visibilidad de la generación de perfiles entre procesos.  Estas opciones están disponibles en la ventana **Asociar al proceso** que aparece al hacer clic en **Asociar al proceso**:  
  
-   **Mostrar los procesos de todos los usuarios**  
  
     Cuando esta opción no está seleccionada, la lista muestra solamente los procesos que pertenecen al usuario actual.  Si se ha seleccionado **Mostrar los procesos de todos los usuarios**, la lista muestra los procesos de todos los usuarios.  
  
-   **Mostrar los procesos de todas las sesiones**  
  
     Cuando esta opción no está seleccionada, la lista muestra los procesos de la sesión actual.  Cuando está seleccionada, la lista muestra los procesos de todas las sesiones.  
  
## Vea también  
 [Temas de introducción](../profiling/overviews-performance-tools.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [How to: Attach to a Running Process](http://msdn.microsoft.com/es-es/636d0a52-4bfd-48d2-89ad-d7b9ca4dc4f4)