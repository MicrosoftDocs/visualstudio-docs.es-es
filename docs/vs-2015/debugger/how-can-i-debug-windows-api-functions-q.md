---
title: Cómo depurar funciones de la API de Windows | Microsoft Docs
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
- vs.debug.api
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- debugging [C++], Windows API functions
- NT symbols and debugging Windows API functions
- Windows API functions, debugging
- Windows API, debugging API functions
- APIs, debugging
ms.assetid: 7c126f57-62ab-4d94-9805-632d696ba1f0
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a84414c6e4d6b46cc0429fb03fd739d1dff94065
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51735633"
---
# <a name="how-can-i-debug-windows-api-functions"></a>Cómo depurar funciones de la API de Windows
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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



