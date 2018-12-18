---
title: Macros para informes | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 57b254323fac5d670cd44399cd8d22c9530c4510
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/27/2018
ms.locfileid: "37056607"
---
# <a name="macros-for-reporting"></a>Macros para los informes
Para la depuración, puede usar el **_RPTn** y **_RPTFn** macros, definidas en CRTDBG. H, para reemplazar el uso de `printf` instrucciones. No es necesario en inclose **#ifdef**s, porque éstas desaparecen automáticamente en su versión de compilación cuando **_DEBUG** no se ha definido.  
  
|Macro|Descripción|  
|-----------|-----------------|  
|**_RPT0**, **_RPT1**, **_RPT2**, **_RPT3**, **_RPT4**|Escribe una cadena de mensaje y cero en cuatro argumentos. De _RPT1 a **_RPT4**, la cadena de mensaje actúa como una cadena de formato de estilo de printf para los argumentos.|  
|**_RPTF0**, **_RPTF1**, **_RPTF2**, **_RPTF4**|Igual que **_RPTn**, pero estas macros también escriben el archivo nombre y número de línea donde se encuentra la macro.|  
  
 Considere el ejemplo siguiente:  
  
```cpp
#ifdef _DEBUG  
    if ( someVar > MAX_SOMEVAR )  
        printf( "OVERFLOW! In NameOfThisFunc( ),  
               someVar=%d, otherVar=%d.\n",  
               someVar, otherVar );  
#endif  
```  
  
 Este código genera los valores de `someVar` y `otherVar` a **stdout**. Se puede utilizar la siguiente llamada a `_RPTF2` para informar de estos mismos valores y, además, del nombre del archivo y el número de línea:  
  
```cpp
if (someVar > MAX_SOMEVAR) _RPTF2(_CRT_WARN, "In NameOfThisFunc( ), someVar= %d, otherVar= %d\n", someVar, otherVar );  
```  
  
Es posible que una determinada aplicación necesita que las macros incluidas con la biblioteca de tiempo de ejecución de C no proporcionan información de depuración. En estos casos, puede escribir una macro diseñada específicamente para satisfacer sus propios requisitos. En uno de los archivos de encabezado, por ejemplo, podría incluir código como el siguiente para definir una macro denominada **ALERT_IF2**:  
  
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
  
 Una llamada a **ALERT_IF2** podría hacer que todas las funciones de la **printf** código:  
  
```cpp
ALERT_IF2(someVar > MAX_SOMEVAR, "OVERFLOW! In NameOfThisFunc( ),   
someVar=%d, otherVar=%d.\n", someVar, otherVar );  
```  
  
 Puede cambiar fácilmente una macro personalizada para informar de más o menos información a diferentes destinos. Este enfoque es especialmente útil, como los requisitos evolucionan.  
  
## <a name="see-also"></a>Vea también  
 [Técnicas de depuración de CRT](../debugger/crt-debugging-techniques.md)
