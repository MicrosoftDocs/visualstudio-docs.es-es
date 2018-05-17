---
title: Consola | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: e825ba66-1383-46ad-8712-396bc9c14036
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e7fb90261453caab8dbe54fce79605c1d891d537
ms.sourcegitcommit: eefffa7ebe339d1297cdc12f51a813e7849d7e95
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/14/2018
---
# <a name="console"></a>Consola
La opción **Consola** de VSPerfCmd.exe inicia la aplicación especificada en una nueva ventana del símbolo del sistema. **Consola** solo puede utilizarse con la opción **Launch** de VSPerfCmd. Si la aplicación no es una aplicación de línea de comandos, **Consola** no tiene ningún efecto.  
  
## <a name="syntax"></a>Sintaxis  
  
```cmd  
VSPerfCmd.exe /Launch:AppName /Console  
```  
  
#### <a name="parameters"></a>Parámetros  
 Ninguna  
  
## <a name="required-options"></a>Opciones necesarias  
 **Consola** solo se puede especificar en una línea de comandos que también contenga la opción **Launch**.  
  
 **Launch:** `AppName`  
 Inicia el generador de perfiles y la aplicación especificada por `AppName`.  
  
## <a name="see-also"></a>Vea también  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Generar perfiles para aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Generar perfiles para aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Generar perfiles de servicios](../profiling/command-line-profiling-of-services.md)