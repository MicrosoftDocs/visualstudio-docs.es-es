---
title: VsgDbg::VsgDbg (Constructor) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 670651e6-5e79-4845-b0c2-671beb7055a8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 04f33b117a7ee47fb0c11932c3722f6f2a4a3541
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
ms.locfileid: "31473308"
---
# <a name="vsgdbgvsgdbg-constructor"></a>VsgDbg::VsgDbg (Constructor)
Construye una instancia de la clase `VsgDbg` con o sin preparar el componente de aplicación de diagnóstico de gráficos para capturar y registrar información de gráficos activamente de forma predeterminada, según el parámetro booleano especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
VsgDbg(  
  bDefaultInit  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `bDefaultInit`  
 Es `true` para especificar que el componente de aplicación de diagnóstico de gráficos debe estar preparado para capturar y grabar activamente información de gráficos; es `false` para especificar que la aplicación no se debe preparar para capturar y grabar activamente información de gráficos en este momento.  
  
## <a name="remarks"></a>Comentarios  
 Cuando se llama al constructor con `bDefaultInit` establecido en `true`, el nombre de archivo del archivo de registro de gráficos está determinado por el modo `DONT_SAVE_VSGLOG_TO_TEMP` y `VSG_DEFAULT_RUN_FILENAME` se definen los símbolos de preprocesador antes `vsgcapture.h` se incluye en la aplicación.  
  
 Cuando se llama al constructor con `bDefaultInit` establecido en `false`, el componente de aplicación de diagnóstico de gráficos se puede preparar para capturar y grabar activamente información de gráficos en otro momento llamando a la función `Init`.  
  
## <a name="see-also"></a>Vea también  
 [VsgDbg:: ~ VsgDbg (Destructor)](vsgdbg-tilde-vsgdbg-destructor.md)   
 [Init](init.md)   
 [DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)   
 [VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)