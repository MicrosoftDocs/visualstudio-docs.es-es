---
title: Sys (VSPerfCmd) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 294a6f9e-b49f-4c83-b322-5ac5411b66fb
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4c733e9ce91ede2e8944616c5db1a727349854b1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="sys-vsperfcmd"></a>Sys (VSPerfCmd)
La opción **Sys** de VSPerfCmd.exe establece el evento de generación de perfiles que se muestrea para eventos de llamada del sistema (llamadas de función desde la aplicación de la que se ha generado el perfil al sistema operativo) y, opcionalmente, cambia el número de llamadas del sistema en un intervalo de muestreo a partir del valor 10 predeterminado.  
  
 **Sys** solo se puede usar en una línea de comandos que también contenga la opción **Launch** o **Attach**.  
  
 De forma predeterminada, el evento de muestreo del generador de perfiles está establecido en los ciclos de reloj de procesador y el intervalo de muestreo está establecido en 10.000.000. Las opciones **Timer**, **PF**, **Sys** y **Counter** permiten establecer el evento de muestreo y el intervalo de muestreo. La opción **GC** recopila datos de memoria de .NET en cada evento de asignación y de recolección de elementos no utilizados. Solamente se puede especificar una de estas opciones en una línea de comandos.  
  
 El evento de muestreo y el intervalo de muestreo solo se pueden establecer en la primera línea de comandos que contenga una opción **Launch** o **Attach**.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
VSPerfCmd.exe {/Launch:AppName|Attach:PID} /Sys[:Events] [Options]  
```  
  
#### <a name="parameters"></a>Parámetros  
 `Events`  
 Valor entero que especifica el número de eventos de llamada del sistema en un intervalo de muestreo. Si no se especifica `Events`, el intervalo se establece en 10.  
  
## <a name="required-options"></a>Opciones necesarias  
 **Sys** requiere una de las opciones siguientes.  
  
 **Launch:** `AppName`  
 Inicia el generador de perfiles y la aplicación especificada por `AppName`.  
  
 **Attach:** `PID`  
 Adjunta el generador de perfiles al proceso especificado por `PID`.  
  
## <a name="invalid-options"></a>Opciones no válidas  
 Las opciones siguientes no se pueden especificar en la misma línea de comandos que **Sys**.  
  
 **PF**[**:**`Events`]  
 Establece el evento de muestreo en los errores de página y, opcionalmente, establece el intervalo del muestreo en `Events`. El intervalo PF predeterminado es 10.  
  
 **Timer**[**:**`Cycles`]  
 Establece el evento de muestreo en los ciclos de reloj de procesador y, opcionalmente, establece el intervalo del muestreo en `Cycles`. El intervalo de Timer predeterminado es 10 000 000.  
  
 **Counter:** `Name`[`,Reload`[`,FriendlyName`]]  
 Establece el evento de muestreo en el contador de rendimiento de la CPU especificado por `Name` y establece el intervalo de muestreo en `Reload`.  
  
 **GC**[**:**{**Allocation**&#124;**Lifetime**}]  
 Recopila datos de memoria de .NET. Mediante la opción (**Allocation**) predeterminada, se recopilan datos en cada evento de asignación de memoria. Cuando se especifica el parámetro **Lifetime**, también se recopilan datos en cada evento de recolección de elementos no utilizados.  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo se muestra cómo establecer el evento de muestreo del generador de perfiles en llamadas al sistema y cómo establecer el intervalo de muestreo en 20 llamadas por muestra.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /Sys:20  
```  
  
## <a name="see-also"></a>Vea también  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Generar perfiles para aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Generar perfiles para aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Generar perfiles de servicios](../profiling/command-line-profiling-of-services.md)