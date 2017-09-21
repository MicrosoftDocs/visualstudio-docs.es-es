---
title: "IDebugDisassemblyStream2::Read | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDisassemblyStream2::Read"
helpviewer_keywords: 
  - "IDebugDisassemblyStream2::Read"
ms.assetid: 7db5f6bb-73ee-45bc-b187-c1b6aa2dfdd5
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugDisassemblyStream2::Read
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Lee instrucciones a partir de la posición actual en la secuencia de desensamblado.  
  
## Sintaxis  
  
```cpp#  
HRESULT Read(   
   DWORD                     dwInstructions,  
   DISASSEMBLY_STREAM_FIELDS dwFields,  
   DWORD*                    pdwInstructionsRead,  
   DisassemblyData*          prgDisassembly  
);  
```  
  
```c#  
int Read(   
   uint                           dwInstructions,  
   enum_DISASSEMBLY_STREAM_FIELDS dwFields,  
   out uint                       pdwInstructionsRead,  
   DisassemblyData[]              prgDisassembly  
);  
```  
  
#### Parámetros  
 `dwInstructions`  
 \[in\]  el número de instrucciones de desensamblar.  Este valor también es la longitud máxima de la matriz de `prgDisassembly` .  
  
 `dwFields`  
 \[in\]  Una combinación de marcadores de enumeración de [DISASSEMBLY\_STREAM\_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md) que indican qué campos de `prgDisassembly` se deben completar.  
  
 `pdwInstructionsRead`  
 \[out\]  devuelve el número de instrucciones desensambladas realmente.  
  
 `prgDisassembly`  
 \[out\]  Una matriz de estructuras de [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) se completa con el código desensamblado, una estructura por la instrucción desensamblada.  La longitud de esta matriz es dictada por el parámetro de `dwInstructions` .  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 El número máximo de instrucciones que están disponibles en el ámbito actual se puede obtener llamando al método de [GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md) .  
  
 La posición actual en la instrucción siguiente se lee de puede cambiar llamando al método de [Buscar](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md) .  
  
 El indicador de `DSF_OPERANDS_SYMBOLS` se puede agregar al marcador de `DSF_OPERANDS` en el parámetro de `dwFields` para indicar que los nombres de símbolo deben utilizar el desensamblar instrucciones.  
  
## Vea también  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [DISASSEMBLY\_STREAM\_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)   
 [GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)   
 [Buscar](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)