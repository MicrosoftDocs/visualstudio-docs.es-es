---
title: Output | Microsoft Docs
description: Obtenga información sobre cómo la opción Output especifica el nombre del archivo de datos de generación de perfiles para la sesión de rendimiento. Output debe usarse con la opción Start.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 5e286e61-4548-42cf-a635-e608c5edbe2b
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 6067e13e33875be778ff59739f5511c4116937ed
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2021
ms.locfileid: "98722807"
---
# <a name="output"></a>Output
La opción **Output** especifica el nombre del archivo de datos de generación de perfiles para la sesión de rendimiento. **Output** debe usarse con la opción **Start**.

## <a name="syntax"></a>Sintaxis

```cmd
VSPerfCmd.exe /Start:Method /Output:FileName [Options]
```

#### <a name="parameters"></a>Parámetros
 `FileName` Nombre del archivo de datos. Se aceptan rutas de acceso completas y parciales. Si no se especifica una ruta de acceso, el archivo se crea en el directorio actual.

## <a name="required-options"></a>Opciones necesarias
 La opción **Output** debe usarse con la opción **Start**.

 **Start:** `Method` Especifica el nombre del archivo de salida.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente, el archivo de datos de generación de perfiles se crea en el directorio actual.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
```

## <a name="see-also"></a>Vea también
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Generar perfiles de aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Generación de perfiles de aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Generar perfiles para servicios](../profiling/command-line-profiling-of-services.md)
