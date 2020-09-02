---
title: VsgDbg::VsgDbg (Constructor) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 670651e6-5e79-4845-b0c2-671beb7055a8
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f3bd179aea7d961df6145b7af2f074927fcdc3e3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157438"
---
# <a name="vsgdbgvsgdbg-constructor"></a>VsgDbg::VsgDbg (Constructor)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Construye una instancia de la clase `VsgDbg` con o sin preparar el componente de aplicación de diagnóstico de gráficos para capturar y registrar información de gráficos activamente de forma predeterminada, según el parámetro booleano especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
VsgDbg(  
  bDefaultInit  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `bDefaultInit`  
 `true` para especificar que el componente de aplicación de diagnóstico de gráficos debe estar preparado para capturar y grabar activamente información de gráficos; `false` para especificar que la aplicación no debe estar preparada para capturar y grabar activamente información de gráficos en este momento.  
  
## <a name="remarks"></a>Comentarios  
 Cuando se llama al constructor con `bDefaultInit` establecido en `true`, el nombre de archivo del archivo de registro de gráficos viene determinado por cómo se hayan definido los símbolos de preprocesador `DONT_SAVE_VSGLOG_TO_TEMP` y `VSG_DEFAULT_RUN_FILENAME` antes de incluir `vsgcapture.h` en la aplicación.  
  
 Cuando se llama al constructor con `bDefaultInit` establecido en `false`, el componente de aplicación de diagnóstico de gráficos se puede preparar para capturar y grabar activamente información de gráficos en otro momento llamando a la función `Init`.  
  
## <a name="see-also"></a>Consulte también  
 [Vsgdbg (:: ~ Vsgdbg ((destructor)](../debugger/vsgdbg-tilde-vsgdbg-destructor.md)   
 [Smss](../debugger/init.md)   
 [DONT_SAVE_VSGLOG_TO_TEMP](../debugger/dont-save-vsglog-to-temp.md)   
 [VSG_DEFAULT_RUN_FILENAME](../debugger/vsg-default-run-filename.md)
