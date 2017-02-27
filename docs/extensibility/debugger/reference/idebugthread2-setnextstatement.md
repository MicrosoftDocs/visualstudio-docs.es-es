---
title: "IDebugThread2::SetNextStatement | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugThread2::SetNextStatement"
helpviewer_keywords: 
  - "IDebugThread2::SetNextStatement"
ms.assetid: 9e2834dd-4ecf-45af-8e6c-f9318ebdac06
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugThread2::SetNextStatement
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Establece el puntero de instrucción actual al contexto determinado de código.  
  
## Sintaxis  
  
```cpp#  
HRESULT SetNextStatement (   
   IDebugStackFrame2*  pStackFrame,  
   IDebugCodeContext2* pCodeContext  
);  
```  
  
```c#  
int SetNextStatement (   
   IDebugStackFrame2  pStackFrame,  
   IDebugCodeContext2 pCodeContext  
);  
```  
  
#### Parámetros  
 `pStackFrame`  
 reservado para uso futuro; establezca en un valor nulo.  
  
 `pCodeContext`  
 \[in\]  Un objeto de [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) que describe la ubicación del código alrededor que se ejecutará y su contexto.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  la tabla siguiente muestra otros valores posibles.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|\_SET\_NEXT\_STATEMENT\_ON\_NONLEAF\_FRAME OF E\_CAN NO|La siguiente instrucción no puede estar en un marco de pila se encuentra más abajo en la pila del cuadro.|  
|\_SETIP\_TO\_DIFFERENT\_FUNCTION OF E\_CAN NO|La instrucción siguiente no está asociado a ningún marco en la pila.|  
|\_SET\_NEXT\_STATEMENT\_ON\_EXCEPTION OF E\_CAN NO|Algunos motores de depuración no pueden establecer la siguiente instrucción después de una excepción.|  
  
## Comentarios  
 el puntero de instrucción indica la instrucción o la instrucción siguiente de ejecutarse.  este método se utiliza para reintentar una línea de código fuente o para forzar la ejecución para continuar en otra función, por ejemplo.  
  
## Vea también  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)