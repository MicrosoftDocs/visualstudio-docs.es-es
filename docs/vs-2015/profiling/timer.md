---
title: Temporizador | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1971868e-89fa-4452-8ee7-76e4daf31b66
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7a17f756a293ba8909054043713a14340ff9bf39
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47578123"
---
# <a name="timer"></a>Temporizador
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [temporizador](https://docs.microsoft.com/visualstudio/profiling/timer).  
  
La opción **Temporizador** de VSPerfCmd.exe establece el evento de generación de perfiles que se muestrea en ciclos de reloj del procesador, y cambia opcionalmente el número de ciclos en un intervalo de muestreo respecto al valor predeterminado de 10.000.000. En un procesador de 1 GH (un giga), 10.000.000 ciclos de reloj representan aproximadamente 100 muestras por segundo. El número mínimo de ciclos que se puede especificar es 50.000.  
  
 **Temporizador** solo se puede usar cuando se utiliza el método de generación de perfiles de muestreo y únicamente se puede usar en una línea de comandos que también contenga las opciones **Launch** o **Attach**.  
  
 De forma predeterminada, el evento de muestreo del generador de perfiles está establecido en los ciclos de reloj de procesador y el intervalo de muestreo está establecido en 10.000.000. Las opciones **Timer**, **PF**, **Sys** y **Counter** permiten establecer el evento de muestreo y el intervalo de muestreo. La opción **GC** recopila datos de memoria de .NET en cada evento de asignación y de recolección de elementos no utilizados. Solamente se puede especificar una de estas opciones en una línea de comandos.  
  
 El evento de muestreo y el intervalo de muestreo solo se pueden establecer en la primera línea de comandos que contenga una opción **Launch** o **Attach**.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
VSPerfCmd.exe {/Launch:AppName|/Attach:PID} /Timer[:Cycles] [Options]  
```  
  
#### <a name="parameters"></a>Parámetros  
 `Cycles`  
 Valor entero que especifica el número de ciclos de reloj del procesador en un intervalo de muestreo. Si no se especifica `Cycles`, el intervalo se establece en 10.000.000. Especifique el valor sin puntos.  
  
## <a name="required-options"></a>Opciones necesarias  
 **Temporizador** solo se puede especificar en una línea de comandos que contenga una de las opciones siguientes.  
  
 **Launch:** `AppName`  
 Inicia el generador de perfiles y la aplicación especificada por `AppName`.  
  
 **Attach:** `PID`  
 Asocia el generador de perfiles al proceso especificado por el identificador de proceso (`PID`).  
  
## <a name="invalid-options"></a>Opciones no válidas  
 Las opciones siguientes no se pueden especificar en la misma línea de comandos que **Temporizador**.  
  
 **PF**[**:**`Events`]  
 Establece el evento de muestreo en los errores de página y, opcionalmente, establece el intervalo del muestreo en `Events`. El intervalo PF predeterminado es 10.  
  
 **Sys**[**:**`Events`]  
 Establece el evento de muestreo en las llamadas al sistema operativo y, opcionalmente, establece el intervalo del muestreo en `Events`. El intervalo Sys predeterminado es 10.  
  
 **Counter**[**:**`Name,Reload,FriendlyName`]  
 Establece el evento de muestreo en el contador de rendimiento de la CPU especificado por `Name` y establece el intervalo de muestreo en `Reload`.  
  
 **GC**[**:**{**Allocation**&#124;**Lifetime**}]  
 Recopila datos de memoria de .NET. Mediante la opción (**Allocation**) predeterminada, se recopilan datos en cada evento de asignación de memoria. Cuando se especifica el parámetro **Lifetime**, también se recopilan datos en cada evento de recolección de elementos no utilizados.  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo se muestra cómo establecer el intervalo de muestreo del generador de perfiles en 1.000.000 ciclos de procesador.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /Timer:1000000  
```  
  
## <a name="see-also"></a>Vea también  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Generar perfiles para aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Generar perfiles para aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Generar perfiles de servicios](../profiling/command-line-profiling-of-services.md)



