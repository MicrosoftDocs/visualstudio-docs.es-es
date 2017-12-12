---
title: ThreadOn y ThreadOff | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5cd5a695-0a14-484a-8952-ed47e13d8e92
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0cce0fcdf74c79dd78656b7dc4de49821549ee80
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="threadon-and-threadoff"></a>ThreadOn y ThreadOff
Los subcomandos **ThreadOff** y **ThreadOn** de VSPerfCmd.exe solo están disponibles en las sesiones de generación de perfiles de la línea de comandos en las que se usa el método de instrumentación. **ThreadOff** y **ThreadOn** pausan y reanudan la generación de perfiles para el subproceso especificado. **ThreadOff** detiene la generación de perfiles del subproceso y **ThreadOn** la inicia.  
  
 En la mayoría de los casos, se especifica **ThreadOn** o **ThreadOff** como la única opción en una línea de comandos de VSPerfCmd.exe, pero también se pueden combinar con los subcomandos **GlobalOn**, **GlobalOff**, **ProcessOn** y **ProcessOff**.  
  
 Los subcomandos **ThreadOn** y **ThreadOff** interactúan con los subcomandos **GlobalOn** y **GlobalOff** que controlan la recopilación de datos para todos los procesos de una sesión de generación de perfiles de línea de comandos, y con los subcomandos **ProcessOn** y **ProcessOff** que controlan la recopilación de datos para un proceso especificado.  
  
 Los subcomandos **ThreadOff** y **ThreadOn** también afectan al recuento de inicios y paradas de subprocesos que se manipula mediante las funciones de API del generador de perfiles.  
  
-   **ThreadOff** establece inmediatamente el contador de inicios y paradas de subproceso en 0 y, por tanto, detiene la generación de perfiles.  
  
-   **ThreadOn** establece inmediatamente el contador de inicios y paradas de subproceso en 1 y, por tanto, reanuda la generación de perfiles.  
  
 Para más información, vea [API de herramientas de generación de perfiles](../profiling/profiling-tools-apis.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
VSPerfCmd.exe /{ThreadOff|ThreadOn}:TID [Options]  
  
```  
  
#### <a name="parameters"></a>Parámetros  
 `TID`  
 Identificador entero del subproceso que se va a iniciar o detener.  
  
## <a name="valid-options"></a>Opciones válidas  
 **ThreadOn** y **ThreadOff** se pueden especificar en líneas de comandos que también contienen los subcomandos siguientes.  
  
 **Start:** `Method`  
 Inicializa la sesión de generación de perfiles de línea de comandos y establece el método de generación de perfiles especificado.  
  
 **GlobalOff** y **GlobalOn**  
 Detiene o inicia la generación de perfiles para todos los procesos en una sesión de generación de perfiles de línea de comandos.  
  
 {**ProcessOff**&#124;**ProcessOn**}**:**`TID`  
 Detiene o inicia la generación de perfiles para el proceso especificado.  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo, se usa el subcomando **ThreadOff** para detener la recopilación de datos de generación de perfiles para que solo se recopilen los datos de inicio de la aplicación.  
  
```  
; Initialize the profiler.  
VSPerfCmd.exe /Start:Trace /Output:Instrument.vsp   
; Start the instrumented application.  
; Stop profiling the thread after startup.  
VSPerfCmd.exe /ThreadOff:12345  
; Shut down the target application.  
; Close the profiler.  
VSPerfCmd /Shutdown  
  
```  
  
## <a name="see-also"></a>Vea también  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Generar perfiles para aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Generar perfiles para aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Generar perfiles de servicios](../profiling/command-line-profiling-of-services.md)