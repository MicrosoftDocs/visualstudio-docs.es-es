---
title: AutoMark | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c4de965e-0364-4f78-9936-1f509e85df74
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8ee6e4beafb21ed7f7695c88fceb8516d5677cdb
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49259267"
---
# <a name="automark"></a>AutoMark
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La opción **AutoMark** especifica el número de milisegundos entre la colección de eventos de los contadores de rendimiento de software de Windows. Los contadores de rendimiento de Windows se especifican en la opción **WinCounter**.  
  
 Solo se puede especificar una opción **AutoMark** en la línea de comandos. Tenga en cuenta que el intervalo de muestreo de **WinCounter** especificado por **AutoMark** es independiente del intervalo de muestreo principal.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
VSPerfCmd.exe /Start:Method /WinCounter:Path /AutoMark:Milliseconds  
```  
  
#### <a name="parameters"></a>Parámetros  
 `Milliseconds`  
 Especifica el número de milisegundos entre las colecciones de eventos de los contadores de rendimiento de Windows.  
  
## <a name="required-options"></a>Opciones necesarias  
 **WinCounter:** `Path`  
 Especifica el contador de rendimiento de Windows que se va a recopilar. Cuando se usa el método de instrumentación, se pueden especificar varios contadores de Windows. Cuando se usa el método de muestreo, solo se puede especificar un contador de Windows. La opción **WinCounter** debe especificarse en una línea de comandos que contenga la opción **Start**.  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo, se establece un intervalo de muestreo de 1000 milisegundos para dos contadores de rendimiento de Windows.  
  
```  
VSPerfCmd.exe /Start:Trace /Output:TestApp.exe.vsp /WinCounter:"\Process(*)\% Processor Time" /WinCounter:"\ASP.NET\Pages/sec" /AutoMark:1000  
VSPerfCmd.exe /Launch:TestApp.exe  
```  
  
## <a name="see-also"></a>Vea también  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Generar perfiles para aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Generar perfiles para aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Generar perfiles de servicios](../profiling/command-line-profiling-of-services.md)



