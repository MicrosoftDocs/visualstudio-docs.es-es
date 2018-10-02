---
title: 'DA0502: Consumo máximo de CPU del proceso del que se está generando el perfil | Microsoft Docs'
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
- vs.performance.rules.DA0502
- vs.performance.DA0502
- vs.performance.502
ms.assetid: 1ee53df5-b0dc-4265-9d4f-527830d08725
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: be9b9ff318ade6546369e20d5508b2ad79dc0bb9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47568061"
---
# <a name="da0502-maximum-cpu-consumption-by-the-process-being-profiled"></a>DA0502: Máximo consumo de CPU por parte del proceso que se va a perfilar
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [DA0502: consumo máximo de CPU del proceso que se está generando el perfil](https://docs.microsoft.com/visualstudio/profiling/da0502-maximum-cpu-consumption-by-the-process-being-profiled).  
  
Id. de regla | DA0502 |  
| Categoría | Supervisión de recursos |  
| Método de generación de perfiles | Todos los |  
| Mensaje | Esta regla es sólo informativa. El contador % de tiempo del procesador del proceso()\\ mide el consumo de CPU del proceso del que está generando perfiles. El valor indicado es el máximo observado de todos los intervalos de medición. |  
| Tipo de regla | Informativo |  
  
 Al generar perfiles mediante los métodos de muestreo, memoria de .NET o contención de recursos, debe reunir al menos 10 ejemplos para activar esta regla.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Este mensaje indica el porcentaje de tiempo máximo que un procesador estuvo ocupado ejecutando instrucciones de la aplicación. El valor notificado es el valor máximo notificado entre todos los intervalos de medición en que estuvo activo el proceso del que se está generando el perfil. El porcentaje puede ser mayor que el 100 % en un equipo con más de un procesador.  
  
## <a name="how-to-use-the-rule-data"></a>Cómo utilizar los datos de la regla  
 Utilice el valor de la regla para comparar el rendimiento de distintas versiones o compilaciones del programa o para entender el rendimiento de la aplicación en otros escenarios de generación de perfiles diferentes.



