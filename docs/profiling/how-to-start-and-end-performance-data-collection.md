---
title: "C&#243;mo: Iniciar y finalizar generaciones de perfiles | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.wizard.summarypage"
helpviewer_keywords: 
  - "herramientas de generación de perfiles, inicio de sesiones"
  - "herramientas de rendimiento, inicio"
  - "herramientas de rendimiento, finalización"
  - "herramientas de generación de perfiles, finalización de sesiones"
ms.assetid: 9f6eb0d5-d9e9-4bec-b627-445065610bce
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# C&#243;mo: Iniciar y finalizar generaciones de perfiles
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Antes de iniciar la generación de perfiles, debe agregar el binario de destino cuyos perfiles desee generar a la sesión de rendimiento.  Para agregar un destino, haga clic con el botón secundario del mouse en **Destinos** en el **Explorador de rendimiento** y, a continuación, haga clic en **Agregar binario de destino**.  En el cuadro de diálogo **Agregar binario de destino**, seleccione el nombre de archivo y, a continuación, haga clic en **Abrir**.  Se agrega un nuevo binario.  
  
### Para iniciar la generación de perfiles  
  
1.  Haga clic con el botón secundario del mouse en el nombre de la sesión de rendimiento en la ventana **Explorador de rendimiento** y elija una de las opciones siguientes:  
  
    -   **Iniciar con generación de perfiles**: inicia la aplicación y comienza inmediatamente la generación de perfiles.  
  
    -   **Inicio con generación de perfiles en pausa**: inicia la aplicación pero no comienza la generación de perfiles.  Puede iniciar la generación de perfiles si selecciona **Reanudar recolección** en la ventana **Control de recolección de datos**.  Para obtener más información, vea [Cómo: Pausar y reanudar la generación de perfiles](../Topic/How%20to:%20Pause%20and%20Resume%20Performance%20Data%20Collection.md).  
  
### Para finalizar la generación de perfiles  
  
-   El mejor método de finalizar una sesión de generación de perfiles es salir de la aplicación.  Para detener inmediatamente la generación de perfiles, en la barra de herramientas del **Explorador de rendimiento** haga clic en **Detener**.  
  
## Vea también  
 [Controlar la recolección de datos](../profiling/controlling-data-collection.md)   
 [Cómo: Pausar y reanudar la generación de perfiles](../Topic/How%20to:%20Pause%20and%20Resume%20Performance%20Data%20Collection.md)