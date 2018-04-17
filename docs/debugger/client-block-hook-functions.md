---
title: Las funciones de enlace con los bloques cliente | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 711f7de86617f6574427a65c6efcef62c558306b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="client-block-hook-functions"></a>Funciones de enlace con los bloques de tipo cliente
Si desea validar o informar del contenido de los datos almacenados en bloques `_CLIENT_BLOCK`, puede escribir una función específicamente para ello. Esta función debe tener un prototipo similar al siguiente, como se define en CRTDBG.H:  
  
```  
void YourClientDump(void *, size_t)  
  
```  
  
 En otras palabras, debe aceptar la función de enlace un **void** puntero al principio del bloque de asignación, junto con un **size_t** escriba el valor que indica el tamaño de la asignación y devolver `void`. Aparte de eso, el contenido se puede elegir libremente.  
  
 Después de instalar la función de enlace mediante [_CrtSetDumpClient](/cpp/c-runtime-library/reference/crtsetdumpclient), recibirá una llamada cada vez un `_CLIENT_BLOCK` el volcado de bloque. A continuación, puede usar [_CrtReportBlockType](/cpp/c-runtime-library/reference/crtreportblocktype) para obtener información acerca del tipo o subtipo de los bloques volcados.  
  
 El puntero a la función que se pasa a `_CrtSetDumpClient` es de tipo **_CRT_DUMP_CLIENT**, tal como se define en CRTDBG. H:  
  
```  
typedef void (__cdecl *_CRT_DUMP_CLIENT)  
   (void *, size_t);  
```  
  
## <a name="see-also"></a>Vea también  
 [Creación de funciones de enlace de depuración](../debugger/debug-hook-function-writing.md)   
 [Ejemplo crt_dbg2](http://msdn.microsoft.com/en-us/21e1346a-6a17-4f57-b275-c76813089167)   
 [_CrtReportBlockType](/cpp/c-runtime-library/reference/crtreportblocktype)