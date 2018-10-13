---
title: Output | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5e286e61-4548-42cf-a635-e608c5edbe2b
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5de5cd907d786b21e7f1a279fec51208b83185a8
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49292349"
---
# <a name="output"></a>Salida
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La opción **Output** especifica el nombre del archivo de datos de generación de perfiles para la sesión de rendimiento. **Output** debe usarse con la opción **Start**.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
VSPerfCmd.exe /Start:Method /Output:FileName [Options]  
```  
  
#### <a name="parameters"></a>Parámetros  
 `FileName`  
 Nombre del archivo de datos. Se aceptan rutas de acceso completas y parciales. Si no se especifica una ruta de acceso, el archivo se crea en el directorio actual.  
  
## <a name="required-options"></a>Opciones necesarias  
 La opción **Output** debe usarse con la opción **Start**.  
  
 **Start:** `Method`  
 Especifica el nombre del archivo de salida.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente, el archivo de datos de generación de perfiles se crea en el directorio actual.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
```  
  
## <a name="see-also"></a>Vea también  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Generar perfiles para aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Generar perfiles para aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Generar perfiles de servicios](../profiling/command-line-profiling-of-services.md)



