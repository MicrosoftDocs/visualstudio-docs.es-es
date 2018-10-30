---
title: Attach | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 79614283-6733-4592-a53a-d428052271ad
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cc3db6b677e23e0752612f688055befd366e34d0
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49845542"
---
# <a name="attach"></a>Attach
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La opción **Attach** de VSPerfCmd.exe comienza la generación de perfiles de muestra del proceso en ejecución que especifica el id. de proceso (PID).  
  
 Para usar la opción **Attach**, debe especificar el método **Sample** en la opción Start.  
  
> [!NOTE]
>  Si la opción **Start** se ha especificado con la opción **CrossSession**, en cualquier llamada a **VSPerfCmd /Attach** o a **VSPerfCmd /Detach** también se debe especificar **CrossSession**.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
VSPerfCmd.exe /Attach:ProcessID [Options]  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ProcessID`  
 Id. de proceso (PID) del proceso en ejecución. El PID de un proceso en ejecución se muestra en la pestaña Procesos del Administrador de tareas de Windows.  
  
## <a name="valid-options"></a>Opciones válidas  
 Las opciones siguientes de **VSPerfCmd** se pueden combinar con la opción **Adjuntar** en una sola línea de comandos.  
  
 **CrossSession**  
 Habilita la generación de perfiles de aplicaciones en las sesiones que no sean la sesión de inicio. Es obligatorio si la opción **Start** se ha especificado con la opción **CrossSession**.  
  
 **Start:** `Method`  
 Inicializa la sesión del generador de perfiles de línea de comandos y establece el método de generación de perfiles especificado.  
  
 **TargetCLR**  
 Especifica la versión de Common Language Runtime (CLR) de .NET Framework para generar perfiles cuando se carga más de una versión en una sesión de generación de perfiles. De forma predeterminada, se genera el perfil de la primera versión cargada.  
  
 **GlobalOn GlobalOff**  
 Reanuda la generación de perfiles de (**GlobalOn**) o detiene la de (**GlobalOff**), pero no finaliza la sesión de generación de perfiles.  
  
 **ProcessOn:** `PID` **ProcessOff:** `PID`  
 Reanuda la generación de perfiles de (**ProcessOn**) o detiene la de (**ProcessOff**) para el proceso especificado.  
  
## <a name="interval-options"></a>Opciones de intervalo  
 Se puede especificar una de las siguientes opciones de intervalo de muestreo en la línea de comandos de Attach. El intervalo de muestreo predeterminado es 10 000 000 ciclos de reloj de procesador.  
  
 **Timer**[**:**`Cycles`]**PF**[**:**`Events`]**Sys**[<strong>:</strong>Events]**Counter**[**:**`Name`,`Reload`,`FriendlyName`]  
 Especifica el número y tipo del intervalo de muestreo.  
  
-   **Timer**: muestrea cada `Cycles` ciclos de reloj de procesador. Si no se especifica `Cycles`, se usan 10 000 000 ciclos.  
  
-   **PF**: muestrea cada `Events` errores de página. Si no se especifica `Events`, se usan 10 errores de página.  
  
-   **Sys**: muestrea cada `Events` llamadas al sistema operativo. Si no se especifica `Events`, se usan 10 llamadas del sistema.  
  
-   **Counter**: muestrea cada número `Reload` del contador de rendimiento de la CPU que especifica `Name`. Opcionalmente, `FriendlyName` puede especificar una cadena que se usará como el encabezado de columna en los informes del generador de perfiles.  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo se muestra cómo adjuntar a una instancia en ejecución de una aplicación con el id. de proceso 12345.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Attach:12345  
```  
  
## <a name="see-also"></a>Vea también  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Generar perfiles para aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Generar perfiles para aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Generar perfiles de servicios](../profiling/command-line-profiling-of-services.md)



