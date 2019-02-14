---
title: 'DA0004: Alto uso del procesador | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.rules.DAHighProcessorUsage
- vs.performance.rules.DA0004
- vs.performance.DA0004
- vs.performance.4
ms.assetid: 2c4fb569-929e-4f1d-8c50-b590ee371351
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a0e14a7400b937c56c2aac49a43d1d59cf96eba0
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "54762529"
---
# <a name="da0004-high-processor-usage"></a>DA0004: Alto uso del procesador
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Id. de regla | DA0004 |  
| Categoría | Uso de herramientas de generación de perfiles |  
| Métodos de generación de perfiles | Muestreo de instrumentación |  
| Mensaje | El uso del procesador está constantemente por encima del 75%. Considere la posibilidad de utilizar el modo de muestreo para aplicaciones enlazadas a la CPU.  
| Tipo de regla | Información |  
  
 Al generar perfiles mediante los métodos de muestreo, memoria de .NET o contención de recursos, debe reunir al menos 10 ejemplos para activar esta regla.  
  
## <a name="cause"></a>Motivo  
 La utilización del procesador (CPU) fue considerablemente alta al generar perfiles de datos recopilados mediante el método de instrumentación. Considere la posibilidad de utilizar el método de generación de perfiles por muestreo al generar perfiles de una aplicación enlazada a la CPU.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Durante esta ejecución de generación de perfiles, el procesador (o procesadores) estuvo siempre muy ocupado. Un uso de CPU elevado puede indicar una aplicación enlazada a la CPU. Los perfiles instrumentados no suelen ser la manera más eficaz para investigar los escenarios de uso de CPU. El muestreo es normalmente más eficaz al generar perfiles de aplicaciones que pasan la mayor parte del tiempo ejecutando instrucciones en el procesador.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Considere la posibilidad de volver a generar perfiles de la aplicación mediante el método de muestreo en lugar del método de instrumentación, a menos que necesite intervalos de función o esté más interesado en conocer los procesos de E/S que los cuellos de botella del procesador.
