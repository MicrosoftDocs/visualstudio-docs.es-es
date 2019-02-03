---
title: Funciones de enlace de bloque cliente | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.hooks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- client blocks, validating and reporting data
- debugging [C++], hook functions
- _CrtSetDumpClient function
- client blocks, hook functions
- hooks, client block
ms.assetid: f21c197e-565d-4e3f-9b27-4c018c9b87fc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7b0e70e559dc75abd6b8de1b325b9ac300055792
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55039272"
---
# <a name="client-block-hook-functions"></a>Funciones de enlace con los bloques de tipo cliente
Si desea validar o informar del contenido de los datos almacenados en bloques `_CLIENT_BLOCK`, puede escribir una función específicamente para ello. Esta función debe tener un prototipo similar al siguiente, como se define en CRTDBG.H:  

```cpp
void YourClientDump(void *, size_t)  
```  

 En otras palabras, la función de enlace debería aceptar un puntero **void**al inicio del bloque de asignación, junto con un valor de tipo **size_t** que indique el tamaño de la asignación y devuelva `void`. Aparte de eso, el contenido se puede elegir libremente.  

 Una vez instalada la función de enlace mediante [_CrtSetDumpClient](/cpp/c-runtime-library/reference/crtsetdumpclient), recibirá una llamada cada vez que se realice un volcado de un bloque `_CLIENT_BLOCK`. Se puede, entonces, utilizar [_CrtReportBlockType](/cpp/c-runtime-library/reference/crtreportblocktype) para obtener información del tipo o subtipo de los bloques volcados.  

 El puntero a la función que se pasó a `_CrtSetDumpClient` es del tipo **_CRT_DUMP_CLIENT**, según se define en CRTDBG.H:  

```cpp
typedef void (__cdecl *_CRT_DUMP_CLIENT)  
   (void *, size_t);  
```  

## <a name="see-also"></a>Vea también  
 [Creación de funciones de enlace de depuración](../debugger/debug-hook-function-writing.md)   
 [crt_dbg2 Sample](https://msdn.microsoft.com/library/21e1346a-6a17-4f57-b275-c76813089167)   
 [_CrtReportBlockType](/cpp/c-runtime-library/reference/crtreportblocktype)
