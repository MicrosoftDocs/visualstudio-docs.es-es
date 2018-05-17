---
title: Desasociar | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: d9d1b52c-7f28-467d-b1e0-512afc4e46c9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 33255899cbd3ac1fb539d29de5d8b6875a7ea8d6
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/11/2018
---
# <a name="detach"></a>Desasociar
La opción **Desasociar** de VSPerfCmd.exe desconecta el generador de perfiles de los procesos especificados o de todos los procesos si no se especifica ninguno. Se debe haber inicializado la generación de perfiles mediante el método de muestreo.  
  
 La generación de perfiles que se ha iniciado con las opciones **Iniciar** o **Adjuntar** se puede desconectar con **Desasociar**. El generador de perfiles se puede volver a adjuntar mediante los comandos **Adjuntar** subsiguientes.  
  
 **Desasociar** no cierra el archivo de datos de generación de perfiles. Use la opción **Cierre** para finalizar la generación de perfiles y cerrar el archivo de datos.  
  
> [!NOTE]
>  Si la opción **Start** se ha especificado con la opción **CrossSession**, en cualquier llamada a **VSPerfCmd /Attach** o a **VSPerfCmd /Detach** también se debe especificar **CrossSession**.  
  
## <a name="syntax"></a>Sintaxis  
  
```cmd  
VSPerfCmd.exe /Detach[:PIDs|ProcessNames]  
```  
  
#### <a name="parameters"></a>Parámetros  
 `PIDs|ProcessNames`  
 `PID`: identificador del sistema numérico de uno o varios procesos.  
  
 `ProcessNames`: nombre del proceso. Si se ejecutan varias instancias del proceso designado, los resultados son imprevisibles.  
  
 Separe varios procesos con comas.  
  
 Si no se especifica ningún proceso, el generador de perfiles se desasocia de todos los procesos para los que se generan perfiles.  
  
## <a name="valid-options"></a>Opciones válidas  
 Las opciones siguientes de **VSPerfCmd** se pueden combinar con la opción **Adjuntar** en una sola línea de comandos.  
  
 **CrossSession**  
 Habilita la generación de perfiles de aplicaciones en las sesiones que no sean la sesión de inicio. Es obligatorio si la opción **Start** se ha especificado con la opción **CrossSession**.  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo, el comando **Desasociar** suspende la generación de perfiles y el comando **Cierre** cierra el archivo de datos del generador de perfiles.  
  
```cmd  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
;REM Excercise the application  
VSPerfCmd.exe /Detach  
VSPerfCmd.exe /Shutdown  
```  
  
## <a name="see-also"></a>Vea también  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Generar perfiles para aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Generar perfiles para aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Generar perfiles de servicios](../profiling/command-line-profiling-of-services.md)