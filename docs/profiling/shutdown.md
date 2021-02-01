---
title: Apagar | Microsoft Docs
description: Obtenga más información sobre cómo la opción Shutdown espera a que termine o se desasocie cualquier proceso del que se generaron perfiles y, después, desactiva el generador de perfiles y cierra el archivo de datos de generación de perfiles.
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: a1e37500-4ad1-4670-9737-3d9a20536386
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: c7a0bf796c91ce339c82f7f698ed63afe90f9c1c
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2021
ms.locfileid: "98720077"
---
# <a name="shutdown"></a>Shutdown
La opción **Apagar** espera a que termine o se desasocie cualquier proceso del que se generaron perfiles y, después, desactiva el generador de perfiles y cierra el archivo de datos de generación de perfiles. La opción **Apagar** debe ser el último comando de una ejecución de generación de perfiles.

 Si no se especifica ningún parámetro de tiempo de espera, la opción **Apagar** esperará indefinidamente. Si se especifica un parámetro de tiempo de espera, la opción vuelve tras el número de segundos especificado sin desactivar el generador de perfiles ni cerrar el archivo de datos.

 La opción **Apagar** debe ser la única especificada en la línea de comandos.

## <a name="syntax"></a>Sintaxis

```cmd
VSPerfCmd.exe /Shutdown[:Timeout]
```

#### <a name="parameters"></a>Parámetros
`Timeout`
- (Opcional) Si se especifica, la opción vuelve tras el número de segundos especificado sin desactivar el generador de perfiles ni cerrar el archivo de datos de generación de perfiles.

## <a name="see-also"></a>Vea también
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Generar perfiles de aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Generación de perfiles de aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Generar perfiles para servicios](../profiling/command-line-profiling-of-services.md)
