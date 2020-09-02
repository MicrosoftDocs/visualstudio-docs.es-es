---
title: Uso de comprobaciones en tiempo de ejecución sin la biblioteca en tiempo de ejecución de C | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1eefddd21817360736b9f20f74ca3dc8a83683fe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65684019"
---
# <a name="using-run-time-checks-without-the-c-run-time-library"></a>Uso de comprobaciones en tiempo de ejecución sin la biblioteca en tiempo de ejecución de C
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si vincula el programa sin la biblioteca en tiempo de ejecución de C, mediante **/NODEFAULTLIB**, y quiere utilizar las comprobaciones en tiempo de ejecución, debe vincular el programa con RunTmChk.lib.  
  
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
  
 Una vez instalada la función de generación de informes de errores predeterminada, puede instalar otras funciones del mismo tipo con `_RTC_SetErrorFuncW`. Para obtener más información, vea [_RTC_SetErrorFuncW](https://msdn.microsoft.com/library/b3e0d71f-1bd3-4c37-9ede-2f638eb3c81a).  
  
## <a name="see-also"></a>Consulte también  
 [Cómo: Uso de comprobaciones nativas en tiempo de ejecución](../debugger/how-to-use-native-run-time-checks.md)
