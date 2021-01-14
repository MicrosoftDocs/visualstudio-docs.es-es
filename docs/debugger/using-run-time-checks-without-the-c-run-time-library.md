---
title: Uso de comprobaciones en tiempo de ejecución sin la biblioteca en tiempo de ejecución de C | Microsoft Docs
description: Puede vincular el programa sin la biblioteca en tiempo de ejecución de C mediante /NODEFAULTLIB. Si lo hace y quiere utilizar las comprobaciones en tiempo de ejecución, debe realizar la vinculación con RunTmChk.lib.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bfa83533b1ae929bf443dd6c3eb7f7dc3e7db165
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/13/2021
ms.locfileid: "98150865"
---
# <a name="using-run-time-checks-without-the-c-run-time-library"></a>Uso de comprobaciones en tiempo de ejecución sin la biblioteca en tiempo de ejecución de C
Si vincula el programa sin la biblioteca en tiempo de ejecución de C, mediante **/NODEFAULTLIB**, y quiere utilizar las comprobaciones en tiempo de ejecución, debe vincular el programa con RunTmChk.lib.

`_RTC_Initialize` inicializa el programa para las comprobaciones en tiempo de ejecución. Si no vincula el programa con la biblioteca en tiempo de ejecución de C, debe comprobar si el programa se ha compilado con las comprobaciones de errores en tiempo de ejecución antes de llamar a `_RTC_Initialize`, tal como:

```cpp
#ifdef __MSVC_RUNTIME_CHECKS
    _RTC_Initialize();
#endif
```

Si no vincula con la biblioteca en tiempo de ejecución de C, también debe definir una función denominada `_CRT_RTC_INITW`. `_CRT_RTC_INITW` instala la función definida por el usuario como función de notificación de errores predeterminada, de la siguiente manera:

```cpp
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

Una vez instalada la función de generación de informes de errores predeterminada, puede instalar otras funciones del mismo tipo con `_RTC_SetErrorFuncW`. Para obtener más información, vea [_RTC_SetErrorFuncW](/cpp/c-runtime-library/reference/rtc-seterrorfuncw).

## <a name="see-also"></a>Vea también
[Cómo: Uso de comprobaciones nativas en tiempo de ejecución](../debugger/how-to-use-native-run-time-checks.md)
