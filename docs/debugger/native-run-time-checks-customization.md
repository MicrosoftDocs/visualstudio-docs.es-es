---
title: Personalización de comprobaciones en tiempo de ejecución nativo | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.crt
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- runtime_checks pragma
- debugger, native run-time checks
- /RTC compiler option [C++], native run-time checks
- customizing CRT error checking
- native run-time checks, customizing
ms.assetid: 76a365fe-6439-49db-8603-34058b78e5a8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 5f07e2e2258190196ee001a19d79989ee58239ff
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
---
# <a name="native-run-time-checks-customization"></a>Personalización de las comprobaciones nativas en tiempo de ejecución
Cuando se compila con **/RTC** (comprobaciones en tiempo de ejecución) o usar el `runtime_checks` pragma, la biblioteca de tiempo de ejecución de C proporciona comprobaciones nativas en tiempo de ejecución. En algunos casos puede ser conveniente personalizar las comprobaciones en tiempo de ejecución:  
  
-   Para enviar los mensajes de comprobación en tiempo de ejecución a un archivo o a un destino distinto del predeterminado.  
  
-   Para especificar un destino de salida para los mensajes de comprobación en tiempo de ejecución en un depurador de otro proveedor.  
  
-   Para generar mensajes de comprobación en tiempo de ejecución desde un programa compilado con una versión de distribución de la biblioteca en tiempo de ejecución de C. Las versiones de distribución de la biblioteca no utilizan `_CrtDbgReportW` para generar informes de errores en tiempo de ejecución. En su lugar, abren un **Assert** cuadro de diálogo para cada error en tiempo de ejecución.  
  
 Para personalizar la comprobación de errores en tiempo de ejecución, puede:  
  
-   Escriba una función que crea un informe de error en tiempo de ejecución. Para obtener más información, consulte [Cómo: escribir una función de notificación de Error de tiempo de ejecución](../debugger/how-to-write-a-run-time-error-reporting-function.md).  
  
-   Personalizar el destino del mensaje de error.  
  
-   Consultar información sobre los errores de comprobación en tiempo de ejecución.  
  
## <a name="customize-the-error-message-destination"></a>Personalizar el destino de los mensajes de error  
 Si utiliza `_CrtDbgReportW` para generar informes de errores, puede usar `_CrtSetReportMode` para especificar el destino de los mensajes de error.  
  
 Si usa una función de generación de informes personalizada, utilice `_RTC_SetErrorType` para asociar un error a un tipo de informe.  
  
## <a name="query-for-information-about-run-time-checks"></a>Consultar información acerca de las comprobaciones en tiempo de ejecución  
 `_RTC_NumErrors` devuelve el número de tipos de errores detectados por las comprobaciones de errores en tiempo de ejecución. Para obtener una breve descripción de cada error, puede recorrer con un bucle desde 0 al valor devuelto `_RTC_NumErrors`, pasando el valor de la iteración a `_RTC_GetErrDesc` en cada bucle. Para obtener más información, consulte [_RTC_NumErrors](/cpp/c-runtime-library/reference/rtc-numerrors) y [_RTC_GetErrDesc](/cpp/c-runtime-library/reference/rtc-geterrdesc).  
  
## <a name="see-also"></a>Vea también  
 [Cómo: utilizar comprobaciones nativas en tiempo de ejecución](../debugger/how-to-use-native-run-time-checks.md)   
 [runtime_checks](/cpp/preprocessor/runtime-checks)   
 [_CrtDbgReport, _CrtDbgReportW](/cpp/c-runtime-library/reference/crtdbgreport-crtdbgreportw)