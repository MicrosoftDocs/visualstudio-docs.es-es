---
title: "Navegador de utilizaci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.performance.utilizationnavigator"
ms.assetid: 522a981a-37ef-4cdd-a04c-f1e7525a2aab
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Navegador de utilizaci&#243;n
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Se puede utilizar el Navegador de utilización en el Visualizador de simultaneidad para seleccionar un intervalo de tiempo en un seguimiento.  El Visualizador de simultaneidad muestra la utilización de núcleos de CPU del proceso de destino a lo largo del tiempo.  Esto facilita examinar las pautas de utilización de la CPU y permite también comparar los datos de uso y los datos en otras vistas.  El Navegador de utilización aparece en la parte superior de cada vista del Visualizador de simultaneidad.  La siguiente ilustración muestra el Navegador de utilización.  
  
 ![Navegador de uso que muestra el marco de tiempo seleccionado](../profiling/media/cvutilizationnavigator.png "CVUtilizationNavigator")  
El Navegador de utilización y un período de tiempo seleccionado  
  
 En la ilustración, el intervalo seleccionado está definido por un rectángulo rojo, conocido como *miniatura*.  
  
 Aquí se muestra cómo se puede utilizar el Navegador de utilización para manipular el intervalo de tiempo mostrado:  
  
-   Se puede hacer un desplazamiento arrastrando el dedo hacia la izquierda o la derecha. \(Teclado: Mueva el foco a la miniatura y después presione la tecla izquierda o derecha\).  
  
-   Se puede cambiar la extensión del intervalo arrastrando uno de los identificadores. \(Teclado: Mueva el foco a un identificador y después presione la tecla derecha o izquierda\).  
  
 Si cambia el intervalo mediante el uso de un control distinto de zoom del Visualizador de simultaneidad, el Navegador de utilización se actualiza para reflejar el cambio.