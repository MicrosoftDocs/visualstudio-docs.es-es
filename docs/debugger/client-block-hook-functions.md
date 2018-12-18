---
title: Funciones de enlace de bloque cliente | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
ms.openlocfilehash: e9de7c0533d3ea55e7b78ca645735a60f84e66df
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49938024"
---
# <a name="client-block-hook-functions"></a>Funciones de enlace con los bloques de tipo cliente
Si desea validar o informar del contenido de los datos almacenados en bloques `_CLIENT_BLOCK`, puede escribir una función específicamente para ello. Esta función debe tener un prototipo similar al siguiente, como se define en CRTDBG.H:  

```cpp
void YourClientDump(void *, size_t)  
```  

 En otras palabras, debe aceptar la función de enlace un **void** puntero al principio del bloque de asignación, junto con un **size_t** tipo de valor que indica el tamaño de la asignación y devuelven `void`. Aparte de eso, el contenido se puede elegir libremente.  

 Una vez haya instalado la función de enlace mediante [_CrtSetDumpClient](/cpp/c-runtime-library/reference/crtsetdumpclient), se llamará cada vez un `_CLIENT_BLOCK` se vuelca el bloque. A continuación, puede usar [_CrtReportBlockType](/cpp/c-runtime-library/reference/crtreportblocktype) para obtener información sobre el tipo o subtipo de los bloques.  

 El puntero a la función que se pasa a `_CrtSetDumpClient` es de tipo **_CRT_DUMP_CLIENT**, tal como se define en CRTDBG. H:  

```cpp
typedef void (__cdecl *_CRT_DUMP_CLIENT)  
   (void *, size_t);  
```  

## <a name="see-also"></a>Vea también  
 [Función de enlace de depuración](../debugger/debug-hook-function-writing.md)   
 [Ejemplo crt_dbg2](https://msdn.microsoft.com/library/21e1346a-6a17-4f57-b275-c76813089167)   
 [_CrtReportBlockType](/cpp/c-runtime-library/reference/crtreportblocktype)
