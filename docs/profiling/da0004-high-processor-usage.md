---
title: 'DA0004: Alto uso del procesador | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DAHighProcessorUsage
- vs.performance.rules.DA0004
- vs.performance.DA0004
- vs.performance.4
ms.assetid: 2c4fb569-929e-4f1d-8c50-b590ee371351
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d5800acfded9d500c68a0e071ffa6501d6b3c77e
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34749615"
---
# <a name="da0004-high-processor-usage"></a>DA0004: Alto uso del procesador
|||  
|-|-|  
|Identificador de regla|DA0004|  
|Categoría|Uso de Herramientas de generación de perfiles|  
|Métodos de generación de perfiles|Instrumentación<br /><br /> Muestreo|  
|Mensaje|El uso del procesador está constantemente por encima del 75 %. Considere la posibilidad de utilizar el modo de muestreo para aplicaciones enlazadas a la CPU.|  
|Tipo de regla|Información|  
  
 Al generar perfiles mediante los métodos de muestreo, memoria de .NET o contención de recursos, debe reunir al menos 10 ejemplos para activar esta regla.  
  
## <a name="cause"></a>Motivo  
 La utilización del procesador (CPU) fue alta al generar perfiles de datos recopilados mediante el método de instrumentación. Considere la posibilidad de utilizar el método de generación de perfiles por muestreo al generar perfiles de una aplicación enlazada a la CPU.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Durante esta ejecución de generación de perfiles, el procesador (o procesadores) estuvo ocupado constantemente. Un uso de CPU elevado puede indicar una aplicación enlazada a la CPU. Los perfiles instrumentados no son la manera más eficaz para investigar los escenarios de uso de CPU. El muestreo es más eficaz al generar perfiles de aplicaciones que pasan la mayor parte del tiempo ejecutando instrucciones en el procesador.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Considere la posibilidad de volver a generar perfiles de la aplicación mediante el método de muestreo en lugar del método de instrumentación, a menos que necesite intervalos de función o esté más interesado en conocer los procesos de E/S que los cuellos de botella del procesador.