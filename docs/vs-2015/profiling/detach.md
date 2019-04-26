---
title: Desasociar | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: d9d1b52c-7f28-467d-b1e0-512afc4e46c9
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1b35765614f57350cdace560aa61c721cc831581
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63444028"
---
# <a name="detach"></a>Desasociar
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La opción **Desasociar** de VSPerfCmd.exe desconecta el generador de perfiles de los procesos especificados o de todos los procesos si no se especifica ninguno. Se debe haber inicializado la generación de perfiles mediante el método de muestreo.  
  
 La generación de perfiles que se ha iniciado con las opciones **Iniciar** o **Adjuntar** se puede desconectar con **Desasociar**. El generador de perfiles se puede volver a adjuntar mediante los comandos **Adjuntar** subsiguientes.  
  
 **Desasociar** no cierra el archivo de datos de generación de perfiles. Use la opción **Cierre** para finalizar la generación de perfiles y cerrar el archivo de datos.  
  
> [!NOTE]
> Si la opción **Start** se ha especificado con la opción **CrossSession**, en cualquier llamada a **VSPerfCmd /Attach** o a **VSPerfCmd /Detach** también se debe especificar **CrossSession**.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
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
  
```  
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
