---
title: "Cómo depurar funciones de la API de Windows | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 66ed3dbd6c67fe247ea514a9d41780584ae8f1e2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="how-can-i-debug-windows-api-functions"></a>Cómo depurar funciones de la API de Windows
Si desea depurar una función de la API de Windows que tiene símbolos de NT cargados, deberá hacer lo siguiente.  
  
### <a name="to-set-a-breakpoint-on-a-windows-api-function-with-nt-symbols-loaded"></a>Para establecer un punto de interrupción en una función API de Windows con símbolos de NT cargados  
  
-   Escriba el nombre de la función junto con el nombre del archivo DLL en el que se encuentra la función. En el código de 32 bits, utilice el formato representativo del nombre de la función. Para establecer un punto de interrupción en **MessageBeep**, por ejemplo, debe especificar lo siguiente.  
  
    ```  
    {,,USER32.DLL}_MessageBeep@4  
    ```  
  
     Para obtener el nombre representativo, vea [ver nombres representativos](http://msdn.microsoft.com/en-us/f79e2717-a4db-4d12-a689-69830cce2be0).  
  
## <a name="see-also"></a>Vea también  
 [Preguntas frecuentes sobre depuración de código nativo](../debugger/debugging-native-code-faqs.md)   
 [Depuración de código nativo](../debugger/debugging-native-code.md)