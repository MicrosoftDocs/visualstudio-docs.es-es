---
title: "DA0017: Tasas altas de memoria paginada activa en disco | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.17"
  - "vs.performance.rules.DA0017"
  - "vs.performance.DA0017"
ms.assetid: 01011eec-5930-43b3-980d-2cb01e2ca7f6
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0017: Tasas altas de memoria paginada activa en disco
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|Identificador de regla|DA0017|  
|Categoría|Memoria y paginación|  
|Método de generación de perfiles|Todos|  
|Mensaje|Alta frecuencia de paginación de memoria activa en el disco.  Puede que la aplicación esté enlazada a memoria.|  
|Tipo de regla|Información|  
  
 Cuando genere perfiles usando métodos de muestreo, memoria de .NET o contención de recursos, debe recopilar al menos 10 muestras para desencadenar esta regla.  
  
## Motivo  
 Los datos de rendimiento del sistema recopilados durante la generación de perfiles indican que se produjo una tasa alta de memoria paginada activa hacia y desde el disco.  Las tasas de paginación en este nivel normalmente afectarán al rendimiento de la aplicación y su capacidad de respuesta.  Puede reducir las asignaciones de memoria mediante la revisión de los algoritmos.  Quizás tenga que considerar también los requisitos de memoria de la aplicación  
  
## Descripción de la regla  
  
> [!NOTE]
>  Esta regla informativa se activa cuando los niveles de paginación de la memoria activa alcanzan una cantidad significativa.  Cuando se produce un nivel de paginación extremadamente elevado, se desencadena en su lugar la regla de advertencia [DA0014: Frecuencia extremadamente alta de paginación de memoria activa en el disco](../Topic/DA0014:%20Extremely%20high%20rates%20of%20paging%20active%20memory%20to%20disk.md).  
  
 La paginación excesiva del disco puede estar originada por una escasez de memoria física.  Si las operaciones de paginación son predominantes en el uso del disco físico donde se encuentra el archivo de paginación, pueden reducir el rendimiento de otras operaciones de disco orientadas a la aplicación del mismo disco.  
  
 Normalmente, las páginas se leen o se escriben en el disco en operaciones de paginación masivas.  El número de salida de páginas por segundo suele ser mucho mayor que el número de escrituras de páginas por segundo, por ejemplo.  Y es que en la salida de páginas por segundo se incluyen también las páginas de datos de la memoria caché de archivos del sistema.  Sin embargo, no siempre resulta fácil determinar qué proceso es el responsable directo de la paginación ni por qué.  
  
## Cómo corregir infracciones  
 Haga doble clic en el mensaje en la ventana Lista de errores para navegar a la vista [Marcas](../profiling/marks-view.md).  Busque la columna **Memoria\\Páginas por segundo**.  Determine si hay fases concretas de la ejecución del programa en la que la actividad de paginación de E\/S es más pesada que en otras.  
  
 Si está recopilando los datos de perfil de una aplicación ASP.NET en un escenario de prueba de carga, intente ejecutar de nuevo la prueba de carga en una máquina configurada con memoria física adicional \(o RAM\).  
  
 Puede reducir las asignaciones de memoria si corrige los algoritmos y evita las API que utilizan mucha memoria, como String.Concat y String.Substring.