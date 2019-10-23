---
title: Macros para informes | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.macros
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- macros, CRT reporting macros
- macros, debugging with
- _RPTFn macro
- CRT, reporting macros
- debugging [CRT], reporting macros
- _RPTn macro
ms.assetid: f2085314-a3a8-4caf-a5a4-2af9ad5aad05
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c2129db98293cef678527fb331992c6c5960d8f9
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72731391"
---
# <a name="macros-for-reporting"></a>Macros para los informes
Para la depuración, puede usar las macros **_RPTn** y **_RPTFn** , definidas en CRTDBG. H, para reemplazar el uso de `printf` instrucciones. No es necesario que las incierre en **#ifdef**s, porque desaparecen automáticamente en la versión de lanzamiento cuando no se define **_ Debug** .

|Macro|Descripción|
|-----------|-----------------|
|**_RPT0**, **_RPT1**, **_RPT2**, **_RPT3**, **_RPT4**|Escribe una cadena de mensaje y cero en cuatro argumentos. De _RPT1 a **_RPT4**, la cadena de mensaje actúa como una cadena de formato al estilo de printf para los argumentos.|
|**_RPTF0**, **_RPTF1**, **_RPTF2**, **_RPTF4**|Igual que **_RPTn**, pero estas macros también escriben el nombre del archivo y el número de línea donde se encuentra la macro.|

 Considere el ejemplo siguiente:

```cpp
#ifdef _DEBUG
    if ( someVar > MAX_SOMEVAR )
        printf( "OVERFLOW! In NameOfThisFunc( ),
               someVar=%d, otherVar=%d.\n",
               someVar, otherVar );
#endif
```

 Este código escribe los valores de `someVar` y `otherVar` en **stdout**. Se puede utilizar la siguiente llamada a `_RPTF2` para informar de estos mismos valores y, además, del nombre del archivo y el número de línea:

```cpp
if (someVar > MAX_SOMEVAR) _RPTF2(_CRT_WARN, "In NameOfThisFunc( ), someVar= %d, otherVar= %d\n", someVar, otherVar );
```

Es posible que una aplicación determinada necesite informes de depuración que no proporcionan las macros proporcionadas con la biblioteca en tiempo de ejecución de C. En estos casos, puede escribir una macro diseñada específicamente para satisfacer sus propios requisitos. En uno de los archivos de encabezado, por ejemplo, se podría incluir código como el siguiente para definir una macro denominada **ALERT_IF2**:

```cpp
#ifndef _DEBUG                  /* For RELEASE builds */
#define  ALERT_IF2(expr, msg, arg1, arg2)  do {} while (0)
#else                           /* For DEBUG builds   */
#define  ALERT_IF2(expr, msg, arg1, arg2) \
    do { \
        if ((expr) && \
            (1 == _CrtDbgReport(_CRT_ERROR, \
                __FILE__, __LINE__, msg, arg1, arg2))) \
            _CrtDbgBreak( ); \
    } while (0)
#endif
```

 Una llamada a **ALERT_IF2** podría realizar todas las funciones del código **printf** :

```cpp
ALERT_IF2(someVar > MAX_SOMEVAR, "OVERFLOW! In NameOfThisFunc( ),
someVar=%d, otherVar=%d.\n", someVar, otherVar );
```

 Puede cambiar fácilmente una macro personalizada para notificar más o menos información a distintos destinos. Este enfoque es especialmente útil a medida que evolucionan los requisitos de depuración.

## <a name="see-also"></a>Vea también
- [Técnicas de depuración de CRT](../debugger/crt-debugging-techniques.md)
