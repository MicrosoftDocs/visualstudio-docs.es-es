---
title: "DA0003: Muchas muestras de kernel | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.rules.DA0003"
  - "vs.performance.DA0003"
  - "vs.performance.3"
  - "vs.performance.rules.DAManyKernelSamples"
ms.assetid: c1f46f77-eb95-42e5-b340-d86bc9de41b4
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# DA0003: Muchas muestras de kernel
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|Identificador de regla|DA0003|  
|Categoría|Uso de Herramientas de generación de perfiles|  
|Métodos de generación de perfiles|Muestreo|  
|Mensaje|Tiene una alta proporción de ejemplos en modo kernel.  Esto puede ser indicativo de un alto volumen de actividad de E\/S o un gran número de cambios de contexto.  Considere generar de nuevo el perfil de la aplicación con el modo de instrumentación.|  
|Tipo de regla|Información|  
  
## Motivo  
 Una proporción considerable de los ejemplos de la pila de llamadas que se recopilaron para la aplicación se estaba ejecutando en modo kernel.  Puede generar perfiles en la aplicación mediante otro método de generación de perfiles.  
  
## Descripción de la regla  
 En Windows, el código se puede ejecutar en modo kernel o modo usuario. \(El modo kernel también se denomina modo privilegiado.\) Solo el código del sistema de bajo nivel, como controladores de dispositivos, se ejecuta en modo kernel.  Una aplicación de modo usuario puede pasar al modo kernel para realizar las operaciones de entrada y salida, esperar las primitivas de sincronización del subproceso o proceso o realizar llamadas al sistema.  
  
 EL muestreo es más efectivo cuando genera perfiles de aplicaciones que pasan la mayor parte del tiempo trabajando en modo usuario.  El número de muestras recopiladas cuando la aplicación se ejecuta en modo kernel puede indicar frecuentes operaciones de E\/S o puede indicar que se están produciendo cambios de contexto.  Ninguno de estas operaciones se puede investigar mediante el método de muestreo.  Si se toman demasiados ejemplos del modo kernel, los datos del muestreo no pueden contener suficientes muestras de modo usuario para ser estadísticamente significativas.  
  
## Cómo corregir infracciones  
 Considere realizar de nuevo la generación de perfiles de la aplicación utilizando una de las opciones siguientes:  
  
-   Generar perfiles utilizando el método de instrumentación.  
  
-   Aumentar la frecuencia de muestreo para intentar recolectar más muestras en modo usuario.