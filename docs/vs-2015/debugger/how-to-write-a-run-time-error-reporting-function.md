---
title: 'Cómo: escribir una función para generar informes de errores en tiempo de ejecución | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
- run-time errors, reporting functions
- reporting function
ms.assetid: 989bf312-5038-44f3-805f-39a34d18760e
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 94bbc0ff7d5ca06ca4ff7f84e1f2cb85c254b197
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47578657"
---
# <a name="how-to-write-a-run-time-error-reporting-function"></a>Cómo: Escribir una función para generar informes de errores en tiempo de ejecución
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Cómo: escribir una función de notificación de Error de tiempo de ejecución](https://docs.microsoft.com/visualstudio/debugger/how-to-write-a-run-time-error-reporting-function).  
  
Una función personalizada para la generación de informes de error en tiempo de ejecución debe tener la misma declaración que `_CrtDbgReportW`. Debe devolver un valor de 1 al depurador.  
  
 En el siguiente ejemplo se muestra el modo de definir una función de supervisión personalizada.  
  
## <a name="example"></a>Ejemplo  
  
```  
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
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo se muestra una función de supervisión personalizada más compleja. En este ejemplo, la instrucción swich controla varios tipos de errores, definidos por el parámetro `reportType` de `_CrtDbgReportW`. Puesto que va a sustituir `_CrtDbgReportW`, no puede utilizar `_CrtSetReportMode`. La función debe controlar la salida. El primer argumento variable de esta función toma un número de error en tiempo de ejecución. Para obtener más información, consulte [_RTC_SetErrorType](http://msdn.microsoft.com/library/f5f99be7-d357-4b11-b8f5-ddd3428f2b06).  
  
```  
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
  
## <a name="example"></a>Ejemplo  
 Utilice `_RTC_SetErrorFuncW` para instalar la función personalizada en lugar de `_CrtDbgReportW`. Para obtener más información, consulte [_RTC_SetErrorFuncW](http://msdn.microsoft.com/library/b3e0d71f-1bd3-4c37-9ede-2f638eb3c81a). El valor devuelto `_RTC_SetErrorFuncW` es la función de generación de informes anterior, que puede guardar y restaurar si es necesario.  
  
```  
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





