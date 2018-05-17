---
title: QueryCounters | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 8059d4b2-af61-4a47-a6c2-8da5c0741c74
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ce82016b16eef3bd7c48cb156c705d0f1b28198b
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/11/2018
---
# <a name="querycounters"></a>QueryCounters
La opción **QueryCounters** enumera los contadores de rendimiento de CPU (hardware) que están disponibles en el equipo.  
  
 **QueryCounters** debe ser la única opción en la línea de comandos.  
  
## <a name="syntax"></a>Sintaxis  
  
```cmd  
VSPerfCmd.exe /QueryCounters  
```  
  
#### <a name="parameters"></a>Parámetros  
 Ninguna  
  
## <a name="remarks"></a>Comentarios  
 Cuando se utiliza el método de instrumentación, el generador de perfiles puede recopilar los valores de uno o varios contadores de rendimiento de CPU en cada evento de recopilación de datos. Cuando se utiliza el método de generación de perfiles de muestreo, puede especificar un evento de contador y el número de repeticiones del evento que se usará como el intervalo de muestreo.  
  
 Diferentes procesadores exponen distintos contadores de rendimiento de CPU. El generador de perfiles define un conjunto de contadores genéricos que se pueden utilizar en casi todos los procesadores. La opción **QueryCounters** muestra los nombres tanto de los contadores genéricos como de los contadores que son específicos del procesador.  
  
## <a name="see-also"></a>Vea también  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Generar perfiles para aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Generar perfiles para aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Generar perfiles de servicios](../profiling/command-line-profiling-of-services.md)