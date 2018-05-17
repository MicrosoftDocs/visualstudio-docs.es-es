---
title: WinCounter | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: ff319ffc-f249-4c3f-9eb2-06e392e3ae80
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4751d44afc2f54ea57866e3674a5bc150444088b
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/11/2018
---
# <a name="wincounter"></a>WinCounter
La opción **WinCounter** especifica un contador de rendimiento de aplicaciones o de Windows para recopilar en intervalos establecidos durante la ejecución de perfiles. Los contadores de rendimiento de aplicaciones y de Windows se muestran como marcas en el archivo de datos de generación de perfiles. Puede especificar varios contadores de rendimiento para recopilar en opciones independientes.  
  
 De forma predeterminada, los contadores se recopilan cada 500 milisegundos. Use la opción **AutoMark** para especificar un intervalo de recopilación diferente.  
  
 Solo se usa una opción **AutoMark**. Si se especifican varias opciones **AutoMark**, se usa la última de ellas.  
  
 La opción **WinCounter** solo se puede usar con la opción **Start**.  
  
## <a name="syntax"></a>Sintaxis  
  
```cmd  
VSPerfCmd.exe /Start:Method /Wincounter:Path [/WinCounter:Path] [AutoMark:Milliseconds] [Options]  
```  
  
#### <a name="parameters"></a>Parámetros  
 `Path`  
 Contador de rendimiento de Windows en formato de ruta de acceso de contador PDH.  
  
## <a name="required-options"></a>Opciones necesarias  
 La opción **WinCounter** solo se puede usar con la opción **Start**.  
  
 **Start:** `Method`  
 La opción **Start** inicializa el generador de perfiles en el método de generación de perfiles especificado.  
  
## <a name="exclusive-options"></a>Opciones exclusivas  
 La opción **AutoMark** solo se puede usar con la opción **WinCounter**.  
  
 **AutoMark:** `Milliseconds`  
 Especifica el número de milisegundos entre la recopilación de datos de contadores de rendimiento de Windows.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente, se especifican dos contadores de rendimiento de Windows para que se recopilen en un intervalo de 1 000 milisegundos.  
  
```cmd  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /WinCounter:"\Processor(0)\% Processor Time" /WinCounter:"\System\Context Switches/sec" /AutoMark:1000  
```  
  
## <a name="see-also"></a>Vea también  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Generar perfiles para aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Generar perfiles para aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Generar perfiles de servicios](../profiling/command-line-profiling-of-services.md)