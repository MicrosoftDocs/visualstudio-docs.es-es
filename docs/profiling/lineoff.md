---
title: LineOff | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 76082063-20ef-47ae-ad64-81b43b654865
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ba5d8c3e2644c94a4e15115661341a34c9e6f761
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/07/2018
ms.locfileid: "34845433"
---
# <a name="lineoff"></a>LineOff
De forma predeterminada, el generador de perfiles recopila el número de línea del código fuente y los datos de desplazamiento del número de línea al usar el método de generación de perfiles de muestreo. La opción VSPerfCmd **LineOff** deshabilita la recopilación de datos de número de línea cuando se usa VSPerfCmd para iniciar la aplicación. Los datos de generación de perfiles se recopilan en el nivel de la función cuando se especifica **LineOff**.  
  
 Puede usar **LineOff** solo con la opción **Launch** y solo cuando el generador de perfiles se ha inicializado para el muestreo mediante la opción **Launch**:**Sample**.  
  
## <a name="syntax"></a>Sintaxis  
  
```cmd  
VSPerfCmd.exe /Launch:AppName /LineOff [Options]  
```  
  
#### <a name="parameters"></a>Parámetros  
 Ninguna  
  
## <a name="required-options"></a>Opciones necesarias  
 La opción **LineOff** solo se puede usar en una línea de comandos que contenga la opción **Launch**.  
  
 **Launch:** `AppName`  
 inicia la aplicación especificada y comienza la generación de perfiles con el método de muestreo.  
  
## <a name="example"></a>Ejemplo  
 Este ejemplo inicia la aplicación y el generador de perfiles, y deshabilita el muestreo en el nivel de línea.  
  
```cmd  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /LineOff  
```  
  
## <a name="see-also"></a>Vea también  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Generación de perfiles de aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Generación de perfiles de aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Generar perfiles para servicios](../profiling/command-line-profiling-of-services.md)