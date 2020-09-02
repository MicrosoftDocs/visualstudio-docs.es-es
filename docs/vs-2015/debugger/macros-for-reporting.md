---
title: Macros para los informes | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.macros
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- macros, CRT reporting macros
- macros, debugging with
- _RPTFn macro
- CRT, reporting macros
- debugging [CRT], reporting macros
- _RPTn macro
ms.assetid: f2085314-a3a8-4caf-a5a4-2af9ad5aad05
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e4aee33d571f95e24a359fa2bc7e12ae8d64eae0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "62431633"
---
# <a name="macros-for-reporting"></a>Macros para los informes
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede usar las macros **_RPTn**y **_RPTFN** definidas en CRTDBG. H, para reemplazar el uso de `printf` instrucciones para la depuración. Estas macros desaparecen automáticamente en la versión de lanzamiento cuando no se define **_DEBUG** , por lo que no es necesario encerrarlos en **#ifdef**s.  
  
|Macro|Descripción|  
|-----------|-----------------|  
|**_RPT0**, **_RPT1**, **_RPT2**, **_RPT3**, **_RPT4**|Escribe una cadena de mensaje y cero en cuatro argumentos. De _RPT1 a **_RPT4**, la cadena de mensaje actúa como una cadena de formato al estilo de printf para los argumentos.|  
|**_RPTF0**, **_RPTF1**, **, _RPTF2**, **_RPTF4**|Igual que **_RPTn** , pero estas macros también generan el nombre de archivo y el número de línea donde se encuentra la macro.|  
  
 Considere el ejemplo siguiente:  
  
```  
#ifdef _DEBUG  
    if ( someVar > MAX_SOMEVAR )  
        printf( "OVERFLOW! In NameOfThisFunc( ),  
               someVar=%d, otherVar=%d.\n",  
               someVar, otherVar );  
#endif  
```  
  
 Este código escribe los valores de `someVar` y `otherVar` en **stdout**. Se puede utilizar la siguiente llamada a `_RPTF2` para informar de estos mismos valores y, además, del nombre del archivo y el número de línea:  
  
```  
if (someVar > MAX_SOMEVAR) _RPTF2(_CRT_WARN, "In NameOfThisFunc( ), someVar= %d, otherVar= %d\n", someVar, otherVar );  
```  
  
 Si una determinada aplicación debe proporcionar información de depuración que las macros de la biblioteca CRT no ofrecen, puede escribir una macro diseñada específicamente para satisfacer sus propios requisitos. En uno de los archivos de encabezado, por ejemplo, se podría incluir código como el siguiente para definir una macro denominada **ALERT_IF2**:  
  
```  
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
  
 Una llamada a **ALERT_IF2** podría realizar todas las funciones del código **printf** al inicio de este tema:  
  
```  
ALERT_IF2(someVar > MAX_SOMEVAR, "OVERFLOW! In NameOfThisFunc( ),   
someVar=%d, otherVar=%d.\n", someVar, otherVar );  
```  
  
 Como una macro personalizada se puede cambiar fácilmente de modo que proporcione más o menos información para diferentes destinos (según convenga), este enfoque puede resultar particularmente útil a medida que los requisitos evolucionan.  
  
## <a name="see-also"></a>Consulte también  
 [Técnicas de depuración de CRT](../debugger/crt-debugging-techniques.md)
