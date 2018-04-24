---
title: Output | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 5e286e61-4548-42cf-a635-e608c5edbe2b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: acaf2271357cb33cfaadbe9da653a8f57bd5627d
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="output"></a>Salida
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