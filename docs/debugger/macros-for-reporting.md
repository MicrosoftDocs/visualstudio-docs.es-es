---
title: Macros para informes | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.macros
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
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 5af21a708a05bfdc0338ca1c5b2bc038e192eb4b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="macros-for-reporting"></a>Macros para los informes
Puede usar el **_RPTn**, y **_RPTFn** macros, definidas en CRTDBG. H, para reemplazar el uso de `printf` instrucciones para la depuración. Estas macros desaparecen automáticamente en la versión de lanzamiento cuando **_DEBUG** no está definido, por lo que no es necesario encerrarlas entre **#ifdef**s.  
  
|Macro|Descripción|  
|-----------|-----------------|  
|**_RPT0**, **_RPT1**, **_RPT2**, **_RPT3**, **_RPT4**|Escribe una cadena de mensaje y cero en cuatro argumentos. De _RPT1 a **_RPT4**, la cadena de mensaje actúa como una cadena de formato de estilo de printf para los argumentos.|  
|**_RPTF0**, **_RPTF1**, **, _RPTF2**, **_RPTF4**|Igual que **_RPTn**, pero estas macros también escriben el archivo nombre y número de línea donde se encuentra la macro.|  
  
 Considere el ejemplo siguiente:  
  
```  
#ifdef _DEBUG  
    if ( someVar > MAX_SOMEVAR )  
        printf( "OVERFLOW! In NameOfThisFunc( ),  
               someVar=%d, otherVar=%d.\n",  
               someVar, otherVar );  
#endif  
```  
  
 Este código escribe los valores de `someVar` y `otherVar` a **stdout**. Se puede utilizar la siguiente llamada a `_RPTF2` para informar de estos mismos valores y, además, del nombre del archivo y el número de línea:  
  
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
  
 Una llamada a **ALERT_IF2** podría realizar todas las funciones de la **printf** código al principio de este tema:  
  
```  
ALERT_IF2(someVar > MAX_SOMEVAR, "OVERFLOW! In NameOfThisFunc( ),   
someVar=%d, otherVar=%d.\n", someVar, otherVar );  
```  
  
 Como una macro personalizada se puede cambiar fácilmente de modo que proporcione más o menos información para diferentes destinos (según convenga), este enfoque puede resultar particularmente útil a medida que los requisitos evolucionan.  
  
## <a name="see-also"></a>Vea también  
 [Técnicas de depuración de CRT](../debugger/crt-debugging-techniques.md)