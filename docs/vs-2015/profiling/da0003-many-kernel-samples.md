---
title: 'DA0003: Muchas muestras de kernel | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.rules.DA0003
- vs.performance.DA0003
- vs.performance.3
- vs.performance.rules.DAManyKernelSamples
ms.assetid: c1f46f77-eb95-42e5-b340-d86bc9de41b4
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ad9a0671595d4628932ff4f2db41a137e060c4d1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68158707"
---
# <a name="da0003-many-kernel-samples"></a>DA0003: Muchas muestras de kernel
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Identificador de regla | DA0003 |  
| Categoría | Uso de Herramientas de generación de perfiles |  
| Métodos de generación de perfiles | Muestreo |  
| Mensaje | Tiene una gran proporción de ejemplos en modo kernel. Esto podría indicar un gran volumen de actividad de E/S o una alta tasa de cambio de contexto. Considere la posibilidad de volver a generar perfiles para la aplicación mediante el modo Instrumentación.|  
| Tipo de regla | Información |  
  
## <a name="cause"></a>Motivo  
 Una proporción considerable de las muestras de la pila de llamadas recopiladas para la aplicación se estaban ejecutando en modo kernel. Considere la posibilidad de generar perfiles para la aplicación mediante un método de generación de perfiles diferente.  
  
## <a name="rule-description"></a>Descripción de la regla  
 En Windows, se puede ejecutar código en modo kernel o en modo de usuario. (El modo kernel también se denomina modo privilegiado). Solo el código del sistema de bajo nivel, como los controladores de dispositivo, se ejecuta en modo kernel. Una aplicación en modo de usuario puede hacer una transición al modo kernel para realizar operaciones de E/S, esperar las primitivas de sincronización de subproceso o proceso o realizar llamadas del sistema.  
  
 El muestreo es más eficaz al generar perfiles de aplicaciones que trabajan en modo de usuario la mayor parte del tiempo. El número de muestras recopiladas cuando la aplicación se ha ejecutado en modo kernel puede indicar que se realizan operaciones de E/S con frecuencia o que se están produciendo cambios de contexto. Ninguna de estas operaciones se puede investigar mediante el método de muestreo. Si se toman demasiadas muestras del modo kernel, puede que los datos de muestreo no contengan suficientes muestras del modo de usuario para tener un valor estadístico significativo.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Considere la posibilidad de volver a generar perfiles para la aplicación mediante una de las opciones siguientes:  
  
- Generar perfiles mediante el método de instrumentación.  
  
- Aumentar la velocidad de muestreo para intentar recopilar más muestras en modo de usuario.
