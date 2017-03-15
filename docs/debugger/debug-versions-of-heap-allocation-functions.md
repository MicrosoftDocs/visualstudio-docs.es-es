---
title: "Versiones de depuraci&#243;n de las funciones de asignaci&#243;n del mont&#243;n | Microsoft Docs"
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
  - "C++"
helpviewer_keywords: 
  - "_CRTDBG_MAP_ALLOC (macro)"
  - "_malloc_dbg (función)"
  - "depurar [CRT], funciones de asignación de montones"
  - "depurar pérdidas de memoria, funciones de la biblioteca de depuración de CRT"
  - "asignación en el montón, depuración"
  - "malloc (función)"
  - "pérdidas de memoria, funciones de la biblioteca de depuración de CRT"
ms.assetid: 91748bdc-f4cd-4d8b-ab98-0493dab7ed0d
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# Versiones de depuraci&#243;n de las funciones de asignaci&#243;n del mont&#243;n
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La biblioteca en tiempo de ejecución de C contiene versiones de depuración especiales de las funciones de asignación de memoria en el montón.  Estas funciones tienen los mismos nombres que las versiones de lanzamiento pero con \_dbg agregado al final.  Este tema describe las diferencias entre la versión de lanzamiento de una función CRT y la versión \_dbg usando `malloc` y `_malloc_dbg` como ejemplos.  
  
 Cuando se define [\_DEBUG](/visual-cpp/c-runtime-library/debug), CRT asigna todas las llamadas de [malloc](/visual-cpp/c-runtime-library/reference/malloc) a [\_malloc\_dbg](/visual-cpp/c-runtime-library/reference/malloc-dbg).  Por lo tanto, no es necesario volver a escribir el código utilizando `_malloc_dbg` en vez de `malloc` para aprovechar sus beneficios mientras se depura.  
  
 No obstante, se puede llamar a `_malloc_dbg` explícitamente.  Llamar explícitamente a `_malloc_dbg` presenta algunas ventajas adicionales:  
  
-   Seguimiento de asignaciones de tipos `_CLIENT_BLOCK`.  
  
-   Almacenamiento del archivo de código fuente y número de línea donde se produjo la solicitud de asignación de memoria.  
  
 Si no desea convertir las llamadas de `malloc` en llamadas a `_malloc_dbg`, puede obtener la información de archivos de código fuente definiendo [\_CRTDBG\_MAP\_ALLOC](/visual-cpp/c-runtime-library/crtdbg-map-alloc), que hace que el preprocesador asigne directamente todas las llamadas de `malloc` a llamadas de `_malloc_dbg`, en vez de utilizar un contenedor que envuelva a `malloc`.  
  
 Para realizar un seguimiento de los tipos de asignaciones que existen en los bloques cliente de forma independiente, se debe llamar directamente a `_malloc_dbg` y asignar a `_CLIENT_BLOCK` el parámetro `blockType`.  
  
 Cuando no está definido \_DEBUG, las llamadas a `malloc` no se modifican, las llamadas a `_malloc_dbg` se resuelven como `malloc`, la definición de [\_CRTDBG\_MAP\_ALLOC](/visual-cpp/c-runtime-library/crtdbg-map-alloc) se omite y no se facilita la información de los archivos de código fuente correspondiente a la solicitud de asignación.  Como `malloc` no utiliza un parámetro de tipo bloque, las solicitudes para tipos `_CLIENT_BLOCK` se tratan como asignaciones estándar.  
  
## Vea también  
 [Técnicas de depuración de CRT](../debugger/crt-debugging-techniques.md)