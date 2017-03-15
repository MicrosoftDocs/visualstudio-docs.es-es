---
title: "Introducci&#243;n a los valores de datos de instrumentaci&#243;n en las herramientas de generaci&#243;n de perfiles | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Herramientas de generación de perfiles, instrumentación"
  - "método de generación de perfiles de instrumentación"
ms.assetid: 2cf94cf9-c317-4a52-bf00-670f1262165e
caps.latest.revision: 29
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 29
---
# Introducci&#243;n a los valores de datos de instrumentaci&#243;n en las herramientas de generaci&#243;n de perfiles
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El método de generación de perfiles *instrumentación* de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] registra la información de tiempo detallada para las llamadas de función, líneas e instrucciones de la aplicación de la que se ha generado el perfil.  
  
 **Requisitos**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
 El método de instrumentación inserta código al inicio y al final de las funciones de destino en el binario del que se ha generado el perfil, así como antes y después de cada llamada hecha por estas funciones a otra función.  El código insertado graba lo siguiente:  
  
-   El intervalo entre este evento de colección y el anterior.  
  
-   Si el sistema operativo ha realizado una operación durante el intervalo.  Por ejemplo, el sistema operativo puede leer o escribir en el disco, o cambiar entre el subproceso de destino y otro subproceso de otro proceso.  
  
 **Requisitos**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
 Para cada intervalo, el análisis del generador de perfiles reconstruye la pila de llamadas que estaba presente al final del intervalo.  Una pila de llamadas es la lista de funciones que están activas en un procesador en un momento dado.  Solo una de las funciones \(la función actual\) ejecuta código; el resto constituyen la cadena de llamadas a funciones que dio lugar a la llamada a la función actual \(la pila de llamadas\).  
  
 Para cada función de la pila de llamadas cuando se registró el intervalo, el análisis del generador de perfiles agrega el intervalo a uno o más de entre cuatro valores de datos para la función.  El análisis agrega el intervalo a un valor de datos para una función de acuerdo con dos criterios:  
  
-   Si el intervalo se produjo en el código de la función o en una *función secundaria* \(una función a la que llamó la función\).  
  
-   Si se produjo un evento del sistema operativo en el intervalo.  
  
 Los valores de datos para el intervalo de tiempo de una función o rango de datos se denominan *inclusivo transcurrido*, *exclusivo transcurrido*, *inclusivo de aplicación* y *exclusivo de aplicación*.  
  
-   Todos los intervalos de una función se agregan al valor de datos denominado inclusivo transcurrido.  
  
-   Si el intervalo se produjo en el código de la función y no en una función secundaria, se agrega al valor de datos de tiempo exclusivo transcurrido de la función.  
  
-   Si no se produjo un evento del sistema operativo durante el intervalo, este último se agrega al valor de datos de tiempo inclusivo de aplicación.  
  
-   Si no se produjo un evento del sistema operativo durante el intervalo y este último tuvo lugar en la ejecución directa del código de la función, es decir, no se produjo en una función secundaria, el intervalo se agrega al valor de datos denominado exclusivo de aplicación.  
  
 Los informes las herramientas de generación de perfiles agregan los valores totales de las funciones en la propia sesión de generación de perfiles, además de en los procesos, subprocesos y binarios de la sesión.  
  
## Valores de tiempo inclusivo transcurrido  
 Tiempo total dedicado a ejecutar una función y sus funciones secundarias.  
  
 Los valores de tiempo inclusivo transcurrido incluyen los intervalos dedicados a ejecutar directamente el código de la función, así como los dedicados a ejecutar las funciones secundarias de la función de destino.  Los intervalos de la función o de sus funciones secundarias que incluyen tiempos de espera del sistema operativo también son valores de tiempo inclusivo transcurrido.  
  
## Valores de tiempo exclusivo transcurrido  
 Tiempo dedicado a ejecutar una función, excluido el tiempo dedicado a las funciones secundarias.  
  
 Los valores de tiempo exclusivo transcurrido incluyen los intervalos dedicados a ejecutar directamente el código de la función, independientemente de si se produjo un evento del sistema operativo durante el intervalo.  Todos los intervalos dedicados a funciones secundarias a las que llamó la función de destino no se incluyen en los valores de tiempo exclusivo transcurrido.  
  
## Valores de tiempo inclusivo de aplicación  
 Tiempo dedicado a ejecutar una función y sus funciones secundarias, excluido el tiempo dedicado a eventos del sistema operativo.  
  
 Los valores de tiempo inclusivo de aplicación no incluyen los intervalos que contienen eventos del sistema operativo.  Dichos valores incluyen todos los intervalos restantes dedicados a ejecutar una función, independientemente de si el intervalo se dedicó a ejecutar directamente el código de la función o a funciones secundarias de la función de destino.  
  
## Valores de tiempo exclusivo de aplicación  
 Tiempo dedicado a ejecutar una función, excluido el tiempo dedicado a funciones secundarias y a eventos del sistema operativo.  
  
 Los valores de tiempo exclusivo de aplicación no incluyen los intervalos que contienen eventos del sistema operativo ni los dedicados a ejecutar funciones llamadas por la función.  Dichos valores incluyen solo los intervalos dedicados a ejecutar directamente el código de la función y que no contienen un evento del sistema operativo.  
  
## Porcentaje de tiempo inclusivo transcurrido  
 Porcentaje del total de los valores de tiempo inclusivo transcurrido de la sesión de generación de perfiles que fueron valores de este tipo de la función, el módulo, el subproceso o el proceso.  
  
 100 \* tiempo inclusivo transcurrido de función\/tiempo inclusivo transcurrido de sesión  
  
## Porcentaje de tiempo exclusivo transcurrido  
 Porcentaje del total de los valores de tiempo inclusivo transcurrido de la sesión de generación de perfiles que fueron valores de tiempo exclusivo transcurrido de la función, el módulo, el subproceso o el proceso.  
  
 100 \* tiempo exclusivo transcurrido de función\/tiempo inclusivo transcurrido de sesión  
  
## Porcentaje de tiempo inclusivo de aplicación  
 Porcentaje del total de los valores de tiempo inclusivo de aplicación de la sesión de generación de perfiles que fueron valores de este tipo de la función, el módulo, el subproceso o el proceso.  
  
 100 \* tiempo inclusivo de aplicación de función\/tiempo inclusivo de aplicación de sesión  
  
## Porcentaje de tiempo exclusivo de aplicación  
 Porcentaje del total de los valores de tiempo inclusivo de aplicación de la sesión de generación de perfiles que fueran intervalos de tipo exclusivo de aplicación de la función, el módulo, el subproceso o el proceso.  
  
 100 \* tiempo exclusivo de aplicación de función\/tiempo inclusivo de aplicación de sesión  
  
## Vea también  
 [Analizar los datos de las Herramientas de generación de perfiles](../profiling/analyzing-performance-tools-data.md)   
 [Cómo: Elegir métodos de recolección](../profiling/how-to-choose-collection-methods.md)