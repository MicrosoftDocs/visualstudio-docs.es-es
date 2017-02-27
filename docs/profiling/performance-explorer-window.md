---
title: "Ventana Explorador de rendimiento | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performanceexplorer"
  - "vs.performance.explorer"
helpviewer_keywords: 
  - "herramientas de rendimiento, Explorador de rendimiento"
ms.assetid: cb6a6efc-93a5-49a2-8d03-6969b5f3b6d7
caps.latest.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 20
---
# Ventana Explorador de rendimiento
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La ventana de **Explorador de rendimiento** en el entorno de desarrollo integrado \(IDE\) de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]permite configurar e iniciar sesiones de rendimiento con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] de generación de perfiles las herramientas.  
  
 **Requisitos**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
## Barra de herramientas del Explorador de rendimiento  
 Las siguientes opciones están disponibles en la barra de herramientas del **Explorador de rendimiento**:  
  
-   **Iniciar Asistente de rendimiento**: muestra el Asistente de rendimiento para agregar una nueva sesión de rendimiento a la ventana Explorador de rendimiento.  
  
-   **Nueva sesión de rendimiento**: agrega una sesión de rendimiento vacía a la ventana Explorador de rendimiento.  
  
-   **Iniciar**: la lista del botón de comando **Iniciar** permite iniciar la aplicación de destino que tiene habilitada la generación de perfiles inmediata \(**Iniciar con generación de perfiles**\) o con la generación de perfiles suspendida \(**Inicio con generación de perfiles en pausa**\).  
  
-   **Método**: especifica si la generación de perfiles de la sesión utiliza el método de muestreo o de instrumentación.  
  
-   **Detener**: sale inmediatamente de la aplicación de destino y del generador de perfiles.  
  
-   **Asociar\/Desasociar**: muestra el cuadro de diálogo **Asociar generador de perfiles al proceso** para seleccionar un proceso en ejecución al que adjuntar el generador de perfiles.  
  
## Ventana Explorador de rendimiento  
 La ventana **Explorador de rendimiento** contiene un control de árbol que muestra los binarios y los archivos de datos de informe de una o varias sesiones de rendimiento.  
  
-   **Nombre de sesión**: la raíz del control de árbol contiene el nombre de la sesión.  Haga clic con el botón secundario del mouse en el nombre de la sesión para establecer las propiedades de esta o para iniciar la aplicación de destino y el generador de perfiles.  
  
-   **Destinos**: muestra los nombres de los binarios de los que se van a generar perfiles en la sesión.  Haga clic con el botón secundario en **Destinos** para agregar o quitar un binario, proyecto de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] o sitio web.  Haga clic con el botón secundario en un nombre de destino para establecer las propiedades del binario individual.  
  
-   **Informes**: muestra los nombres de los archivos de datos del generador de perfiles que se generan para la sesión.  Haga clic con el botón secundario en **Informes** para agregar un informe existente o comparar dos archivos de datos del generador de perfiles.  Haga clic con el botón secundario en el nombre de un informe para abrir, quitar o exportar un archivo de datos del generador de perfiles.  
  
## Vea también  
 [Temas de introducción](../profiling/overviews-performance-tools.md)   
 [Configurar sesiones de rendimiento](../profiling/configuring-performance-sessions.md)   
 [Controlar la recolección de datos](../profiling/controlling-data-collection.md)