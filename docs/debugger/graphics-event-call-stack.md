---
title: "Pila de llamadas de eventos de gr&#225;ficos | Microsoft Docs"
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
  - "vs.graphics.callstack"
ms.assetid: 8a30168d-8b39-4de1-b094-c7356ba101a3
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Pila de llamadas de eventos de gr&#225;ficos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La pila de llamadas de eventos gráficos del Analizador de gráficos de Visual Studio le ayuda a establecer la relación entre los eventos de gráficos problemáticos y el código fuente de la aplicación.  
  
 Esta es la ventana de la Pila de llamadas de eventos:  
  
 ![La pila de llamadas que precede a un evento DrawIndexed.](../debugger/media/gfx_diag_demo_graphics_event_call_stack_orientation.png "gfx\_diag\_demo\_graphics\_event\_call\_stack\_orientation")  
  
## Descripción de la pila de llamadas de eventos gráficos  
 Puede utilizar la Pila de llamadas de eventos para comprender el flujo de ejecución que llevó a un determinado evento de Direct3D.  Se asemeja a la ventana de la pila de llamadas de Visual Studio con la excepción de que, en lugar de mostrar la pila de llamadas actual del subproceso activo en una aplicación que se ejecuta, muestra la pila de llamadas tal y como se encontraba cuando se produjo el evento de Direct3D seleccionado.  Desde la Pila de llamadas de eventos, puede ir directamente al sitio de llamada del evento de Direct3D seleccionado para inspeccionar el código que lo rodea.  
  
 Si usa la Pila de llamadas de eventos para identificar la ruta de acceso del código donde se origina un evento de problema, puede utilizar sus conocimientos sobre el código base para deducir los posibles orígenes del problema. También puede agregar puntos de interrupción en el código fuente de la aplicación para poder utilizar las técnicas tradicionales de depuración con el fin de examinar cómo el estado de los parámetros de la aplicación o el evento provocan el comportamiento incorrecto del evento.  Con esta valoración, le resultará más fácil encontrar los problemas del código fuente que solo se manifiestan como problemas de representación.  
  
### Información de la Pila de llamadas de eventos gráficos  
 La Pila de llamadas de eventos no admite los eventos anteriores a la trama ni los eventos definidos por el usuario.  La pila de llamadas de eventos gráficos se muestra en formato de tabla.  
  
|Columna|Descripción|  
|-------------|-----------------|  
|**Nombre**|Símbolo que identifica de forma única la función que contiene el sitio de llamada.  El símbolo de depuración de la función se muestra cuando está disponible. Cuando no lo está, se muestra el desplazamiento de función.|  
|**Archivo**|El nombre de archivo del archivo de código fuente o el archivo de biblioteca que contiene el sitio de llamada.|  
|**Ubicación**|El número de línea del sitio de llamada.|  
  
### Vínculos a objetos gráficos  
 Para entender el evento de gráficos seleccionado, puede que necesite información sobre el objeto de Direct3D al que está asociado.  La ventana **Pila de llamadas de eventos gráficos** proporciona vínculos a esta información.  
  
## Vea también  
 [Tutorial: Objetos ausentes debido al sombreado de vértices](../debugger/walkthrough-missing-objects-due-to-vertex-shading.md)