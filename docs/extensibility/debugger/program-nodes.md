---
title: "Nodos de programa | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "nodos de programa, el contexto de depuración"
  - "depurar [SDK de depuración], programar nodos"
  - "nodos de programa, agregar"
  - "nodos de programa, sustitución"
ms.assetid: 1c5a5c13-c14d-42c3-af11-4c63f1032c8d
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# Nodos de programa
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

En términos de arquitectura del depurador, **un nodo de programa**:  
  
-   es una descripción ligera de un programa.  
  
-   Puede identificarse y el proceso que se está ejecutando en, y se puede asociar a, se desasoció de, y describir el motor de depuración \(DE\) que lo creó, si procede.  
  
-   Se representa mediante una interfaz de [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) , creada normalmente por un OF o un puerto.  Los nodos del programa se agregan a un puerto llamando a [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md).  Cuando un nodo de programa se agrega a un puerto, se agrega al proceso que contiene el programa que este nodo de programa representa.  
  
 En algún momento después de comenzar una sesión de depuración, dependiendo de la implementación del paquete de depuración, los nodos de programa se utilizan para crear programas correspondientes.  Cuando un proceso se consulta para los programas, los programas se enumeran, uno para cada nodo del programa.  
  
 Antes de que un programa se asocia a, el IDE sólo necesita una descripción ligera del programa.  Esta información se puede obtener del nodo del programa.  Una vez que el programa se adjunta a, el IDE necesita generar información más detallada, como una lista de todos los subprocesos que se ejecutan en el programa.  Esta información se obtiene del propio.  
  
## Vea también  
 [Programas](../../extensibility/debugger/programs.md)   
 [Procesos](../../extensibility/debugger/processes.md)   
 [Motor de depuración](../../extensibility/debugger/debug-engine.md)   
 [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)