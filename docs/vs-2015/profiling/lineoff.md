---
title: LineOff | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76082063-20ef-47ae-ad64-81b43b654865
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 93fe4acedfcae36f75ed38bef102ccc35f08f2ce
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51759679"
---
# <a name="lineoff"></a>LineOff
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

De forma predeterminada, el generador de perfiles recopila el número de línea del código fuente y los datos de desplazamiento del número de línea al usar el método de generación de perfiles de muestreo. La opción VSPerfCmd **LineOff** deshabilita la recopilación de datos de número de línea cuando se usa VSPerfCmd para iniciar la aplicación. Los datos de generación de perfiles se recopilan en el nivel de la función cuando se especifica **LineOff**.  
  
 Puede usar **LineOff** solo con la opción **Launch** y solo cuando el generador de perfiles se ha inicializado para el muestreo mediante la opción **Launch**:**Sample**.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
VSPerfCmd.exe /Launch:AppName /LineOff [Options]  
```  
  
#### <a name="parameters"></a>Parámetros  
 Ninguna  
  
## <a name="required-options"></a>Opciones necesarias  
 La opción **LineOff** solo se puede usar en una línea de comandos que contenga la opción **Launch**.  
  
 **Launch:** `AppName`  
 inicia la aplicación especificada y comienza la generación de perfiles con el método de muestreo.  
  
## <a name="example"></a>Ejemplo  
 Este ejemplo inicia la aplicación y el generador de perfiles, y deshabilita el muestreo en el nivel de línea.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /LineOff  
```  
  
## <a name="see-also"></a>Vea también  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Generar perfiles para aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Generar perfiles para aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Generar perfiles de servicios](../profiling/command-line-profiling-of-services.md)



