---
title: Apagar | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: a1e37500-4ad1-4670-9737-3d9a20536386
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 045f84542334b16d7e3d57fb48099e61f144cadd
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54992339"
---
# <a name="shutdown"></a>Apagar
La opción **Apagar** espera a que termine o se desasocie cualquier proceso del que se generaron perfiles y, después, desactiva el generador de perfiles y cierra el archivo de datos de generación de perfiles. La opción **Apagar** debe ser el último comando de una ejecución de generación de perfiles.  
  
 Si no se especifica ningún parámetro de tiempo de espera, la opción **Apagar** esperará indefinidamente. Si se especifica un parámetro de tiempo de espera, la opción vuelve tras el número de segundos especificado sin desactivar el generador de perfiles ni cerrar el archivo de datos.  
  
 La opción **Apagar** debe ser la única especificada en la línea de comandos.  
  
## <a name="syntax"></a>Sintaxis  
  
```cmd  
VSPerfCmd.exe /Shutdown[:Timeout]  
```  
  
#### <a name="parameters"></a>Parámetros  
 `Timeout`  
 -   (Opcional) Si se especifica, la opción vuelve tras el número de segundos especificado sin desactivar el generador de perfiles ni cerrar el archivo de datos de generación de perfiles.  
  
## <a name="see-also"></a>Vea también  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Generación de perfiles de aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Generación de perfiles de aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Generar perfiles para servicios](../profiling/command-line-profiling-of-services.md)