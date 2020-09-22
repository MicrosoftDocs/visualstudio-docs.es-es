---
title: PF | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: cdc0a094-a986-4629-bd1c-dd5fdca323dc
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 243d5fada7342bc05d8768a7e33cca6f55e309ef
ms.sourcegitcommit: fb8babf5cd72f1fc2f97ffe4ad7b62d91f325f61
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/07/2020
ms.locfileid: "90842882"
---
# <a name="pf"></a>PF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La opción **PF** de VSPerfCmd.exe establece el evento de generación de perfiles que se muestrea en errores de página y cambia opcionalmente el número de errores de página en un intervalo de muestreo respecto al valor predeterminado de 10.  
  
> [!NOTE]
> PF no puede usarse en sistemas de 64 bits.  
  
 **Tenga en cuenta que PF** no se admite en equipos de 64 bits. **PF** solo se puede usar en una línea de comandos que también contenga las opciones **Launch** o **Attach**.  
  
 De forma predeterminada, el evento de muestreo está establecido en los ciclos de reloj de procesador y el intervalo de muestreo está establecido en 10.000.000. Las opciones **Timer**, **PF**, **Sys** y **Counter** le permiten establecer el intervalo de muestreo y de eventos de ejemplo. La opción **GC** recopila datos de memoria de .NET en cada evento de asignación y de recolección de elementos no utilizados. Solamente se puede especificar una de estas opciones en una línea de comandos.  
  
 El evento de muestreo y el intervalo de muestreo solo se pueden establecer en la primera línea de comandos que contenga una opción **Launch** o **Attach**.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
VSPerfCmd.exe {/Launch:AppName|/Attach:PID} /PF[:Events] [Options]  
```  
  
#### <a name="parameters"></a>Parámetros  
 `Events`  
 Valor entero que especifica el número de eventos de error de página en un intervalo de muestreo. Si no se especifica `Events`, el intervalo se establece en 10.  
  
## <a name="required-options"></a>Opciones necesarias  
 **PF** solo se puede especificar en una línea de comandos que contenga una de las opciones siguientes.  
  
 **Iniciar:**`AppName`  
 Inicia el generador de perfiles y la aplicación especificada por AppName.  
  
 **Asociar:**`PID`  
 Adjunta el generador de perfiles al proceso especificado por AppName.  
  
## <a name="invalid-options"></a>Opciones no válidas  
 Las opciones siguientes no se pueden especificar en la misma línea de comandos que **PF**.  
  
 **Temporizador**[**:** `Cycles` ]  
 Establece el evento de muestreo en los ciclos de reloj de procesador y, opcionalmente, establece el intervalo del muestreo en `Cycles`. El intervalo de Timer predeterminado es 10 000 000.  
  
 **Sys**[**:** `Events` ]  
 Establece el evento de muestreo en llamadas de la aplicación para la que se genera el perfil al kernel del sistema operativo (syscalls) y, opcionalmente, establece el intervalo de muestreo en `Events`. El intervalo Sys predeterminado es 10.  
  
 **Contador:** `Name` [`,Reload`[`,FriendlyName`]]  
 Establece el evento de muestreo en el contador de rendimiento de la CPU especificado por `Name` y establece el intervalo de muestreo en `Reload`.  
  
 **GC**[**:**{**Allocation**&#124;**Lifetime**}]  
 Recopila datos de memoria de .NET. De forma predeterminada (**asignación**), los datos se recopilan en cada evento de asignación de memoria. Cuando se especifica el parámetro **Lifetime** , también se recopilan datos en cada evento de recolección de elementos no utilizados.  
  
## <a name="example"></a>Ejemplo  
 Este ejemplo muestra cómo establecer el evento de ejemplo de generación de perfiles en errores de página y establecer el intervalo de muestreo en 20 errores de página.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /PF:20  
```  
  
## <a name="see-also"></a>Consulte también  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Generar perfiles de aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Generar perfiles de aplicaciones Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Generación de perfiles de servicios](../profiling/command-line-profiling-of-services.md)
