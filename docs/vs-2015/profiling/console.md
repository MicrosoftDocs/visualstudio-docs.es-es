---
title: Consola | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: e825ba66-1383-46ad-8712-396bc9c14036
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e947fb28c92323f0d4d66c697c272699fc63450e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68161317"
---
# <a name="console"></a>Consola
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La opción **Consola** de VSPerfCmd.exe inicia la aplicación especificada en una nueva ventana del símbolo del sistema. **Consola** solo puede utilizarse con la opción **Launch** de VSPerfCmd. Si la aplicación no es una aplicación de línea de comandos, **Consola** no tiene ningún efecto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
VSPerfCmd.exe /Launch:AppName /Console  
```  
  
#### <a name="parameters"></a>Parámetros  
 None  
  
## <a name="required-options"></a>Opciones necesarias  
 **Consola** solo se puede especificar en una línea de comandos que también contenga la opción **Launch**.  
  
 **Launch:** `AppName`  
 Inicia el generador de perfiles y la aplicación especificada por `AppName`.  
  
## <a name="see-also"></a>Otras referencias  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Generar perfiles para aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Generar perfiles para aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Generar perfiles de servicios](../profiling/command-line-profiling-of-services.md)
