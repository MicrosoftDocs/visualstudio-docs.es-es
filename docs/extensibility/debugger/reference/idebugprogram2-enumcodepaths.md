---
title: "IDebugProgram2::EnumCodePaths | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2::EnumCodePaths"
helpviewer_keywords: 
  - "IDebugProgram2::EnumCodePaths"
ms.assetid: fb100c3c-9c29-4d63-bd1f-a3e531cb395f
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgram2::EnumCodePaths
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Recupera una lista de las rutas de acceso del código para una posición determinada de un archivo de código fuente.  
  
## Sintaxis  
  
```cpp#  
HRESULT EnumCodePaths(   
   LPCOLESTR            pszHint,  
   IDebugCodeContext2*  pStart,  
   IDebugStackFrame2*   pFrame,  
   BOOL                 fSource,  
   IEnumCodePaths2**    ppEnum,  
   IDebugCodeContext2** ppSafety  
);  
```  
  
```c#  
int EnumCodePaths(   
   string                 pszHint,  
   IDebugCodeContext2     pStart,  
   IDebugStackFrame2      pFrame,  
   Int                    fSource,  
   out IEnumCodePaths2    ppEnum,  
   out IDebugCodeContext2 ppSafety  
);  
```  
  
#### Parámetros  
 `pszHint`  
 \[in\]  La palabra bajo el cursor de **código fuente** o las vistas de **Desensamblado** en el IDE.  
  
 `pStart`  
 \[in\]  Un objeto de [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) que representa el contexto actual del código.  
  
 `pFrame`  
 \[in\]  Un objeto de [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) que representa el marco de pila asociado al punto de interrupción actual.  
  
 `fSource`  
 \[in\]  Cero \(`TRUE`\) si en la vista de **código fuente** , o cero \(`FALSE`\) si en la vista de **Desensamblado** .  
  
 `ppEnum`  
 \[out\]  Devuelve un objeto de [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md) que contiene una lista de las rutas de acceso del código.  
  
 `ppSafety`  
 \[out\]  Devuelve un objeto de [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) que representa un contexto de código adicional que se establecerá como punto de interrupción en caso de que se omite la ruta de acceso de código elegida.  Esto puede ocurrir en el caso de una expresión booleana cortocircuitada, por ejemplo.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Una ruta de acceso de código describe el nombre de un método o función que se invoca para obtener el punto actual en la ejecución del programa.  una lista de rutas de acceso de código representa la pila de llamadas.  
  
## Vea también  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)