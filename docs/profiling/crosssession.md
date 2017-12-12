---
title: CrossSession | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b9fcb9c3-7903-478c-9b7c-dbd94092fcba
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 196107019a43f8f76beeb55cde6a56034375b9d9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="crosssession"></a>CrossSession
La opción **CrossSession** de VSPerfCmd.exe permite que el generador de perfiles recopile datos de cualquier sesión de consola. La opción **CrossSession** debe usarse con la opción **Start**.  
  
 Puede usar la abreviatura **CS** en lugar de **CrossSession**.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
VSPerfCmd.exe /Start:Method /CrossSession [Options]  
```  
  
#### <a name="parameters"></a>Parámetros  
 Ninguna  
  
## <a name="valid-options"></a>Opciones válidas  
 Para habilitar la generación de perfiles en otra sesión, la opción **CrossSession** debe especificarse con la opción **Start**. También debe especificarse **CrossSession** en todos los comandos **VSPerfCmd Attach** y **Detach** posteriores.  
  
 **Start:** `Method`  
 La opción **Start** inicializa el generador de perfiles en el método de generación de perfiles especificado.  
  
 **Attach:** *PID*[**,***PID*]  
 Inicia la generación de perfiles de los procesos especificados.  
  
 **Detach**[**:***PID*[,*PID*]]  
 Detiene la generación de perfiles de los procesos especificados.  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo, se usa la opción **CrossSession** para adjuntar a una aplicación que se ha iniciado en otra sesión de consola.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /CrossSession  
VSPerfCmd.exe /Attach:12345 /CS  
```  
  
## <a name="see-also"></a>Vea también  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Generar perfiles para aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Generar perfiles para aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Generar perfiles de servicios](../profiling/command-line-profiling-of-services.md)