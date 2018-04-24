---
title: Uso de tiempo de ejecución comprueba sin la biblioteca de tiempo de ejecución de C | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.runtime
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- run-time errors, error checks
- CRT, run-time checks
- debugger, native run-time checks
- run-time errors, run-time checks
- run-time checks, /RTC option
- debugging [Visual Studio], run-time routines
ms.assetid: 30ed90f3-9323-4784-80a4-937449eb54f6
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 533e4254b6222af1713691a0c448cad1383cd273
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
---
# <a name="using-run-time-checks-without-the-c-run-time-library"></a>Utilizar comprobaciones en tiempo de ejecución sin la biblioteca en tiempo de ejecución de C
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
  
 Una vez instalada la función de generación de informes de errores predeterminada, puede instalar otras funciones del mismo tipo con `_RTC_SetErrorFuncW`. Para obtener más información, consulte [_RTC_SetErrorFuncW](/cpp/c-runtime-library/reference/rtc-seterrorfuncw).  
  
## <a name="see-also"></a>Vea también  
 [Cómo: Usar comprobaciones nativas en tiempo de ejecución](../debugger/how-to-use-native-run-time-checks.md)