---
title: Funciones de enlace de bloque cliente | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.hooks
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- client blocks, validating and reporting data
- debugging [C++], hook functions
- _CrtSetDumpClient function
- client blocks, hook functions
- hooks, client block
ms.assetid: f21c197e-565d-4e3f-9b27-4c018c9b87fc
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3eb0891911e5dacbad2447ba3d141a81286e7dc8
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58997016"
---
# <a name="client-block-hook-functions"></a>Funciones de enlace con los bloques de tipo cliente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si desea validar o informar del contenido de los datos almacenados en bloques `_CLIENT_BLOCK`, puede escribir una función específicamente para ello. Esta función debe tener un prototipo similar al siguiente, como se define en CRTDBG.H:  
  
```  
void YourClientDump(void *, size_t)  
  
```  
  
 En otras palabras, la función de enlace debería aceptar un puntero **void**al inicio del bloque de asignación, junto con un valor de tipo **size_t** que indique el tamaño de la asignación y devuelva `void`. Aparte de eso, el contenido se puede elegir libremente.  
  
 Una vez instalada la función de enlace mediante [_CrtSetDumpClient](http://msdn.microsoft.com/library/f3dd06d0-c331-4a12-b68d-25378d112033), recibirá una llamada cada vez que se realice un volcado de un bloque `_CLIENT_BLOCK`. Se puede, entonces, utilizar [_CrtReportBlockType](http://msdn.microsoft.com/library/0f4b9da7-bebb-4956-9541-b2581640ec6b) para obtener información del tipo o subtipo de los bloques volcados.  
  
 El puntero a la función que se pasó a `_CrtSetDumpClient` es del tipo **_CRT_DUMP_CLIENT**, según se define en CRTDBG.H:  
  
```  
typedef void (__cdecl *_CRT_DUMP_CLIENT)  
   (void *, size_t);  
```  
  
## <a name="see-also"></a>Vea también  
 [Creación de funciones de enlace de depuración](../debugger/debug-hook-function-writing.md)   
 [Ejemplo crt_dbg2](http://msdn.microsoft.com/21e1346a-6a17-4f57-b275-c76813089167)   
 [_CrtReportBlockType](http://msdn.microsoft.com/library/0f4b9da7-bebb-4956-9541-b2581640ec6b)
