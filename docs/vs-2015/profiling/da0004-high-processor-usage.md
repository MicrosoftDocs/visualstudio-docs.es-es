---
title: 'DA0004: Alto uso del procesador | Microsoft Docs'
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
- vs.performance.rules.DAHighProcessorUsage
- vs.performance.rules.DA0004
- vs.performance.DA0004
- vs.performance.4
ms.assetid: 2c4fb569-929e-4f1d-8c50-b590ee371351
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 759ba305335c75591bf975e40f011f31edd1bdb5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47582474"
---
# <a name="da0004-high-processor-usage"></a>DA0004: Alto uso del procesador
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [DA0004: alto uso del procesador](https://docs.microsoft.com/visualstudio/profiling/da0004-high-processor-usage).  
  
Id. de regla | DA0004 |  
| Categoría | Uso de herramientas de generación de perfiles |  
| Métodos de generación de perfiles | Muestreo de instrumentación |  
| Mensaje | El uso del procesador está constantemente por encima del 75%. Considere el uso de modo de muestreo para aplicaciones enlazadas a la CPU. |  
| Tipo de regla | Información |  
  
 Al generar perfiles mediante los métodos de muestreo, memoria de .NET o contención de recursos, debe reunir al menos 10 ejemplos para activar esta regla.  
  
## <a name="cause"></a>Motivo  
 La utilización del procesador (CPU) fue considerablemente alta al generar perfiles de datos recopilados mediante el método de instrumentación. Considere la posibilidad de utilizar el método de generación de perfiles por muestreo al generar perfiles de una aplicación enlazada a la CPU.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Durante esta ejecución de generación de perfiles, el procesador (o procesadores) estuvo siempre muy ocupado. Un uso de CPU elevado puede indicar una aplicación enlazada a la CPU. Los perfiles instrumentados no suelen ser la manera más eficaz para investigar los escenarios de uso de CPU. El muestreo es normalmente más eficaz al generar perfiles de aplicaciones que pasan la mayor parte del tiempo ejecutando instrucciones en el procesador.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Considere la posibilidad de volver a generar perfiles de la aplicación mediante el método de muestreo en lugar del método de instrumentación, a menos que necesite intervalos de función o esté más interesado en conocer los procesos de E/S que los cuellos de botella del procesador.




