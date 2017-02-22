---
title: "C&#243;mo: Recopilar datos de contadores de Windows | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.property.syscounter"
  - "vs.performance.property.wincounter"
helpviewer_keywords: 
  - "contadores de Windows"
  - "herramientas de rendimiento, uso de contadores de Windows"
  - "herramientas de generación de perfiles, uso de contadores de Windows"
ms.assetid: db4fbac2-bea5-4558-aa8b-160fcccf4b33
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# C&#243;mo: Recopilar datos de contadores de Windows
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Los contadores de Windows son contadores de rendimiento del sistema que se pueden recopilar a intervalos regulares durante la generación de perfiles.  En la vista Marcas de los informes de herramientas de generación de perfiles, hay una fila con la etiqueta **Automarcar** para cada intervalo de recolección.  La fila contiene columnas que describen los valores del contador de rendimiento en ese intervalo.  Para restringir el análisis a un período de tiempo entre dos marcas concretas, seleccione las marcas, haga clic con el botón secundario en y, a continuación selecciona **Filtrar por** \-\> **Marcas** en el menú contextual.  
  
 **Requisitos**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
> [!NOTE]
>  Las características de seguridad mejoradas en Windows 8 y Windows Server 2012 requirieron cambios significativos en la forma en que el generador de perfiles de Visual Studio recopila datos en estas plataformas.  Las aplicaciones de la Tienda Windows también requieren nuevas técnicas de recolección.  Vea [Generar perfiles de aplicaciones de Windows 8 y Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
### Para recopilar datos de contadores de Windows  
  
1.  En el Explorador de rendimiento, haga clic con el botón secundario en la sesión para la que desea configurar los contadores de Windows y seleccione **Propiedades**.  
  
2.  En **Páginas de propiedades**, haga clic en **Contadores de Windows**.  
  
3.  Active la casilla **Recopilar contadores de Windows**.  
  
4.  En el cuadro de texto **Intervalo de recolección \(ms\)**, escriba un intervalo de tiempo.  
  
5.  Seleccione una categoría en la lista desplegable **Categoría de contador**.  
  
6.  Seleccione una instancia en la lista desplegable **Instancia**.  
  
7.  Seleccione los contadores que desea usar al generar el perfil de su aplicación.  
  
8.  Haga clic en **Aplicar.**  
  
## Vea también  
 [Configurar sesiones de rendimiento](../profiling/configuring-performance-sessions.md)   
 [Propiedades de las sesiones de rendimiento](../profiling/performance-session-properties.md)   
 [Contadores de Windows y de CPU](../profiling/cpu-and-windows-counters.md)