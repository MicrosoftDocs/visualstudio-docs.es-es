---
title: 'DA0003: Muchas muestras de kernel | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DA0003
- vs.performance.DA0003
- vs.performance.3
- vs.performance.rules.DAManyKernelSamples
ms.assetid: c1f46f77-eb95-42e5-b340-d86bc9de41b4
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 97e2e745b59a22110f6392e2cd6fec1aea0a667a
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34750238"
---
# <a name="da0003-many-kernel-samples"></a>DA0003: Muchas muestras de kernel
|||  
|-|-|  
|Identificador de regla|DA0003|  
|Categoría|Uso de Herramientas de generación de perfiles|  
|Métodos de generación de perfiles|Muestreo|  
|Mensaje|Tiene una proporción elevada de muestras en modo kernel. Esto podría indicar un gran volumen de actividad de E/S o una alta tasa de cambio de contexto. Considere la posibilidad de volver a generar perfiles para la aplicación mediante el modo Instrumentación.|  
|Tipo de regla|Información|  
  
## <a name="cause"></a>Motivo  
 Una proporción considerable de las muestras de la pila de llamadas recopiladas para la aplicación se estaban ejecutando en modo kernel. Considere la posibilidad de generar perfiles para la aplicación mediante un método de generación de perfiles diferente.  
  
## <a name="rule-description"></a>Descripción de la regla  
 En Windows, se puede ejecutar código en modo kernel o en modo de usuario. (El modo kernel también se denomina modo privilegiado). En modo kernel solo se ejecuta código de sistema de bajo nivel, como los controladores de dispositivos. Una aplicación en modo de usuario puede hacer una transición al modo kernel para realizar operaciones de E/S, esperar las primitivas de sincronización de subproceso o proceso o realizar llamadas del sistema.  
  
 El muestreo es más eficaz al generar perfiles de aplicaciones que trabajan en modo de usuario la mayor parte del tiempo. El número de muestras recopiladas cuando la aplicación se ha ejecutado en modo kernel puede indicar que se realizan operaciones de E/S con frecuencia o que se están produciendo cambios de contexto. Ninguna de estas operaciones se puede investigar mediante el método de muestreo. Si se toman demasiadas muestras del modo kernel, puede que los datos de muestreo no contengan suficientes muestras del modo de usuario para tener un valor estadístico significativo.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Considere la posibilidad de volver a generar perfiles para la aplicación mediante una de las opciones siguientes:  
  
-   Generar perfiles mediante el método de instrumentación.  
  
-   Aumentar la velocidad de muestreo para intentar recopilar más muestras en modo de usuario.