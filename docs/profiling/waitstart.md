---
title: WaitStart | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 6c737177-2dfb-4150-963e-a49ac9aaa591
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8271d28c21bc26c96c1481a114b2f5a322b148b4
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/11/2018
---
# <a name="waitstart"></a>WaitStart
La opción WaitStart hace que el subcomando Start de VSPerfCmd.exe solo se devuelva cuando el generador de perfiles se ha inicializado o cuando ha pasado el número de segundos especificado. De forma predeterminada, el comando Start se devuelve inmediatamente. Si se devuelve el subcomando Start sin inicializar el generador de perfiles, se muestra un error. Si no se especifica el número de segundos, el comando Start espera indefinidamente.  
  
 La opción WaitStart es útil en los archivos por lotes para asegurar que el generador de perfiles se ha inicializado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cmd  
VSPerfCmd.exe /Start:Method /Output:FileName[Options] /StartWait[:Seconds]  
```  
  
#### <a name="parameters"></a>Parámetros  
 `Seconds`  
 El número de segundos que hay que esperar antes de regresar del subcomando Start.  
  
## <a name="required-options"></a>Opciones necesarias  
 La opción de WaitStart solo se puede utilizar con el subcomando Start.  
  
 **Salida:** `filename`  
 Especifica el nombre del archivo de salida.  
  
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