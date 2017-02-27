---
title: "IDebugDisassemblyStream2::Seek | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDisassemblyStream2::Seek"
helpviewer_keywords: 
  - "IDebugDisassemblyStream2::Seek"
ms.assetid: afec3008-b1e0-4803-ad24-195dbfb6497e
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugDisassemblyStream2::Seek
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Mueve el puntero de lectura en el desensamblado transmite un número especificado de instrucciones en relación con una posición especificada.  
  
## Sintaxis  
  
```cpp#  
HRESULT Seek(   
   SEEK_START          dwSeekStart,  
   IDebugCodeContext2* pCodeContext,  
   UINT64              uCodeLocationId,  
   INT64               iInstructions  
);  
```  
  
```c#  
int Seek(   
   enum_SEEK_START    dwSeekStart,  
   IDebugCodeContext2 pCodeContext,  
   ulong              uCodeLocationId,  
   long               iInstructions  
);  
```  
  
#### Parámetros  
 `dwSeekStart`  
 \[in\]  Un valor de enumeración de [SEEK\_START](../../../extensibility/debugger/reference/seek-start.md) que especifica la posición relativa para iniciar el proceso de búsqueda.  
  
 `pCodeContext`  
 \[in\]  El objeto de [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) que representa el contexto del código que la operación de búsqueda es relativo.  Se utiliza este parámetro únicamente si `dwSeekStart` \= `SEEK_START_CODECONTEXT`; si no, este parámetro se omite y puede ser un valor NULL.  
  
 `uCodeLocationId`  
 \[in\]  El identificador de la ubicación del código que la operación de búsqueda es relativo.  se utiliza este parámetro si `dwSeekStart` \= `SEEK_START_CODELOCID`; si no, este parámetro se omite y se puede establecer en 0.  Vea la sección comentarios para el método de [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md) para obtener una descripción de un identificador de la ubicación del código.  
  
 `iInstructions`  
 \[in\]  El número de instrucciones de desplazarse en relación con la posición especificada en `dwSeekStart`.  Este valor puede ser negativo desplazarse hacia atrás.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`.  Devuelve `S_FALSE` si la posición de la búsqueda se realizó un punto más allá de la lista de instrucciones disponibles.  De lo contrario, devuelve un código de error.  
  
## Comentarios  
 Si la búsqueda se a una posición antes de que el principio de la lista, la posición de lectura está establecida en la primera instrucción en la lista.  Si el considerar estaba a una posición después del final de la lista, la posición de la lectura se establezca en la última instrucción de la lista.  
  
## Vea también  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [SEEK\_START](../../../extensibility/debugger/reference/seek-start.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)