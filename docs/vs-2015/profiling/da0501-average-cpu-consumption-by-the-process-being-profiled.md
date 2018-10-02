---
title: 'DA0501: Promedio de consumo de CPU por parte del proceso que se va a perfilar. | Microsoft Docs'
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
- vs.performance.rules.DA0501
- vs.performance.DA0501
- vs.performance.501
ms.assetid: b01946b4-75e3-47d5-a1a1-cebfae66a3af
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d7c9b36521c9d4afec0daba945de415477bcd948
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47574991"
---
# <a name="da0501-average-cpu-consumption-by-the-process-being-profiled"></a>DA0501: Promedio de consumo de CPU por parte del proceso que se va a perfilar.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [DA0501: consumo de CPU promedio del proceso que se va a perfilar.](https://docs.microsoft.com/visualstudio/profiling/da0501-average-cpu-consumption-by-the-process-being-profiled).  
  
Id. de regla | DA501 |  
| Categoría | Supervisión de recursos |  
| Método de generación de perfiles | Todos los |  
| Mensaje | Promedio de consumo de CPU del proceso que se va a perfilar. |  
| Tipo de regla | Información |  
  
 Al generar perfiles mediante los métodos de muestreo, memoria de .NET o contención de recursos, debe reunir al menos 10 ejemplos para activar esta regla.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Este mensaje indica el porcentaje de tiempo que un procesador estuvo ocupado ejecutando instrucciones de la aplicación. El valor notificado es el promedio de todos los intervalos de medición en que estuvo activo el proceso del que se está generando el perfil. El valor puede ser mayor que el 100 % en un equipo con más de un procesador.  
  
## <a name="how-to-use-rule-data"></a>Cómo utilizar datos de regla  
 Utilice el valor de la regla para comparar el rendimiento de distintas versiones o compilaciones del programa o para entender el rendimiento de la aplicación en otros escenarios de prueba diferentes.



