---
title: Launch | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: f81bde5c-3394-4b79-a315-c2f6491689b3
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 97ccdd3bf5e78af277430be1d86a95fad2f180e8
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/19/2019
ms.locfileid: "54778933"
---
# <a name="launch"></a>Launch
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La opción **Launch** inicia el generador de perfiles mediante el método de muestreo y también inicia la aplicación especificada.  
  
 Para usar la opción **Launch**, debe especificar el método **Sample** en la opción **Start**.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
VSPerfCmd.exe /Launch:AppName [Options]  
```  
  
#### <a name="parameters"></a>Parámetros  
 `AppName`  
 El nombre de la aplicación que se va a iniciar. Se admiten rutas de acceso completas y parciales desde el directorio actual.  
  
## <a name="valid-options"></a>Opciones válidas  
 Las opciones siguientes de VSPerfCmd se pueden combinar con la opción **Launch** en una sola línea de comandos.  
  
 **Start:** `Method`  
 Inicializa la sesión del generador de perfiles de línea de comandos y establece el método de generación de perfiles especificado.  
  
 **GlobalOn** y **GlobalOff**  
 Reanuda la generación de perfiles de (**GlobalOn**) o detiene la de (**GlobalOff**), pero no finaliza la sesión de generación de perfiles.  
  
 **ProcessOn:** `PID` y **ProcessOff**:`PID`  
 Reanuda la generación de perfiles de (**ProcessOn**) o detiene la de (**ProcessOff**) para el proceso especificado.  
  
 **TargetCLR**  
 Especifica la versión de Common Language Runtime (CLR) de .NET Framework para generar perfiles cuando se carga más de una versión en una sesión de generación de perfiles. De forma predeterminada, se genera el perfil de la primera versión cargada.  
  
## <a name="exclusive-options"></a>Opciones exclusivas  
 Las opciones siguientes solo se pueden usar con la opción **Launch**.  
  
 **Consola**  
 Inicia la aplicación de línea de comandos especificada en una nueva ventana.  
  
 **Args:** `ArgList`  
 Especifica la lista de argumentos para pasar a la aplicación.  
  
 **LineOff**  
 Deshabilita la recopilación de datos de generación de perfiles en el nivel de línea.  
  
## <a name="sampling-options"></a>Opciones de muestreo  
 Se puede especificar una de las siguientes opciones de intervalo de muestreo en la línea de comandos de **Launch**. El intervalo de muestreo predeterminado es 10 000 000 ciclos de reloj de procesador.  
  
 **Timer**[**:**`Cycles`]**PF**[**:**`Events`]**Sys**[**:**`Events`]**Counter**[**:**`Name`,`Reload`,`FriendlyName`]**GC**[:**allocation**&#124;**lifetime**]  
 Especifica el número y tipo del intervalo de muestreo.  
  
-   **Timer**: muestrea cada `Cycles` ciclos de reloj de procesador no detenidos. Si no se especifica `Cycles`, se usan 10 000 000 ciclos.  
  
-   **PF**: muestrea cada `Events` errores de página. Si no se especifica `Events`, 10 errores de página.  
  
-   **Sys**: muestrea cada `Events` llamadas al sistema operativo. Si no se especifica `Events`, se usan 10 llamadas del sistema.  
  
-   **Counter**: muestrea cada número `Reload` del contador de rendimiento de la CPU que especifica `Name`. Opcionalmente, `FriendlyName` puede especificar una cadena que se usará como el encabezado de columna en los informes del generador de perfiles.  
  
-   **GC**: recopila datos de memoria de .NET. Mediante la opción (**allocation**), predeterminada, se recopilan datos en cada evento de asignación de memoria. Cuando se especifica el parámetro **lifetime**, también se recopilan datos en cada evento de recolección de elementos no utilizados.  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo se muestra el uso de **Launch** para iniciar una aplicación.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
```  
  
## <a name="see-also"></a>Vea también  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Generar perfiles para aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Generar perfiles para aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Generar perfiles de servicios](../profiling/command-line-profiling-of-services.md)
