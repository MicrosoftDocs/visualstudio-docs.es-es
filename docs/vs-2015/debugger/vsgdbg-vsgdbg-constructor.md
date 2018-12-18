---
title: VsgDbg::VsgDbg (Constructor) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 670651e6-5e79-4845-b0c2-671beb7055a8
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 056c5f5e19a4d1e025969aa40ad75f3852b4201b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51781925"
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
 Es `true` para especificar que el componente de aplicación de diagnóstico de gráficos debe estar preparado para capturar y grabar activamente información de gráficos; es `false` para especificar que la aplicación no se debe preparar para capturar y grabar activamente información de gráficos en este momento.  
  
## <a name="remarks"></a>Comentarios  
 Cuando se llama al constructor con `bDefaultInit` establecido en `true`, el nombre de archivo del archivo de registro de gráficos viene determinada por el modo `DONT_SAVE_VSGLOG_TO_TEMP` y `VSG_DEFAULT_RUN_FILENAME` se definen los símbolos de preprocesador antes `vsgcapture.h` se incluye en la aplicación.  
  
 Cuando se llama al constructor con `bDefaultInit` establecido en `false`, el componente de aplicación de diagnóstico de gráficos se puede preparar para capturar y grabar activamente información de gráficos en otro momento llamando a la función `Init`.  
  
## <a name="see-also"></a>Vea también  
 [VsgDbg:: ~ VsgDbg (Destructor)](../debugger/vsgdbg-tilde-vsgdbg-destructor.md)   
 [Init](../debugger/init.md)   
 [DONT_SAVE_VSGLOG_TO_TEMP](../debugger/dont-save-vsglog-to-temp.md)   
 [VSG_DEFAULT_RUN_FILENAME](../debugger/vsg-default-run-filename.md)



