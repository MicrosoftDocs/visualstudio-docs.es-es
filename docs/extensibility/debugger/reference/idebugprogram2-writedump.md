---
title: "IDebugProgram2::WriteDump | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2::WriteDump"
helpviewer_keywords: 
  - "IDebugProgram2::WriteDump"
ms.assetid: 375afb8c-882d-44db-bfa7-e2c9eb555122
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugProgram2::WriteDump
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Escribe un volcado en un archivo.  
  
## Sintaxis  
  
```cpp#  
HRESULT WriteDump(   
   DUMPTYPE  DumpType,  
   LPCOLESTR pszDumpUrl  
);  
```  
  
```c#  
int WriteDump(   
   enum_DUMPTYPE  DumpType,  
   string         pszDumpUrl  
);  
```  
  
#### Parámetros  
 `DumpType`  
 \[in\]  Un valor de enumeración de [DUMPTYPE](../../../extensibility/debugger/reference/dumptype.md) que especifica el tipo de volcado, por ejemplo, corto o long.  
  
 `pszDumpUrl`  
 \[in\]  La dirección URL para escribir el volcado en.  Normalmente, es en forma de `file://c: \ ruta \ filename.ext`, pero puede ser cualquier dirección URL válida.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Un volcado de memoria de programa incluiría normalmente el marco de pila actual, la pila propio, una lista de los subprocesos que se ejecutan en el programa, y posiblemente cualquier memoria que el programa posee.  
  
## Vea también  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)