---
title: GC (VSPerfCmd) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7c81e88b-a748-4cf5-a7a1-3429608e1b54
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a97b45c9bc9db61e579430bb3e2ceeb48206ef50
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54992456"
---
# <a name="gc-vsperfcmd"></a>GC (VSPerfCmd)
La opción **GC** habilita la recopilación de datos de asignación de memoria de .NET Framework y de duración de objetos. La opción **GC** solo puede usarse con el método de generación de perfiles de muestreo y únicamente con la opción **Launch**.  
  
 Al utilizar la opción **GC**, el comando **/sampleon** de VSPerfClrEnv no es necesario.  
  
 Si no se especifica ningún parámetro, o si se especifica el parámetro **Asignación**, solo se recopilan datos de asignación de memoria de .NET Framework. Si se especifica el parámetro **Duración**, se recopilan datos de asignación de memoria de .NET Framework y de duración de objetos de .NET Framework.  
  
## <a name="syntax"></a>Sintaxis  
  
```cmd  
VSPerfCmd.exe /Launch:AppName /GC[:{Allocation|Lifetime}] [Options]  
```  
  
#### <a name="parameters"></a>Parámetros  
 **Asignación**  
 Predeterminado Recopila datos de asignación de memoria de .NET Framework.  
  
 **Duración**  
 Recopila datos de asignación de memoria de .NET Framework y de duración de objetos de .NET Framework.  
  
## <a name="required-options"></a>Opciones necesarias  
 La opción **GC** solo se puede usar con la opción **Launch**.  
  
 **Launch:** `AppName`  
 inicia la aplicación especificada y comienza la generación de perfiles con el método de muestreo.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se inicia una aplicación y se recopilan datos de asignación de memoria de .NET Framework.  
  
```cmd  
VSPerfCmd.exe /Launch:TestApp.exe /gc  
```  
  
## <a name="see-also"></a>Vea también  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Generación de perfiles de aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Generación de perfiles de aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Generar perfiles para servicios](../profiling/command-line-profiling-of-services.md)