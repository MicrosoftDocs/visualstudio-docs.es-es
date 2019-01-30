---
title: 'DA0501: Promedio de consumo de CPU del proceso del que se está generando el perfil. | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DA0501
- vs.performance.DA0501
- vs.performance.501
ms.assetid: b01946b4-75e3-47d5-a1a1-cebfae66a3af
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b7bd27ceb83105a9d790937b3a5fcb904adf3abd
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54983981"
---
# <a name="da0501-average-cpu-consumption-by-the-process-being-profiled"></a>DA0501: Promedio de consumo de CPU del proceso del que se está generando el perfil.

|||  
|-|-|  
|Identificador de regla|DA501|  
|Categoría|Supervisión de recursos|  
|Método de generación de perfiles|Todas|  
|Mensaje|Promedio de consumo de CPU del proceso del que se está generando el perfil.|  
|Tipo de regla|Información|  

 Al generar perfiles mediante los métodos de muestreo, memoria de .NET o contención de recursos, debe reunir al menos 10 ejemplos para activar esta regla.  

## <a name="rule-description"></a>Descripción de la regla  
 Este mensaje indica el porcentaje de tiempo que un procesador estuvo ocupado ejecutando instrucciones de la aplicación. El valor notificado es el promedio de todos los intervalos de medición en que estuvo activo el proceso del que se está generando el perfil. El valor puede ser mayor que el 100 % en un equipo con más de un procesador.  

## <a name="how-to-use-rule-data"></a>Cómo usar los datos de la regla  
 Utilice el valor de la regla para comparar el rendimiento de distintas versiones o compilaciones del programa o para entender el rendimiento de la aplicación en otros escenarios de prueba diferentes.