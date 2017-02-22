---
title: "Introducci&#243;n a los valores de datos de muestreo en las herramientas de generaci&#243;n de perfiles | Microsoft Docs"
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
  - "método de generación de perfiles mediante muestreo"
  - "herramientas de generación de perfiles, muestreo"
ms.assetid: fad540a8-24b6-4ff9-91ce-e67e9a58399d
caps.latest.revision: 22
caps.handback.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Introducci&#243;n a los valores de datos de muestreo en las herramientas de generaci&#243;n de perfiles
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El método de generación de perfiles de *muestreo* de las herramientas de generación de perfiles de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] interrumpe el procesador del equipo a intervalos establecidos y recopila la pila de llamadas a funciones.  Una *pila de llamadas* es una estructura dinámica que almacena información sobre las funciones que se ejecutan en el procesador.  
  
 **Requisitos**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
 El análisis del generador de perfiles determina si el procesador está ejecutando código en el proceso de destino.  Si el procesador no está ejecutando código en dicho proceso, se descarta la muestra.  
  
 Si el procesador está ejecutando el código de destino, el generador de perfiles incrementa los recuentos de muestras para cada función de la pila de llamadas.  En el momento que se toma el ejemplo, solo una función de la pila de llamadas está ejecutando código.  Las demás funciones de la pila son elementos primarios en la jerarquía de las llamadas de función que están esperando la vuelta de las funciones secundarias.  
  
 En el evento de ejemplo, el generador de perfiles incrementa el recuento de muestras *exclusivas* de la función que está ejecutando sus instrucciones.  Dado que una muestra exclusiva forma también parte del número de muestras totales \(*inclusivas*\) de la función, también se incrementa el recuento de muestras inclusivas de la función actualmente activa.  
  
 El generador de perfiles incrementa el recuento de muestras inclusivas del resto de las funciones de la pila de llamadas.  
  
## Muestras inclusivas  
 Número total de muestras recopiladas durante la ejecución de la función de destino.  
  
 Incluye las muestras recopiladas durante la ejecución directa del código de función y las muestras recopiladas durante la ejecución de funciones secundarias a las que llama la función de destino.  
  
## Muestras exclusivas  
 Número de muestras recopiladas durante la ejecución directa de las instrucciones de la función de destino.  
  
 Entre las muestras exclusivas no se incluyen las muestras recopiladas durante la ejecución de funciones a las que llama la función de destino.  
  
## Porcentaje de inclusión  
 Porcentaje del número total de muestras inclusivas de la función o rango de datos en la generación de perfiles.  
  
## Porcentaje de exclusión  
 Porcentaje del número total de muestras exclusivas de la función o rango de datos en la generación de perfiles.  
  
## Vea también  
 [Cómo: Elegir métodos de recolección](../profiling/how-to-choose-collection-methods.md)   
 [Analizar los datos de las Herramientas de generación de perfiles](../profiling/analyzing-performance-tools-data.md)