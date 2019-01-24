---
title: Funciones de enlace de bloque cliente | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: 2b16dc9eaff974e98e411d4f49d8aed6f9f656e8
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51773943"
---
# <a name="client-block-hook-functions"></a>Funciones de enlace con los bloques de tipo cliente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si desea validar o informar del contenido de los datos almacenados en bloques `_CLIENT_BLOCK`, puede escribir una función específicamente para ello. Esta función debe tener un prototipo similar al siguiente, como se define en CRTDBG.H:  
  
```  
void YourClientDump(void *, size_t)  
  
```  
  
 En otras palabras, debe aceptar la función de enlace un **void** puntero al principio del bloque de asignación, junto con un **size_t** tipo de valor que indica el tamaño de la asignación y devuelven `void`. Aparte de eso, el contenido se puede elegir libremente.  
  
 Una vez haya instalado la función de enlace mediante [_CrtSetDumpClient](http://msdn.microsoft.com/library/f3dd06d0-c331-4a12-b68d-25378d112033), se llamará cada vez un `_CLIENT_BLOCK` se vuelca el bloque. A continuación, puede usar [_CrtReportBlockType](http://msdn.microsoft.com/library/0f4b9da7-bebb-4956-9541-b2581640ec6b) para obtener información sobre el tipo o subtipo de los bloques.  
  
 El puntero a la función que se pasa a `_CrtSetDumpClient` es de tipo **_CRT_DUMP_CLIENT**, tal como se define en CRTDBG. H:  
  
```  
typedef void (__cdecl *_CRT_DUMP_CLIENT)  
   (void *, size_t);  
```  
  
## <a name="see-also"></a>Vea también  
 [Función de enlace de depuración](../debugger/debug-hook-function-writing.md)   
 [Ejemplo crt_dbg2](http://msdn.microsoft.com/en-us/21e1346a-6a17-4f57-b275-c76813089167)   
 [_CrtReportBlockType](http://msdn.microsoft.com/library/0f4b9da7-bebb-4956-9541-b2581640ec6b)



