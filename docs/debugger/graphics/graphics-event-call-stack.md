---
title: Pila de llamadas de eventos de gráficos | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics.callstack
ms.assetid: 8a30168d-8b39-4de1-b094-c7356ba101a3
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 77c53db002fd0d300a01b5cc142f6ed2daf4daa2
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/03/2018
ms.locfileid: "39510583"
---
# <a name="graphics-event-call-stack"></a>Pila de llamadas de eventos de gráficos
La pila de llamadas de eventos gráficos del Analizador de gráficos de Visual Studio le ayuda a establecer la relación entre los eventos de gráficos problemáticos y el código fuente de la aplicación.  
  
 Esta es la ventana de la Pila de llamadas de eventos:  
  
 ![La pila de llamadas que precede a un evento DrawIndexed. ](media/gfx_diag_demo_graphics_event_call_stack_orientation.png "gfx_diag_demo_graphics_event_call_stack_orientation")  
  
## <a name="understanding-the-graphics-event-call-stack"></a>Descripción de la pila de llamadas de eventos gráficos  
 Puede utilizar la Pila de llamadas de eventos para comprender el flujo de ejecución que llevó a un determinado evento de Direct3D. Se parece a la ventana Pila de llamadas de Visual Studio, excepto en que en lugar de mostrar la pila de llamadas actual del subproceso actual en una aplicación en ejecución, muestra la pila de llamadas que existía cuando se produjo el evento de Direct3D seleccionado. Desde la Pila de llamadas de eventos, puede ir directamente al sitio de llamada del evento de Direct3D seleccionado para inspeccionar el código que lo rodea.  
  
 Si usa la Pila de llamadas de eventos para identificar la ruta de acceso del código donde se origina un evento de problema, puede utilizar sus conocimientos sobre el código base para deducir los posibles orígenes del problema. También puede agregar puntos de interrupción en el código fuente de la aplicación para poder utilizar las técnicas tradicionales de depuración con el fin de examinar cómo el estado de los parámetros de la aplicación o el evento provocan el comportamiento incorrecto del evento. Con esta valoración, le resultará más fácil encontrar los problemas del código fuente que solo se manifiestan como problemas de representación.  
  
### <a name="graphics-event-call-stack-information"></a>Información de la Pila de llamadas de eventos gráficos  
 La Pila de llamadas de eventos no admite los eventos anteriores a la trama ni los eventos definidos por el usuario. La pila de llamadas de eventos gráficos se muestra en formato de tabla.  
  
|Columna|Descripción|  
|------------|-----------------|  
|**Name**|Símbolo que identifica de forma única la función que contiene el sitio de llamada. El símbolo de depuración de la función se muestra cuando está disponible. Cuando no lo está, se muestra el desplazamiento de función.|  
|**Archivo**|El nombre de archivo del archivo de código fuente o el archivo de biblioteca que contiene el sitio de llamada.|  
|**Ubicación**|El número de línea del sitio de llamada.|  
  
### <a name="links-to-graphics-objects"></a>Vínculos a objetos gráficos  
 Para entender el evento de gráficos seleccionado, puede que necesite información sobre el objeto de Direct3D al que está asociado. El **pila de llamadas de eventos de gráficos** ventana proporciona vínculos a esta información.  
  
## <a name="see-also"></a>Vea también  
 [Tutorial: Objetos ausentes debido al sombreado de vértices](walkthrough-missing-objects-due-to-vertex-shading.md)