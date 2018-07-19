---
title: Cómo depurar funciones de la API de Windows | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.api
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], Windows API functions
- NT symbols and debugging Windows API functions
- Windows API functions, debugging
- Windows API, debugging API functions
- APIs, debugging
ms.assetid: 7c126f57-62ab-4d94-9805-632d696ba1f0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 042f243c0469b8b37e301cf5c9f2410cf201f7be
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/27/2018
ms.locfileid: "37058617"
---
# <a name="how-can-i-debug-windows-api-functions"></a>Cómo depurar funciones de la API de Windows
Si desea depurar una función de la API de Windows que tiene símbolos de NT cargados, deberá hacer lo siguiente.  
  
### <a name="to-set-a-breakpoint-on-a-windows-api-function-with-nt-symbols-loaded"></a>Para establecer un punto de interrupción en una función API de Windows con símbolos de NT cargados  
  
-   Escriba el nombre de la función junto con el nombre del archivo DLL en el que se encuentra la función. En el código de 32 bits, utilice el formato representativo del nombre de la función. Para establecer un punto de interrupción en **MessageBeep**, por ejemplo, debe especificar lo siguiente.  
  
    ```cpp
    {,,USER32.DLL}_MessageBeep@4  
    ```  
  
     Para obtener el nombre representativo, vea [ver nombres representativos](http://msdn.microsoft.com/en-us/f79e2717-a4db-4d12-a689-69830cce2be0).  
  
## <a name="see-also"></a>Vea también  
 [Preguntas frecuentes sobre depuración de código nativo](../debugger/debugging-native-code-faqs.md)   
 [Depuración de código nativo](../debugger/debugging-native-code.md)
