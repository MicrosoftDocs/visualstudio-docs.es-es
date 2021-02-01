---
title: Consola | Microsoft Docs
description: Use la opción Console de VSPerfCmd.exe para iniciar la aplicación especificada en una nueva ventana del símbolo del sistema. Debe usarse con la opción Launch.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: e825ba66-1383-46ad-8712-396bc9c14036
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 93c39bfb503bec9858e33b7acf04e0f0433264b9
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2021
ms.locfileid: "98720910"
---
# <a name="console"></a>Consola
La opción **Consola** de VSPerfCmd.exe inicia la aplicación especificada en una nueva ventana del símbolo del sistema. **Consola** solo puede utilizarse con la opción **Launch** de VSPerfCmd. Si la aplicación no es una aplicación de línea de comandos, **Consola** no tiene ningún efecto.

## <a name="syntax"></a>Sintaxis

```cmd
VSPerfCmd.exe /Launch:AppName /Console
```

#### <a name="parameters"></a>Parámetros
 None

## <a name="required-options"></a>Opciones necesarias
 **Consola** solo se puede especificar en una línea de comandos que también contenga la opción **Launch**.

 **Launch:** `AppName` Inicia el generador de perfiles y la aplicación especificada por `AppName`.

## <a name="see-also"></a>Vea también
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Generar perfiles de aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Generación de perfiles de aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Generar perfiles para servicios](../profiling/command-line-profiling-of-services.md)
