---
title: LineOff | Microsoft Docs
description: Obtenga más información sobre cómo la opción VSPerfCmd LineOff deshabilita la recopilación de datos de número de línea cuando se usa VSPerfCmd para iniciar la aplicación.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 76082063-20ef-47ae-ad64-81b43b654865
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 45ec3592049e00d6a492c489e8fb60254003ac6d
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2021
ms.locfileid: "98721416"
---
# <a name="lineoff"></a>LineOff
De forma predeterminada, el generador de perfiles recopila el número de línea del código fuente y los datos de desplazamiento del número de línea al usar el método de generación de perfiles de muestreo. La opción VSPerfCmd **LineOff** deshabilita la recopilación de datos de número de línea cuando se usa VSPerfCmd para iniciar la aplicación. Los datos de generación de perfiles se recopilan en el nivel de la función cuando se especifica **LineOff**.

 Puede usar **LineOff** solo con la opción **Launch** y solo cuando el generador de perfiles se ha inicializado para el muestreo mediante la opción **Launch**:**Sample**.

## <a name="syntax"></a>Sintaxis

```cmd
VSPerfCmd.exe /Launch:AppName /LineOff [Options]
```

#### <a name="parameters"></a>Parámetros
 None

## <a name="required-options"></a>Opciones necesarias
 La opción **LineOff** solo se puede usar en una línea de comandos que contenga la opción **Launch**.

 **Launch:** `AppName` Inicia la aplicación especificada y comienza la generación de perfiles con el método de muestreo.

## <a name="example"></a>Ejemplo
 Este ejemplo inicia la aplicación y el generador de perfiles, y deshabilita el muestreo en el nivel de línea.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /LineOff
```

## <a name="see-also"></a>Vea también
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Generar perfiles de aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Generación de perfiles de aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Generar perfiles para servicios](../profiling/command-line-profiling-of-services.md)
