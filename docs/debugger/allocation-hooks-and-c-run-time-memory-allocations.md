---
title: "Enlaces de asignaci&#243;n y asignaciones de memoria en tiempo de ejecuci&#243;n de C | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.hooks"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "enlaces de asignación"
  - "depurar [C++], funciones de enlace"
  - "enlaces, asignación"
  - "asignación de memoria, solucionar problemas de enlaces de asignaciones"
ms.assetid: cc34ee96-3d91-41bd-a019-aa3759139e7e
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Enlaces de asignaci&#243;n y asignaciones de memoria en tiempo de ejecuci&#243;n de C
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Una restricción muy importante acerca de las funciones de enlace de asignación consiste en que éstas deben omitir explícitamente los bloques `_CRT_BLOCK` \(las asignaciones de memoria realizadas internamente por las funciones de la biblioteca en tiempo de ejecución de C\) si realizan alguna llamada a las funciones de la biblioteca en tiempo de ejecución de C que asigne memoria interna.  Los bloques `_CRT_BLOCK` se pueden omitir si se incluye código como el siguiente al inicio de la función de enlace de asignación:  
  
```  
if ( nBlockUse == _CRT_BLOCK )  
    return( TRUE );  
```  
  
 Si la función de enlace de asignación no omite los bloques `_CRT_BLOCK`, entonces cualquier función de la biblioteca en tiempo de ejecución de C a la que se llame en el enlace puede hacer que el programa quede atrapado en un bucle sin fin.  Por ejemplo, `printf` realiza una asignación interna.  Si el código del enlace llama a `printf`, la asignación resultante hará que se vuelva a llamar al enlace, que llamará de nuevo a **printf** , etc. hasta que se desborde la pila.  Si necesita informar de las operaciones de asignación de `_CRT_BLOCK`, una forma de evitar esta restricción consiste en utilizar funciones de la API de Windows, en vez de funciones en tiempo de ejecución de C, para operaciones de formato y salida.  Como las API de Windows no utilizan el montón de la biblioteca en tiempo de ejecución de C, no bloquearán el enlace de asignación en un bucle sin fin.  
  
 Si examina los archivos de código fuente de la biblioteca en tiempo de ejecución, verá que la función de enlace de asignación predeterminada, **CrtDefaultAllocHook** \(que simplemente devuelve **TRUE**\), se encuentra en un archivo independiente, DBGHOOK.C.  Si desea llamar al enlace de asignación incluso en las asignaciones realizadas por el código de inicio en tiempo de ejecución que se ejecuta antes que la función **main** de la aplicación, puede reemplazar esta función predeterminada por una propia en lugar de usar [\_CrtSetAllocHook](/visual-cpp/c-runtime-library/reference/crtsetallochook).  
  
## Vea también  
 [Creación de funciones de enlace de depuración](../debugger/debug-hook-function-writing.md)   
 [crt\_dbg2 Sample](http://msdn.microsoft.com/es-es/21e1346a-6a17-4f57-b275-c76813089167)