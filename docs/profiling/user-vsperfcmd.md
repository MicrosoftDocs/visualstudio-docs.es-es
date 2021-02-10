---
title: User (VSPerfCmd) | Microsoft Docs
description: Obtenga más información sobre cómo la opción User especifica el dominio y el nombre de usuario de la cuenta propietaria del proceso para el que se han generado perfiles.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ee1a478e-374d-4f30-ae28-d260b9d4723a
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b0240a4dcf0830dca6667bcbd055d677ef7bc204
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99886007"
---
# <a name="user-vsperfcmd"></a>User (VSPerfCmd)
La opción **User** especifica el dominio y el nombre de usuario de la cuenta propietaria del proceso para el que se han generado perfiles. Esta opción solamente es necesaria si el proceso se está ejecutando como otro usuario distinto del usuario que inició sesión. El propietario del proceso se muestra en la columna Nombre de usuario de la pestaña **Procesos** del Administrador de tareas de Windows.

 La opción **User** solo se puede especificar en una línea de comandos que también contenga la opción **Start**.

## <a name="syntax"></a>Sintaxis

```cmd
VSPerfCmd.exe /Start:Method /Output:FileName /User:[Domain\]UserName [Options]
```

#### <a name="parameters"></a>Parámetros
 `Domain` Nombre del dominio de usuario.

 `UserName` Nombre del usuario.

## <a name="required-options"></a>Opciones necesarias
 La opción **User** solo se puede usar con la opción **Start**.

 **Start:** `Method` Inicializa el generador de perfiles en el método de generación de perfiles especificado.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra el uso de la opción **User**.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /User:SYSTEM
```

## <a name="see-also"></a>Vea también
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Generar perfiles de aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Generación de perfiles de aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Generar perfiles para servicios](../profiling/command-line-profiling-of-services.md)
