---
title: "Programas | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "depurar [SDK de depuración], programas"
  - "programas, depuración"
ms.assetid: e1f955d8-95da-493b-837e-e97741a26d7e
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Programas
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

En términos de arquitectura del depurador, **un programa**:  
  
-   Es un contenedor para un grupo de subprocesos y un conjunto de módulos.  un programa no tiene ninguna analogía en el sistema operativo Windows.  
  
     un programa es una clase de subproceso.  Por ejemplo, al depurar un sitio Web, un script puede considerarse como un programa.  Como un script se ejecuta en el proceso del motor de scripting, independientemente de otros scripts, también tiene su propio conjunto de subprocesos.  Un motor de depuración \(DE\) asocia un programa, y no a un proceso o un subproceso.  
  
-   Puede identificarse y el proceso que se está ejecutando en, y se puede asociar a, se desasoció de, y describir el OF que lo creó, si procede.  Un programa puede ejecutar, detener, continúa, y se finaliza.  
  
-   Puede mostrar todos los subprocesos.  Un programa puede proporcionar su propia secuencia de desensamblado, y puede enumerar todos los contextos de código de una posición determinada del documento.  
  
-   Se representa mediante una interfaz de [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) , creada antes de que se adjunte el programa, o como parte del proceso de asociación, dependiendo de la implementación.  Cuando un puerto enumera los programas de un proceso, cada programa se crea de acuerdo con una interfaz correspondiente de [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) pasa como argumento a [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md).  Mientras que los motores de depuración también crean las interfaces de `IDebugProgram2` para representar los programas, estos programas no se crean de acuerdo con un nodo de programa.  Las interfaces de `IDebugProgramNode2` creadas por un OF se utilizan para depuración real, mientras que los creados por un puerto se utilizan únicamente para detectar los programas se ejecutan en un proceso.  
  
## Vea también  
 [Procesos](../../extensibility/debugger/processes.md)   
 [Nodos de programa](../../extensibility/debugger/program-nodes.md)   
 [Módulos](../../extensibility/debugger/modules.md)   
 [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)   
 [Motor de depuración](../../extensibility/debugger/debug-engine.md)   
 [Posición del documento](../../extensibility/debugger/document-position.md)   
 [Contexto de código](../../extensibility/debugger/code-context.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)