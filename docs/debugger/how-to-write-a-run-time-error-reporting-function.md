---
title: Escritura de una función para generar informes de errores en tiempo de ejecución | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- run-time errors, reporting functions
- reporting function
ms.assetid: 989bf312-5038-44f3-805f-39a34d18760e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 22445868cca1533cad3d7e395452a6b19e102952
ms.sourcegitcommit: 023f52f10fb91850824558478cbfd2ec965054f0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/10/2020
ms.locfileid: "94407645"
---
# <a name="how-to-write-a-run-time-error-reporting-function-c"></a>Procedimiento Escritura de una función para generar informes de errores en tiempo de ejecución (C++)
Una función personalizada para la generación de informes de error en tiempo de ejecución debe tener la misma declaración que `_CrtDbgReportW`. Debe devolver un valor de 1 al depurador.

En el siguiente ejemplo se muestra el modo de definir una función de supervisión personalizada.

## <a name="example-1"></a>Ejemplo 1

```cpp
#include <stdio.h>
int errorhandler = 0;
void configureMyErrorFunc(int i)
{
    errorhandler = i;
}

int MyErrorFunc(int errorType, const wchar_t *filename,
                int linenumber, const wchar_t *moduleName,
                const wchar_t *format, ...)
{
    switch (errorhandler)
    {
    case 0:
    case 1:
        wprintf(L"Error type %d at %s line %d in %s",
                errorType, filename, linenumber, moduleName);
        break;
    case 2:
    case 3:
        fprintf(stderr, "Error type");
        break;
    }

    return 1;
}
```

## <a name="example-2"></a>Ejemplo 2
En el siguiente ejemplo se muestra una función de supervisión personalizada más compleja. En este ejemplo, la instrucción swich controla varios tipos de errores, definidos por el parámetro `reportType` de `_CrtDbgReportW`. Puesto que va a sustituir `_CrtDbgReportW`, no puede utilizar `_CrtSetReportMode`. La función debe controlar la salida. El primer argumento variable de esta función toma un número de error en tiempo de ejecución. Para obtener más información, vea [_RTC_SetErrorType](/cpp/c-runtime-library/reference/rtc-seterrortype).

```cpp
#include <windows.h>
#include <stdarg.h>
#include <rtcapi.h>
#include <malloc.h>
#pragma runtime_checks("", off)
int Catch_RTC_Failure(int errType, const wchar_t *file, int line,
                      const wchar_t *module, const wchar_t *format, ...)
{
    // Prevent re-entrance.
    static long running = 0;
    while (InterlockedExchange(&running, 1))
        Sleep(0);
    // Now, disable all RTC failures.
    int numErrors = _RTC_NumErrors();
    int *errors=(int*)_alloca(numErrors);
    for (int i = 0; i < numErrors; i++)
        errors[i] = _RTC_SetErrorType((_RTC_ErrorNumber)i, _RTC_ERRTYPE_IGNORE);

    // First, get the rtc error number from the var-arg list.
    va_list vl;
    va_start(vl, format);
    _RTC_ErrorNumber rtc_errnum = va_arg(vl, _RTC_ErrorNumber);
    va_end(vl);

    wchar_t buf[512];
    const char *err = _RTC_GetErrDesc(rtc_errnum);
    swprintf_s(buf, 512, L"%S\nLine #%d\nFile:%s\nModule:%s",
        err,
        line,
        file ? file : L"Unknown",
        module ? module : L"Unknown");
    int res = (MessageBox(NULL, buf, L"RTC Failed...", MB_YESNO) == IDYES) ? 1 : 0;
    // Now, restore the RTC errortypes.
    for(int i = 0; i < numErrors; i++)
        _RTC_SetErrorType((_RTC_ErrorNumber)i, errors[i]);
    running = 0;
    return res;
}
#pragma runtime_checks("", restore)
```

## <a name="example-3"></a>Ejemplo 3
Utilice `_RTC_SetErrorFuncW` para instalar la función personalizada en lugar de `_CrtDbgReportW`. Para obtener más información, vea [_RTC_SetErrorFuncW](/cpp/c-runtime-library/reference/rtc-seterrorfuncw). El valor devuelto `_RTC_SetErrorFuncW` es la función de generación de informes anterior, que puede guardar y restaurar si es necesario.

```cpp
#include <rtcapi.h>
int main()
{
    _RTC_error_fnW oldfunction, newfunc;
    oldfunction = _RTC_SetErrorFuncW(&MyErrorFunc);
    // Run some code.
    newfunc = _RTC_SetErrorFuncW(oldfunction);
    // newfunc == &MyErrorFunc;
    // Run some more code.
}
```

## <a name="see-also"></a>Vea también
[Personalización de las comprobaciones nativas en tiempo de ejecución](../debugger/native-run-time-checks-customization.md)
