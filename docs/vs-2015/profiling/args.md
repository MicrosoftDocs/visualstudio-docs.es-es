---
title: Args | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 20c35949-1f29-4282-ac75-4e6c237d71bc
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ad83466a01b1a9dc1aea406d84d24b81f44458a6
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51788672"
---
# <a name="args"></a>Args
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La opción **Args** de VSPerfCmd.exe especifica una lista de argumentos que se pasan a la aplicación de destino del subcomando **Launch**.  
  
 **Args** solo puede utilizarse cuando **Launch** también se especifica en la línea de comandos. **Args** es opcional si se especifica **Launch**.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
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
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /Args:"123, 'Hello World'"  
```  
  
## <a name="see-also"></a>Vea también  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Generar perfiles para aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Generar perfiles para aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Generar perfiles de servicios](../profiling/command-line-profiling-of-services.md)



