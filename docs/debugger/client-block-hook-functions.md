---
title: Funciones de enlace con los bloques de tipo cliente | Microsoft Docs
description: Escriba una función de enlace con bloques de tipo cliente para validar el contenido de los datos almacenados en bloques _CLIENT_BLOCK o informar sobre él.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0378f2260a9bf71cf7ac1192b7eb7a2259d8ace2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99865883"
---
# <a name="client-block-hook-functions"></a>Funciones de enlace con los bloques de tipo cliente
Si desea validar o informar del contenido de los datos almacenados en bloques `_CLIENT_BLOCK`, puede escribir una función específicamente para ello. Esta función debe tener un prototipo similar al siguiente, como se define en CRTDBG.H:

```cpp
void YourClientDump(void *, size_t)
```

 En otras palabras, la función de enlace debería aceptar un puntero **void** al inicio del bloque de asignación, junto con un valor de tipo **size_t** que indique el tamaño de la asignación y devuelva `void`. Aparte de eso, el contenido se puede elegir libremente.

 Una vez instalada la función de enlace mediante [_CrtSetDumpClient](/cpp/c-runtime-library/reference/crtsetdumpclient), recibirá una llamada cada vez que se realice un volcado de un bloque `_CLIENT_BLOCK`. Se puede, entonces, utilizar [_CrtReportBlockType](/cpp/c-runtime-library/reference/crtreportblocktype) para obtener información del tipo o subtipo de los bloques volcados.

 El puntero a la función que se pasó a `_CrtSetDumpClient` es del tipo **_CRT_DUMP_CLIENT**, según se define en CRTDBG.H:

```cpp
typedef void (__cdecl *_CRT_DUMP_CLIENT)
   (void *, size_t);
```

## <a name="see-also"></a>Vea también

- [Creación de funciones de enlace de depuración](../debugger/debug-hook-function-writing.md)
- [Ejemplo crt_dbg2](/previous-versions/b31tft51(v=vs.100))
- [_CrtReportBlockType](/cpp/c-runtime-library/reference/crtreportblocktype)