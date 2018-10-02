---
title: Uso de tiempo de ejecución comprueba sin la biblioteca de tiempo de ejecución de C | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.runtime
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- run-time errors, error checks
- CRT, run-time checks
- debugger, native run-time checks
- run-time errors, run-time checks
- run-time checks, /RTC option
- debugging [Visual Studio], run-time routines
ms.assetid: 30ed90f3-9323-4784-80a4-937449eb54f6
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 864e21d2c2ec2a9922d70e6b69192d9268556737
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47581261"
---
# <a name="using-run-time-checks-without-the-c-run-time-library"></a>Utilizar comprobaciones en tiempo de ejecución sin la biblioteca en tiempo de ejecución de C
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [utilizando tiempo de ejecución comprueba sin el C Run-Time Library](https://docs.microsoft.com/visualstudio/debugger/using-run-time-checks-without-the-c-run-time-library).  
  
Si vincula el programa sin la biblioteca de tiempo de ejecución de C, utilizando **/NODEFAULTLIB**y desea utilizar comprobaciones en tiempo de ejecución, debe vincular el programa con RunTmChk.lib.  
  
 `_RTC_Initialize` inicializa el programa para las comprobaciones en tiempo de ejecución. Si no vincula el programa con la biblioteca en tiempo de ejecución de C, debe comprobar si el programa se ha compilado con las comprobaciones de errores en tiempo de ejecución antes de llamar a `_RTC_Initialize`, tal como:  
  
```  
#ifdef __MSVC_RUNTIME_CHECKS  
    _RTC_Initialize();  
#endif  
```  
  
 Si no vincula con la biblioteca en tiempo de ejecución de C, también debe definir una función denominada `_CRT_RTC_INITW`. `_CRT_RTC_INITW` instala la función definida por el usuario como función de notificación de errores predeterminada, de la siguiente manera:  
  
```  
// C version:  
_RTC_error_fnW __cdecl _CRT_RTC_INITW(  
        void *res0, void **res1, int res2, int res3, int res4)  
{  
    // set the error handler.  
    return &MyErrorFunc;   
}  
  
// C++ version:  
extern "C" _RTC_error_fnW __cdecl _CRT_RTC_INITW(  
       void *res0, void **res1, int res2, int res3, int res4)  
{  
    // set the error handler:  
    return &MyErrorFunc;  
}  
```  
  
 Una vez instalada la función de generación de informes de errores predeterminada, puede instalar otras funciones del mismo tipo con `_RTC_SetErrorFuncW`. Para obtener más información, consulte [_RTC_SetErrorFuncW](http://msdn.microsoft.com/library/b3e0d71f-1bd3-4c37-9ede-2f638eb3c81a).  
  
## <a name="see-also"></a>Vea también  
 [Cómo: Usar comprobaciones nativas en tiempo de ejecución](../debugger/how-to-use-native-run-time-checks.md)





