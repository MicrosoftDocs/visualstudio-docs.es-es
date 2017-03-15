---
title: "Marcos de pila | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "marcos de pila, depuración"
  - "depurar [SDK de depuración], marcos de pila"
  - "marcos de pila"
ms.assetid: b5e439d4-1e9d-4e13-9cad-bb8b136d4ca8
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# Marcos de pila
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

En términos de arquitectura del depurador, **un marco de pila**:  
  
-   Es una abstracción de pila que proporciona el contexto de ejecución de un subproceso.  Un subproceso siempre se ejecuta dentro de una función.  Un marco de pila contiene las variables locales de la función, y los argumentos del.  Para depurar con Visual Studio, el idioma o el entorno que se está depurando debe admitir los marcos de pila.  
  
-   puede identificar y describirse, y puede devolver el subproceso asociado.  Un marco de pila también puede devolver el contexto del código que representa el puntero de instrucción actual, así como los contextos asociado de la documentación y evaluación de la expresión.  
  
-   Tiene propiedades que describen el nombre, el tipo, y el valor de las variables locales y de argumentos, y que aparecen en las distintas ventanas de depuración del IDE.  
  
-   Se representa mediante una interfaz de [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) , creada normalmente por un motor de depuración \(DE\) o una máquina virtual como resultado de ejecutar un subproceso.  
  
## Vea también  
 [Contextos de depurador](../../extensibility/debugger/debugger-contexts.md)   
 [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)   
 [Motor de depuración](../../extensibility/debugger/debug-engine.md)   
 [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)