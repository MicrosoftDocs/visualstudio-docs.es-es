---
title: User (VSPerfCmd) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ee1a478e-374d-4f30-ae28-d260b9d4723a
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5c6c442da6bad7ce2a718b58c98bae8cd559576a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="user-vsperfcmd"></a>User (VSPerfCmd)
La opción **User** especifica el dominio y el nombre de usuario de la cuenta propietaria del proceso para el que se han generado perfiles. Esta opción solamente es necesaria si el proceso se está ejecutando como otro usuario distinto del usuario que inició sesión. El propietario del proceso se muestra en la columna Nombre de usuario de la pestaña Procesos del Administrador de tareas de Windows.  
  
 La opción **User** solo se puede especificar en una línea de comandos que también contenga la opción **Start**.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
VSPerfCmd.exe /Start:Method /Output:FileName /User:[Domain\]UserName [Options]  
```  
  
#### <a name="parameters"></a>Parámetros  
 `Domain`  
 Nombre del dominio de usuario.  
  
 `UserName`  
 Nombre del usuario.  
  
## <a name="required-options"></a>Opciones necesarias  
 La opción **User** solo se puede usar con la opción **Start**.  
  
 **Start:** `Method`  
 Inicializa el generador de perfiles en el método de generación de perfiles especificado.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el uso de la opción **User**.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /User:SYSTEM  
```  
  
## <a name="see-also"></a>Vea también  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Generar perfiles para aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Generar perfiles para aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Generar perfiles de servicios](../profiling/command-line-profiling-of-services.md)