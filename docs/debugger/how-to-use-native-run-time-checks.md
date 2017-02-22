---
title: "C&#243;mo: Utilizar comprobaciones nativas en tiempo de ejecuci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.runtime.errorchecks"
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
  - "/O (opción del compilador), /RTC (opción)"
  - "/RTC (opción del compilador) [C++], /O (opción del compilador)"
  - "matrices [Visual Studio], depurar"
  - "depurador, comprobaciones nativas en tiempo de ejecución"
  - "depurador, errores en tiempo de ejecución"
  - "depurar matrices"
  - "comprobaciones nativas en tiempo de ejecución"
  - "O (opción del compilador), /RTC (opción)"
  - "opción de compilación optimizada"
  - "RTC (opción del compilador), /O (opción del compilador)"
  - "comprobaciones en tiempo de ejecución"
  - "comprobaciones en tiempo de ejecución, nativas"
  - "errores en tiempo de ejecución, depurar"
  - "errores en tiempo de ejecución, comprobaciones de errores"
  - "runtime_checks (pragma)"
  - "punteros de pila"
  - "punteros de pila, daños"
  - "pila, daños en el puntero"
  - "variables [depurador], interceptar dependencias en variables locales sin inicializar"
  - "variables [depurador], pérdida de datos"
ms.assetid: dc7b2f1e-5ff6-42e0-89b3-dc9dead83ee1
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# C&#243;mo: Utilizar comprobaciones nativas en tiempo de ejecuci&#243;n
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En Visual C\+\+, puede realizar [runtime\_checks](/visual-cpp/preprocessor/runtime-checks) nativas para detectar errores en tiempo de ejecución, tales como:  
  
-   Daños en el puntero de la pila  
  
-   Saturación de matrices locales  
  
-   Daños en la pila  
  
-   Dependencias en variables locales sin inicializar  
  
-   Pérdida de datos en una asignación a una variable corta.  
  
 Si utiliza **\/RTC** con una generación optimizada \(**\/O**\), obtendrá un error del compilador. Si utiliza un pragma `runtime_checks` en una versión optimizada, el pragma no surte ningún efecto.  
  
 Cuando se depura un programa con las comprobaciones en tiempo de ejecución habilitadas, la acción predeterminada es la de que el programa se detenga y se interrumpa su depuración cuando se produzca un error en tiempo de ejecución. Puede cambiar este comportamiento predeterminado para cualquier comprobación en tiempo de ejecución. Para obtener más información, consulta [Administración de excepciones con el depurador](../debugger/managing-exceptions-with-the-debugger.md).  
  
 Los siguientes procedimientos describen cómo habilitar las comprobaciones en tiempo de ejecución nativas en una versión de depuración y cómo modificar el comportamiento de la comprobación en tiempo de ejecución nativa.  
  
 Los demás temas de esta sección contienen información sobre:  
  
-   [Personalizar las comprobaciones en tiempo de ejecución con la biblioteca en tiempo de ejecución de C](../debugger/native-run-time-checks-customization.md)  
  
-   [Utilizar comprobaciones en tiempo de ejecución sin la biblioteca en tiempo de ejecución de C](../debugger/using-run-time-checks-without-the-c-run-time-library.md)  
  
### Para habilitar las comprobaciones nativas en tiempo de ejecución en una versión de depuración  
  
-   Utilice la opción **\/RTC** y vincule la versión de depuración de una biblioteca C en tiempo de ejecución \(\/MDd, por ejemplo\).  
  
### Para modificar el comportamiento de las comprobaciones nativas en tiempo de ejecución  
  
-   Utilice la directiva pragma `runtime_checks`.  
  
## Vea también  
 [Depurar en Visual Studio](../debugger/debugging-in-visual-studio.md)   
 [runtime\_checks](/visual-cpp/preprocessor/runtime-checks)   
 [Comprobar errores en tiempo de ejecución](/visual-cpp/c-runtime-library/run-time-error-checking)