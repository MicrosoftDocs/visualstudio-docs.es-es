---
title: Iniciar | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b85d0fe9-f67a-4b7c-8d48-7eecf3f2dfe9
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f7da3855a699ae350c24646386d3b1a7e39520b4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="start"></a>Iniciar
La opción **Iniciar** es una opción de VSPerfCmd.exe que inicializa el generador de perfiles al método de generación de perfiles especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
VSPerfCmd.exe /Start:Method /Output:FileName [Options]  
```  
  
#### <a name="parameters"></a>Parámetros  
 `Method`  
 Debe ser una de las siguientes palabras clave:  
  
-   **TRACE**: especifica el método de instrumentación.  
  
-   **SAMPLE**: especifica el método de muestreo.  
  
-   **COVERAGE**: especifica la cobertura de código.  
  
-   **CONCURRENCY**: especifica el método de contención de recursos.  
  
## <a name="required-options"></a>Opciones necesarias  
 La opción **Salida** debe especificarse cuando se especifica **Iniciar** en la línea de comandos.  
  
 **Salida:** `filename`  
 Especifica el nombre del archivo de salida.  
  
## <a name="exclusive-options"></a>Opciones exclusivas  
 Las siguientes opciones solo pueden usarse con la opción **Iniciar** en una línea de comandos.  
  
 **CrossSession**|**CS**  
 Habilita la generación de perfiles entre procesos. Los nombres de opción **CrossSession** y **CS** son compatibles.  
  
 **User:**[`domain\`]`username`  
 Permite el acceso de cliente al monitor desde la cuenta especificada.  
  
 **WinCounter:** `Path` [**Automark**:`n`]  
 **WinCounter** especifica un contador de rendimiento de Windows para incluirlo como una marca en el archivo de datos de generación de perfiles. **AutoMark** especifica el intervalo en milisegundos entre las recopilaciones del archivo de datos.  
  
## <a name="invalid-options"></a>Opciones no válidas  
 Las siguientes opciones no pueden usarse con la opción **Iniciar** en una línea de comandos.  
  
 **Status**  
 **Status** se aplica a los procesos de los que se generan perfiles. Muestra los procesos y subprocesos y su estado de perfil actual (On/Off). Por ejemplo, si se detiene un proceso, **Status** no lo indicará en el informe. **Status** mostrará que ya se han generado perfiles del proceso o no.  
  
 **Shutdown**[**:**`Timeout`]  
 Desactiva el generador de perfiles.  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo se muestra cómo utilizar la opción **Iniciar** de VSPerfCmd.exe para inicializar el generador de perfiles.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
```  
  
## <a name="see-also"></a>Vea también  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Generar perfiles para aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Generar perfiles para aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Generar perfiles de servicios](../profiling/command-line-profiling-of-services.md)