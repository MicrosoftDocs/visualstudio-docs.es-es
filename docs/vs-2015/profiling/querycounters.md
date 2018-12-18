---
title: QueryCounters | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8059d4b2-af61-4a47-a6c2-8da5c0741c74
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1f5bedfd794dc7666240b1657cbdc4125b46708b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51809290"
---
# <a name="querycounters"></a>QueryCounters
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La opción **QueryCounters** enumera los contadores de rendimiento de CPU (hardware) que están disponibles en el equipo.  
  
 **QueryCounters** debe ser la única opción en la línea de comandos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
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



