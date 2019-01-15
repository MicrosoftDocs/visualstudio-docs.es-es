---
title: 'DA0502: Consumo máximo de CPU del proceso cuyo perfil se está generando | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DA0502
- vs.performance.DA0502
- vs.performance.502
ms.assetid: 1ee53df5-b0dc-4265-9d4f-527830d08725
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ac4f4ff8c5ccc35dee7144da864ccf3385a6817f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53949919"
---
# <a name="da0502-maximum-cpu-consumption-by-the-process-being-profiled"></a>DA0502: Consumo máximo de CPU del proceso cuyo perfil se está generando

|||  
|-|-|  
|Identificador de regla|DA0502|  
|Categoría|Supervisión de recursos|  
|Método de generación de perfiles|Todas|  
|Mensaje|Esta regla es solo informativa. El contador % de tiempo del procesador del proceso()\\ mide el consumo de CPU del proceso del que está generando perfiles. El valor notificado es el máximo observado de todos los intervalos de medición.|  
|Tipo de regla|Informativa|  

 Al generar perfiles mediante los métodos de muestreo, memoria de .NET o contención de recursos, debe reunir al menos 10 ejemplos para activar esta regla.  

## <a name="rule-description"></a>Descripción de la regla  
 Este mensaje indica el porcentaje de tiempo máximo que un procesador estuvo ocupado ejecutando instrucciones de la aplicación. El valor notificado es el valor máximo notificado entre todos los intervalos de medición en que estuvo activo el proceso del que se está generando el perfil. El porcentaje puede ser mayor que el 100 % en un equipo con más de un procesador.  

## <a name="how-to-use-the-rule-data"></a>Cómo usar los datos de la regla  
 Utilice el valor de la regla para comparar el rendimiento de distintas versiones o compilaciones del programa o para entender el rendimiento de la aplicación en otros escenarios de generación de perfiles diferentes.