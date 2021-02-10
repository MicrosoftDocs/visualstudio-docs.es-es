---
title: WaitStart | Microsoft Docs
description: Obtenga más información sobre el hecho de que la opción WaitStart hace que el subcomando Start de VSPerfCmd.exe solo se devuelva cuando el generador de perfiles se ha inicializado o cuando ha pasado el número de segundos especificado.
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 6c737177-2dfb-4150-963e-a49ac9aaa591
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b883ae215854994918419fb311d94ad921989740
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99911474"
---
# <a name="waitstart"></a>WaitStart
La opción WaitStart hace que el subcomando Start de *VSPerfCmd.exe* solo se devuelva cuando el generador de perfiles se ha inicializado o cuando ha pasado el número de segundos especificado. De forma predeterminada, el comando Start se devuelve inmediatamente. Si se devuelve el subcomando Start sin inicializar el generador de perfiles, se muestra un error. Si no se especifica el número de segundos, el comando Start espera indefinidamente.

 La opción WaitStart es útil en los archivos por lotes para asegurar que el generador de perfiles se ha inicializado.

## <a name="syntax"></a>Sintaxis

```cmd
VSPerfCmd.exe /Start:Method /Output:FileName[Options] /WaitStart[:Seconds]
```

#### <a name="parameters"></a>Parámetros
 `Seconds` El número de segundos que hay que esperar antes de regresar del subcomando Start.

## <a name="required-options"></a>Opciones necesarias
 La opción de WaitStart solo se puede utilizar con el subcomando Start.

 **Salida:** `filename` Especifica el nombre del archivo de salida.

## <a name="remarks"></a>Comentarios

## <a name="example"></a>Ejemplo
 El comando Start esperará 5 segundos a que el generador de perfiles se inicialice en este ejemplo del archivo por lotes.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /WaitStart:5
if not %errorlevel% 0 goto :error_tag
VSPerfCmd.exe /Launch:TestApp.exe
goto :end
:error_tag
@echo Could not start Profiler!
@echo Error %errorlevel%
:end
```
