---
title: WaitStart | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6c737177-2dfb-4150-963e-a49ac9aaa591
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 13f52c2c9449b8f1abdc51fca9c9f989163a2a39
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51760291"
---
# <a name="waitstart"></a>WaitStart
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La opción WaitStart hace que el subcomando Start de VSPerfCmd.exe solo se devuelva cuando el generador de perfiles se ha inicializado o cuando ha pasado el número de segundos especificado. De forma predeterminada, el comando Start se devuelve inmediatamente. Si se devuelve el subcomando Start sin inicializar el generador de perfiles, se muestra un error. Si no se especifica el número de segundos, el comando Start espera indefinidamente.  
  
 La opción WaitStart es útil en los archivos por lotes para asegurar que el generador de perfiles se ha inicializado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
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
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /WaitStart:5  
if not %errorlevel% 0 goto :error_tag  
VSPerfCmd.exe /Launch:TestApp.exe  
goto :end  
:error_tag  
@echo Could not start Profiler!  
@echo Error %errorlevel%  
:end  
```



