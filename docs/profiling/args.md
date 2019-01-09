---
title: Args | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 20c35949-1f29-4282-ac75-4e6c237d71bc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 40de97d134f24832c56b0cda7b8462a3f8f8c937
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53845543"
---
# <a name="args"></a>Args
La opción **Args** de VSPerfCmd.exe especifica una lista de argumentos que se pasan a la aplicación de destino del subcomando **Launch**.  
  
 **Args** solo puede utilizarse cuando **Launch** también se especifica en la línea de comandos. **Args** es opcional si se especifica **Launch**.  
  
## <a name="syntax"></a>Sintaxis  
  
```cmd  
VSPerfCmd.exe /Launch:AppName /Args:Arguments [Options]  
```  
  
#### <a name="parameters"></a>Parámetros  
 `Arguments`  
 Una lista de argumentos para la aplicación de destino del comando **Launch**.  
  
## <a name="required-options"></a>Opciones necesarias  
 **Launch:** `AppName`  
 inicia la aplicación especificada y comienza la generación de perfiles con el método de muestreo.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se utiliza la opción **Args** para pasar argumentos a TestApp.exe.  
  
```cmd  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /Args:"123, 'Hello World'"  
```  
  
## <a name="see-also"></a>Vea también  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Generación de perfiles de aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Generación de perfiles de aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Generar perfiles para servicios](../profiling/command-line-profiling-of-services.md)