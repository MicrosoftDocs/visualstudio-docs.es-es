---
title: "Personalizaci&#243;n de las comprobaciones nativas en tiempo de ejecuci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.crt"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "/RTC (opción del compilador) [C++], comprobaciones nativas en tiempo de ejecución"
  - "personalizar la comprobación de errores CRT"
  - "depurador, comprobaciones nativas en tiempo de ejecución"
  - "comprobaciones nativas en tiempo de ejecución, personalizar"
  - "runtime_checks (pragma)"
ms.assetid: 76a365fe-6439-49db-8603-34058b78e5a8
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# Personalizaci&#243;n de las comprobaciones nativas en tiempo de ejecuci&#243;n
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cuando se compila con la opción **\/RTC** \(comprobación en tiempo de ejecución\) o se usa el pragma `runtime_checks`, la biblioteca en tiempo de ejecución de C proporciona comprobaciones nativas en tiempo de ejecución.  En algunos casos puede ser conveniente personalizar las comprobaciones en tiempo de ejecución:  
  
-   Para enviar los mensajes de comprobación en tiempo de ejecución a un archivo o a un destino distinto del predeterminado.  
  
-   Para especificar un destino de salida para los mensajes de comprobación en tiempo de ejecución en un depurador de otro proveedor.  
  
-   Para generar mensajes de comprobación en tiempo de ejecución desde un programa compilado con una versión de distribución de la biblioteca en tiempo de ejecución de C.  Las versiones de distribución de la biblioteca no utilizan `_CrtDbgReportW` para generar informes de errores en tiempo de ejecución.  En su lugar, abren un cuadro de diálogo **Aserción** para cada error en tiempo de ejecución.  
  
 Para personalizar la comprobación de errores en tiempo de ejecución, puede:  
  
-   Escriba una función que crea un informe de error en tiempo de ejecución.  Para obtener más información, vea [Cómo: Escribir una función para generar informes de errores en tiempo de ejecución](../debugger/how-to-write-a-run-time-error-reporting-function.md).  
  
-   Personalizar el destino del mensaje de error.  
  
-   Consultar información sobre los errores de comprobación en tiempo de ejecución.  
  
## Personalizar el destino de los mensajes de error  
 Si utiliza `_CrtDbgReportW` para generar informes de errores, puede usar `_CrtSetReportMode` para especificar el destino de los mensajes de error.  
  
 Si usa una función de generación de informes personalizada, utilice `_RTC_SetErrorType` para asociar un error a un tipo de informe.  
  
## Consultar información acerca de las comprobaciones en tiempo de ejecución  
 `_RTC_NumErrors` devuelve el número de tipos de errores detectados por las comprobaciones de errores en tiempo de ejecución.  Para obtener una breve descripción de cada error, puede recorrer con un bucle desde 0 al valor devuelto `_RTC_NumErrors`, pasando el valor de la iteración a `_RTC_GetErrDesc` en cada bucle.  Para obtener más información, vea [\_RTC\_NumErrors](/visual-cpp/c-runtime-library/reference/rtc-numerrors) y [\_RTC\_GetErrDesc](/visual-cpp/c-runtime-library/reference/rtc-geterrdesc).  
  
## Vea también  
 [Cómo: Utilizar comprobaciones nativas en tiempo de ejecución](../debugger/how-to-use-native-run-time-checks.md)   
 [runtime\_checks](/visual-cpp/preprocessor/runtime-checks)   
 [\_CrtDbgReport, \_CrtDbgReportW](/visual-cpp/c-runtime-library/reference/crtdbgreport-crtdbgreportw)