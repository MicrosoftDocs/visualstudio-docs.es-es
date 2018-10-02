---
title: 'DA0003: Muchas muestras de kernel | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.rules.DA0003
- vs.performance.DA0003
- vs.performance.3
- vs.performance.rules.DAManyKernelSamples
ms.assetid: c1f46f77-eb95-42e5-b340-d86bc9de41b4
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fd4412fc120eb0a0fa039ac91bec4da4ba4a6f44
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47580747"
---
# <a name="da0003-many-kernel-samples"></a>DA0003: Muchas muestras de kernel
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [DA0003: muchas muestras de kernel](https://docs.microsoft.com/visualstudio/profiling/da0003-many-kernel-samples).  
  
Id. de regla | DA0003 |  
| Categoría | Uso de herramientas de generación de perfiles |  
| Métodos de generación de perfiles | Muestreo |  
| Mensaje | Tener una proporción elevada de muestras en modo Kernel. Esto podría indicar un gran volumen de actividad de E/S o una alta tasa de cambio de contexto. Considere la posibilidad de generación de perfiles de la aplicación utilizando el modo de instrumentación de nuevo. |  
| Tipo de regla | Información |  
  
## <a name="cause"></a>Motivo  
 Una proporción considerable de las muestras de la pila de llamadas recopiladas para la aplicación se estaban ejecutando en modo kernel. Considere la posibilidad de generar perfiles para la aplicación mediante un método de generación de perfiles diferente.  
  
## <a name="rule-description"></a>Descripción de la regla  
 En Windows, se puede ejecutar código en modo kernel o en modo de usuario. (El modo kernel también se denomina modo privilegiado). En modo kernel solo se ejecuta código de sistema de bajo nivel, como los controladores de dispositivos. Una aplicación en modo de usuario puede hacer una transición al modo kernel para realizar operaciones de E/S, esperar las primitivas de sincronización de subproceso o proceso o realizar llamadas del sistema.  
  
 El muestreo es más eficaz al generar perfiles de aplicaciones que trabajan en modo de usuario la mayor parte del tiempo. El número de muestras recopiladas cuando la aplicación se ha ejecutado en modo kernel puede indicar que se realizan operaciones de E/S con frecuencia o que se están produciendo cambios de contexto. Ninguna de estas operaciones se puede investigar mediante el método de muestreo. Si se toman demasiadas muestras del modo kernel, puede que los datos de muestreo no contengan suficientes muestras del modo de usuario para tener un valor estadístico significativo.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Considere la posibilidad de volver a generar perfiles para la aplicación mediante una de las opciones siguientes:  
  
-   Generar perfiles mediante el método de instrumentación.  
  
-   Aumentar la velocidad de muestreo para intentar recopilar más muestras en modo de usuario.



